---
title: releaseHandleFailed MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed debugging assistants (MDAs), handles
- release handle failed
- CriticalHandle class, run-time errors
- releaseHandleFailed MDA
- ReleaseHandle method
- SafeHandle class, run-time errors
- MDAs (managed debugging assistants), handles
ms.assetid: 44cd98ba-95e5-40a1-874d-e8e163612c51
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cbd6e2a52eb576f321dfa7dda5682d325f554158
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="releasehandlefailed-mda"></a>releaseHandleFailed MDA
`releaseHandleFailed` Yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilmiş ise geliştiriciler bildirmek için zaman <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> yöntemi bir sınıfın türetilen <xref:System.Runtime.InteropServices.SafeHandle> veya <xref:System.Runtime.InteropServices.CriticalHandle> döndürür `false`.  
  
## <a name="symptoms"></a>Belirtiler  
 Kaynak veya bellek sızıntıları.  Varsa <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> türetme sınıfının yöntemi <xref:System.Runtime.InteropServices.SafeHandle> veya <xref:System.Runtime.InteropServices.CriticalHandle> sınıfı tarafından kapsüllenmiş kaynak değil yayımlanan veya olabilir Temizlenen sonra başarısız olur.  
  
## <a name="cause"></a>Sebep  
 Kullanıcılar, uygulama sağlamalıdır <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> , sınıfları oluşturursanız, yöntemi türetilen <xref:System.Runtime.InteropServices.SafeHandle> veya <xref:System.Runtime.InteropServices.CriticalHandle>; bu nedenle, koşullar tek tek kaynak için belirli. Ancak, gereksinimleri şunlardır:  
  
-   <xref:System.Runtime.InteropServices.SafeHandle>ve <xref:System.Runtime.InteropServices.CriticalHandle> türleri önemli işlem kaynakları çevresinde sarmalayıcıları temsil eder. Bellek sızıntısı işlemi zamanla kullanılamamasına neden.  
  
-   <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> Yöntemi kendi işlevini gerçekleştirmesi başarısız olmalıdır. Böyle bir kaynak işlemi aldıktan sonra <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> serbest tek yoludur. Bu nedenle, hata kaynak sızıntıları anlamına gelir.  
  
-   Yürütülmesi sırasında oluşan herhangi bir hata <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>, kaynak sürümü engelleyen, hatanın uygulamasında <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> yöntemin kendisi. Bu kod, kendi işlevini gerçekleştirmesi için başka bir kullanıcı tarafından yazılan kodu çağırır olsa bile sözleşme yerine getirildiğinden emin olmak için programcı sorumluluğundadır.  
  
## <a name="resolution"></a>Çözüm  
 Belirli kullanan kodu <xref:System.Runtime.InteropServices.SafeHandle> (veya <xref:System.Runtime.InteropServices.CriticalHandle>) MDA bildirim yükseltilmiş türü gözden geçirileceğini, yerler ham tanıtıcı değeri ayıkladığınız gelen arayan <xref:System.Runtime.InteropServices.SafeHandle> ve başka bir yerde kopyalanır. Bu normal içinde başarısızlık nedeni <xref:System.Runtime.InteropServices.SafeHandle> veya <xref:System.Runtime.InteropServices.CriticalHandle> uygulamaları ham tanıtıcı değeri kullanımını sonra artık olmadığından çalışma zamanı tarafından izlenir. Ham tanıtıcı kopyalama sonradan kapattıysanız, daha sonra sunabilir <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> çağrısı close an geçersiz aynı tanıtıcı üzerinde çalıştığı için başarısız.  
  
 Yanlış işleyici çoğaltma oluşabilen çeşitli yollarla vardır:  
  
-   Aramak için Ara <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A> yöntemi. Bu yönteme çağrıları verebilmesine nadir ve bulduğunuz herhangi yapılan çağrılar tarafından çevrelenen <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> ve <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> yöntemleri. Bu ikinci yöntemleri bölge içinde güvenle ham tanıtıcı değeri kullanılabilir kodu belirtin. Bu bölge dışında veya başvuru sayısı hiçbir zaman ilk başta artırılır, tanıtıcı değeri herhangi bir anda bir çağrı tarafından geçersiz <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> veya <xref:System.Runtime.InteropServices.SafeHandle.Close%2A> başka bir iş parçacığı üzerinde. Bir kez tüm kullanımlarını <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A> izlendiği aşağı, yolun ham işleyicisini alır, değil karmalayan kapalı sonunda çağıracak bazı bileşenine emin olmak için izlemeniz gereken `CloseHandle` veya tanıtıcı yayın başka bir alt düzey yerel yöntemi.  
  
-   Başlatmak için kullanılan kod emin <xref:System.Runtime.InteropServices.SafeHandle> tanıtıcı değeri geçerli bir ham tanıtıcı sahip. Form, bir <xref:System.Runtime.InteropServices.SafeHandle> bir tanıtıcı kodunuzu ayarlamadan sahip olmadığından `ownsHandle` parametresi `false` temel oluşturucuyu ve ardından her ikisini de <xref:System.Runtime.InteropServices.SafeHandle> ve gerçek tanıtıcı sahibi tanıtıcı kapatmak birhatailesonuçlanandeneyebilirsiniz<xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> varsa <xref:System.Runtime.InteropServices.SafeHandle> yarış kaybeder.  
  
