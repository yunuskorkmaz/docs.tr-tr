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
ms.openlocfilehash: 268acb01a6777315829378e6fd8c06c46d3136d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181757"
---
# <a name="releasehandlefailed-mda"></a>releaseHandleFailed MDA
Yönetilen `releaseHandleFailed` hata ayıklama yardımcısı (MDA) etkinleştirildiğinde, bir <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> sınıfın yöntemi türetilen <xref:System.Runtime.InteropServices.CriticalHandle> `false` <xref:System.Runtime.InteropServices.SafeHandle> veya döndürdüğünde geliştiricilere bildirmektir.  
  
## <a name="symptoms"></a>Belirtiler  
 Kaynak veya bellek sızıntıları.  Sınıfın <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> türünden kaynaklanan <xref:System.Runtime.InteropServices.SafeHandle> veya <xref:System.Runtime.InteropServices.CriticalHandle> başarısız olan yöntem, sınıf tarafından kapsüllenen kaynak serbest bırakılmamış veya temizlenmemiş olabilir.  
  
## <a name="cause"></a>Nedeni  
 Kullanıcılar, bu yöntemden <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> türeyen sınıflar <xref:System.Runtime.InteropServices.SafeHandle> oluşturuyorsa <xref:System.Runtime.InteropServices.CriticalHandle>veya bu yöntemin uygulanmasını sağlamalıdır; bu nedenle, koşullar bireysel kaynağa özgüdir. Ancak, gereksinimleri şunlardır:  
  
- <xref:System.Runtime.InteropServices.SafeHandle>ve <xref:System.Runtime.InteropServices.CriticalHandle> türleri hayati işlem kaynakları etrafında sarmalayıcıları temsil. Bir bellek sızıntısı işlemi zaman içinde kullanılamaz hale getirecek.  
  
- Yöntem <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> işlevini gerçekleştirmek için başarısız olmamalıdır. İşlem böyle bir kaynağı satın <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> aldıktan sonra, onu serbest bırakmanın tek yoludur. Bu nedenle, hata kaynak sızıntıları anlamına gelir.  
  
- Yürütme sırasında meydana gelen herhangi <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>bir hata , kaynak serbest bırakılması engelleyen, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> yöntemin kendisi uygulanmasında bir hatadır. Bu kod, işlevini yerine getirmek için başka biri tarafından yazılmış kodu çağırsa bile, sözleşmenin yerine getirildiğinden emin olmak programcının sorumluluğundadır.  
  
## <a name="resolution"></a>Çözüm  
 MDA bildirimini <xref:System.Runtime.InteropServices.SafeHandle> yükselten <xref:System.Runtime.InteropServices.CriticalHandle>belirli (veya) türünü kullanan kod gözden geçirilmeli ve ham tutamaç değerinin <xref:System.Runtime.InteropServices.SafeHandle> başka bir yerden ayıklandığı ve kopyalandığı yerler araştırılmalıdır. Ham tanıtıcı değerinin kullanımı <xref:System.Runtime.InteropServices.SafeHandle> artık <xref:System.Runtime.InteropServices.CriticalHandle> çalışma süresine göre izlenmediği için, bu, içindeki veya uygulamalardaki hataların olağan nedenidir. Ham tutamak kopyası daha sonra kapatılırsa, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> kapatma artık geçersiz olan aynı tutamaç üzerinde denendiği için daha sonra bir aramanın başarısız olmasına neden olabilir.  
  
 Yanlış tutamaç yinelemesinin neden olabilir çeşitli yolları vardır:  
  
- <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A> Yönteme yapılan çağrıları arayın. Bu yönteme yapılan aramalar son derece nadir olmalıdır ve bulduğunuz <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> herhangi <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> bir arama ve yöntemlerle çevrelenmelidir. Bu ikinci yöntemler, ham tutamaç değerinin güvenle kullanılabileceği kod bölgesini belirtir. Bu bölgenin dışında veya başvuru sayısı ilk etapta hiç artımlı değilse, tanıtıcı değeri herhangi bir zamanda <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> <xref:System.Runtime.InteropServices.SafeHandle.Close%2A> başka bir iş parçacığına yapılan bir çağrı yla geçersiz kılınabilir. Tüm kullanımları <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A> izlendikten sonra, ham sapın sonunda arayacak `CloseHandle` bir bileşene veya tutamacı serbest bırakacak başka bir alt düzey yerel yönteme teslim edilmemesini sağlamak için ham tutamacın izlediği yolu izlemelisiniz.  
  
