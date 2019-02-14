---
title: Hata işleme
ms.date: 03/30/2017
ms.assetid: c948841a-7db9-40ae-9b78-587d216cbcaf
ms.openlocfilehash: ddc3921fbb6b453db43ed3939134650395ade670
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2019
ms.locfileid: "56261160"
---
# <a name="error-handling"></a>Hata işleme
## <a name="error-handling-in-windows-communication-foundation"></a>Windows Communication Foundation işleme hatası  
 Bir hizmet bir beklenmeyen özel durum veya hata ile karşılaştığında, bir özel durum işleme çözümü tasarlamak için birden çok yolu vardır. Varken hiçbir tek "doğru" veya "en iyi uygulama" hata işleme çözüm, birden fazla geçerli yol için dikkate alınması gereken bir vardır. Normalde bir işlenmemiş yapısını birden çok yaklaşımın WCF uygulaması, tür ve özel durumları, işlenmiş sıklığını karmaşıklığına bağlı olarak, aşağıdaki listeden bir araya getiren karma çözümü uygulamanız önerilir özel durumlar ve tüm izleme, günlüğe kaydetme ve ilke gereksinimlerinizi ilişkili.  
  
 Bu çözümler, bu bölümün geri kalanında daha derin bir şekilde açıklanmıştır.  
  
