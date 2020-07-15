---
title: Kısıtlı Yürütme Bölgeleri
description: Güvenilir yönetilen kod yazmak için bir mekanizmanın parçası olan kısıtlanmış yürütme bölgelerini (CER) kullanmaya başlayın.
ms.date: 03/30/2017
helpviewer_keywords:
- constrained execution regions
- CERs
ms.assetid: 99354547-39c1-4b0b-8553-938e8f8d1808
ms.openlocfilehash: d928c9357af4a02e389d9ffd5df4ad0195edab06
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309618"
---
# <a name="constrained-execution-regions"></a>Kısıtlı Yürütme Bölgeleri
Kısıtlanmış bir yürütme bölgesi (CER), güvenilir yönetilen kod yazma mekanizmalarının bir parçasıdır. Bir CER, ortak dil çalışma zamanının (CLR), alandaki kodun tamamen yürütülmesini önleyen bant dışı özel durumlar oluşturmamaya sınırlı bir alan tanımlar. Bu bölge içinde, Kullanıcı kodu, bant dışı özel durumların oluşmasına neden olacak kodu yürütmenin kısıtlanıyor. <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>Yöntem bir `try` blok ve işaret `catch` , `finally` , ve `fault` kısıtlamalı yürütme bölgesi olarak bloklara kadar önce gelmelidir. Kısıtlanmış bölge olarak işaretlendikten sonra, kod yalnızca güçlü güvenilirlik sözleşmeleri ile diğer kodu çağırmalıdır ve kod hatalara hazırlanmaya hazırlanmadığı sürece kodun hazırlanmamış veya güvenilmeyen yöntemlere sanal çağrılar yapması ya da olmaması gerekir. Bir CER içinde yürütülen kod için CLR gecikmeleri iş parçacığı iptal eder.  

> [!IMPORTANT]
> CER yalnızca .NET Framework desteklenir. Bu makale .NET Core veya .NET 5 ve üzeri için geçerlidir.

 Kısıtlanmış yürütme bölgeleri, ek açıklamalı bloğa ek olarak CLR 'de farklı formlarda `try` <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject> ve yöntemi kullanılarak yürütülen sınıf ve koddan türetilmiş sınıflarda yürütülen özellikle kritik sonlandırıcılar kullanır <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> .  
  
## <a name="cer-advance-preparation"></a>CER ön hazırlığı  
 CLR, bellek dışı koşulların önüne geçmek için CERs 'i önceden hazırlar. Tam zamanında derleme veya tür yükleme sırasında CLR yetersiz bellek koşuluna neden olmadığından, ön hazırlık gereklidir.  
  
 Geliştirici, bir kod bölgesinin bir CER olduğunu göstermek için gereklidir:  
  
- En üst düzey CER bölgesi ve özniteliği uygulanmış olan tam çağrı grafiğindeki Yöntemler <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> önceden hazırlanır. <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute>Yalnızca veya için garanti verebilir <xref:System.Runtime.ConstrainedExecution.Cer.Success> <xref:System.Runtime.ConstrainedExecution.Cer.MayFail> .  
  
- Sanal dağıtım gibi statik olarak belirlenemeyen çağrılar için ön hazırlık gerçekleştirilemiyor. <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>Bu durumlarda yöntemini kullanın. <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A>Yöntemi kullanılırken, <xref:System.Runtime.ConstrainedExecution.PrePrepareMethodAttribute> özniteliği Temizleme koduna uygulanmalıdır.  
  
## <a name="constraints"></a>Kısıtlamalar  
 Kullanıcılar, bir CER 'ye yazdıkları kod türünde kısıtlanmıştır. Kod, bant dışı bir özel duruma neden olamaz, örneğin, aşağıdaki işlemlerden kaynaklanıyor olabilir:  
  
- Açık ayırma.  
  
- Lamak.  
  
- Kilit alınıyor.  
  
- Hazırlanmamış Yöntemler hemen çağrılıyor.  
  
