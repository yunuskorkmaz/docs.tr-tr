---
title: invalidCERCall MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- invalid CER calls
- InvalidCERCall MDA
- MDAs (managed debugging assistants), CER calls
- constrained execution regions
- CER calls
- managed debugging assistants (MDAs), CER calls
ms.assetid: c4577410-602e-44e5-9dab-fea7c55bcdfe
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0c051e1513f8e8ad1735085cb93f106b4fb9b0d7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="invalidcercall-mda"></a>invalidCERCall MDA
`invalidCERCall` Yönetilen hata ayıklama Yardımcısı (MDA) kısıtlı yürütme bölge (CER) grafik içinde hiçbir güvenilirlik sözleşme veya aşırı zayıf bir sözleşme içeren bir yöntem çağrısı olduğunda etkinleştirilir. Zayıf bir sözleşme çağrısı, diğer bir deyişle, geçirilen örneği daha büyük kapsamının en kötü durumu case bozulması olduğunu bildiren bir sözleşmedir <xref:System.AppDomain> işlem durumu bozuksa veya sonucu her zaman belirleyici biçimde computable olmayan içinde bir CER çağrıldığında.  
  
## <a name="symptoms"></a>Belirtiler  
 Kod bir CER yürütülürken beklenmeyen sonuçlar. Belirtiler özel değildir. Beklenmeyen bir olabilir <xref:System.OutOfMemoryException>, <xref:System.Threading.ThreadAbortException>, veya diğer özel durumlar güvenilmez yöntemiyle çağrısında çalışma zamanı olmamasından önceden hazırlayın veya ondan korumak <xref:System.Threading.ThreadAbortException> çalışma zamanında özel durum. Daha büyük bir tehdit yöntemden zamanında kaynaklanan bir özel durumla bırakabilir olduğu <xref:System.AppDomain> veya işlem bir CER amacı aykırı kararsız bir durumda. Bu gibi durumu bozulmaları önlemek için bir CER oluşturulan neden gerekir. Bozuk durum belirtileri uygulamaya özel olduklarından uygulamalar arasında tutarlı bir duruma tanımını farklıdır.  
  
## <a name="cause"></a>Sebep  
 Bir CER içindeki kod içermeyen bir işlevi çağırmak <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> veya bir zayıf ile <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> bir CER çalıştıran ile uyumlu değil.  
  
 Güvenilirlik sözleşme sözdizimi açısından zayıf bir sözleşme belirtmediği sözleşmedir bir <xref:System.Runtime.ConstrainedExecution.Consistency> numaralandırma değeri veya belirten bir <xref:System.Runtime.ConstrainedExecution.Consistency> değerini <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>, <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain>, veya <xref:System.Runtime.ConstrainedExecution.Cer.None>. Bu koşulların herhangi biri çağrılan kodu tutarlı durumunu korumak üzere çabalarına CER diğer kod engelleyebilecek gösterir.  CERs uygulamaya önemli iç invariants koruma ve, bellek yetersiz özel durumları gibi geçici hataları yüz çalışmaya devam etmesini sağlayan çok belirleyici bir şekilde hataları işlemek kod sağlar.  
  
 Bu MDA etkinleştirme CER çağrılan yöntem arayan değil beklediğiniz neydi veya, ayrıldığında bir şekilde başarısız olasılığı gösterir <xref:System.AppDomain> veya işlem durumu bozuk veya kurtarılamaz. Elbette, çağrılan kodu doğru yürütebilir ve yalnızca eksik sözleşme sorunudur. Ancak, güvenilir kod yazma ilgili sorunları zarif ve bir sözleşme yokluğu kodu doğru yürütmeme iyi bir göstergesidir. Sözleşmeler Programcı güvenilir bir şekilde kodlanmış ve aynı zamanda bu garantiler kodu düzeltmelerini gelecekte değiştirmez taahhüt eder göstergesidir.  Diğer bir deyişle, sözleşmeler amacı ve yalnızca uygulama ayrıntılarını bildirimlerini ' dir.  
  
 Çalışma zamanı kendi beklenmeyen hataları hiçbirini geç JIT-derleme tarafından genel türler sözlüğü sunulan yöntemi kaldırmak denemez zayıf veya var olmayan bir sözleşmeyi herhangi bir yöntemle potansiyel olarak birçok beklenmedik şekilde başarısız olabileceğinden popülasyon ya da iş parçacığı, örneğin durdurur. Diğer bir deyişle, bu MDA etkinleştirildiğinde, çalışma zamanı tanımlanmakta CER içinde çağrılan yöntemin içermeyen belirtir; Bu alt ağaç hazırlamak etmeden olası hata maske yardımcı olan arama grafiği bu düğümde sonlandırıldı.  
  
## <a name="resolution"></a>Çözüm  
 İşlev geçerli güvenilirlik sözleşme eklemek veya bu işlev çağrısı kullanmaktan kaçının.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 Zayıf bir sözleşme CER çağırma etkisini işlemlerini tamamlamak için CER hata olabilir. Bu bozulmasına yol açabilir <xref:System.AppDomain> işlem durumu.  
  
## <a name="output"></a>Çıkış  
 Bu MDA dosyasından örnek çıktı verilmiştir.  
  
 `Method 'MethodWithCer', while executing within a constrained execution region, makes a call at IL offset 0x000C to 'MethodWithWeakContract', which does not have a sufficiently strong reliability contract and might cause non-deterministic results.`  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>  
 <xref:System.Runtime.ConstrainedExecution>  
 [Yönetilen hata ayıklama Yardımcıları ile hataları tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
