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
ms.openlocfilehash: 265344cb100a41cde5443cd0914dc66271aabf93
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216131"
---
# <a name="releasehandlefailed-mda"></a>releaseHandleFailed MDA
`releaseHandleFailed` yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilir, <xref:System.Runtime.InteropServices.SafeHandle> veya <xref:System.Runtime.InteropServices.CriticalHandle> türetilen bir sınıfın <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> yöntemi `false`döndürdüğünde geliştiricilere bildirimde bulunur.  
  
## <a name="symptoms"></a>Belirtiler  
 Kaynak veya bellek sızıntıları.  <xref:System.Runtime.InteropServices.SafeHandle> veya <xref:System.Runtime.InteropServices.CriticalHandle> ' den türetilen sınıfın <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> yöntemi başarısız olursa, sınıf tarafından kapsüllenmiş kaynak serbest bırakılmış veya temizlenmiş olabilir.  
  
## <a name="cause"></a>Nedeni  
 Kullanıcılar, <xref:System.Runtime.InteropServices.SafeHandle> veya <xref:System.Runtime.InteropServices.CriticalHandle>türetilen sınıflar oluşturduklarında <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> yönteminin uygulanmasını sağlamalıdır; Bu nedenle, koşullar bireysel kaynağa özgüdür. Ancak, gereksinimler aşağıdaki gibidir:  
  
- <xref:System.Runtime.InteropServices.SafeHandle> ve <xref:System.Runtime.InteropServices.CriticalHandle> türler, önemli işlem kaynakları etrafındaki sarmalayıcıları temsil eder. Bellek sızıntısı işlemi zaman içinde kullanılamaz hale getirir.  
  
- <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> yöntemi işlevini gerçekleştirememelidir. İşlem böyle bir kaynağı aldıktan sonra, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> serbest bırakmak için tek yoldur. Bu nedenle, hata kaynak sızıntılarını gösterir.  
  
- <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>yürütülmesi sırasında oluşan herhangi bir hata, kaynağın yayımlanmasından sonra, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> yönteminin bir uygulamasındaki hatadır. Bu kod, kendi işlevini gerçekleştirmek için başka biri tarafından yazılan kodu çağırıyor olsa bile, sözleşmenin karşılandığından emin olmak için programcının sorumluluğundadır.  
  
## <a name="resolution"></a>Çözüm  
 MDA bildirimini oluşturan belirli <xref:System.Runtime.InteropServices.SafeHandle> (veya <xref:System.Runtime.InteropServices.CriticalHandle>) türünü kullanan kod incelenmelidir, ham tanıtıcı değerinin <xref:System.Runtime.InteropServices.SafeHandle> ayıklandığı ve başka bir yere kopyalandığı yerleri aramalıdır. Ham tanıtıcı değerinin kullanımı artık çalışma zamanı tarafından izlenmediğinden, bu, <xref:System.Runtime.InteropServices.SafeHandle> veya <xref:System.Runtime.InteropServices.CriticalHandle> uygulamalarındaki hataların olağan nedendir. Ham tutamaç kopyası daha sonra kapatılırsa, daha sonra aynı tanıtıcıda bir kapatma denendiğinden daha sonra bir <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> çağrısının başarısız olmasına neden olabilir.  
  
 Yanlış tanıtıcı çoğaltmanın gerçekleşebileceği çeşitli yollar vardır:  
  
- <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A> metoduna yapılan çağrıları arayın. Bu yönteme yapılan çağrılar, nadir olarak seyrek kullanılmalıdır ve bulduğunuz her türlü, <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> ve <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> yöntemlerine yapılan çağrılarla çevrelenmelidir. Bu ikinci Yöntemler, ham tanıtıcı değerinin güvenli bir şekilde kullanılabileceği kod bölgesini belirtir. Bu bölgenin dışında veya başvuru sayısı ilk yerde hiç artmadıysa, tanıtıcı değeri başka bir iş parçacığında <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> veya <xref:System.Runtime.InteropServices.SafeHandle.Close%2A> çağrısıyla herhangi bir zamanda geçersiz kılınabilir. Tüm <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A> kullanımları aşağı izlendikten sonra, ham tanıtıcının, sonunda `CloseHandle` veya tanıtıcıyı oluşturacak başka bir alt düzey yerel yöntemi çağıran bazı bir bileşene kapalı olmamasını sağlamak için aldığı yolu izlemelisiniz.  
  
