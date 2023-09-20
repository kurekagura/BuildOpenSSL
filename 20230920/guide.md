# ガイド

OpenSSL（OpenSSL_1_1_1w）のWindowsビルド（x64版）。MSYSなどは利用せず、VS2022のみでビルドできることを確認。

## 環境

「x64 Native Tools Command Prompt for VS 2022」を開き、環境の確認。

```console
>where perl & perl -v
O:\sw\Strawberry\perl\bin\perl.exe

This is perl 5, version 32, subversion 1 (v5.32.1) built for MSWin32-x64-multi-thread

>where nasm & nasm -v
C:\sw\NASM\nasm.exe
NASM version 2.15.05 compiled on Aug 28 2020

>where nmake cl
C:\Program Files\Microsoft Visual Studio\2022\Community\VC\Tools\MSVC\14.37.32822\bin\Hostx64\x64\nmake.exe
C:\Program Files\Microsoft Visual Studio\2022\Community\VC\Tools\MSVC\14.37.32822\bin\Hostx64\x64\cl.exe
```

## ビルド

タグから特定のバージョン（OpenSSL_1_1_1w）をビルドする。

```console
cd o:\src
git clone https://github.com/openssl/openssl.git
cd openssl
git checkout refs/tags/OpenSSL_1_1_1w

perl Configure VC-WIN64A

nmake

namke test

# 最後に以下のように表示された。
All tests successful.
Files=159, Tests=2565, 520 wallclock secs ( 1.62 usr +  0.17 sys =  1.80 CPU)
Result: PASS
```

## 参考

- [Notes for Windows platforms](https://github.com/openssl/openssl/blob/master/NOTES-WINDOWS.md)

    記載通りの手順で特にトラブルはありませんでした。
