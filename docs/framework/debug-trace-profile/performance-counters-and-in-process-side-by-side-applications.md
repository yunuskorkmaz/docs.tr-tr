---
title: Performans Sayaçları ve Devam Eden Yan Yana Uygulamalar
description: .NET ' te performans sayaçlarını ve işlem içi yan yana uygulamaları inceleyin. Performans sayaçlarını çalışma zamanına göre ayırmak için Perfmon.exe kullanın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- performance counters
- performance counters,and in-process side-by-side applications
- performance,.NET Framework applications
- performance monitoring,counters
ms.assetid: 6888f9be-c65b-4b03-a07b-df7ebdee2436
ms.openlocfilehash: eb05d9f5f930420827c6b3d94ea0ed34f64464fd
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803865"
---
# <a name="performance-counters-and-in-process-side-by-side-applications"></a>Performans Sayaçları ve Devam Eden Yan Yana Uygulamalar
Performans Izleyicisi 'ni (Perfmon.exe) kullanarak, performans sayaçlarını çalışma zamanına göre ayırmak mümkündür. Bu konuda, bu işlevi etkinleştirmek için gereken kayıt defteri değişikliği açıklanmaktadır.  
  
## <a name="the-default-behavior"></a>Varsayılan davranış  
 Varsayılan olarak performans Izleyicisi, performans sayaçlarını uygulama başına temelinde görüntüler. Bununla birlikte, bunun sorunlu olduğu iki senaryo vardır:  
  
- Aynı ada sahip iki uygulamayı izlerken. Örneğin, her iki uygulama da myapp.exe adlandırılmışsa, birisi **MyApp** olarak ve diğeri ise **örnek** sütununda **MyApp # 1** olarak görüntülenir. Bu durumda, bir performans sayacını belirli bir uygulamayla eşleştirmek zordur. **MyApp # 1** için toplanan verilerin ilk myapp.exe mı yoksa ikinci myapp.exe mı başvurduğu yok net değildir.  
  
- Bir uygulama ortak dil çalışma zamanının birden çok örneğini kullandığında. .NET Framework 4, işlem içi yan yana barındırma senaryolarını destekler; diğer bir deyişle, tek bir işlem veya uygulama ortak dil çalışma zamanının birden çok örneğini yükleyebilir. myapp.exe adlı tek bir uygulama iki çalışma zamanı örneği yüklerse varsayılan olarak **MyApp** ve **MyApp # 1**olarak **örnek** sütununda atanır. Bu durumda, **MyApp** ve **MyApp # 1** ' in aynı ada sahip iki uygulamayı ya da iki çalışma alanıyla aynı uygulamayı ifade etmeksizin net değildir. Aynı ada sahip birden çok uygulama birden fazla çalışma zamanı yüklese, belirsizlik daha da büyüktür.  
  
 Bu belirsizliği ortadan kaldırmak için bir kayıt defteri anahtarı ayarlayabilirsiniz. .NET Framework 4 kullanılarak geliştirilen uygulamalar için, bu kayıt defteri değişikliği bir işlem tanımlayıcısı ve ardından bir çalışma zamanı örneği tanımlayıcısı, **örnek** sütunundaki uygulama adına eklenir. *Uygulama veya* *uygulama*#1 yerine, uygulama artık örnek sütununda *Application*_ `p` *ProcessId* \_ `r` *runtimeId* **Instance** olarak tanımlanır. Bir uygulama, ortak dil çalışma zamanının önceki bir sürümü kullanılarak geliştirilmişse, bu örnek .NET Framework 4 ' ün yüklü olduğu *uygulama \_ * `p` *işlem kimliği* olarak gösterilir.  
  
## <a name="performance-counters-for-in-process-side-by-side-applications"></a>Işlem Içi yan yana uygulamalar için performans sayaçları  
 Tek bir uygulamada barındırılan birden çok ortak dil çalışma zamanı sürümü için performans sayaçlarını işlemek üzere, aşağıdaki tabloda gösterildiği gibi tek bir kayıt defteri anahtarı ayarını değiştirmeniz gerekir.  
  
