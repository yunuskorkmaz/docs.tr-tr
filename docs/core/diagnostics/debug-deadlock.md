---
title: Hata ayıklama kilitlenmesi-.NET Core
description: .NET Core 'da kilitleme sorununu ayıklamada size kılavuzluk eden bir öğretici.
ms.topic: tutorial
ms.date: 07/20/2020
ms.openlocfilehash: 6f060e1ae801eb4eacbbd1fb67110f827c37f597
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557886"
---
# <a name="debug-a-deadlock-in-net-core"></a>.NET Core 'da kilitlenmeyle hata ayıklama

**Bu makale şu şekilde geçerlidir: ✔️** .net Core 3,1 SDK ve sonraki sürümleri

Bu öğreticide, bir kilitlenme senaryosunda hata ayıklamayı öğreneceksiniz. [Web uygulaması](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) kaynak kodu deposu ASP.NET Core sunulan örneği kullanarak, kasıtlı olarak bir kilitlenmeye neden olabilirsiniz. Uç nokta, askıda kalma ve iş parçacığı birikmesi ile karşılaşacaktır. Temel dökümler, temel döküm Analizi ve işlem izleme gibi sorunları çözümlemek için çeşitli araçları nasıl kullanabileceğinizi öğreneceksiniz.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
>
> - Uygulama askıda kalmasına araştırma
> - Temel döküm dosyası oluşturma
> - Döküm dosyasındaki işlem iş parçacıklarını çözümleyin
> - Çağrı yığınlarını ve eşitleme bloklarını çözümle
> - Bir kilitlenmesi tanılayın ve çözün

## <a name="prerequisites"></a>Ön koşullar

Öğretici şunları kullanır:

- [.NET Core 3,1 SDK](https://dotnet.microsoft.com/download/dotnet-core) veya sonraki bir sürümü
- [Örnek hata ayıklama hedefi-](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) senaryoyu tetiklemek için Web uygulaması
- [DotNet-](dotnet-trace.md) liste işlemlerine izleme
- [DotNet-](dotnet-dump.md) döküm dosyasını toplamak ve analiz etmek için döküm

## <a name="core-dump-generation"></a>Temel döküm oluşturma

Uygulamanın yanıt verme hızını araştırmak için, temel döküm veya bellek dökümü, iş parçacıklarının durumunu ve çekişme sorunları olabilecek olası kilitleri incelemenizi sağlar. Örnek kök dizininden aşağıdaki komutu kullanarak [örnek hata ayıklama](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) uygulamasını çalıştırın:

```dotnetcli
dotnet run
```

İşlem KIMLIĞINI bulmak için aşağıdaki komutu kullanın:

```dotnetcli
dotnet-trace ps
```

Komut çıktıınızdan işlem KIMLIĞI ' ni bir yere göz atın. İşlem KIMLIĞINIZ idi `4807` , ancak sizinki farklı olacak. Örnek sitede bir API uç noktası olan aşağıdaki URL 'ye gidin:

`https://localhost:5001/api/diagscenario/deadlock`

Siteye yönelik API isteği askıda kalır ve yanıt vermez. İsteğin yaklaşık 10-15 saniye çalışmasına izin verin. Ardından aşağıdaki komutu kullanarak çekirdek dökümünü oluşturun:

### <a name="linux"></a>[Linux](#tab/linux)

```bash
sudo dotnet-dump collect -p 4807
```

### <a name="windows"></a>[Windows](#tab/windows)

```console
dotnet-dump collect -p 4807
```

---

## <a name="analyze-the-core-dump"></a>Çekirdek dökümünü analiz etme

Temel döküm analizini başlatmak için aşağıdaki komutu kullanarak çekirdek dökümünü açın `dotnet-dump analyze` . Bağımsız değişkeni, daha önce toplanan temel döküm dosyasının yoludur.

```dotnetcli
dotnet-dump analyze  ~/.dotnet/tools/core_20190513_143916
```

Olası bir askıda kalma olduğunu bakıyorsunuzdur, işlemdeki iş parçacığı etkinliği için genel bir fikir istiyorsunuz. `threads`Komutunu aşağıda gösterildiği gibi kullanabilirsiniz:

```console
> threads
*0 0x1DBFF (121855)
 1 0x1DC01 (121857)
 2 0x1DC02 (121858)
 3 0x1DC03 (121859)
 4 0x1DC04 (121860)
 5 0x1DC05 (121861)
 6 0x1DC06 (121862)
 7 0x1DC07 (121863)
 8 0x1DC08 (121864)
 9 0x1DC09 (121865)
 10 0x1DC0A (121866)
 11 0x1DC0D (121869)
 12 0x1DC0E (121870)
 13 0x1DC10 (121872)
 14 0x1DC11 (121873)
 15 0x1DC12 (121874)
 16 0x1DC13 (121875)
 17 0x1DC14 (121876)
 18 0x1DC15 (121877)
 19 0x1DC1C (121884)
 20 0x1DC1D (121885)
 21 0x1DC1E (121886)
 22 0x1DC21 (121889)
 23 0x1DC22 (121890)
 24 0x1DC23 (121891)
 25 0x1DC24 (121892)
 26 0x1DC25 (121893)
...
...
 317 0x1DD48 (122184)
 318 0x1DD49 (122185)
 319 0x1DD4A (122186)
 320 0x1DD4B (122187)
 321 0x1DD4C (122188)
 ```

Çıktıda, ilişkili hata ayıklayıcı iş parçacığı KIMLIĞI ve işletim sistemi iş parçacığı KIMLIĞI ile işlemde çalışmakta olan tüm iş parçacıkları gösterilmektedir. Çıkışa göre 300 ' den fazla iş parçacığı vardır.

Bir sonraki adım, her iş parçacığının çağrı yığınını alarak iş parçacıklarının Şu anda neler yaptığını daha iyi anlayabilmektir. `clrstack`Komut, callyığınları çıkarmak için kullanılabilir. Tek bir çağrı yığını veya tüm çağrı yığınlarının çıktısını alabilir. İşlemdeki tüm iş parçacıkları için tüm çağrı yığınlarının çıkışını almak için aşağıdaki komutu kullanın:

```console
clrstack -all
```

Çıktının temsili bir kısmı şöyle görünür:

```console
  ...
  ...
  ...
        Child SP               IP Call Site
00007F2AE37B5680 00007f305abc6360 [GCFrame: 00007f2ae37b5680]
00007F2AE37B5770 00007f305abc6360 [GCFrame: 00007f2ae37b5770]
00007F2AE37B57D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae37b57d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE37B5920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE37B5950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE37B5CA0 00007f30593044af [GCFrame: 00007f2ae37b5ca0]
00007F2AE37B5D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae37b5d70]
OS Thread Id: 0x1dc82
        Child SP               IP Call Site
00007F2AE2FB4680 00007f305abc6360 [GCFrame: 00007f2ae2fb4680]
00007F2AE2FB4770 00007f305abc6360 [GCFrame: 00007f2ae2fb4770]
00007F2AE2FB47D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae2fb47d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE2FB4920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE2FB4950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE2FB4CA0 00007f30593044af [GCFrame: 00007f2ae2fb4ca0]
00007F2AE2FB4D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae2fb4d70]
OS Thread Id: 0x1dc83
        Child SP               IP Call Site
00007F2AE27B3680 00007f305abc6360 [GCFrame: 00007f2ae27b3680]
00007F2AE27B3770 00007f305abc6360 [GCFrame: 00007f2ae27b3770]
00007F2AE27B37D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae27b37d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE27B3920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE27B3950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE27B3CA0 00007f30593044af [GCFrame: 00007f2ae27b3ca0]
00007F2AE27B3D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae27b3d70]
OS Thread Id: 0x1dc84
        Child SP               IP Call Site
00007F2AE1FB2680 00007f305abc6360 [GCFrame: 00007f2ae1fb2680]
00007F2AE1FB2770 00007f305abc6360 [GCFrame: 00007f2ae1fb2770]
00007F2AE1FB27D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae1fb27d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE1FB2920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE1FB2950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE1FB2CA0 00007f30593044af [GCFrame: 00007f2ae1fb2ca0]
00007F2AE1FB2D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae1fb2d70]
OS Thread Id: 0x1dc85
        Child SP               IP Call Site
00007F2AE17B1680 00007f305abc6360 [GCFrame: 00007f2ae17b1680]
00007F2AE17B1770 00007f305abc6360 [GCFrame: 00007f2ae17b1770]
00007F2AE17B17D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae17b17d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE17B1920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE17B1950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE17B1CA0 00007f30593044af [GCFrame: 00007f2ae17b1ca0]
00007F2AE17B1D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae17b1d70]
OS Thread Id: 0x1dc86
        Child SP               IP Call Site
00007F2AE0FB0680 00007f305abc6360 [GCFrame: 00007f2ae0fb0680]
00007F2AE0FB0770 00007f305abc6360 [GCFrame: 00007f2ae0fb0770]
00007F2AE0FB07D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae0fb07d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE0FB0920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE0FB0950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE0FB0CA0 00007f30593044af [GCFrame: 00007f2ae0fb0ca0]
00007F2AE0FB0D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae0fb0d70]
OS Thread Id: 0x1dc87
        Child SP               IP Call Site
00007F2AE07AF680 00007f305abc6360 [GCFrame: 00007f2ae07af680]
00007F2AE07AF770 00007f305abc6360 [GCFrame: 00007f2ae07af770]
00007F2AE07AF7D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae07af7d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE07AF920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE07AF950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE07AFCA0 00007f30593044af [GCFrame: 00007f2ae07afca0]
00007F2AE07AFD70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae07afd70]
OS Thread Id: 0x1dc88
        Child SP               IP Call Site
00007F2ADFFAE680 00007f305abc6360 [GCFrame: 00007f2adffae680]
00007F2ADFFAE770 00007f305abc6360 [GCFrame: 00007f2adffae770]
00007F2ADFFAE7D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2adffae7d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2ADFFAE920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2ADFFAE950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2ADFFAECA0 00007f30593044af [GCFrame: 00007f2adffaeca0]
00007F2ADFFAED70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2adffaed70]
...
...
```

Tüm 300 + iş parçacıkları için çağrı yığınlarının gözlemlenme, iş parçacıklarının büyük çoğunluğunun ortak bir çağrı yığınını paylaştığı bir model gösterir:

```console
OS Thread Id: 0x1dc88
        Child SP               IP Call Site
00007F2ADFFAE680 00007f305abc6360 [GCFrame: 00007f2adffae680]
00007F2ADFFAE770 00007f305abc6360 [GCFrame: 00007f2adffae770]
00007F2ADFFAE7D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2adffae7d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2ADFFAE920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2ADFFAE950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2ADFFAECA0 00007f30593044af [GCFrame: 00007f2adffaeca0]
00007F2ADFFAED70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2adffaed70]
```

Çağrı yığını, isteğin, bir çağrısı yaptığı kilitlenme yönteemizdeki geldiğini gösteriyor gibi görünüyor `Monitor.ReliableEnter` . Bu yöntem, iş parçacıklarının bir izleyici kilidi girmeye çalışıyor olduğunu gösterir. Kilit kullanılabilirliğini bekliyor. Muhtemelen farklı bir iş parçacığı tarafından kilitlenmiş olabilir.

Sonraki adımda, hangi iş parçacığının gerçekten izleyici kilidini tuttuğıdır. İzleyiciler genellikle eşitleme bloğu tablosunda kilit bilgilerini depodıklarından, `syncblk` daha fazla bilgi almak için komutunu kullanabiliriz:

```console
> syncblk
Index         SyncBlock MonitorHeld Recursion Owning Thread Info          SyncBlock Owner
   43 00000246E51268B8          603         1 0000024B713F4E30 5634  28   00000249654b14c0 System.Object
   44 00000246E5126908            3         1 0000024B713F47E0 51d4  29   00000249654b14d8 System.Object
-----------------------------
Total           344
CCW             1
RCW             2
ComClassFactory 0
Free            0
```

İlgi **çekici ve** **sahip iş parçacığı bilgilerinin**iki ilginç sütunu. **Monitortutuldu** sütunu, bir iş parçacığı ve bekleme iş parçacığı sayısı tarafından bir izleyici kilidinin elde edilip edilmeyeceğini gösterir. **Sahip Iş parçacığı bilgileri** sütununda, şu anda izleyici kilidine sahip olan iş parçacığı gösterilir. İş parçacığı bilgisinde üç farklı alt sütun vardır. İkinci alt sütun, işletim sistemi iş parçacığı KIMLIĞINI gösterir.

Bu noktada, iki farklı iş parçacığını (0x5634 ve 0x51d4) bir izleyici kilidi tutabiliyoruz. Sonraki adım, bu iş parçacıklarının yaptığına göz atabilmenizdir. Kilidi sonsuza kadar sürekli olarak takılıp takıldıklarından emin olmamız gerekiyor. `setthread` `clrstack` Her iş parçacığının her birine geçiş yapmak ve çağrı yığınlarını göstermek için ve komutlarını kullanalım.

İlk iş parçacığına bakmak için `setthread` komutunu çalıştırın ve 0x5634 iş parçacığının dizinini bulun (dizinimiz 28 idi). Kilitlenme işlevi bir kilit almayı bekliyor, ancak kilidin zaten var. Kilitlenmeyle zaten tuttuğu kilidi bekliyor.

```console
> setthread 28
> clrstack
OS Thread Id: 0x5634 (28)
        Child SP               IP Call Site
0000004E46AFEAA8 00007fff43a5cbc4 [GCFrame: 0000004e46afeaa8]
0000004E46AFEC18 00007fff43a5cbc4 [GCFrame: 0000004e46afec18]
0000004E46AFEC68 00007fff43a5cbc4 [HelperMethodFrame_1OBJ: 0000004e46afec68] System.Threading.Monitor.Enter(System.Object)
0000004E46AFEDC0 00007FFE5EAF9C80 testwebapi.Controllers.DiagScenarioController.DeadlockFunc() [C:\Users\dapine\Downloads\Diagnostic_scenarios_sample_debug_target\Controllers\DiagnosticScenarios.cs @ 58]
0000004E46AFEE30 00007FFE5EAF9B8C testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_0() [C:\Users\dapine\Downloads\Diagnostic_scenarios_sample_debug_target\Controllers\DiagnosticScenarios.cs @ 26]
0000004E46AFEE80 00007FFEBB251A5B System.Threading.ThreadHelper.ThreadStart_Context(System.Object) [/_/src/System.Private.CoreLib/src/System/Threading/Thread.CoreCLR.cs @ 44]
0000004E46AFEEB0 00007FFE5EAEEEEC System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/_/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
0000004E46AFEF20 00007FFEBB234EAB System.Threading.ThreadHelper.ThreadStart() [/_/src/System.Private.CoreLib/src/System/Threading/Thread.CoreCLR.cs @ 93]
0000004E46AFF138 00007ffebdcc6b63 [GCFrame: 0000004e46aff138]
0000004E46AFF3A0 00007ffebdcc6b63 [DebuggerU2MCatchHandlerFrame: 0000004e46aff3a0]
```

İkinci iş parçacığı benzerdir. Ayrıca, sahip olduğu bir kilidi almaya çalışıyor. Tüm bekleyen 300 + iş parçacıkları büyük olasılıkla kilitlenmeye neden olan kilitleri da bekler.

## <a name="see-also"></a>Ayrıca bkz.

- [DotNet-](dotnet-trace.md) liste işlemlerine izleme
- [DotNet-](dotnet-counters.md) yönetilen bellek kullanımını denetlemek için sayaçlar
- [DotNet-](dotnet-dump.md) döküm dosyasını toplamak ve analiz etmek için döküm
- [DotNet/Diagnostics](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [.NET Core 'da kullanılabilen tanılama araçları](index.md)
