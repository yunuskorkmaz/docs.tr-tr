---
title: releaseHandleFailed MDA
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), handles
- release handle failed
- CriticalHandle class, run-time errors
- releaseHandleFailed MDA
- ReleaseHandle method
- SafeHandle class, run-time errors
- MDAs (managed debugging assistants), handles
ms.assetid: 44cd98ba-95e5-40a1-874d-e8e163612c51
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 155cf7138d4074467195bdc1302e28c0789f93cf
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53151011"
---
# <a name="releasehandlefailed-mda"></a>releaseHandleFailed MDA
`releaseHandleFailed` Yönetilen hata ayıklama Yardımcısı (MDA) geliştiriciler bildirmek için etkinleştirilmiştir olduğunda <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> sınıfından türetilen bir sınıfın yöntemini <xref:System.Runtime.InteropServices.SafeHandle> veya <xref:System.Runtime.InteropServices.CriticalHandle> döndürür `false`.  
  
## <a name="symptoms"></a>Belirtiler  
 Kaynak veya bellek sızıntısı.  Varsa <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> türetilen sınıfın yöntemi <xref:System.Runtime.InteropServices.SafeHandle> veya <xref:System.Runtime.InteropServices.CriticalHandle> sınıfı tarafından Kapsüllenen kaynak değil yayımlanan veya olabilir Temizlenen sonra başarısız olur.  
  
## <a name="cause"></a>Sebep  
 Kullanıcılar uygulamasını sağlamalıdır <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> yöntemi, sınıfları oluşturursanız, türetilen <xref:System.Runtime.InteropServices.SafeHandle> veya <xref:System.Runtime.InteropServices.CriticalHandle>; bu nedenle, tek kaynak için belirli koşullar. Ancak, gereksinimleri aşağıda belirtilmiştir:  
  
-   <xref:System.Runtime.InteropServices.SafeHandle> ve <xref:System.Runtime.InteropServices.CriticalHandle> türleri sarmalayıcılar önemli işlem kaynaklarını temsil eder. Bir bellek sızıntısı işlemi kullanılamaz zamanla hale getirir.  
  
-   <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> Yöntemi kendi işlevini gerçekleştirmesi başarısız olmalıdır. Böyle bir kaynak işlemi aldıktan sonra <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> serbest tek yoludur. Bu nedenle, hata, kaynak sızıntılarını anlamına gelir.  
  
-   Yürütülmesi sırasında oluşan herhangi bir hata <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>kaynak sürümü kaydettiği, hatanın uygulamasında <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> yöntemi. Sözleşme yerine bile bu kodu kendi işlevini gerçekleştirmesi için başka biri tarafından yazılan kodu çağıran emin olmak için programcının sorumluluğundadır.  
  
## <a name="resolution"></a>Çözüm  
 Belirli kullanan kodu <xref:System.Runtime.InteropServices.SafeHandle> (veya <xref:System.Runtime.InteropServices.CriticalHandle>) MDA bildirimi harekete gözden geçirileceğini, yerleri burada ham işleyici değeri ayıklanır gelen arayan <xref:System.Runtime.InteropServices.SafeHandle> ve başka bir yerde kopyalanır. İçinde hata normal nedeni budur <xref:System.Runtime.InteropServices.SafeHandle> veya <xref:System.Runtime.InteropServices.CriticalHandle> uygulamaları ham işleyici değeri kullanımını sonra uzun olduğu için çalışma zamanı tarafından izlenir. Ham tanıtıcı kopyalama sonradan kapalıysa, bir sonraki açabilir <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> kapatma, artık geçersiz aynı tanıtıcı üzerinde çalıştığı için başarısız çağrı.  
  
 Yanlış işleyici çoğaltma durum ortaya çıkabilir çeşitli yollarla vardır:  
  
-   Aramak için Ara <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A> yöntemi. Bu yönteme çağrıları verebilmesine nadir ve bulduğunuz herhangi yapılan çağrılar tarafından çevrelenen <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> ve <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> yöntemleri. Bu ikinci yöntemleri, güvenli bir şekilde ham tanıtıcı değeri kullanılabilir kod bölge belirtin. Bu bölge dışında veya başvuru sayısı ilk başta hiçbir zaman artırılır, işleyici değeri herhangi bir zamanda bir çağrı tarafından geçersiz kılınabilir <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> veya <xref:System.Runtime.InteropServices.SafeHandle.Close%2A> başka bir iş parçacığı üzerinde. Bir kez tüm kullanımları <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A> izlenen aşağı, ham tanıtıcısını alır, değil. Bu sayede kapalı sonunda çağıracak bazı bileşenine emin olmak için yolu izlemelisiniz `CloseHandle` veya tanıtıcı yayımlayacaktır başka bir alt düzey yerel yöntemi.  
  
