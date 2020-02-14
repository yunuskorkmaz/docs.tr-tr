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
ms.openlocfilehash: f8e467401f7c50898613c7cf6eca68a8a705431a
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217389"
---
# <a name="invalidcercall-mda"></a>invalidCERCall MDA
`invalidCERCall` yönetilen hata ayıklama Yardımcısı (MDA), sınırlı yürütme bölgesi (CER) grafiğinde, güvenilirlik sözleşmesi olmayan bir yönteme veya aşırı zayıf bir sözleşmeye bir çağrı yapıldığında etkinleştirilir. Zayıf bir sözleşme, en kötü durum durumu bozulmasının çağrıya geçirilen örnekten daha büyük kapsam olduğunu bildiren bir sözleşmedir, yani <xref:System.AppDomain> veya işlem durumu bozulabilir veya bir CER içinde çağrıldığında her zaman belirleyici bir tablo değildir.  
  
## <a name="symptoms"></a>Belirtiler  
 Bir CER 'de kod yürütürken beklenmedik sonuçlar. Belirtiler özel değildir. Çalışma zamanı bir süre önce hazırlanmadığından veya çalışma zamanında <xref:System.Threading.ThreadAbortException> özel durumlarla korunmadığından, bu durum beklenmeyen bir <xref:System.OutOfMemoryException>, <xref:System.Threading.ThreadAbortException>veya güvenilir olmayan yönteme yapılan çağrıda yer alabilir. Daha büyük bir tehdit, çalışma zamanında yönteminden kaynaklanan tüm özel durumlar <xref:System.AppDomain> veya işlemi bir CER hedefi olan kararsız bir durumda bırakabilir. Bir CER 'nin oluşturulma nedeni, bu gibi durum bozukluklarının önüne girmaktır. Tutarlı durumun tanımı uygulamalar arasında farklı olduğundan, bozuk durum belirtileri uygulamaya özgüdür.  
  
## <a name="cause"></a>Nedeni  
 Bir CER içindeki kod, <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> olmayan bir işlevi veya bir CER içinde çalışan ile uyumlu olmayan zayıf bir <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> çağırır.  
  
 Güvenilirlik sözleşmesi sözdizimi açısından, zayıf bir sözleşme <xref:System.Runtime.ConstrainedExecution.Consistency> numaralandırma değeri belirtmeyen veya <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>, <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain>veya <xref:System.Runtime.ConstrainedExecution.Cer.None><xref:System.Runtime.ConstrainedExecution.Consistency> değerini belirten bir anlaşmadır. Bu koşullardan herhangi biri, olarak adlandırılan kodun, CER 'deki diğer kodun çalışmalarını, tutarlı durum sağlamak üzere engelleyebileceğini belirtir.  CERs, kodun hataları çok belirleyici bir şekilde ele almasını sağlar, böylece uygulama için önemli olan iç ınvaryantları koruyun ve bellek dışı özel durumlar gibi geçici hatalar halinde çalışmaya devam etmesine izin verilir.  
  
 Bu MDA 'ın etkinleştirilmesi, CER 'de çağrılan yöntemin, çağıranın beklemediği veya <xref:System.AppDomain> ya da işlem durumunun bozulmuş ya da kurtarılamayan bir şekilde başarısız olmasına yol açabilir. Kuşkusuz, çağrılan kod doğru şekilde yürütülemeyebilir ve sorun yalnızca eksik bir anlaşmada olur. Ancak, güvenilir kod yazma ile ilgili sorunlar hafif ve bir sözleşmenin yokluğu iyi bir göstergedir ve kod doğru bir şekilde yürütülmeyebilir. Sözleşmeler, programcının güvenilir bir şekilde kodlandığı ve ayrıca bu garantilere kodun gelecekteki düzeltmeleri içinde değişmeyecektir.  Diğer bir deyişle, sözleşmelerin yalnızca uygulama ayrıntıları değil, amaç bildirimleri vardır.  
  
 Zayıf veya varolmayan bir sözleşmeye sahip herhangi bir yöntem potansiyel olarak çok sayıda öngörülemeyen şekilde başarısız olabileceğinden, çalışma zamanı, yavaş JıT oluşturma, genel türler sözlüğü tarafından tanıtılan yöntemden kendi öngörülemeyen hatalarından hiçbirini kaldırmaya çalışmaz Örneğin, popülasyon veya iş parçacığı iptal eder. Diğer bir deyişle, bu MDA etkin olduğunda, çalışma zamanının tanımlanmakta olan CER 'ye çağrılan yöntemi içermediğini belirtir; Bu alt ağacı hazırlamaya devam etmek olası hatayı maskelemek için bu düğümde çağrı grafı sonlandırıldı.  
  
## <a name="resolution"></a>Çözüm  
 İşleve geçerli bir güvenilirlik sözleşmesi ekleyin veya bu işlev çağrısını kullanmaktan kaçının.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bir CER 'den zayıf bir sözleşmeyi çağırma etkisi, işlemlerini tamamlamaya yönelik CER hatası olabilir. Bu, <xref:System.AppDomain> işlem durumunun bozulmasına yol açabilir.  
  
## <a name="output"></a>Çıktı  
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
