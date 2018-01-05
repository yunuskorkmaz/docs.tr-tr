---
title: "Kısıtlı Yürütme Bölgeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- constrained execution regions
- CERs
ms.assetid: 99354547-39c1-4b0b-8553-938e8f8d1808
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4f046f26391d581bc1663e9a7041225ede99bd31
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="constrained-execution-regions"></a>Kısıtlı Yürütme Bölgeleri
Kısıtlı yürütme bölge (CER) güvenilir yönetilen kod yazma için bir mekanizma bir parçasıdır. Bir CER kodu alanının tamamının yürütülmesini önleyen bant dışı özel durumları atma ortak dil çalışma zamanı (CLR) kısıtlı bir alanı tanımlar. Bu bölge içinde kullanıcı kodu atma bant dışı özel durumları neden olan kod yürütülmesini sınırlı değildir. <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> Yöntemi hemen gelmelidir bir `try` bloğu ve işaretleri `catch`, `finally`, ve `fault` kısıtlı yürütme bölgeleri olarak engeller. Kısıtlanmış bir bölge işaretlenmiş sonra kod güçlü güvenilirlik sözleşmeleri ile başka bir kod yalnızca çağırmanız gerekir ve kod ayırmak veya gerekir kod hataları işlemek için hazırlanan sürece hazırlıksız ya da güvenilir olmayan yöntemleri sanal çağrı yapmak. Bir CER yürütülen kod için CLR gecikmeler iş parçacığı durdurur.  
  
 Kısıtlı yürütme bölgeleri yanı sıra ek açıklama CLR farklı formlarında kullanılan `try` bloğunu özellikle türetilmiş sınıflardaki yürütme kritik sonlandırıcılar <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject> sınıfı ve kullanılarak yürütülen kod <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> yöntemi.  
  
## <a name="cer-advance-preparation"></a>CER ön hazırlık  
 CLR CERs önceden bellek yetersiz durumlardan kaçınmak için hazırlar. CLR yetersiz bellek durumu yalnızca zaman derleme veya tür yüklemesi sırasında neden olmaz ve böylece ön hazırlık gereklidir.  
  
 Geliştirici kod bölgesini bir CER olduğunu belirtmek için gereklidir:  
  
-   Üst düzey CER bölge ve sahip yöntemleri tam çağrı grafikte <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> uygulanan öznitelik hazırlanmış önceden. <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> Garanti yalnızca durum <xref:System.Runtime.ConstrainedExecution.Cer.Success> veya <xref:System.Runtime.ConstrainedExecution.Cer.MayFail>.  
  
-   Statik olarak, sanal gönderme gibi belirlenemiyor çağrıları için ön hazırlık gerçekleştirilemiyor. Kullanım <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> bu gibi durumlarda yöntemi. Kullanırken <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> yöntemi, <xref:System.Runtime.ConstrainedExecution.PrePrepareMethodAttribute> özniteliği kod Temizleme için uygulanması.  
  
## <a name="constraints"></a>Kısıtlamalar  
 Kullanıcılar bir CER yazabilirsiniz kod türünü kısıtlanmıştır. Kod bir bant dışı özel sebep olamaz, aşağıdaki işlemlerden gibi neden olabilir:  
  
-   Açık ayırma.  
  
-   Kutulama.  
  
-   Kilit alınıyor.  
  
-   Neredeyse hazırlıksız yöntemleri çağırma.  
  
-   Zayıf veya var olmayan güvenilirliğini sözleşme ile yöntemleri çağırma.  
  
 .NET Framework sürüm 2. 0'da, bu kısıtlamaların yönergelerdir. Tanılama kod çözümleme araçları sağlanır.  
  
## <a name="reliability-contracts"></a>Güvenilirlik sözleşmeleri  
 <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> Belgeleri güvenilirlik garanti ve belirli bir yöntemin Bozulması durumunu özel bir özniteliktir.  
  
### <a name="reliability-guarantees"></a>Güvenilirlik garanti  
 Tarafından temsil edilen güvenilirlik garanti <xref:System.Runtime.ConstrainedExecution.Cer> numaralandırma değerleri, belirli bir yöntemin güvenilirliğini derecesini gösterir:  
  
-   <xref:System.Runtime.ConstrainedExecution.Cer.MayFail>. Olağanüstü koşullarda yöntemi başarısız olabilir. Bu durumda, yöntem başarılı veya başarısız olup olmadığını çağıran yönteme bildirir. Yöntemin dönüş değeri raporlayabilirsiniz emin olmak için bir CER bulunması gerekir.  
  
-   <xref:System.Runtime.ConstrainedExecution.Cer.None>. Yöntemi, tür veya derleme bir CER kavramına sahiptir ve büyük olasılıkla değil durumu bozulmaya önemli azaltma olmadan CER içinde çağırmak güvenli. CER garanti avantajlarından almaz. Bu aşağıdaki anlamına gelir:  
  
    1.  Olağanüstü koşullarda yöntemi başarısız olabilir.  
  
    2.  Yöntem olabilir veya başarısız olduğunu rapor edemeyebilir.  
  
    3.  Yöntem CER, en olası senaryo kullanılacak yazılmaz.  
  
    4.  Yöntemi, tür veya derleme açıkça başarılı olması için özelikle tanımlanamıyorsa, onu örtük olarak tanımlanan <xref:System.Runtime.ConstrainedExecution.Cer.None>.  
  