- Geçerli bir ham tanıtıcı değeri olan <xref:System.Runtime.InteropServices.SafeHandle> başlatmak için kullanılan kodun tanıtıcıya sahip olduğundan emin olun. Bir tutamacı etrafında bir <xref:System.Runtime.InteropServices.SafeHandle> oluşturursanız, kodunuzun temel oluşturucuda `false` için `ownsHandle` parametresini ayarlamamak zorunda kalmadan, her ikisi de <xref:System.Runtime.InteropServices.SafeHandle> ve gerçek tanıtıcı sahibi tanıtıcıyı kapatmaya çalışabilir ve bu da <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> bir hatayı kaybeder.<xref:System.Runtime.InteropServices.SafeHandle>  
  
- Uygulama etki alanları arasında bir <xref:System.Runtime.InteropServices.SafeHandle> sıralanmışsa, kullanılan <xref:System.Runtime.InteropServices.SafeHandle> Türetmenin seri hale getirilebilir olarak işaretlendiğinden emin olun. <xref:System.Runtime.InteropServices.SafeHandle> 'den türetilen bir sınıfın seri hale getirilebilir olduğu nadir durumlarda, <xref:System.Runtime.Serialization.ISerializable> arabirimini uygulamalıdır veya serileştirme ve seri durumdan çıkarma işlemini el ile denetlemek için diğer tekniklerin birini kullanmalıdır. Bu, varsayılan serileştirme eylemi iliştirilmiş ham tanıtıcı değerinin bit düzeyinde bir kopyasını oluşturmak olduğu için gereklidir, sonuçta iki <xref:System.Runtime.InteropServices.SafeHandle> örneği de aynı tanıtıcıya sahip olduğunu düşünmektedir. Her ikisi de aynı tanıtıcıda <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> bir noktada çağrı yapmayı dener. Bunu yapmak için ikinci <xref:System.Runtime.InteropServices.SafeHandle> başarısız olur. Bir <xref:System.Runtime.InteropServices.SafeHandle> serileştirilirken doğru eylem kursu, farklı bir yasal tanıtıcı kopyası oluşturmak için `DuplicateHandle` işlevini veya yerel tanıtıcı türü için benzer bir işlevi çağırmak olur. Tanıtıcı türü bunu desteklemiyorsa <xref:System.Runtime.InteropServices.SafeHandle> tür kaydırması seri hale getirilebilir yapılamaz.  
  
- Bir tanıtıcının erken kapatılmakta olduğunu izlemek mümkün olabilir, örneğin `CloseHandle` işlevi gibi tanıtıcıyı serbest bırakmak için kullanılan yerel yordama bir hata ayıklayıcı kesme noktası yerleştirilerek <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> yöntemi son çağrıldığında bir hata ile başa çıkabilir. Bu işlem, genellikle ile ilgili olan yoğun trafik nedeniyle, yük senaryoları veya hatta orta ölçekli işlevsel sınamalar için mümkün olmayabilir. Arayanın kimliğini veya büyük olasılıkla tam bir yığın izlemesini ve serbest bırakılmakta olan tanıtıcının değerini yakalamak için, yerel yayın yöntemini çağıran kodu işaretlememeye yardımcı olabilir.  Tanıtıcı değeri, bu MDA tarafından raporlanan değerle karşılaştırılabilir.  
  
- `CloseHandle` işlev aracılığıyla yayımlananan tüm Win32 tutamaçları gibi bazı yerel tanıtıcı türleri aynı tanıtıcı ad alanını paylaşır. Bir tanıtıcı türünün hatalı bir sürümü başka bir sorun oluşmasına neden olabilir. Örneğin, yanlışlıkla bir Win32 olay işleyicisini iki kez kapatmak, ilişkisiz bir dosya tutamacının zamanından önce kapanmasına yol açabilir. Bu, tanıtıcı serbest bırakıldığında ve tanıtıcı değeri başka bir kaynağı izlemek için kullanılabilir hale geldiğinde (büyük olasılıkla başka bir tür) gerçekleşir. Bu durumda ve ardından hatalı ikinci bir yayın varsa, ilgisiz bir iş parçacığının tanıtıcısı geçersiz kılınabilir.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıktı  
 Bir <xref:System.Runtime.InteropServices.SafeHandle> veya <xref:System.Runtime.InteropServices.CriticalHandle> tanıtıcıyı doğru bir şekilde serbest bırakmadığını belirten bir ileti. Örneğin:  
  
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
 Aşağıda `releaseHandleFailed` MDA ' i etkinleştirebilecek bir kod örneği verilmiştir.  
  
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