- Zayıf veya varolmayan bir güvenilirlik sözleşmesiyle Yöntemler çağırma.  
  
 .NET Framework sürüm 2,0 ' de, bu kısıtlamalar kılavuzlardır. Tanılama, kod analizi araçları aracılığıyla sağlanır.  
  
## <a name="reliability-contracts"></a>Güvenilirlik sözleşmeleri  
 , <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> Güvenilirlik garantilerini ve belirli bir yöntemin bozulma durumunu belgeleyen özel bir özniteliktir.  
  
### <a name="reliability-guarantees"></a>Güvenilirlik garantisi  
 Numaralandırma değerlerine göre temsil edilen güvenilirlik garantisi <xref:System.Runtime.ConstrainedExecution.Cer> , belirli bir yöntemin güvenilirlik derecesini belirtir:  
  
- <xref:System.Runtime.ConstrainedExecution.Cer.MayFail>. Olağanüstü koşullarda, yöntemi başarısız olabilir. Bu durumda yöntem, başarılı veya başarısız olsun çağırma yöntemine rapor gönderir. Dönüş değerini bildirebildiğinden emin olmak için yöntem bir CER içinde bulunmalıdır.  
  
- <xref:System.Runtime.ConstrainedExecution.Cer.None>. Yöntem, tür veya derlemenin bir CER kavramı yoktur ve büyük olasılıkla durum bozulması önemli ölçüde azalmadan bir CER içinde çağrı yapmak çok daha güvenli değildir. CER garantisi avantajlarından faydalanır. Bu, aşağıdakileri gösterir:  
  
    1. Olağanüstü koşullarda, yöntemi başarısız olabilir.  
  
    2. Yöntemi başarısız olmuş olabilir veya rapormayabilir.  
  
    3. Yöntemi, en olası senaryoyu bir CER kullanmak üzere yazılmadı.  
  
    4. Bir yöntem, tür veya derleme açık bir şekilde başarılı olarak tanımlanmamışsa, örtülü olarak tanımlanır <xref:System.Runtime.ConstrainedExecution.Cer.None> .  
  
- <xref:System.Runtime.ConstrainedExecution.Cer.Success>. Olağanüstü koşullarda, yöntemin başarılı olması garanti edilir. Bu güvenilirlik düzeyini elde etmek için, CER olmayan bir bölgenin içinden çağrıldığında bile çağrılan yöntemi etrafında her zaman bir CER oluşturmanız gerekir. Bir yöntem, ne amaçlandığını başarıyorsa başarılı olur, ancak başarı subjecolarak görüntülenebilir. Örneğin, Count `ReliabilityContractAttribute(Cer.Success)` değeri, BIR cer altında çalıştırıldığında, her zaman içindeki öğe sayısının sayısını döndürür <xref:System.Collections.ArrayList> ve iç alanları hiçbir zaman belirlenmemiş bir durumda bırakmaz.  Ancak, <xref:System.Threading.Interlocked.CompareExchange%2A> Yöntem başarı olarak işaretlenir ve bu da başarıyı anlamak, bir yarış durumu nedeniyle değerin yeni bir değerle değiştirilemedi.  Anahtar noktası, yöntemin davranışta belgelendiği şekilde davrandığı ve CER kodunun doğru ancak güvenilir olmayan kodun nasıl görüneceğine ilişkin olağandışı davranışları beklemek üzere yazılması gerekmez.  
  
### <a name="corruption-levels"></a>Bozulma düzeyleri  
 Sabit listesi değerleriyle temsil edilen bozulma düzeyleri <xref:System.Runtime.ConstrainedExecution.Consistency> , belirli bir ortamda ne kadar durum bozulmuş olabileceğini belirtir:  
  
- <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain>. Olağanüstü koşullarda, ortak dil çalışma zamanı (CLR) geçerli uygulama etki alanında durum tutarlılığı konusunda hiçbir garanti vermez.  
  
