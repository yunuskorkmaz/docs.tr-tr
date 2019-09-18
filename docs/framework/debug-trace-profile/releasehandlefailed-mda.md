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
ms.openlocfilehash: 41f6b67ff63d096cc1fa2c599abb06c9c1129952
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052304"
---
# <a name="releasehandlefailed-mda"></a>releaseHandleFailed MDA
<xref:System.Runtime.InteropServices.SafeHandle> <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> `false` <xref:System.Runtime.InteropServices.CriticalHandle> Yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilir, veya sınıfından türetilen bir sınıf yöntemi olduğunda geliştiricilere bildirimde bulunur. `releaseHandleFailed`  
  
## <a name="symptoms"></a>Belirtiler  
 Kaynak veya bellek sızıntıları.  Sınıfın yöntemi öğesinden <xref:System.Runtime.InteropServices.SafeHandle> türetiliyor veya <xref:System.Runtime.InteropServices.CriticalHandle> başarısız olursa, sınıf tarafından kapsüllenmiş kaynak serbest bırakılmış veya temizlenmiş olabilir. <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>  
  
## <a name="cause"></a>Sebep  
 Veya <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> <xref:System.Runtime.InteropServices.SafeHandle> ' den türetilen sınıflar oluşturduklarında, kullanıcıların yöntemi uygulamasını sağlaması gerekir; bu nedenle, koşullar ayrı kaynağa özgüdür. <xref:System.Runtime.InteropServices.CriticalHandle> Ancak, gereksinimler aşağıdaki gibidir:  
  
- <xref:System.Runtime.InteropServices.SafeHandle>ve <xref:System.Runtime.InteropServices.CriticalHandle> türler, önemli işlem kaynakları etrafındaki sarmalayıcıları temsil eder. Bellek sızıntısı işlemi zaman içinde kullanılamaz hale getirir.  
  
- Yöntemi <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> , işlevini gerçekleştirememelidir. İşlem böyle bir kaynağı aldıktan sonra, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> bunu serbest bırakmaya yönelik tek yoldur. Bu nedenle, hata kaynak sızıntılarını gösterir.  
  
- ' Nin <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>yürütülmesi sırasında oluşan herhangi bir hata, kaynağın serbest bırakılması sırasında oluşan bir hata, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> yöntemin kendi uygulamasındaki bir hatadır. Bu kod, kendi işlevini gerçekleştirmek için başka biri tarafından yazılan kodu çağırıyor olsa bile, sözleşmenin karşılandığından emin olmak için programcının sorumluluğundadır.  
  
## <a name="resolution"></a>Çözüm  
 MDA bildirimini oluşturan belirli <xref:System.Runtime.InteropServices.SafeHandle> (veya <xref:System.Runtime.InteropServices.CriticalHandle>) türü kullanan kod, ham tanıtıcı <xref:System.Runtime.InteropServices.SafeHandle> değerinin öğesinden ayıklanıp başka bir yerde kopyalandığı yerleri arayarak incelenmelidir. Ham tanıtıcı değerinin kullanımı artık çalışma zamanı tarafından <xref:System.Runtime.InteropServices.SafeHandle> izlenmediğinden, bu, veya <xref:System.Runtime.InteropServices.CriticalHandle> uygulamalarındaki hataların olağan nedendir. Ham tutamaç kopyası daha sonra kapatılırsa, bu durum artık geçersiz olan tanıtıcı aynı <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> tanıtıcıda denendiğinden sonraki çağrının başarısız olmasına neden olabilir.  
  
 Yanlış tanıtıcı çoğaltmanın gerçekleşebileceği çeşitli yollar vardır:  
  
- <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A> Yöntemine yapılan çağrıları arayın. Bu yönteme yapılan çağrılar, seyrek görülen bir şekilde yazılmalıdır ve bulduğunuz her türlü, <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> ve <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> yöntemlerine yapılan çağrılarla çevrelenmelidir. Bu ikinci Yöntemler, ham tanıtıcı değerinin güvenli bir şekilde kullanılabileceği kod bölgesini belirtir. Bu bölgenin dışında veya başvuru sayısı ilk yerde hiç artmadıysa, tanıtıcı değeri başka bir iş parçacığı üzerinde <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> veya <xref:System.Runtime.InteropServices.SafeHandle.Close%2A> üzerinde yapılan bir çağrı tarafından herhangi bir zamanda geçersiz kılınabilir. ' Nin <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A> tüm kullanımları izlendikten sonra, ham tanıtıcının, sonunda çağrı `CloseHandle` yapılacak bir bileşen veya tanıtıcıyı serbest bırakılacak başka bir alt düzey yerel yöntem için kullanıma almadığından emin olmak için bu yolu izlemelisiniz.  
  
