---
title: releaseHandleFailed MDA
description: .NET 'teki kaynak veya bellek sızıntıları nedeniyle etkinleştirilebilecek releaseHandleFailed Managed hata ayıklama Yardımcısı 'nı (MDA) gözden geçirin.
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
ms.openlocfilehash: 167a304b4571aa35f758a2054caf6ae1c60a3c60
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803644"
---
# <a name="releasehandlefailed-mda"></a>releaseHandleFailed MDA
`releaseHandleFailed`Yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilir, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> veya sınıfından türetilen bir sınıf yöntemi olduğunda geliştiricilere bildirimde bulunur <xref:System.Runtime.InteropServices.SafeHandle> <xref:System.Runtime.InteropServices.CriticalHandle> `false` .  
  
## <a name="symptoms"></a>Belirtiler  
 Kaynak veya bellek sızıntıları.  <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>Sınıfın yöntemi öğesinden türetiliyor <xref:System.Runtime.InteropServices.SafeHandle> veya <xref:System.Runtime.InteropServices.CriticalHandle> başarısız olursa, sınıf tarafından kapsüllenmiş kaynak serbest bırakılmış veya temizlenmiş olabilir.  
  
## <a name="cause"></a>Nedeni  
 <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>Veya ' den türetilen sınıflar oluşturduklarında, kullanıcıların yöntemi uygulamasını sağlaması gerekir; bu <xref:System.Runtime.InteropServices.SafeHandle> <xref:System.Runtime.InteropServices.CriticalHandle> nedenle, koşullar ayrı kaynağa özgüdür. Ancak, gereksinimler aşağıdaki gibidir:  
  
- <xref:System.Runtime.InteropServices.SafeHandle>ve <xref:System.Runtime.InteropServices.CriticalHandle> türler, önemli işlem kaynakları etrafındaki sarmalayıcıları temsil eder. Bellek sızıntısı işlemi zaman içinde kullanılamaz hale getirir.  
  
- <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>Yöntemi, işlevini gerçekleştirememelidir. İşlem böyle bir kaynağı aldıktan sonra, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> bunu serbest bırakmaya yönelik tek yoldur. Bu nedenle, hata kaynak sızıntılarını gösterir.  
  
- ' Nin yürütülmesi sırasında oluşan herhangi bir hata, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> kaynağın serbest bırakılması sırasında oluşan bir hata, yöntemin kendi uygulamasındaki bir hatadır <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> . Bu kod, kendi işlevini gerçekleştirmek için başka biri tarafından yazılan kodu çağırıyor olsa bile, sözleşmenin karşılandığından emin olmak için programcının sorumluluğundadır.  
  
## <a name="resolution"></a>Çözüm  
 <xref:System.Runtime.InteropServices.SafeHandle>MDA bildirimini oluşturan belirli (veya) türü kullanan kod, <xref:System.Runtime.InteropServices.CriticalHandle> Ham tanıtıcı değerinin öğesinden <xref:System.Runtime.InteropServices.SafeHandle> ayıklanıp başka bir yerde kopyalandığı yerleri arayarak incelenmelidir. <xref:System.Runtime.InteropServices.SafeHandle> <xref:System.Runtime.InteropServices.CriticalHandle> Ham tanıtıcı değerinin kullanımı artık çalışma zamanı tarafından izlenmediğinden, bu, veya uygulamalarındaki hataların olağan nedendir. Ham tutamaç kopyası daha sonra kapatılırsa, bu durum <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> artık geçersiz olan tanıtıcı aynı tanıtıcıda denendiğinden sonraki çağrının başarısız olmasına neden olabilir.  
  
 Yanlış tanıtıcı çoğaltmanın gerçekleşebileceği çeşitli yollar vardır:  
  
- Yöntemine yapılan çağrıları arayın <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A> . Bu yönteme yapılan çağrılar, seyrek görülen bir şekilde yazılmalıdır ve bulduğunuz her türlü, ve yöntemlerine yapılan çağrılarla çevrelenmelidir <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> . Bu ikinci Yöntemler, ham tanıtıcı değerinin güvenli bir şekilde kullanılabileceği kod bölgesini belirtir. Bu bölgenin dışında veya başvuru sayısı ilk yerde hiç artmadıysa, tanıtıcı değeri <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> <xref:System.Runtime.InteropServices.SafeHandle.Close%2A> başka bir iş parçacığı üzerinde veya üzerinde yapılan bir çağrı tarafından herhangi bir zamanda geçersiz kılınabilir. ' Nin tüm kullanımları <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A> izlendikten sonra, ham tanıtıcının, sonunda çağrı yapılacak `CloseHandle` bir bileşen veya tanıtıcıyı serbest bırakılacak başka bir alt düzey yerel yöntem için kullanıma almadığından emin olmak için bu yolu izlemelisiniz.  
  
