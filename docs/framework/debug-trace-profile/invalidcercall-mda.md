---
title: invalidCERCall MDA
ms.date: 03/30/2017
helpviewer_keywords:
- invalid CER calls
- InvalidCERCall MDA
- MDAs (managed debugging assistants), CER calls
- constrained execution regions
- CER calls
- managed debugging assistants (MDAs), CER calls
ms.assetid: c4577410-602e-44e5-9dab-fea7c55bcdfe
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1a68aac2a92a0569e288da858e4a4e4695fd5eaa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59193921"
---
# <a name="invalidcercall-mda"></a>invalidCERCall MDA
`invalidCERCall` Yönetilen hata ayıklama Yardımcısı (MDA) hiçbir güvenilirlik sözleşme veya aşırı zayıf bir sözleşme olan bir yönteme bir çağrı kısıtlı yürütme bölge (CER) grafik içinde olduğunda etkinleştirilir. Zayıf bir sözleşme çağrısı, diğer bir deyişle, geçirilen örneği daha büyük bir kapsamın en kötü durum durumu bozulması olduğunu bildiren bir sözleşmedir <xref:System.AppDomain> veya işlem durumu bozuksa ya da sonuç her zaman hesaplanabilir belirleyici olmayan içinde bir CER çağrıldığında.  
  
## <a name="symptoms"></a>Belirtiler  
 Kod içinde bir CER yürütülürken beklenmeyen sonuçlar. Belirtiler özgü değildir. Beklenmeyen bir olabilir <xref:System.OutOfMemoryException>, <xref:System.Threading.ThreadAbortException>, veya diğer özel durumlar, güvenilir olmayan bir yöntem çağrısına çalışma zamanı olmamasından önceden hazırlama veya sunucusundan <xref:System.Threading.ThreadAbortException> çalışma zamanında özel durum. Çalışma zamanında yöntemden kaynaklanan bir özel durumla bırakabilir büyük tehdit olarak <xref:System.AppDomain> veya işlem bir CER amacı aykırı kararsız bir durumda. Bir CER oluşturulan nedeni bu gibi durum bozulmaları kaçınmaktır. Bozuk durum belirtileri uygulamaya özgü olduğu uygulamalar arasında tutarlı bir duruma tanımını farklıdır.  
  
## <a name="cause"></a>Sebep  
 Kod bir CER içinde olmayan bir işlev çağırma <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> veya bir zayıf <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> bir CER içinde çalışan ile uyumlu değil.  
  
 Güvenilirlik sözleşme söz dizimi bakımından zayıf bir sözleşme belirttiğinde sözleşmedir bir <xref:System.Runtime.ConstrainedExecution.Consistency> numaralandırma değeri veya belirtir bir <xref:System.Runtime.ConstrainedExecution.Consistency> değerini <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>, <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain>, veya <xref:System.Runtime.ConstrainedExecution.Cer.None>. Bu koşullardan herhangi biri çağrılan kodu tutarlı durumunu korumak üzere CER diğer kod çabalarını engelleyebilecek gösterir.  Uygulama için önemli olan iç okuduğunuzda bakımını yapma ve bellek yetersiz özel durumlar gibi geçici hatalardan yüzü içinde çalışmaya devam etmesine izin çok belirlenimci bir şekilde hata değerlendirilecek kod CERs sağlar.  
  
 CER içinde çağrılan yöntemin bırakır, veya çağıranın girmek istemediğiniz bir yolla devredebilirsiniz olasılığı bu mda'nın etkinleştirilmesinden gösterir <xref:System.AppDomain> veya işlem durumu bozuk veya kurtarılamaz. Elbette, çağrılan kodu doğru paralellikle çalışabilir ve yalnızca eksik bir sözleşme sorunudur. Ancak, güvenilir kod yazma konuları belirsizdir ve kodu doğru yürütülemeyebilir iyi bir göstergesi sözleşme bildirilmesidir. Programcı güvenilir bir biçimde kodlanmış ve ayrıca bu garanti gelecek düzeltmeler kod değişmez taahhüt göstergeleri sözleşmeler var.  Diğer bir deyişle, anlaşmalar amacı ve yalnızca uygulama ayrıntılarını bildirimlerdir.  
  
 Çalışma zamanı yavaş JIT-derleme tarafından genel türler sözlüğü sunulan yöntemi herhangi bir öngörülemeyen kendi hataları kaldırmak denemez zayıf veya varolmayan bir sözleşmeyi herhangi bir yöntemle potansiyel olarak birçok beklenmedik şekilde başarısız olabileceğinden doldurma veya iş parçacığı, örneğin durdurur. Diğer bir deyişle, bu ciddi bir şekilde bu MDA etkinleştirildiğinde, çalışma zamanı tanımlanan CER içinde çağrılan yöntem içermiyordu gösterir; Bu alt ağaç hazırlamak devam etmeden olası hata maske yardımcı olan için çağrı grafı bu düğümde sonlandırıldı.  
  
## <a name="resolution"></a>Çözüm  
 Geçerli güvenilirlik sözleşme işleve ekleyin veya bu işlev çağrısı kullanmaktan kaçının.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi  
 Bir CER zayıf bir sözleşme çağırma etkisi, bakımın tamamlanması CER hata olabilir. Bu bozulmasına neden <xref:System.AppDomain> işlem durumu.  
  
## <a name="output"></a>Çıkış  
 Bu MDA'dosyasından örnek çıktı verilmiştir.  
  
 `Method 'MethodWithCer', while executing within a constrained execution region, makes a call at IL offset 0x000C to 'MethodWithWeakContract', which does not have a sufficiently strong reliability contract and might cause non-deterministic results.`  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