- Geçerli bir ham tanıtıcı değeri <xref:System.Runtime.InteropServices.SafeHandle> ile baş harfe getirmek için kullanılan kodun tutamacın sahibi olduğundan emin olun. Bir <xref:System.Runtime.InteropServices.SafeHandle> tutamacı etrafında oluşturursanız, kodunuzu temel `ownsHandle` oluşturucuya parametre `false` ayarlamadan sahip <xref:System.Runtime.InteropServices.SafeHandle> değildir, o zaman hem de gerçek tutamaç <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> sahibi, <xref:System.Runtime.InteropServices.SafeHandle> yarışı kaybederse bir hataya yol açarak tutamacı kapatmayı deneyebilirsiniz.  
  
- Uygulama <xref:System.Runtime.InteropServices.SafeHandle> etki alanları arasında bir mareşal olduğunda, kullanılan <xref:System.Runtime.InteropServices.SafeHandle> türetmenin serileştirilebilir olarak işaretlendiğini onaylayın. Bir sınıfın <xref:System.Runtime.InteropServices.SafeHandle> serileştirilebilir hale getirildiği nadir durumlarda, <xref:System.Runtime.Serialization.ISerializable> arabirimi uygulamalı veya serileştirme ve deserialization işlemini el ile denetlemek için diğer tekniklerden birini kullanmalıdır. Varsayılan serileştirme eylemi, kapalı ham tutamak değerinin bityönünde bir klon oluşturmak olduğundan, <xref:System.Runtime.InteropServices.SafeHandle> aynı tutamacın ait olduğunu düşünen iki örnekle sonuçlanır. Her ikisi de <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> bir noktada aynı kolu aramak için çalışacağız. Bunu <xref:System.Runtime.InteropServices.SafeHandle> yapmak için ikinci başarısız olacaktır. A <xref:System.Runtime.InteropServices.SafeHandle> serihale ederken doğru eylem yolu, `DuplicateHandle` farklı bir yasal tanıtıcı kopyası yapmak için yerel tanıtıcı türünüz için işlevi veya benzer bir işlevi çağırmaktır. Tutamak türünüz bunu desteklemiyorsa, <xref:System.Runtime.InteropServices.SafeHandle> tür sarma sıcamı serileştirilebilir hale getirilemez.  
  
- Bir tanıtıcının nerede erken kapatıldığını izlemek mümkün olabilir, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> bu da yöntem nihayet çağrıldığında, örneğin `CloseHandle` işlevi işlemek için kullanılan yerel yordama bir hata ayıklama kesme noktası yerleştirerek bir hataya yol açabilir. Bu durum, sık sık bu tür rutinlerin ele uğraştığı yoğun trafik nedeniyle stres senaryoları ve hatta orta ölçekli fonksiyonel testler için mümkün olmayabilir. Arayanın kimliğini veya büyük olasılıkla tam bir yığın izini ve serbest bırakılan tanıtıcının değerini yakalamak için yerel sürüm yöntemini çağıran kodu niçin algılamaya yardımcı olabilir.  Tanıtıcı değeri, bu MDA tarafından bildirilen değerle karşılaştırılabilir.  
  
- `CloseHandle` İşlev aracılığıyla serbest bırakılabilen tüm Win32 tutamaçları gibi bazı yerel tanıtıcı türlerinin aynı tanıtıcı ad alanını paylaştığını unutmayın. Bir tutamaç türünün hatalı bir sürümü başka bir tür ile sorunlara neden olabilir. Örneğin, yanlışlıkla bir Win32 olay tutamacını iki kez kapatmak, görünüşte ilgisiz bir dosya tutamacının erken kapanmasına neden olabilir. Bu, iştiş kolu serbest bırakıldığında ve işleme değeri başka bir kaynağı izlemek için kullanılabilir hale geldiğinde olur, potansiyel olarak başka bir tür. Bu durumda ve hatalı bir ikinci sürüm tarafından takip edilirse, ilgisiz bir iş parçacığının tutamacı geçersiz kılınabilir.  
  
## <a name="effect-on-the-runtime"></a>Çalışma Süresi üzerindeki etkisi  
 Bu MDA'nın CLR üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıktı  
 Bir veya bir <xref:System.Runtime.InteropServices.SafeHandle> tutamacı <xref:System.Runtime.InteropServices.CriticalHandle> düzgün bir şekilde serbest bırakmak için başarısız olduğunu belirten bir ileti. Örnek:  
  
```output
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
 Aşağıda `releaseHandleFailed` MDA'yı etkinleştirebilecek bir kod örneği verilmiştir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma Hazırlama](../interop/interop-marshaling.md)