- <xref:System.Runtime.InteropServices.SafeHandle>Geçerli bir ham tanıtıcı değeri ile başlatmak için kullanılan kodun tanıtıcıya sahip olduğundan emin olun. Bir <xref:System.Runtime.InteropServices.SafeHandle> tanıtıcı etrafında bir `ownsHandle` parametre oluşturduğunuzda, kodunuzun temel oluşturucuda öğesine ayarlamadan önce, `false` hem hem de <xref:System.Runtime.InteropServices.SafeHandle> gerçek tutamaç sahibi tanıtıcıyı kapatmayı deneyebilir, bu da, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> <xref:System.Runtime.InteropServices.SafeHandle> yarış durumu kaybederse içindeki bir hataya önde gelen bir hataya neden olabilir.  
  
- <xref:System.Runtime.InteropServices.SafeHandle>Uygulama etki alanları arasında bir sıraya eklendiğinde, <xref:System.Runtime.InteropServices.SafeHandle> kullanılan Türetmenin seri hale getirilebilir olarak işaretlendiğinden emin olun. Öğesinden türetilen bir sınıfın <xref:System.Runtime.InteropServices.SafeHandle> seri hale getirilebilir olduğu nadir durumlarda, <xref:System.Runtime.Serialization.ISerializable> arabirimini uygulamalıdır veya serileştirme ve seri durumdan çıkarma işlemini el ile denetlemek için diğer tekniklerin birini kullanmalıdır. Bu, varsayılan serileştirme eylemi, iliştirilmiş ham tanıtıcı değerinin bit düzeyinde bir kopyasını oluşturmak olduğu için gereklidir, sonuçta iki <xref:System.Runtime.InteropServices.SafeHandle> örnek de aynı tutamaya sahip olduğunu düşünmektedir. Her ikisi de <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> aynı tanıtıcıda bir noktada çağrı yapmayı dener. <xref:System.Runtime.InteropServices.SafeHandle>Bunu yapmak için ikinci işlem başarısız olur. Bir işlem serileştirilirken doğru eylem kursu, <xref:System.Runtime.InteropServices.SafeHandle> `DuplicateHandle` farklı bir yasal tanıtıcı kopyası oluşturmak için yerel tanıtıcı türü için işlevi veya benzer bir işlevi çağırmak olur. Tanıtıcı türü bunu desteklemiyorsa <xref:System.Runtime.InteropServices.SafeHandle> tür kaydırması seri hale getirilebilir yapılamaz.  
  
- Bir tanıtıcının erken kapatılmakta olduğunu izlemek mümkün olabilir, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> Örneğin, işleyiciyi serbest bırakmak için kullanılan yerel yordama bir hata ayıklayıcı kesme noktası yerleştirilerek, yöntemin son çağrıldığı bir hata ile başa dön, örneğin `CloseHandle` işlev. Bu işlem, genellikle ile ilgili olan yoğun trafik nedeniyle, yük senaryoları veya hatta orta ölçekli işlevsel sınamalar için mümkün olmayabilir. Arayanın kimliğini veya büyük olasılıkla tam bir yığın izlemesini ve serbest bırakılmakta olan tanıtıcının değerini yakalamak için, yerel yayın yöntemini çağıran kodu işaretlememeye yardımcı olabilir.  Tanıtıcı değeri, bu MDA tarafından raporlanan değerle karşılaştırılabilir.  
  
- İşlev aracılığıyla yayımlanabileceği tüm Win32 tutamaçları gibi bazı yerel tanıtıcı türleri `CloseHandle` aynı tanıtıcı ad alanını paylaşır. Bir tanıtıcı türünün hatalı bir sürümü başka bir sorun oluşmasına neden olabilir. Örneğin, yanlışlıkla bir Win32 olay işleyicisini iki kez kapatmak, ilişkisiz bir dosya tutamacının zamanından önce kapanmasına yol açabilir. Bu, tanıtıcı serbest bırakıldığında ve tanıtıcı değeri başka bir kaynağı izlemek için kullanılabilir hale geldiğinde (büyük olasılıkla başka bir tür) gerçekleşir. Bu durumda ve ardından hatalı ikinci bir yayın varsa, ilgisiz bir iş parçacığının tanıtıcısı geçersiz kılınabilir.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıktı  
 Bir veya ' nin <xref:System.Runtime.InteropServices.SafeHandle> <xref:System.Runtime.InteropServices.CriticalHandle> tanıtıcıyı doğru bir şekilde serbest bırakmadığını belirten bir ileti. Örneğin:  
  
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
 Aşağıda, MDA ' i etkinleştirebilecek bir kod örneği verilmiştir `releaseHandleFailed` .  
  
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
