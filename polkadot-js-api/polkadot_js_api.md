## Note: Extrinsic == Hoạt động

# Khởi tạo

```
import { ApiPromise, WsProvider } from "@polkadot/api";

const wsProvider = new WsProvider("wss://rpc.shibuya.astar.network");
const api = await ApiPromise.create({ provider: wsProvider });
```

# Màn 6:

Dùng curl

# Màn 5:

```
const blockHash = await api.rpc.chain.getBlockHash(blockNumber);
const signedBlock = await api.rpc.chain.getBlock(blockHash);

// Hash của block
console.log(signedBlock.block.header.hash.toHex());

// Hash của block đằng trước
console.log(signedBlock.toHuman().block.header.parentHash);

// Hash của mỗi hoạt động trong block
signedBlock.block.extrinsics.forEach((ex, index) => {
  console.log(index, ex.hash.toHex());
});

// Thông tin của mỗi hoạt động trong block
signedBlock.block.extrinsics.forEach((ex, index) => {
  console.log(index, ex.toHuman());
  const { isSigned, meta, method: { args, method, section } } = ex;
  if (isSigned) {
    console.log(`signer=${ex.signer.toString()}, nonce=${ex.nonce.toString()}`);
  }
```

[Xem thêm](https://polkadot.js.org/docs/api/cookbook/blocks)
# Màn 1

"Lắng nghe" và liên tục nhận về thông tin của các block mới nhất:
```
await api.rpc.chain.subscribeNewHeads((lastHeader) => {
  console.log(`${chain}: last block #${lastHeader.number} has hash ${lastHeader.hash}`);
});
```

Tổng số khối == Sô thứ tự của block mới nhất

Các hoạt động gần đây == Các hoạt động có trong khối mới nhất

[Xem thêm](https://polkadot.js.org/docs/api/start/api.rpc)

# Màn 2

Danh sách các khối

# Màn 3

Danh sách các hoạt động