- Geçerli bir ham tanıtıcı değeri <xref:System.Runtime.InteropServices.SafeHandle> ile başlatmak için kullanılan kodun tanıtıcıya sahip olduğundan emin olun. Bir tanıtıcı etrafında bir <xref:System.Runtime.InteropServices.SafeHandle> `ownsHandle` parametre oluşturduğunuzda, kodunuzun temel oluşturucuda öğesine `false` ayarlamadan önce, hem <xref:System.Runtime.InteropServices.SafeHandle> hem de gerçek tutamaç sahibi tanıtıcıyı kapatmaya çalışabilir, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> Eğer ,<xref:System.Runtime.InteropServices.SafeHandle> yarış durumu kaybeder.  
  
- Uygulama etki <xref:System.Runtime.InteropServices.SafeHandle> alanları arasında bir sıraya eklendiğinde, kullanılan <xref:System.Runtime.InteropServices.SafeHandle> Türetmenin seri hale getirilebilir olarak işaretlendiğinden emin olun. Öğesinden <xref:System.Runtime.InteropServices.SafeHandle> türetilen bir sınıfın seri hale getirilebilir olduğu nadir durumlarda, <xref:System.Runtime.Serialization.ISerializable> arabirimini uygulamalıdır veya serileştirme ve seri durumdan çıkarma işlemini el ile denetlemek için diğer tekniklerin birini kullanmalıdır. Bu, varsayılan serileştirme eylemi, iliştirilmiş ham tanıtıcı değerinin bit düzeyinde bir kopyasını oluşturmak olduğu için gereklidir, sonuçta iki <xref:System.Runtime.InteropServices.SafeHandle> örnek de aynı tutamaya sahip olduğunu düşünmektedir. Her ikisi de aynı tanıtıcıda bir noktada çağrı <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> yapmayı dener. Bunu yapmak <xref:System.Runtime.InteropServices.SafeHandle> için ikinci işlem başarısız olur. Bir <xref:System.Runtime.InteropServices.SafeHandle> işlem serileştirilirken doğru eylem kursu, farklı bir yasal tanıtıcı `DuplicateHandle` kopyası oluşturmak için yerel tanıtıcı türü için işlevi veya benzer bir işlevi çağırmak olur. Tanıtıcı türü bunu <xref:System.Runtime.InteropServices.SafeHandle> desteklemiyorsa tür kaydırması seri hale getirilebilir yapılamaz.  
  
- Bir tanıtıcının erken kapatılmakta olduğunu izlemek mümkün olabilir, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> `CloseHandle` Örneğin, işleyiciyi serbest bırakmak için kullanılan yerel yordama bir hata ayıklayıcı kesme noktası yerleştirilerek, yöntemin son çağrıldığı bir hata ile başa dön, örneğin işlev. Bu işlem, genellikle ile ilgili olan yoğun trafik nedeniyle, yük senaryoları veya hatta orta ölçekli işlevsel sınamalar için mümkün olmayabilir. Arayanın kimliğini veya büyük olasılıkla tam bir yığın izlemesini ve serbest bırakılmakta olan tanıtıcının değerini yakalamak için, yerel yayın yöntemini çağıran kodu işaretlememeye yardımcı olabilir.  Tanıtıcı değeri, bu MDA tarafından raporlanan değerle karşılaştırılabilir.  
  
- `CloseHandle` İşlev aracılığıyla yayımlanabileceği tüm Win32 tutamaçları gibi bazı yerel tanıtıcı türleri aynı tanıtıcı ad alanını paylaşır. Bir tanıtıcı türünün hatalı bir sürümü başka bir sorun oluşmasına neden olabilir. Örneğin, yanlışlıkla bir Win32 olay işleyicisini iki kez kapatmak, ilişkisiz bir dosya tutamacının zamanından önce kapanmasına yol açabilir. Bu, tanıtıcı serbest bırakıldığında ve tanıtıcı değeri başka bir kaynağı izlemek için kullanılabilir hale geldiğinde (büyük olasılıkla başka bir tür) gerçekleşir. Bu durumda ve ardından hatalı ikinci bir yayın varsa, ilgisiz bir iş parçacığının tanıtıcısı geçersiz kılınabilir.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
 <xref:System.Runtime.InteropServices.SafeHandle> Bir<xref:System.Runtime.InteropServices.CriticalHandle> veya ' nin tanıtıcıyı doğru bir şekilde serbest bırakmadığını belirten bir ileti. Örneğin:  
  
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
 Aşağıda, `releaseHandleFailed` mda ' i etkinleştirebilecek bir kod örneği verilmiştir.  
  
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
- [Birlikte Çalışma için Hazırlama](../interop/interop-marshaling.md)
