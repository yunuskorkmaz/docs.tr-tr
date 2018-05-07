---
title: Performans Sayaçları ve Devam Eden Yan Yana Uygulamalar
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf8a5a7c97969fb0018bb1dba4ea027fe7afd2c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="performance-counters-and-in-process-side-by-side-applications"></a>Performans Sayaçları ve Devam Eden Yan Yana Uygulamalar
Performans İzleyicisi'ni (Perfmon.exe) kullanarak, çalışma zamanı başına temelinde performans sayaçları ayırt etmek mümkün değildir. Bu konu, bu işlevselliği etkinleştirmek için gerekli kayıt defteri değişikliği açıklar.  
  
## <a name="the-default-behavior"></a>Varsayılan davranış  
 Varsayılan olarak, uygulama başına temelinde performans sayaçlarını Performans İzleyicisi'ni görüntüler. Ancak, bu sorunlu olan iki senaryo vardır:  
  
-   Ne zaman aynı ada sahip iki uygulamalarını izleyin. Her iki uygulamayı myapp.exe olarak adlandırılmışsa, örneğin, olarak görüntülenir **Uygulamam** ve diğer olarak **Uygulamam #1** içinde **örneği** sütun. Bu durumda, belirli bir uygulama için bir performans sayacı eşleşecek şekilde zordur. İçin toplanan veriler olup NET değil **Uygulamam #1** ilk myapp.exe veya ikinci myapp.exe anlamına gelir.  
  
-   Ne zaman bir uygulama, ortak dil çalışma zamanı birden çok örneğini kullanır. [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] Destekler işlem içi yan yana barındırma senaryolarını; diğer bir deyişle, tek bir işlem veya uygulama ortak dil çalışma zamanı birden çok örneğini yükleyebilirsiniz. Tek bir uygulama myapp.exe yükleri iki çalışma zamanı örnekleri, varsayılan olarak adlandırılan, bunlar içinde atanır **örneği** sütun olarak **Uygulamam** ve **Uygulamam #1**. Bu durumda, NET değil olup olmadığını **Uygulamam** ve **Uygulamam #1** aynı ada sahip iki uygulama ya da iki çalışma zamanları ile aynı uygulamanın. Birden çok uygulama aynı ada sahip birden çok çalışma zamanları yüklerseniz karışıklık bile daha büyük.  
  
 Bu belirsizliği ortadan kaldırmak için bir kayıt defteri anahtarı ayarlayabilirsiniz. Kullanılarak geliştirilen uygulamaları için [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], bu kayıt defteri değişikliği uygulama adı için bir çalışma zamanı örneği tanımlayıcısı tarafından izlenen bir işlem tanımlayıcısı ekler **örneği** sütun. Yerine *uygulama* veya *uygulama*#1, uygulama artık tanımlanmıştır *uygulama*_`p`*ProcessId* \_ `r` *runtimeID* içinde **örneği** sütun. Ortak dil çalışma zamanı önceki bir sürümünü kullanarak bir uygulama geliştirilmiştir, bu örneği olarak temsil edilir *uygulama\_*`p`*ProcessId* koşuluyla [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] yüklenir.  
  
## <a name="performance-counters-for-in-process-side-by-side-applications"></a>İşlem içi yan yana uygulamalar için performans sayaçları  
 Tek bir uygulama içinde barındırılan birden çok ortak dil çalışma zamanı sürümü için performans sayaçları işlemek için aşağıdaki tabloda gösterildiği gibi bir tek kayıt defteri anahtarı ayarı değiştirmeniz gerekir.  
  
|||  
|-|-|  
|Anahtar adı|HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\. NETFramework\Performance|  
|Değer adı|Eklemek|  
|Değer türü|REG_DWORD|  
|Değer|1 (0x00000001)|  
  
 İçin 0 değerini `ProcessNameFormat` varsayılan davranışı; olan etkin, Perfmon.exe bir uygulama başına temelinde performans sayaçlarını görüntüler gösterir. Bu değer 1 olarak ayarlayın, Perfmon.exe bir uygulama birden fazla sürümünü açıklar ve bir çalışma zamanı başına temelinde performans sayaçlarını sağlar. Başka bir değer için `ProcessNameFormat` kayıt defteri anahtarı ayarı desteklenmeyen ve gelecekte kullanılmak üzere ayrılmış.  
  
 Güncelleştirdikten sonra `ProcessNameFormat` kayıt defteri anahtarı böylece yeni örneğini adlandırma özelliği düzgün çalıştığını ayarı Perfmon.exe veya herhangi bir tüketiciye performans sayaçları yeniden başlatmanız gerekir.  
  
 Aşağıdaki örnekte nasıl değiştirileceğini gösterir `ProcessNameFormat` program aracılığıyla değeri.  
  
 [!code-csharp[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/cs/regsetting1.cs#1)]
 [!code-vb[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/vb/regsetting1.vb#1)]  
  
 Bu kayıt defteri değişikliğini yaptığınızda, Perfmon.exe uygulamaları adlarını hedefleyen görüntüler. [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] olarak *uygulama*_`p`*ProcessId* \_ `r` *runtimeID*, burada *uygulama* uygulama adı *ProcessId* uygulamanın işlem tanımlayıcısı ve  *runtimeID* bir ortak dil çalışma zamanı tanımlayıcısı. Örneğin, bir uygulama ortak dil çalışma zamanı iki örneğini myapp.exe yükleri adlandırırsanız Perfmon.exe bir örneği olarak myapp_p1416_r10 ve ikinci myapp_p3160_r10 olarak tanımlayabilir. Çalışma zamanı tanımlayıcı yalnızca bir işlem içinde çalışma zamanları açıklar; çalışma zamanı hakkında herhangi bir bilgi sağlamaz. (Örneğin, çalışma zamanı kimliği sürümü veya SKU çalışma zamanının hiçbir ilişki yoktur.)  
  
 Varsa [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] olan yüklü, kayıt defteri değişikliği de .NET Framework'ün önceki sürümleri kullanılarak geliştirilen uygulamaları etkiler. Bunlar Perfmon.exe görünür *application_*`p`*ProcessId*, burada *uygulama* uygulama adı ve *ProcessId* işlem tanımlayıcısı. Performans sayaçları myapp.exe adlı iki uygulamalarının izleniyorsa, örneğin, bir myapp_p23900 diğeri de myapp_p24908 olarak görünebilir.  
  
> [!NOTE]
>  İşlem tanımlayıcısını çalışma zamanı'nın önceki sürümlerini kullanan iki uygulamalar aynı ada sahip çözümleme belirsizliği ortadan kaldırır. Ortak dil çalışma zamanı önceki sürümlerini yan yana senaryolarda desteklemediği için bir çalışma zamanı tanımlayıcı önceki sürümler için gerekli değildir.  
  
 Varsa [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] mevcut değil ya da kaldırılmış, kayıt defteri anahtarı ayarı hiçbir etkisi olmaz. Aynı ada sahip iki uygulama Perfmon.exe olarak görünmeye devam edecek yani *uygulama* ve *uygulama #1* (örneğin, **Uygulamam** ve **Uygulamam #1**).
