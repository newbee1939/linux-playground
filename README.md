# linux-playground

『[試して理解]Linuxのしくみ 増補改訂版』の実験コード（[linux-in-practice-2nd](https://github.com/satoru-takeuchi/linux-in-practice-2nd)）を動かす学習用環境。Mac 上に Lima で Ubuntu 20.04 の VM を立てる。

## なぜ Lima か

- Mac を汚さない。すべて VM 内に閉じ、`limactl delete` で消せる
- Docker はカーネル共有のため、cgroup・perf・KVM などの実験ができない
- 本書の推奨は x86_64 だが、エミュレーションは遅く性能計測に向かないため arm64 で代用する

## 環境構築

```console
$ brew install lima
$ limactl start --name=lip ./lima.yaml
$ limactl shell lip
$ cd ~/linux-in-practice-2nd
```

- 本書のコードは VM 内の `~/linux-in-practice-2nd` に clone される
- このリポジトリは VM 内の同じパスに書き込み可能でマウントされる

## 片付け

```console
$ limactl delete -f lip
```