- <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptInstance>. Olağanüstü koşullarda, durum bozulmasını geçerli örnekle sınırlamak için yöntemi garanti edilir.  
  
- <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>Olağanüstü koşullarda, CLR durum tutarlılığı konusunda garanti vermez; diğer bir deyişle, bu durum işlemi bozmayabilir.  
  
- <xref:System.Runtime.ConstrainedExecution.Consistency.WillNotCorruptState>. Olağanüstü koşullarda, metodun durumu Bozulmamaları garanti edilir.  
  
## <a name="reliability-trycatchfinally"></a>Güvenilirlik try/catch/finally  
 Güvenilirlik, `try/catch/finally` yönetilmeyen sürümle aynı tahmine dayalı garanti garantisi düzeyine sahip bir özel durum işleme mekanizmasıdır. `catch/finally`Blok, cer 'dir. Bloktaki yöntemler için ön hazırlık gerekir ve noninterruptible olmalıdır.  
  
 .NET Framework sürüm 2,0 ' de, kod, bir try bloğundan hemen önce çağırarak çalışma zamanına bir TRY güvenilir olduğunu bildirir <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> . <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A><xref:System.Runtime.CompilerServices.RuntimeHelpers>, bir derleyici desteği sınıfının üyesidir. Çağrı <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> , derleyiciler aracılığıyla doğrudan kullanılabilirliğini bekliyor.  
  
## <a name="noninterruptible-regions"></a>Noninterruptible bölgeleri  
 Bir noninterruptible bölgesi, bir dizi yönergede bir CER öğesine gruplandırır.  
  
 .NET Framework sürüm 2,0 ' de, derleyici desteği aracılığıyla kullanım bekleniyor, Kullanıcı kodu, bir yöntem çağrısının önünde boş bir try/catch bloğu içeren, güvenilir bir try/catch/finally ile kesilebilir olmayan bölgeler oluşturur <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> .  
  
## <a name="critical-finalizer-object"></a>Kritik Sonlandırıcı nesnesi  
 <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>Çöp toplamanın sonlandırıcıyı yürütebilmesi güvence altına alınır. Ayırma sonrasında Sonlandırıcı ve çağrı grafı önceden hazırlanır. Sonlandırıcı yöntemi bir CER içinde yürütülür ve CERs ve sonlandırıcılarda tüm kısıtlamalara uymalıdır.  
  
 Ve ' den devralan her türlü tür <xref:System.Runtime.InteropServices.SafeHandle> <xref:System.Runtime.InteropServices.CriticalHandle> , bir cer içinde kendi sonlandırıcılarını yürütme garantisi. <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> <xref:System.Runtime.InteropServices.SafeHandle> Tanıtıcıyı serbest bırakmak için gereken herhangi bir kodu yürütmek üzere türetilmiş sınıflarda uygulayın.  
  
## <a name="code-not-permitted-in-cers"></a>CERs içinde koda Izin verilmiyor  
 CERs içinde aşağıdaki işlemlere izin verilmez:  
  
- Açık ayırmalar.  
  
- Kilit alınıyor.  
  
- Lamak.  
  
- Çok boyutlu dizi erişimi.  
  
- Yöntemi yansıma aracılığıyla çağırır.  
  
- <xref:System.Threading.Monitor.Enter%2A> veya <xref:System.IO.FileStream.Lock%2A>.  
  
- Güvenlik denetimleri. Talepler gerçekleştirmeyin, yalnızca bağlantı taleplerine ihtiyaç kalmaz.  
  
- <xref:System.Reflection.Emit.OpCodes.Isinst>ve <xref:System.Reflection.Emit.OpCodes.Castclass> com nesneleri ve proxy 'leri için  
  
- Saydam bir ara sunucuda alanlar alma veya ayarlama.  
  
- Getir.  
  
- İşlev işaretçileri ve temsilciler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenilirlik En İyi Yöntemleri](reliability-best-practices.md)