|||  
|-|-|  
|Anahtar adı|\System\CurrentControlSet\Services HKEY_LOCAL_MACHINE \\ . NETFramework\Performance|  
|Değer adı|ProcessNameFormat|  
|Değer türü|REG_DWORD|  
|Değer|1 (0x00000001)|  
  
 İçin 0 değeri, `ProcessNameFormat` varsayılan davranışın etkin olduğunu gösterir; yani Perfmon.exe performans sayaçlarını uygulama başına temelinde görüntüler. Bu değeri 1 olarak ayarlarsanız, bir uygulamanın birden çok sürümünü ayırt Perfmon.exe ve çalışma zamanı başına performans sayaçlarını sağlar. `ProcessNameFormat`Kayıt defteri anahtarı ayarı için başka bir değer desteklenmez ve gelecekte kullanılmak üzere ayrılmıştır.  
  
 `ProcessNameFormat`Kayıt defteri anahtarı ayarını güncelleştirdikten sonra yeni örnek adlandırma özelliğinin düzgün çalışması için Perfmon.exe veya bazı performans sayacı tüketicilerini yeniden başlatmanız gerekir.  
  
 Aşağıdaki örnek, `ProcessNameFormat` programlı olarak değerin nasıl değiştirileceğini gösterir.  
  
 [!code-csharp[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/cs/regsetting1.cs#1)]
 [!code-vb[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/vb/regsetting1.vb#1)]  
  
 Bu kayıt defteri değişikliğini yaparken Perfmon.exe, *uygulama _* işlemkimliği runtimeId olarak .NET Framework 4 ' ü hedefleyen uygulamaların adlarını görüntüler; `p` *processID* \_ `r` *runtimeID*burada *uygulama* uygulamanın adıdır, *İşlemKimliği* uygulamanın işlem tanımlayıcısıdır ve *runtimeId* ise ortak bir dil çalışma zamanı tanımlayıcısıdır. Örneğin, myapp.exe adlı bir uygulama ortak dil çalışma zamanının iki örneğini yüklerse, Perfmon.exe bir örneği myapp_p1416_r10 ve ikincisi myapp_p3160_r10 olarak tanımlayabilir. Çalışma zamanı tanımlayıcısı yalnızca bir işlemdeki çalışma zamanlarını belirsizlaştırır; çalışma zamanı hakkında başka herhangi bir bilgi sağlamaz. (Örneğin, çalışma zamanı KIMLIĞI, çalışma zamanının sürümü veya SKU 'SU ile ilişkili değildir.)  
  
 .NET Framework 4 yüklüyse, kayıt defteri değişikliği, .NET Framework önceki sürümleri kullanılarak geliştirilen uygulamaları da etkiler. Bunlar *application_* `p` , *uygulama* adı ve *İşlemKimliği* işlem tanıtıcısıdır application_*işlem kimliği*olarak Perfmon.exe görüntülenir. Örneğin, myapp.exe adlı iki uygulamanın performans sayaçları izleniyorsa, biri myapp_p23900 ve diğeri myapp_p24908 olarak görünebilir.  
  
> [!NOTE]
> İşlem tanımlayıcısı, çalışma zamanının önceki sürümlerini kullanan aynı ada sahip iki uygulamanın çözümlenme belirsizliğin ortadan kaldırır. Ortak dil çalışma zamanının önceki sürümleri yan yana senaryoları desteklemediğinden, önceki sürümler için bir çalışma zamanı tanımlayıcısı gerekli değildir.  
  
 .NET Framework 4 yoksa veya kaldırılmışsa, kayıt defteri anahtarının ayarlanması etkisizdir. Bu, aynı ada sahip iki uygulamanın *uygulama* ve *1. uygulama* olarak Perfmon.exe (örneğin, **MyApp** ve **MyApp # 1**olarak) görünmeye devam edemeyeceği anlamına gelir.
