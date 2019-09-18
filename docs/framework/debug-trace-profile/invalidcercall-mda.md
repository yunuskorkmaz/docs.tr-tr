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
ms.openlocfilehash: d508beb697e07f7d3b960b6627b9a07ffe25adf4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052630"
---
# <a name="invalidcercall-mda"></a>invalidCERCall MDA
`invalidCERCall` Yönetilen hata ayıklama Yardımcısı (MDA), güvenilirlik sözleşmesi olmayan bir yönteme veya aşırı derecede zayıf bir sözleşmeye sahip olan kısıtlı yürütme bölgesi (cer) grafiğinde bir çağrı olduğunda etkinleştirilir. Zayıf bir sözleşme, en kötü durum durumu bozulmasının çağrıya geçirilen örnekten daha büyük kapsam olduğunu bildiren bir sözleşmedir, yani <xref:System.AppDomain> veya işlem durumu bozulmuş olabilir ya da sonucun her zaman kesin bir şekilde bir tablo olmadığından emin olur bir CER içinde çağrıldığında.  
  
## <a name="symptoms"></a>Belirtiler  
 Bir CER 'de kod yürütürken beklenmedik sonuçlar. Belirtiler özel değildir. Bu, çalışma zamanı bir <xref:System.OutOfMemoryException> <xref:System.Threading.ThreadAbortException> süre önce <xref:System.Threading.ThreadAbortException>hazırlanmadığından veya çalışma zamanında özel durumlarla korunmadığından, güvenilir olmayan yönteme yapılan çağrıda beklenmedik, bir veya başka bir özel durum olabilir. Daha büyük bir tehdit, çalışma zamanında yönteminden kaynaklanan herhangi bir özel durumun <xref:System.AppDomain> veya işlemin bir cer hedefi olan kararsız bir durumda kalmasını sağlayabilir. Bir CER 'nin oluşturulma nedeni, bu gibi durum bozukluklarının önüne girmaktır. Tutarlı durumun tanımı uygulamalar arasında farklı olduğundan, bozuk durum belirtileri uygulamaya özgüdür.  
  
## <a name="cause"></a>Sebep  
 Bir cer içindeki kod, bir işlev olmadan <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> veya bir cer 'de çalışan ile uyumlu olmayan zayıf <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> bir işlevi çağırıyor.  
  
 Güvenilirlik sözleşmesi sözdizimi açısından, zayıf <xref:System.Runtime.ConstrainedExecution.Consistency> bir sözleşme, bir numaralandırma değeri belirtmeyen veya <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>, <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain>ya <xref:System.Runtime.ConstrainedExecution.Cer.None>da <xref:System.Runtime.ConstrainedExecution.Consistency> değerini belirten bir anlaşmadır. Bu koşullardan herhangi biri, olarak adlandırılan kodun, CER 'deki diğer kodun çalışmalarını, tutarlı durum sağlamak üzere engelleyebileceğini belirtir.  CERs, kodun hataları çok belirleyici bir şekilde ele almasını sağlar, böylece uygulama için önemli olan iç ınvaryantları koruyun ve bellek dışı özel durumlar gibi geçici hatalar halinde çalışmaya devam etmesine izin verilir.  
  
 Bu mda ' ın etkinleştirilmesi, cer 'de çağrılan yöntemin çağırıcının beklemediği veya <xref:System.AppDomain> bozulan ya da kurtarılamayan veya kurtarılamaz bir şekilde başarısız olmasına neden olduğunu gösterir. Kuşkusuz, çağrılan kod doğru şekilde yürütülemeyebilir ve sorun yalnızca eksik bir anlaşmada olur. Ancak, güvenilir kod yazma ile ilgili sorunlar hafif ve bir sözleşmenin yokluğu iyi bir göstergedir ve kod doğru bir şekilde yürütülmeyebilir. Sözleşmeler, programcının güvenilir bir şekilde kodlandığı ve ayrıca bu garantilere kodun gelecekteki düzeltmeleri içinde değişmeyecektir.  Diğer bir deyişle, sözleşmelerin yalnızca uygulama ayrıntıları değil, amaç bildirimleri vardır.  
  
 Zayıf veya varolmayan bir sözleşmeye sahip herhangi bir yöntem potansiyel olarak çok sayıda öngörülemeyen şekilde başarısız olabileceğinden, çalışma zamanı, yavaş JıT oluşturma, genel türler sözlüğü tarafından tanıtılan yöntemden kendi öngörülemeyen hatalarından hiçbirini kaldırmaya çalışmaz Örneğin, popülasyon veya iş parçacığı iptal eder. Diğer bir deyişle, bu MDA etkin olduğunda, çalışma zamanının tanımlanmakta olan CER 'ye çağrılan yöntemi içermediğini belirtir; Bu alt ağacı hazırlamaya devam etmek olası hatayı maskelemek için bu düğümde çağrı grafı sonlandırıldı.  
  
## <a name="resolution"></a>Çözüm  
 İşleve geçerli bir güvenilirlik sözleşmesi ekleyin veya bu işlev çağrısını kullanmaktan kaçının.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bir CER 'den zayıf bir sözleşmeyi çağırma etkisi, işlemlerini tamamlamaya yönelik CER hatası olabilir. Bu <xref:System.AppDomain> işlem durumu bozulmasına yol açabilir.  
  
## <a name="output"></a>Çıkış  
 Bu MDA 'ın örnek çıktısı aşağıda verilmiştir.  
  
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
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