### <a name="the-microsoft-enterprise-library"></a>Microsoft Kurumsal kitaplığı  
 Microsoft Kurumsal kitaplık özel durum işleme uygulama bloğu, sık karşılaşılan tasarım desenleri uygulamak ve kuruluş uygulaması mimari katmanları tüm oluşan özel durumları işlemek için bir tutarlı stratejisi oluşturma yardımcı olur. Uygulama bileşenleri catch deyimlerinde yer alan tipik kod desteklemek için tasarlanmıştır. Bu kod (örneğin, özel durum bilgilerini kaydeden kod) uygulamanın tamamında aynı catch bloğu içinde yinelenen yerine, geliştiricilere yeniden kullanılabilir bir özel durum işleyicileri olarak bu mantığı yalıtılacak özel durum işleme uygulama bloğu sağlar.  
  
 Bu kitaplık,-hazır bir hataya sözleşme özel durum işleyicisi içerir. Bu özel durum işleyicisi, Windows® Communication Foundation (WCF) hizmet sınırlarındaki kullanılmak üzere tasarlanmış ve yeni bir hata sözleşme özel durumu oluşturur.  
  
 Yaygın olarak kullanılan en iyi uygulamaları ekleyebilir ve özel durum işleme uygulamanız genelinde yaygın bir yaklaşım sağlamak için uygulama blokları hedeflenir. Öte yandan, özel hata işleyicilerini ve hata sözleşmelerine birinin üzerinde kendi geliştirilen ayrıca çok kullanışlı olabilir. Örneğin, özel hata işleyicilerini FaultExceptions için tüm özel durumları otomatik olarak Yükselt ve günlüğe kaydetme özellikleri uygulamanıza eklemek için mükemmel bir fırsat sağlar.  
  
 Daha fazla bilgi için lütfen bkz [Microsoft Enterprise Library](https://docs.microsoft.com/previous-versions/msp-n-p/ff632023(v=pandp.10)).  
  
### <a name="dealing-with-expected-exceptions"></a>Beklenen özel durumlar uğraşmanızı  
 Eylemin doğru kurs olan her işlem ya da ilgili genişletilebilirlik noktası beklenen özel durumları yakalamak için bunlar gelen kurtarılabilir bir FaultException içinde uygun özel hata dönüş bildirmeyeceğinize karar verdikten sonra\<T >  
  
### <a name="dealing-with-unexpected-exceptions-using-an-ierrorhandler"></a>Beklenmeyen bir Ierrorhandler kullanarak özel durumları ile ilgilenme  
 Beklenmeyen özel durumlar için önerilen eylem çalıştıysa "bir Ierrorhandler kanca" sağlamaktır. Hata işleyicilerini yalnızca özel durumları yakalama WCF çalışma zamanı düzeyinde ("hizmet modeli" katman), kanal katmanda değil. Kanal düzeyinde bir Ierrorhandler yeteneklerinizi tek yolu, çoğu senaryoda önerilmez özel bir kanal oluşturmaktır.  
  
 "Beklenmeyen bir özel durum" genellikle kurtarılamaz bir özel durum ya da bir işlem özel durumu olan; Bu, bunun yerine, beklenmeyen bir kullanıcı özel durumdur. Kurtarılamaz bir özel durum (bir bellek yetersiz özel durum gibi) – bir genel olarak işlenen tarafından [hizmet modeli özel durum işleyicisi](xref:System.ServiceModel.Dispatcher.ExceptionHandler) otomatik olarak – genellikle düzgün bir şekilde, işlenemez ve yalnızca nedeni böyle bir özel durum işleme Ek günlükler yapmak hiç olabilir veya standart bir özel durum istemciye döndürmek için. Genellikle çok erken ya da çok geç tarafından müdahale hata işleyicisi olduğundan – ileti işlemede işleme özel durum oluşur, serileştirme, kodlayıcı veya biçimlendirici düzeyinde – genellikle bir Ierrorhandler işlenemez Bu özel durumlar meydana süre. Benzer şekilde, bir Ierrorhandler aktarımı özel durumları işlenemez.  
  
 Bir Ierrorhandler ile bir özel durum oluştuğunda uygulamanızın davranışını açıkça denetleyebilirsiniz. Şunları yapabilirsiniz:  
  
1.  İstemciye bir hata göndermek gerekip gerekmediğini karar verin  
  
2.  Bir özel durum bir hata ile değiştirin.  
  
3.  Bir hata başka bir hata ile değiştirin.  
  
4.  Günlüğe kaydetme veya izleme gerçekleştirme  
  
5.  Diğer özel etkinlikler gerçekleştirme  
  
 Hizmetiniz için kanal dağıtıcıları ErrorHandlers özelliğini ekleyerek bir özel hata işleyicisi yükleyebilirsiniz.  Birden fazla hata işleyicisini olması mümkündür ve bu koleksiyona eklendikleri sırayla çağrılır.  
  
 IErrorHandler.ProvideFault istemciye gönderilen hata iletisini kontrol eder. Bu yöntem, bir işlem hizmet tarafından oluşturulan özel durumun türünden bağımsız olarak çağrılır. Hiçbir işlem burada gerçekleştirilirse, WCF varsayılan davranışını varsayar ve yokmuş gibi hiçbir özel hata işleyicilerini yerinde devam eder.  
  
 Tek bir alanda, belki de bu yaklaşımı kullanabilirsiniz (örnek değil atıldı ve kanal için hatalı durumuna taşınıp taşınmayacağı sağlama) istemciye gönderilmeden önce hataları için özel durumlar dönüştürme için merkezi bir konum oluşturmak istediğiniz durumdur.  
  
 IErrorHandler.HandleError yöntemi genellikle hata aramayla ilgili davranışlarını gibi hata günlüğü, sistem bildirimleri, uygulama, vb. kapatılıyor uygulamak için kullanılır. Hizmeti içinde birden çok yerlerdeki IErrorHandler.HandleError çağrılabilir ve burada bir hata oluşturulur, bağlı olarak, HandleError yöntemi olabilir veya işlemi ile aynı iş parçacığı tarafından çağrılan değildir; Bu bağlamda yapılan hiçbir şekilde garanti etmez.  
  
### <a name="dealing-with-exceptions-outside-wcf"></a>Özel durumlar dışında WCF uğraşmanızı  
 Genellikle, yapılandırma özel durumlar, veritabanı bağlantı dizesi özel durumları ve diğer benzer özel durumları WCF uygulaması bağlamında oluşabilir ancak kendileri olmayan özel durumların nedeni hizmet modeli veya web hizmeti. Bu özel durumlar özel durumlar "Normal" dış web hizmetine ve yalnızca dış diğer özel durumlar ortamda işlenecek olduğundan yapılması gerekir.  
  
### <a name="tracing-exceptions"></a>Özel durum izleme  
 İzleme, bir büyük olasılıkla tüm özel durumları görebileceğiniz yalnızca "catch-all" yerdir. İzleme ve günlüğe kaydetme, izleme ve özel durumları hakkında daha fazla bilgi için bkz.  
  
### <a name="uri-template-errors-when-using-webgetattribute-and-webinvokeattribute"></a>WebGetAttribute ve WebInvokeAttribute kullanırken URI şablonu hataları  
 WebGet ve Webınvoke öznitelikleri isteği adresi bileşenlerinin işlem parametrelerini eşleyen bir URI şablonu belirtmenizi sağlar. Örneğin, URI şablonu "hava durumu / {state} / {Şehir}" değişmez değer belirteçleri, durumu adlı bir parametre ve şehir adlı bir parametre istek adresiyle eşleşir. Bu parametreleri ardından adına göre bazı işlemin biçimsel parametrelerin bağlı olması.  
  
 Yazılı sözleşme biçimsel parametreler dize olmayan türlerde olabilir şablon parametreleri URI içinde dizeleri biçiminde görünür. Bu nedenle, bir dönüştürme işlemi çağrılmadan önce gerçekleşmesi gerekir. A [dönüştürme biçimleri tablosunun](wcf-web-http-programming-model-overview.md) kullanılabilir.  
  
 Ancak, dönüştürme başarısız olursa, ardından bir sorun oluştu olduğunu biliyorsanız işlemi izin vermek için hiçbir yolu yoktur. Tür dönüştürme, bunun yerine bir dağıtım hatası biçiminde ortaya çıkarır.  
  
 Tür dönüştürme gönderme hatası olabilir birçok farklı türde gönderme hataları gibi aynı hata işleyicisini yükleyerek inceledi. Ierrorhandler genişletilebilirlik noktası, hizmet düzeyi özel durumları işlemek için çağrılır. Buradan çağırana geri – gönderilecek yanıt olarak da herhangi bir özel görevleri gerçekleştirmek ve raporlama – seçmiş olabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Temel WCF Programlama](../basic-wcf-programming.md)
