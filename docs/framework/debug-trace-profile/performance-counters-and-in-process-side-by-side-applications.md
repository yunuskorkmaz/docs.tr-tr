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
ms.openlocfilehash: 5cc3951c65a0be37294324c767a00bc7a35634b8
ms.sourcegitcommit: 78eb25647b0c750cd80354ebd6ce83a60668e22c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2021
ms.locfileid: "99065044"
---
# <a name="performance-counters-and-in-process-side-by-side-applications"></a>Performans Sayaçları ve Devam Eden Yan Yana Uygulamalar

Performans Izleyicisi 'ni (Perfmon.exe) kullanarak, performans sayaçlarını çalışma zamanına göre ayırmak mümkündür. Bu konuda, bu işlevi etkinleştirmek için gereken kayıt defteri değişikliği açıklanmaktadır.  
  
## <a name="the-default-behavior"></a>Varsayılan davranış  

 Varsayılan olarak performans Izleyicisi, performans sayaçlarını uygulama başına temelinde görüntüler. Bununla birlikte, bunun sorunlu olduğu iki senaryo vardır:  
  
- Aynı ada sahip iki uygulamayı izlerken. Örneğin, her iki uygulama da myapp.exe adlandırılmışsa, birisi **MyApp** olarak ve diğeri ise **örnek** sütununda **MyApp # 1** olarak görüntülenir. Bu durumda, bir performans sayacını belirli bir uygulamayla eşleştirmek zordur. **MyApp # 1** için toplanan verilerin ilk myapp.exe mı yoksa ikinci myapp.exe mı başvurduğu yok net değildir.  
  
- Bir uygulama ortak dil çalışma zamanının birden çok örneğini kullandığında. .NET Framework 4, işlem içi yan yana barındırma senaryolarını destekler; diğer bir deyişle, tek bir işlem veya uygulama ortak dil çalışma zamanının birden çok örneğini yükleyebilir. myapp.exe adlı tek bir uygulama iki çalışma zamanı örneği yüklerse varsayılan olarak **MyApp** ve **MyApp # 1** olarak **örnek** sütununda atanır. Bu durumda, **MyApp** ve **MyApp # 1** ' in aynı ada sahip iki uygulamayı ya da iki çalışma alanıyla aynı uygulamayı ifade etmeksizin net değildir. Aynı ada sahip birden çok uygulama birden fazla çalışma zamanı yüklese, belirsizlik daha da büyüktür.  
  
 Bu belirsizliği ortadan kaldırmak için bir kayıt defteri anahtarı ayarlayabilirsiniz. .NET Framework 4 kullanılarak geliştirilen uygulamalar için, bu kayıt defteri değişikliği bir işlem tanımlayıcısı ve ardından bir çalışma zamanı örneği tanımlayıcısı, **örnek** sütunundaki uygulama adına eklenir. *Uygulama veya* *uygulama*#1 yerine, uygulama artık örnek sütununda *Application* _ `p` *ProcessId* \_ `r` *runtimeId*  olarak tanımlanır. Bir uygulama, ortak dil çalışma zamanının önceki bir sürümü kullanılarak geliştirilmişse, bu örnek .NET Framework 4 ' ün yüklü olduğu *uygulama \_* `p` *işlem kimliği* olarak gösterilir.  
  
## <a name="performance-counters-for-in-process-side-by-side-applications"></a>Yan yana uygulamalar In-Process için performans sayaçları  

 Tek bir uygulamada barındırılan birden çok ortak dil çalışma zamanı sürümü için performans sayaçlarını işlemek üzere, aşağıdaki tabloda gösterildiği gibi tek bir kayıt defteri anahtarı ayarını değiştirmeniz gerekir.  
  
|||  
|-|-|  
|Anahtar adı|HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\ . NETFramework\Performance|  
|Değer adı|ProcessNameFormat|  
|Değer türü|REG_DWORD|  
|Değer|2 (0x00000002)|
  
 İçin 0 değeri, `ProcessNameFormat` varsayılan davranışın etkin olduğunu gösterir; yani Perfmon.exe performans sayaçlarını uygulama başına temelinde görüntüler. Bu değeri 2 olarak belirlediğinizde, bir uygulamanın birden çok sürümünü ayırt Perfmon.exe ve çalışma zamanı başına performans sayaçlarını sağlar. `ProcessNameFormat`Kayıt defteri anahtarı ayarı için başka bir değer desteklenmez ve gelecekte kullanılmak üzere ayrılmıştır.
  
 `ProcessNameFormat`Kayıt defteri anahtarı ayarını güncelleştirdikten sonra yeni örnek adlandırma özelliğinin düzgün çalışması için Perfmon.exe veya bazı performans sayacı tüketicilerini yeniden başlatmanız gerekir.  
  
 Aşağıdaki örnek, `ProcessNameFormat` programlı olarak değerin nasıl değiştirileceğini gösterir.  
  
 [!code-csharp[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/cs/regsetting1.cs#1)]
 [!code-vb[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/vb/regsetting1.vb#1)]  
  
 Bu kayıt defteri değişikliğini yaptığınızda ve .NET Framework 4 veya üzeri bir sürüm yüklüyse, *Perfmon.exe uygulamanın adlarını Application _* `p` *procesadı* olarak görüntüler; burada *uygulama* uygulamanın adıdır ve *İşlemKimliği* uygulamanın işlem tanımlayıcısıdır. Örneğin, myapp.exe adlı bir uygulama ortak dil çalışma zamanının iki örneğini yüklerse, Perfmon.exe bir örneği myapp_1416 ve ikincisi myapp_3160 olarak tanımlayabilir.
  
> [!NOTE]
> İşlem tanımlayıcısı, çalışma zamanının önceki sürümlerini kullanan aynı ada sahip iki uygulamanın çözümlenme belirsizliğin ortadan kaldırır. Ortak dil çalışma zamanının önceki sürümleri yan yana senaryoları desteklemediğinden, önceki sürümler için bir çalışma zamanı tanımlayıcısı gerekli değildir.  
  
 .NET Framework 4 veya sonraki bir sürüm yoksa veya kaldırılmışsa, kayıt defteri anahtarının ayarlanması etkisizdir. Bu, aynı ada sahip iki uygulamanın *uygulama* ve *1. uygulama* olarak Perfmon.exe (örneğin, **MyApp** ve **MyApp # 1** olarak) görünmeye devam edemeyeceği anlamına gelir.