-   Başlatmak için kullanılan kod emin <xref:System.Runtime.InteropServices.SafeHandle> geçerli bir ham tanıtıcı, tanıtıcı değeri sahip. Oluşturursa, bir <xref:System.Runtime.InteropServices.SafeHandle> bir işleyici kodunuzu ayarlamadan sahip olmadığından `ownsHandle` parametresi `false` temel oluşturucu, sonra hem de <xref:System.Runtime.InteropServices.SafeHandle> ve gerçek tanıtıcı sahibi tanıtıcı kapatmak hata içinöndegelendeneyebilirsiniz<xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> varsa <xref:System.Runtime.InteropServices.SafeHandle> yarışı kaybeder.  
  
-   Olduğunda bir <xref:System.Runtime.InteropServices.SafeHandle> olan uygulama etki alanları arasında sıralanmış, onaylayın <xref:System.Runtime.InteropServices.SafeHandle> kullanılmasını türetme işaretlendi olarak seri hale getirilebilir. Burada sınıfından türetilen bir sınıf nadir durumlarda <xref:System.Runtime.InteropServices.SafeHandle> olmuştur seri hale getirilebilir yapılan, uygulamanız gerekir <xref:System.Runtime.Serialization.ISerializable> arabirim veya diğer tekniklerden birini serileştirme denetlemek için kullanın ve el ile işlem seri durumdan çıkarma. Varsayılan serileştirme eylemi iki kaynaklanan kapalı ham tanıtıcı değerin bit düzeyinde bir kopyasını oluşturmak için gerekli olmasıdır <xref:System.Runtime.InteropServices.SafeHandle> örnekleri aynı tanıtıcı oldukları düşünüyorum. Her ikisi de çağırmayı deneyin <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> belirli bir noktada aynı tutamacı. İkinci <xref:System.Runtime.InteropServices.SafeHandle> Bunu yapmak için başarısız olur. Doğru kurs serileştirilirken eyleminin bir <xref:System.Runtime.InteropServices.SafeHandle> çağırmaktır `DuplicateHandle` işlevi veya benzer bir işlev türü farklı yasal tanıtıcı kopyalanmasına işlemek için yerel. Tanıtıcı türüne bu desteklemiyorsa sonra <xref:System.Runtime.InteropServices.SafeHandle> türü, kaydırma yapılamıyor seri hale getirilebilir.  
  
-   Burada bir tanıtıcı erken kapatılıyor izlemek olası olabilir bir arıza öndeki olduğunda <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> yöntemi son çağrılır, tanıtıcı, örneğin serbest bırakmak için kullanılan yerel yordamı üzerinde bir hata ayıklayıcı kesme noktası yerleştirerek `CloseHandle` işlevi. Bu yoğun senaryolar veya böyle rutinleri genellikle uğraşmanız bile orta ölçekli işlevsel testleri yoğun trafik nedeniyle mümkün olmayabilir. Arayan veya büyük olasılıkla tam yığın izlemesi kimliğini ve yayımlanan tanıtıcı değeri yakalamak için yerel sürüm yöntemi çağıran kodu araç haline getirmek için yardımcı olabilir.  İşleyici değeri, bu mda'nın tarafından bildirilen değeri ile karşılaştırılabilir.  
  
-   Win32 gibi bazı yerel tanıtıcı türleri işleme, Not serbest bırakılabilir aracılığıyla `CloseHandle` işlev, aynı işleyici ad paylaşın. Bir tanıtıcı türü hatalı bir sürümünde başka sorunlara neden olabilir. Örneğin, yanlışlıkla bir Win32 olayı işleyicisi iki kez kapatma zamanından önce kapatılan bir görünüşe göre ilgisiz dosya tanıtıcısı neden olabilir. Bu tanıtıcıyı serbest bırakılır ve işleyici değeri başka bir türde olabilecek başka bir kaynak izlemek üzere kullanım için kullanılabilir olur. Bu olur ve hatalı ikinci bir yayın tarafından izlenen, ilgisiz bir iş parçacığı tanıtıcısı geçersiz.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi  
 Bu mda'nın CLR üzerinde etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
 Belirten bir ileti bir <xref:System.Runtime.InteropServices.SafeHandle> veya <xref:System.Runtime.InteropServices.CriticalHandle> düzgün tanıtıcıyı serbest bırakılamadı. Örneğin:  
  
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
 Etkinleştirebilmek için bir kod örneği verilmiştir `releaseHandleFailed` MDA.  
  
```csharp
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
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