-   Zaman bir <xref:System.Runtime.InteropServices.SafeHandle> olan uygulama etki alanları arasında sıralanmış, onaylayın <xref:System.Runtime.InteropServices.SafeHandle> kullanılan türetme işaretlendi olarak serileştirilebilir. Burada bir sınıf türetilen nadir durumlarda <xref:System.Runtime.InteropServices.SafeHandle> bırakıldı seri hale getirilebilir yapılan, uygulamanız gerekir <xref:System.Runtime.Serialization.ISerializable> arabirimi veya başka teknikler birini serileştirme denetlemek için kullanın ve işlemi el ile seri durumundan çıkarma. Varsayılan seri hale getirme eylem iki kaynaklanan kapalı ham tanıtıcı değer Bitsel bir kopyasını oluşturmak için gerekli olmasıdır <xref:System.Runtime.InteropServices.SafeHandle> aynı tutamaç oldukları düşünüyorum örnekleri. Her ikisi de çağırmak deneyecek <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> belirli bir noktada aynı tutamacı. İkinci <xref:System.Runtime.InteropServices.SafeHandle> Bunu yapmak için başarısız olur. Serileştirilirken eylem doğru seyri bir <xref:System.Runtime.InteropServices.SafeHandle> çağırmaktır `DuplicateHandle` işlevi veya ayrı yasal tanıtıcı kopyasının türünü işlemek yerel için benzer bir işlev. Tanıtıcı türü bu desteklemiyorsa sonra <xref:System.Runtime.InteropServices.SafeHandle> , sarmalama türü yapılamaz seri hale getirilebilir.  
  
-   Burada bir tanıtıcı erken, kapatıldığını izlemenizi mümkün olabilir önde gelen bir hata olduğunda <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> yöntemi son çağrılır, tanıtıcı örneğin serbest bırakmak için kullanılan yerel yordamı üzerinde bir hata ayıklayıcı kesme noktası koyarak `CloseHandle` işlevi. Bu stres senaryoları veya uğraşmanız genellikle böyle yordamları bile orta ölçekli işlevsel testleri yoğun trafik nedeniyle mümkün olmayabilir. Çağıran veya büyük olasılıkla tam yığın izlemesi kimliğini ve yayımlanan tanıtıcı değerini yakalamak üzere yerel yayın yöntemini çağıran kodu işaretlemesini yardımcı olabilir.  Tanıtıcı değeri, bu MDA tarafından bildirilen değeri ile karşılaştırılabilir.  
  
-   Tüm Win32 gibi bazı yerel işleyici türleri işleme, Not serbest bırakılabilir aracılığıyla `CloseHandle` işlev, aynı işleyici ad paylaşın. Bir tanıtıcı türü hatalı bir sürümü başka sorunlara neden olabilir. Örneğin, yanlışlıkla bir Win32 olay işleyicisi iki kez kapatma erken kapatılan bir görünüşe göre ilgisiz dosya tanıtıcısı neden olabilir. Bu tanıtıcıyı yayımlanan ve tanıtıcı değer büyük olasılıkla başka bir türde başka bir kaynak izlemek kullanılmak üzere kullanılabilir olur. Bu olur ve bir hatalı ikinci sürüm tarafından izlenir, ilgisiz bir iş parçacığı tanıtıcısı geçersiz.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 Bu MDA CLR üzerinde etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
 Belirten bir ileti bir <xref:System.Runtime.InteropServices.SafeHandle> veya <xref:System.Runtime.InteropServices.CriticalHandle> düzgün işleyici yayınlama başarısız oldu. Örneğin:  
  
```  
"A SafeHandle or CriticalHandle of type 'MyBrokenSafeHandle'   
failed to properly release the handle with value 0x0000BEEF. This   
usually indicates that the handle was released incorrectly via   
another means (such as extracting the handle using DangerousGetHandle   
and closing it directly or building another SafeHandle around it."  
```  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <releaseHandleFailed/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki etkinleştirebilirsiniz bir kod örneğidir `releaseHandleFailed` MDA.  
  
```  
bool ReleaseHandle()  
{  
    // Calling the Win32 CloseHandle function to release the   
    // native handle wrapped by this SafeHandle. This method returns   
    // false on failure, but should only fail if the input is invalid   
    // (which should not happen here). The method specifically must not   
    // fail simply because of lack of resources or other transient   
    // failures beyond the user’s control. That would make it unacceptable   
    // to call CloseHandle as part of the implementation of this method.  
    return CloseHandle(handle);  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Yönetilen hata ayıklama Yardımcıları ile hataları tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Birlikte çalışma hazırlama](../../../docs/framework/interop/interop-marshaling.md)
