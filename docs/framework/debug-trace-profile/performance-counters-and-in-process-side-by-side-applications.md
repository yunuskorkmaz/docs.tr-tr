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
ms.openlocfilehash: dd3501bc74da2c9a812f9c4816b5a081b3780cd0
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490037"
---
# <a name="performance-counters-and-in-process-side-by-side-applications"></a>Performans Sayaçları ve Devam Eden Yan Yana Uygulamalar
Performans İzleyicisi'ni (Perfmon.exe) kullanarak, çalışma zamanı başına temelinde performans sayaçları ayırmak mümkündür. Bu konu, bu özelliği etkinleştirmek için gerekli kayıt defteri değişikliği açıklar.  
  
## <a name="the-default-behavior"></a>Varsayılan davranış  
 Varsayılan olarak, uygulama başına temelinde performans sayaçlarını Performans İzleyicisi'ni görüntüler. Ancak, bu sorunlu olduğu iki senaryo vardır:  
  
- Ne zaman aynı ada sahip iki uygulamaları izleyin. Her iki uygulamayı myapp.exe olarak adlandırılmışsa, örneğin, biri olarak görüntülenir **myapp** ve diğer **myapp #1** içinde **örneği** sütun. Bu durumda, belirli bir uygulama için bir performans sayacı eşleştirilecek zordur. İçin toplanan verileri olup olmadığını NET değil **myapp #1** ilk myapp.exe veya ikinci myapp.exe anlamına gelir.  
  
- Ne zaman bir uygulama, ortak dil çalışma zamanının birden çok örneğini kullanır. .NET Framework 4, işlem içi yan yana barındırma senaryolarını destekler. diğer bir deyişle, tek bir işlem veya uygulama ortak dil çalışma zamanının birden çok örneğini yükleyebilirsiniz. Tek bir uygulama myapp.exe yükleri iki çalışma zamanı örneği, varsayılan olarak adlandırılan, bunlar içinde atanacak **örneği** sütun olarak **myapp** ve **myapp #1**. Bu durumda, NET değil olmadığını **myapp** ve **myapp #1** aynı ada sahip iki uygulama ya da iki çalışma zamanları ile aynı uygulama. Birden çok uygulama aynı ada sahip birden fazla çalışma zamanı yüklerseniz, belirsizliği daha büyüktür.  
  
 Bu belirsizliği ortadan kaldırmak için bir kayıt defteri anahtarını ayarlayabilirsiniz. .NET Framework 4 kullanılarak geliştirilen uygulamalar için uygulama adı için bir çalışma zamanı örneği tanımlayıcısı tarafından izlenen işlem tanımlayıcısı bu kayıt defteri değişikliği ekler **örneği** sütun. Yerine *uygulama* veya *uygulama*#1, uygulama artık tanımlanmıştır *uygulama*_`p`*ProcessId* \_ `r` *runtimeID* içinde **örneği** sütun. Ortak dil çalışma zamanı'nın önceki bir sürümünü kullanarak bir uygulama geliştirildiği bilgisayardakinden, bu örneği olarak temsil edilen *uygulama\_* `p`*ProcessId* koşuluyla. NET Framework 4 yüklü.  
  
## <a name="performance-counters-for-in-process-side-by-side-applications"></a>İşlem içi yan yana uygulamalar için performans sayaçları  
 Tek bir uygulama içinde barındırılan birden çok ortak dil çalışma zamanı sürümleri için performans sayaçları işlemek için aşağıdaki tabloda gösterildiği gibi ayarlama, tek bir kayıt defteri anahtarını değiştirmeniz gerekir.  
  
|||  
|-|-|  
|Anahtar adı|HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\. NETFramework\Performance|  
|Değer adı|Eklemek|  
|Değer türü|REG_DWORD|  
|Değer|1 (0x00000001)|  
  
 Bir değer için 0 `ProcessNameFormat` varsayılan davranışı; olan etkin, uygulama başına temelinde Perfmon.exe görüntüler performans sayaçları gösterir. Bu değer 1 olarak ayarlayın, Perfmon.exe bir uygulamanın birden çok sürümünü belirgin hale getirir ve tek başına çalışma zamanı temelinde performans sayaçları sağlar. İçin herhangi bir değer `ProcessNameFormat` kayıt defteri anahtarı ayarı desteklenmemektedir ve gelecekte kullanılmak üzere ayrılmış.  
  
 Güncelleştirmeden sonra `ProcessNameFormat` kayıt defteri anahtarı yeni örneğini adlandırma özelliği düzgün şekilde çalışır, böylece ayarını Perfmon.exe veya herhangi bir tüketiciye performans sayaçlarını yeniden başlatmanız gerekir.  
  
 Aşağıdaki örnek nasıl değiştirileceğini gösterir `ProcessNameFormat` programlı olarak değeri.  
  
 [!code-csharp[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/cs/regsetting1.cs#1)]
 [!code-vb[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/vb/regsetting1.vb#1)]  
  
 Bu kayıt defteri değişikliğini yaptığınızda Perfmon.exe olarak .NET Framework 4 hedefleyen uygulamalar adlarını görüntüler *uygulama*_`p`*ProcessId* \_ `r` *runtimeID*burada *uygulama* uygulama adı *ProcessId* uygulamanın işlem tanımlayıcısı ve  *runtimeID* bir ortak dil çalışma zamanı tanımlayıcısı. Örneğin, bir uygulamanın iki ortak dil çalışma zamanı örneğini myapp.exe yükleri verdiyseniz Perfmon.exe myapp_p1416_r10 olarak bir örnek ve ikinci myapp_p3160_r10 olarak tanımlayabilir. Çalışma zamanı tanımlayıcısı yalnızca bir işlem içinde çalışma zamanları belirgin hale getirir; çalışma zamanı hakkında herhangi bir bilgi sağlamaz. (Örneğin, çalışma zamanı kimliği sürümü veya SKU çalışma zamanının ilgisi yoktur.)  
  
 .NET Framework 4 yüklü değilse, kayıt defteri değişikliği de .NET Framework'ün önceki sürümleri kullanılarak geliştirilen uygulamaları etkiler. Bunlar Perfmon.exe görünen *application_* `p`*ProcessId*burada *uygulama* uygulama adıdır ve *ProcessId* işlem tanımlayıcısı. İzlenen myapp.exe adlı iki uygulama performans sayaçları, örneğin, bir myapp_p23900 diğeri de myapp_p24908 olarak görünebilir.  
  
> [!NOTE]
>  İşlem tanımlayıcısı çalışma zamanı'nın önceki sürümlerini kullanan iki uygulama aynı ada sahip çözümleme belirsizliği ortadan kaldırır. Ortak dil çalışma zamanı önceki sürümlerini yan yana senaryolarda desteklemediği bir çalışma zamanı tanımlayıcısı önceki sürümler için gerekli değil.  
  
 .NET Framework 4 mevcut değil veya kaldırıldı, kayıt defteri anahtarı ayarı etkisizdir. Aynı ada sahip iki uygulama Perfmon.exe görünmesini devam edecek yani *uygulama* ve *uygulama #1* (örneğin, **myapp** ve **myapp #1**).
