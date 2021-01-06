---
title: Hata ayıklama StackOverflow hataları
description: StackOverflow özel durumlarını tanılamayı öğrenin
ms.topic: tutorial
ms.date: 12/22/2020
ms.openlocfilehash: 92edf854ddcc2e778949d74eff1370cf27db25b4
ms.sourcegitcommit: c0b803bffaf101e12f071faf94ca21b46d04ff30
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/24/2020
ms.locfileid: "97764935"
---
# <a name="debugging-stackoverflow-errors"></a>Hata ayıklama StackOverflow hataları

<xref:System.StackOverflowException>Çok fazla iç içe geçmiş yöntem çağrısı içerdiğinden, yürütme yığını taştığında bir oluşturulur.  

Örneğin, aşağıdaki gibi bir uygulamanız olduğunu varsayalım:

````
using System;

namespace temp
{
    class Program
    {
        static void Main(string[] args)
        {
            Main(args); // oops this recursion won't stop
        }
    }
}
````

Daha fazla yığın alanı olmadığından Main yöntemi sürekli olarak kendisini çağırır.  Daha fazla yığın alanı yoksa, yürütme devam edemez ve bir oluşturur <xref:System.StackOverflowException> .  

````
> dotnet run
Stack overflow.
````

> [!NOTE]
> .NET 5 ve sonraki sürümlerde, çağrı yığını konsola çıktıdır.

> [!NOTE]
> Bu makalede lldb ile bir yığın taşmasından nasıl hata ayıklaması yapılacağı açıklanır. Windows üzerinde çalıştırıyorsanız, [Visual Studio](/visualstudio/debugger/what-is-debugging) veya [Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)ile uygulamada hata ayıklamayı öneririz.  

## <a name="example"></a>Örnek

1. Uygulamayı çökmeyle ilgili döküm toplamak üzere yapılandırılmış şekilde Çalıştır

    ````
    > export COMPlus_DbgEnableMiniDump=1
    > dotnet run
    Stack overflow.
    Writing minidump with heap to file /tmp/coredump.6412
    Written 58191872 bytes (14207 pages) to core file
    ````

2. [DotNet-sos](dotnet-sos.md) kullanarak SOS uzantısını yükler

    ````
    dotnet-sos install
    ````

3. Başarısız yığını görmek için lldb 'de dökümde hata ayıklayın

    ````
    lldb --core /temp/coredump.6412
    (lldb) bt
    ...
        frame #261930: 0x00007f59b40900cc
        frame #261931: 0x00007f59b40900cc
        frame #261932: 0x00007f59b40900cc
        frame #261933: 0x00007f59b40900cc
        frame #261934: 0x00007f59b40900cc
        frame #261935: 0x00007f5a2d4a080f libcoreclr.so`CallDescrWorkerInternal at unixasmmacrosamd64.inc:867
        frame #261936: 0x00007f5a2d3cc4c3 libcoreclr.so`MethodDescCallSite::CallTargetWorker(unsigned long const*, unsigned long*, int) at callhelpers.cpp:70
        frame #261937: 0x00007f5a2d3cc468 libcoreclr.so`MethodDescCallSite::CallTargetWorker(this=<unavailable>, pArguments=0x00007ffe8222e7b0, pReturnValue=0x0000000000000000, cbReturnValue=0) at callhelpers.cpp:604
        frame #261938: 0x00007f5a2d4b6182 libcoreclr.so`RunMain(MethodDesc*, short, int*, PtrArray**) [inlined] MethodDescCallSite::Call(this=<unavailable>, pArguments=<unavailable>) at callhelpers.h:468
    ...
    ````

4. En üstteki çerçeve `0x00007f59b40900cc` birkaç kez yinelenir. [](sos-debugging-extension.md) `ip2md` Adreste hangi yöntemin olduğunu anlamak için sos komutunu kullanın `0x00007f59b40900cc`

    ````
    (lldb) ip2md 0x00007f59b40900cc
    MethodDesc:   00007f59b413ffa8
    Method Name:          temp.Program.Main(System.String[])
    Class:                00007f59b4181d40
    MethodTable:          00007f59b4190020
    mdToken:              0000000006000001
    Module:               00007f59b413dbf8
    IsJitted:             yes
    Current CodeAddr:     00007f59b40900a0
    Version History:
      ILCodeVersion:      0000000000000000
      ReJIT ID:           0
      IL Addr:            0000000000000000
         CodeAddr:           00007f59b40900a0  (MinOptJitted)
         NativeCodeVersion:  0000000000000000
    Source file:  /temp/Program.cs @ 9
    ````

5. Belirtilen yöntem geçici bölümüne bakın. Size yanlış olduğunu anlamak için program. Main (System. String []) ve Source "/temp/Program.cs @ 9". Hala temizlemediği takdirde kodun bu alanına günlük ekleyebilirsiniz.

## <a name="see-also"></a>Ayrıca Bkz.

* [.NET 'teki döküme giriş](dumps.md)
* [Linux dökümlerinin hatasını ayıklama](debug-linux-dumps.md)
* [.NET için SOS hata ayıklama uzantısı](sos-debugging-extension.md)
