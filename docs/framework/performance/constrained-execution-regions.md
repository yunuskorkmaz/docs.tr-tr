---
title: Kısıtlı Yürütme Bölgeleri
ms.date: 03/30/2017
helpviewer_keywords:
- constrained execution regions
- CERs
ms.assetid: 99354547-39c1-4b0b-8553-938e8f8d1808
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d4c1d07e2469a36c4b8e1ef7b8d90a80a3530ae3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097180"
---
# <a name="constrained-execution-regions"></a>Kısıtlı Yürütme Bölgeleri
Kısıtlı yürütme bölge (CER) güvenilir yönetilen kod yazmak için bir mekanizma bir parçasıdır. Bir CER alanında kod tamamen yürütülmesini engelleyen bant dışı özel durumları atma gelen ortak dil çalışma zamanı (CLR) kısıtlı bir alan tanımlar. Bu bölge içinde kullanıcı kodu bant dışı özel durumları atma neden olan kod yürütülmesini sınırlıdır. <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> Yöntemi hemen gelmelidir bir `try` blok ve işaretleri `catch`, `finally`, ve `fault` kısıtlı yürütme bölgeleri olarak engeller. Kısıtlı bölge işaretlenmiş bir kez kod yalnızca diğer güçlü bir güvenilirlik sözleşmeleri koduyla çağırmanız gerekir ve kod ayırmak veya gerekir kod hatalarını işlemek için hazırlanan sürece hazırlıksız ya da güvenilir olmayan yöntemleri sanal çağrı yapmak. İçinde bir CER yürütülmekte olan kod için CLR gecikmeler iş parçacığını durdurur.  
  
 Kısıtlı yürütme bölgeleri ek açıklamalı bir CLR farklı formlarında kullanılan `try` özellikle türetilen sınıflarda yürütme kritik sonlandırıcılar bloğunda <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject> sınıfı ve kod kullanılarak yürütülen <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> yöntemi.  
  
## <a name="cer-advance-preparation"></a>CER ön hazırlık  
 CLR CERs önceden bellek yetersiz koşullar önlemek için hazırlar. Ön hazırlık gerekli olduğundan CLR tam zamanında derleme veya tür yükleme sırasında bir bellek yetersizliği koşulu neden olmaz.  
  
 Geliştirici kodu bölge bir CER olduğunu belirtmek için gereklidir:  
  
-   Tam çağrı grafı sahip yöntemleri ve üst düzey CER bölge <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> uygulanan öznitelik hazır önceden. <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> Garanti etmez. yalnızca durum <xref:System.Runtime.ConstrainedExecution.Cer.Success> veya <xref:System.Runtime.ConstrainedExecution.Cer.MayFail>.  
  
-   Statik olarak, sanal gönderme gibi belirlenemiyor çağrıları için ön hazırlık gerçekleştirilemiyor. Kullanım <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> bu gibi durumlarda yöntemi. Kullanırken <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> yöntemi <xref:System.Runtime.ConstrainedExecution.PrePrepareMethodAttribute> özniteliği için kod temizleme uygulanması.  
  
## <a name="constraints"></a>Kısıtlamalar  
 Kullanıcılar, içinde bir CER yazmak kodun türünü kısıtlanmıştır. Kod, bir bant dışı özel neden olamaz, aşağıdaki işlemlerinden gibi neden olabilir:  
  
-   Açık ayırma.  
  
-   Kutulama.  
  
-   Bir kilit alınırken.  
  
-   Neredeyse hazır değil yöntemleri çağırma.  
  
-   Zayıf ya da yok güvenilirlik sözleşme ile arama yöntemleri.  
  
 .NET Framework sürüm 2. 0'da, bu kısıtlamaları yönergelerdir. Tanılama kod çözümleme araçları sağlanır.  
  
## <a name="reliability-contracts"></a>Güvenilirlik sözleşmeleri  
 <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> Güvenilirlik garantisi ve belirli bir yöntemin Bozulması durumunu belgeler özel bir özniteliktir.  
  
### <a name="reliability-guarantees"></a>Güvenilirlik garantisi  
 Güvenilirlik garantisi, tarafından temsil edilen <xref:System.Runtime.ConstrainedExecution.Cer> sabit listesi değerleri, belirli bir yöntemin güvenilirliğini derecesini gösterir:  
  
-   <xref:System.Runtime.ConstrainedExecution.Cer.MayFail>. Olağanüstü durumlarda, yöntem başarısız olabilir. Bu durumda, yöntem başarılı veya başarısız olmadığını çağıran Metoda bildirir. Yöntemin dönüş değeri bildirebilirsiniz emin olmak için bir CER yer almalıdır.  
  
-   <xref:System.Runtime.ConstrainedExecution.Cer.None>. Yöntemi, türün veya derlemenin bir CER kavramı vardır ve en büyük olasılıkla önemli bir risk azaltma durumu Bozulması olmadan bir CER içinde çağırmak güvenli. CER garanti avantajlarından almaz. Bu, aşağıdaki gelir:  
  
    1.  Olağanüstü durumlarda, yöntem başarısız olabilir.  
  
    2.  Yöntem olabilir veya başarısız olduğunu rapor edemeyebilir.  
  
    3.  Yöntem bir CER en olası senaryo kullanılacak yazılmaz.  
  
    4.  Yöntemi, tür veya derleme açıkça başarılı olması için tanımlanmamışsa, örtük olarak tanımlandığını <xref:System.Runtime.ConstrainedExecution.Cer.None>.  
  
