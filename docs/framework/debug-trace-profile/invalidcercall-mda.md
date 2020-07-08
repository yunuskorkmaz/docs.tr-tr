---
title: invalidCERCall MDA
description: Kısıtlanmış yürütme bölgesi (CER) grafiğinde geçersiz bir çağrı varsa etkinleştirilen ınvalidcercall yönetilen hata ayıklama Yardımcısı 'nı (MDA) gözden geçirin.
ms.date: 03/30/2017
helpviewer_keywords:
- invalid CER calls
- InvalidCERCall MDA
- MDAs (managed debugging assistants), CER calls
- constrained execution regions
- CER calls
- managed debugging assistants (MDAs), CER calls
ms.assetid: c4577410-602e-44e5-9dab-fea7c55bcdfe
ms.openlocfilehash: dec32a81929d72274757b75cb03d6615d9fa948b
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051798"
---
# <a name="invalidcercall-mda"></a>invalidCERCall MDA
`invalidCERCall`Yönetilen hata ayıklama Yardımcısı (MDA), güvenilirlik sözleşmesi olmayan bir yönteme veya aşırı derecede zayıf bir sözleşmeye sahip olan kısıtlı yürütme bölgesi (cer) grafiğinde bir çağrı olduğunda etkinleştirilir. Zayıf bir sözleşme, en kötü durum durumu bozulmasının çağrıya geçirilen örnekten daha büyük kapsam olduğunu bildiren bir sözleşmedir, yani <xref:System.AppDomain> veya işlem durumu bozulabilir veya BIR cer içinde çağrıldığında her zaman kesin bir şekilde oluşturulabilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Bir CER 'de kod yürütürken beklenmedik sonuçlar. Belirtiler özel değildir. <xref:System.OutOfMemoryException> <xref:System.Threading.ThreadAbortException> Bu, çalışma zamanı bir süre önce hazırlanmadığından veya çalışma zamanında özel durumlarla korunmadığından, güvenilir olmayan yönteme yapılan çağrıda beklenmedik, bir veya başka bir özel durum olabilir <xref:System.Threading.ThreadAbortException> . Daha büyük bir tehdit, çalışma zamanında yönteminden kaynaklanan herhangi bir özel durumun <xref:System.AppDomain> veya işlemin BIR cer hedefi olan kararsız bir durumda kalmasını sağlayabilir. Bir CER 'nin oluşturulma nedeni, bu gibi durum bozukluklarının önüne girmaktır. Tutarlı durumun tanımı uygulamalar arasında farklı olduğundan, bozuk durum belirtileri uygulamaya özgüdür.  
  
## <a name="cause"></a>Nedeni  
 Bir CER içindeki kod, bir işlev olmadan veya bir <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> cer 'de çalışan ile uyumlu olmayan zayıf bir işlevi çağırıyor.  
  
 Güvenilirlik sözleşmesi sözdizimi açısından, zayıf bir sözleşme, bir <xref:System.Runtime.ConstrainedExecution.Consistency> numaralandırma değeri belirtmeyen veya <xref:System.Runtime.ConstrainedExecution.Consistency> , ya da değerini belirten bir anlaşmadır <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess> <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain> <xref:System.Runtime.ConstrainedExecution.Cer.None> . Bu koşullardan herhangi biri, olarak adlandırılan kodun, CER 'deki diğer kodun çalışmalarını, tutarlı durum sağlamak üzere engelleyebileceğini belirtir.  CERs, kodun hataları çok belirleyici bir şekilde ele almasını sağlar, böylece uygulama için önemli olan iç ınvaryantları koruyun ve bellek dışı özel durumlar gibi geçici hatalar halinde çalışmaya devam etmesine izin verilir.  
  
 Bu MDA ' ın etkinleştirilmesi, CER 'de çağrılan yöntemin çağırıcının beklemediği veya bozulan ya da kurtarılamayan veya kurtarılamaz bir şekilde başarısız olmasına neden olduğunu gösterir <xref:System.AppDomain> . Kuşkusuz, çağrılan kod doğru şekilde yürütülemeyebilir ve sorun yalnızca eksik bir anlaşmada olur. Ancak, güvenilir kod yazma ile ilgili sorunlar hafif ve bir sözleşmenin yokluğu iyi bir göstergedir ve kod doğru bir şekilde yürütülmeyebilir. Sözleşmeler, programcının güvenilir bir şekilde kodlandığı ve ayrıca bu garantilere kodun gelecekteki düzeltmeleri içinde değişmeyecektir.  Diğer bir deyişle, sözleşmelerin yalnızca uygulama ayrıntıları değil, amaç bildirimleri vardır.  
  
 Zayıf veya varolmayan bir sözleşmeye sahip herhangi bir yöntem potansiyel olarak çok sayıda öngörülemeyen şekilde başarısız olabileceğinden, çalışma zamanı, yavaş JıT derleme, genel türler sözlüğü popülasyonu veya iş parçacığı arızalarıyla tanıtılan yöntemden kendi öngörülemeyen hatalarından hiçbirini kaldırmaya çalışmaz. Diğer bir deyişle, bu MDA etkin olduğunda, çalışma zamanının tanımlanmakta olan CER 'ye çağrılan yöntemi içermediğini belirtir; Bu alt ağacı hazırlamaya devam etmek olası hatayı maskelemek için bu düğümde çağrı grafı sonlandırıldı.  
  
## <a name="resolution"></a>Çözüm  
 İşleve geçerli bir güvenilirlik sözleşmesi ekleyin veya bu işlev çağrısını kullanmaktan kaçının.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bir CER 'den zayıf bir sözleşmeyi çağırma etkisi, işlemlerini tamamlamaya yönelik CER hatası olabilir. Bu işlem durumu bozulmasına yol açabilir <xref:System.AppDomain> .  
  
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