-   <xref:System.Runtime.ConstrainedExecution.Cer.Success>. Olağanüstü koşullarda yöntemi başarılı olması için sağlanır. Bu düzeyde elde etmek için her zaman bir CER geçici olarak adlandırılan, hatta zaman onu CER olmayan bölge içinde çağrılır yöntemi oluşturmalısınız. Bir yöntem başarı subjectively görüntülenebilir ancak ne yöneliktir gerçekleştirir başarılı olur. Örneğin, Count ile işaretleme `ReliabilityContractAttribute(Cer.Success)` CER altında çalışırken, bu her zaman öğelerin sayısını döndürdüğünü gelir <xref:System.Collections.ArrayList> ve hiçbir zaman belirlenmemiş bir durum içinde iç alanlarını bırakabilirsiniz.  Ancak, <xref:System.Threading.Interlocked.CompareExchange%2A> yöntemi başarı değeri değiştirilmemişse bir yarış durumu nedeniyle yeni bir değerle olduğu anlamına gelebilir anlama ile de başarılı işaretlenir.  Anahtar yöntemi davranmasına belirtildiği şekilde davranır ve CER kodu hangi doğru ancak güvenilmeyen kod aşağıdaki gibidir ötesinde herhangi olağan dışı davranış beklenir yazılması gerekmez noktasıdır.  
  
### <a name="corruption-levels"></a>Bozulması düzeyleri  
 Bozulması düzeyleri temsil ettiği <xref:System.Runtime.ConstrainedExecution.Consistency> numaralandırma değerlerini göstermek ne kadar durum verilen ortamda bozulmuş olabilir:  
  
-   <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain>. Olağanüstü koşullar altında geçerli uygulama etki alanında garanti durumu tutarlılık ilgili ortak dil çalışma zamanı (CLR) sağlar.  
  
-   <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptInstance>. Olağanüstü koşullar altında geçerli örnek durum bozulmasına sınırlamak için yöntemi sağlanır.  
  
-   <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>, Olağanüstü koşullar altında CLR garanti durumu tutarlılık; ilgili hale getirir. diğer bir deyişle, koşul işlemi bozulmasına neden olabilir.  
  
-   <xref:System.Runtime.ConstrainedExecution.Consistency.WillNotCorruptState>. Olağanüstü koşullarda yöntemi garanti durumu bozuk değil.  
  
## <a name="reliability-trycatchfinally"></a>Güvenilirlik try/catch/finally  
 Güvenilirlik `try/catch/finally` işleme mekanizması yönetilmeyen sürümü aynı düzeyde öngörülebilirlik garanti ile bir durum. `catch/finally` CER taşıdır. Blok yöntemlerinde ön hazırlık gerektirir ve noninterruptible olması gerekir.  
  
 .NET Framework sürüm 2. 0'da, kodu çalışma zamanı çağırarak, bir try güvenilir olduğunu bildirir <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> hemen try bloğunun önceki. <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>üye <xref:System.Runtime.CompilerServices.RuntimeHelpers>, derleyici desteği sınıfı. Çağrı <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> doğrudan derleyicileri aracılığıyla, kullanılabilirlik bekliyor.  
  
## <a name="noninterruptible-regions"></a>Noninterruptible bölgeleri  
 Noninterruptible bölge bir CER içine yönergeler kümesini gruplandırır.  
  
 .NET Framework sürüm 2.0, derleyici desteği aracılığıyla kullanılabilirlik bekleyen kullanıcı kodu kesilebilir olmayan bölgeleri ile bir güvenilir try/catch/öncesinde boş bir try/catch bloğu içeren finally oluşturur bir <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> yöntem çağrısı.  
  
## <a name="critical-finalizer-object"></a>Kritik sonlandırıcıyı nesnesi  
 A <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject> çöp toplama sonlandırıcıyı yürütecek garantiler. Ayırma sırasında sonlandırıcıyı ve kendi arama grafiği önceden hazırlanır. Sonlandırıcı yöntemi bir CER yürütür ve CERs ve sonlandırıcılar tüm kısıtlamalar uyma gerekir.  
  
 İçinden devralma türleri <xref:System.Runtime.InteropServices.SafeHandle> ve <xref:System.Runtime.InteropServices.CriticalHandle> CER içinde yürütme kendi sonlandırıcıyı olması garanti. Uygulama <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> içinde <xref:System.Runtime.InteropServices.SafeHandle> türetilmiş sınıfları tanıtıcı boşaltmak için gerekli herhangi bir kod yürütün.  
  
## <a name="code-not-permitted-in-cers"></a>Kod CERs içinde izin verilmiyor  
 Aşağıdaki işlemleri CERs içinde izin verilmiyor:  
  
-   Açık ayırma.  
  
-   Kilit alınıyor.  
  
-   Kutulama.  
  
-   Çok boyutlu dizi erişimi.  
  
-   Yansıma yoluyla yöntemini çağırır.  
  
-   <xref:System.Threading.Monitor.Enter%2A>veya <xref:System.IO.FileStream.Lock%2A>.  
  
-   Güvenlik denetimleri. Taleplerin gerçekleştirmek değil, yalnızca taleplerini bağlayın.  
  
-   <xref:System.Reflection.Emit.OpCodes.Isinst>ve <xref:System.Reflection.Emit.OpCodes.Castclass> COM nesneleri ve proxy'ler  
  
-   Alma veya saydam bir proxy alanlarını ayarlama.  
  
-   Seri hale getirme.  
  
-   İşlev işaretçileri ve temsilciler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenilirlik En İyi Yöntemleri](../../../docs/framework/performance/reliability-best-practices.md)