-   <xref:System.Runtime.ConstrainedExecution.Cer.Success>. Olağanüstü durumlarda, yöntem başarılı olması garanti edilir. Bu düzeyde güvenilirlik elde etmek için her zaman, hatta zaman bunu CER olmayan bölge içinde çağrılır çağrılan yöntem etrafında bir CER oluşturmak. Bir yöntem başarı subjectively görüntülenebilir ancak amaçlanan, gerçekleştirir başarılı olur. Örneğin, sayısı ile işaretlemeyi `ReliabilityContractAttribute(Cer.Success)` bir CER altında çalışırken, her zaman öğelerin sayısını döndürür, gelir <xref:System.Collections.ArrayList> ve hiçbir zaman iç alanların belirsiz bir durumda bırakılabilir.  Ancak, <xref:System.Threading.Interlocked.CompareExchange%2A> yöntemi başarı değeri değil yerine bir yarış durumu nedeniyle yeni bir değerle gelebilir anlama ile de başarılı işaretlenir.  Anahtar yöntemi davranmaya belirtildiği şekilde davranan ve CER kodu, doğru ancak güvenilir olmayan kod gibi görünür ötesinde herhangi bir olağan dışı davranış beklenir yazılması gerekmez. noktasıdır.  
  
### <a name="corruption-levels"></a>Bozulma düzeyleri  
 Bozulma düzeyi temsil ettiği <xref:System.Runtime.ConstrainedExecution.Consistency> numaralandırma değerlerini göstermek verilen ortamda ne kadar durumu bozulmuş olabilir:  
  
-   <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain>. Olağanüstü durumlarda, ortak dil çalışma zamanı (CLR) geçerli uygulama etki alanında ilgili durum tutarlılık garantisi sağlar.  
  
-   <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptInstance>. Olağanüstü durumlarda yöntem geçerli örneğe durumu Bozulması sınırlamak için sağlanır.  
  
-   <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>, Özel koşullar altında CLR durumu tutarlılık; ilgili garanti sağlar. diğer bir deyişle, koşul, işlemin bozulmasına neden olabilir.  
  
-   <xref:System.Runtime.ConstrainedExecution.Consistency.WillNotCorruptState>. Olağanüstü durumlarda, yöntem durumunun bozulmasına neden olmayan garanti edilir.  
  
## <a name="reliability-trycatchfinally"></a>Güvenilirlik try/catch/finally  
 Güvenilirlik `try/catch/finally` olan bir özel durum işleme mekanizmasını ile yönetilmeyen sürümü aynı düzeyde öngörülebilirlik garanti eder. `catch/finally` CER bloğudur. Yöntem bloğunda ön hazırlık gerektirir ve noninterruptible olmalıdır.  
  
 .NET Framework 2.0 sürümünde, kodu çalışma zamanı çağırarak bir try güvenilir olduğunu bildirir <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> try bloğunun hemen öncesindeki. <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> bir üyesidir <xref:System.Runtime.CompilerServices.RuntimeHelpers>, derleyici desteği sınıfı. Çağrı <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> kullanılabilirliğini derleyiciler aracılığıyla doğrudan bekliyor.  
  
## <a name="noninterruptible-regions"></a>Noninterruptible bölgeleri  
 Noninterruptible bölge yönergeleri bir CER içine kümesini gruplar.  
  
 .NET Framework sürüm 2.0, derleyici desteği aracılığıyla kullanılabilirlik bekleyen bir güvenilir try/catch/öncesinde boş bir try/catch bloğu içeren finally ile kesilebilir olmayan bölgeleri kullanıcı kod oluşturur bir <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> yöntem çağrısı.  
  
## <a name="critical-finalizer-object"></a>Kritik bir sonlandırıcı nesnesi  
 A <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject> çöp toplama Sonlandırıcı yürütecek garanti eder. Ayırma sırasında Sonlandırıcı ve kendi çağrı grafı önceden hazırlanır. Sonlandırıcı yöntemi içinde bir CER yürütür ve CERs ve sonlandırıcılar tüm kısıtlamalar uyma gerekir.  
  
 Öğesinden devralan tüm türleri <xref:System.Runtime.InteropServices.SafeHandle> ve <xref:System.Runtime.InteropServices.CriticalHandle> içinde bir CER yürütme kendi Sonlandırıcı sahip olacağı garanti edilir. Uygulama <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> içinde <xref:System.Runtime.InteropServices.SafeHandle> türetilmiş sınıfları, tanıtıcı boşaltmak için gerekli herhangi bir kod yürütmek için.  
  
## <a name="code-not-permitted-in-cers"></a>Kod içinde CERs izin verilmez  
 Aşağıdaki işlemleri CERs içinde izin verilmez:  
  
-   Açık ayırmalar.  
  
-   Bir kilit alınırken.  
  
-   Kutulama.  
  
-   Çok boyutlu bir dizi erişim.  
  
-   Yansıma yoluyla yöntemini çağırır.  
  
-   <xref:System.Threading.Monitor.Enter%2A> veya <xref:System.IO.FileStream.Lock%2A>.  
  
-   Güvenlik denetimleri. Talepleri gerçekleştirmek değil, yalnızca taleplerini bağlantı.  
  
-   <xref:System.Reflection.Emit.OpCodes.Isinst> ve <xref:System.Reflection.Emit.OpCodes.Castclass> COM nesneleri ve proxy'ler  
  
-   Alma veya saydam bir proxy alanlarını ayarlama.  
  
-   Seri hale getirme.  
  
-   İşlev işaretçileri ve temsilciler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenilirlik En İyi Yöntemleri](../../../docs/framework/performance/reliability-best-practices.md)
