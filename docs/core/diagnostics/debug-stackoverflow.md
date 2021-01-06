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
# <a name="debugging-stackoverflow-errors"></a><span data-ttu-id="3e156-103">Hata ayıklama StackOverflow hataları</span><span class="sxs-lookup"><span data-stu-id="3e156-103">Debugging StackOverflow errors</span></span>

<span data-ttu-id="3e156-104"><xref:System.StackOverflowException>Çok fazla iç içe geçmiş yöntem çağrısı içerdiğinden, yürütme yığını taştığında bir oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3e156-104">A <xref:System.StackOverflowException> is thrown when when the execution stack overflows because it contains too many nested method calls.</span></span>  

<span data-ttu-id="3e156-105">Örneğin, aşağıdaki gibi bir uygulamanız olduğunu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="3e156-105">For example, suppose you have an app as follows:</span></span>

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

<span data-ttu-id="3e156-106">Daha fazla yığın alanı olmadığından Main yöntemi sürekli olarak kendisini çağırır.</span><span class="sxs-lookup"><span data-stu-id="3e156-106">The Main method will continuously call itself until there is no more stack space.</span></span>  <span data-ttu-id="3e156-107">Daha fazla yığın alanı yoksa, yürütme devam edemez ve bir oluşturur <xref:System.StackOverflowException> .</span><span class="sxs-lookup"><span data-stu-id="3e156-107">Once there is no more stack space, execution cannot continue and so it will throw a <xref:System.StackOverflowException>.</span></span>  

````
> dotnet run
Stack overflow.
````

> [!NOTE]
> <span data-ttu-id="3e156-108">.NET 5 ve sonraki sürümlerde, çağrı yığını konsola çıktıdır.</span><span class="sxs-lookup"><span data-stu-id="3e156-108">On .NET 5 and later, the callstack is output to the console.</span></span>

> [!NOTE]
> <span data-ttu-id="3e156-109">Bu makalede lldb ile bir yığın taşmasından nasıl hata ayıklaması yapılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="3e156-109">This article describes how to debug a stack overflow with lldb.</span></span> <span data-ttu-id="3e156-110">Windows üzerinde çalıştırıyorsanız, [Visual Studio](/visualstudio/debugger/what-is-debugging) veya [Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)ile uygulamada hata ayıklamayı öneririz.</span><span class="sxs-lookup"><span data-stu-id="3e156-110">If you are running on Windows, we suggest debugging the app with [Visual Studio](/visualstudio/debugger/what-is-debugging) or [Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging).</span></span>  

## <a name="example"></a><span data-ttu-id="3e156-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="3e156-111">Example</span></span>

1. <span data-ttu-id="3e156-112">Uygulamayı çökmeyle ilgili döküm toplamak üzere yapılandırılmış şekilde Çalıştır</span><span class="sxs-lookup"><span data-stu-id="3e156-112">Run the app with it configured to collect a dump on crash</span></span>

    ````
    > export COMPlus_DbgEnableMiniDump=1
    > dotnet run
    Stack overflow.
    Writing minidump with heap to file /tmp/coredump.6412
    Written 58191872 bytes (14207 pages) to core file
    ````

2. <span data-ttu-id="3e156-113">[DotNet-sos](dotnet-sos.md) kullanarak SOS uzantısını yükler</span><span class="sxs-lookup"><span data-stu-id="3e156-113">Install the SOS extension using [dotnet-sos](dotnet-sos.md)</span></span>

    ````
    dotnet-sos install
    ````

3. <span data-ttu-id="3e156-114">Başarısız yığını görmek için lldb 'de dökümde hata ayıklayın</span><span class="sxs-lookup"><span data-stu-id="3e156-114">Debug the dump in lldb to see the failing stack</span></span>

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

4. <span data-ttu-id="3e156-115">En üstteki çerçeve `0x00007f59b40900cc` birkaç kez yinelenir.</span><span class="sxs-lookup"><span data-stu-id="3e156-115">The top frame `0x00007f59b40900cc` is repeated several times.</span></span> <span data-ttu-id="3e156-116">[](sos-debugging-extension.md) `ip2md` Adreste hangi yöntemin olduğunu anlamak için sos komutunu kullanın `0x00007f59b40900cc`</span><span class="sxs-lookup"><span data-stu-id="3e156-116">Use the [SOS](sos-debugging-extension.md) `ip2md` command to figure out what method is located at the `0x00007f59b40900cc` address</span></span>

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

5. <span data-ttu-id="3e156-117">Belirtilen yöntem geçici bölümüne bakın. Size yanlış olduğunu anlamak için program. Main (System. String []) ve Source "/temp/Program.cs @ 9".</span><span class="sxs-lookup"><span data-stu-id="3e156-117">Go look at the indicated method temp.Program.Main(System.String[]) and source "/temp/Program.cs @ 9" to see if you can figure out what you did wrong.</span></span> <span data-ttu-id="3e156-118">Hala temizlemediği takdirde kodun bu alanına günlük ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e156-118">If it still wasn't clear you could add logging in that area of the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="3e156-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3e156-119">See Also</span></span>

* [<span data-ttu-id="3e156-120">.NET 'teki döküme giriş</span><span class="sxs-lookup"><span data-stu-id="3e156-120">An introduction to dumps in .NET</span></span>](dumps.md)
* [<span data-ttu-id="3e156-121">Linux dökümlerinin hatasını ayıklama</span><span class="sxs-lookup"><span data-stu-id="3e156-121">Debug Linux dumps</span></span>](debug-linux-dumps.md)
* [<span data-ttu-id="3e156-122">.NET için SOS hata ayıklama uzantısı</span><span class="sxs-lookup"><span data-stu-id="3e156-122">SOS Debugging Extension for .NET</span></span>](sos-debugging-extension.md)
