---
title: Hata işleme
ms.date: 03/30/2017
ms.assetid: c948841a-7db9-40ae-9b78-587d216cbcaf
ms.openlocfilehash: 9c7d6814a6bf1189fd85de5eb440ec4a6840447e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539989"
---
# <a name="error-handling-in-windows-communication-foundation-wcf"></a>Windows Communication Foundation hata işleme (WCF)

Bir hizmet beklenmeyen bir özel durumla veya hatayla karşılaştığında, özel durum işleme çözümünü tasarlamak için birden çok yol vardır. Tek bir "doğru" veya "en iyi uygulama" hata işleme çözümü olmasa da, bir tane göz önünde bulundurmanız için birden çok geçerli yol vardır. Genellikle, WCF uygulamasının karmaşıklığına, özel durumların tür ve sıklığının yanı sıra özel durumların işlenme ve işlenmemiş doğası ile ilişkili izleme, günlüğe kaydetme veya ilke gereksinimlerinin ne olduğuna bağlı olarak, aşağıdaki listeden birden çok yaklaşımı birleştiren bir karma çözüm uygulamanız önerilir.

Bu çözümler, bu bölümün geri kalanında daha derin açıklanmıştır.

## <a name="the-microsoft-enterprise-library"></a>Microsoft Kurumsal kitaplığı

Microsoft Kurumsal kitaplık özel durum Işleme uygulaması bloğunda ortak tasarım desenleri uygulamaya ve bir kurumsal uygulamanın tüm mimari katmanlarında gerçekleşen özel durumları işlemeye yönelik tutarlı bir strateji oluşturulmasına yardımcı olur. Uygulama bileşenlerinde bulunan catch deyimlerine dahil edilen tipik kodu desteklemek için tasarlanmıştır. Bu kodu (özel durum bilgilerini kaydeden kod gibi) bir uygulama genelinde özdeş catch bloklarına yinelemek yerine, özel durum Işleme uygulama bloğu, geliştiricilerin bu mantığı yeniden kullanılabilir özel durum işleyicileri olarak kapsüllemelerini sağlar.

Bu kitaplık, kullanıma hazır bir hata sözleşmesi özel durum Işleyicisi içerir. Bu özel durum işleyicisi, WCF hizmet sınırları 'nda kullanılmak üzere tasarlanmıştır ve özel durumdan yeni bir hata sözleşmesi oluşturur.

Uygulama blokları, yaygın olarak kullanılan en iyi uygulamaları dahil etmek ve uygulamanızın tamamında özel durum işleme için ortak bir yaklaşım sağlamak üzere hedeflenir. Diğer taraftan, özel hata işleyicileri ve tek başına geliştirilen hata sözleşmeleri de çok yararlı olabilir. Örneğin, özel hata işleyicileri, tüm özel durumları FaultExceptions ' a otomatik olarak yükseltmek ve ayrıca uygulamanıza günlük özellikleri eklemek için harika bir fırsat sağlar.

Daha fazla bilgi için lütfen bkz. [Microsoft Kurumsal kitaplığı](/previous-versions/msp-n-p/ff632023(v=pandp.10)).

## <a name="dealing-with-expected-exceptions"></a>Beklenen özel durumlarla ilgilenme

Doğru eylem kursu, her işlem veya ilgili genişletilebilirlik noktasındaki beklenen özel durumları yakalamak, ' den kurtarılıp kurtarılamayacağına karar vermek ve bir FaultException içinde uygun özel hatayı geri döndürmaktır \<T> .
  
## <a name="dealing-with-unexpected-exceptions-using-an-ierrorhandler"></a>IErrorHandler kullanarak beklenmeyen özel durumlarla ilgilenme

Beklenmeyen özel durumlarla başa çıkmak için, önerilen eylem "kanca" bir IErrorHandler ' dir. Hata işleyicileri yalnızca WCF çalışma zamanı düzeyinde ("hizmet modeli" katmanı) özel durumları yakalar, bu da kanal katmanında değil. Kanal düzeyinde bir IErrorHandler 'i bağlamak için tek yol, Çoğu senaryoda önerilmeyen özel bir kanal oluşturmaktır.

"Beklenmeyen özel durum" genellikle kurtarılamaz bir özel durum ya da bir işleme özel durumu değildir; Bunun yerine, beklenmeyen bir kullanıcı özel durumu. Kurtarılamaz bir özel durum (örneğin, bellek dışı özel durum) – genel olarak [hizmet modeli özel durum işleyicisi](xref:System.ServiceModel.Dispatcher.ExceptionHandler) tarafından genel olarak ele alınamaz. genellikle düzgün bir şekilde işlenemeyebilir ve bu tür bir özel durumu işlemenin tek nedeni ek günlüğe kaydetme veya istemciye standart özel durum döndürme olabilir. İleti işlenirken bir işleme özel durumu oluşur. Örneğin, serileştirme, kodlayıcı veya biçimlendirici düzeyinde genellikle, bu özel durumlar meydana geldiğinde hata işleyicisine müdahale etmek için genellikle çok erken veya çok geç olduğundan, genellikle bir IErrorHandler üzerinden işlenemez. Benzer şekilde, taşıma özel durumları bir IErrorHandler üzerinde işlenemez.

Bir IErrorHandler ile, bir özel durum oluştuğunda uygulamanızın davranışını açık bir şekilde denetleyebilirsiniz. Şunları yapabilirsiniz:  

1. İstemciye bir hata gönderilmesi gerekip gerekmediğine karar verin.

2. Özel durumu bir hata ile değiştirin.

3. Hatayı başka bir hata ile değiştirin.

4. Günlüğe kaydetmeyi veya izlemeyi gerçekleştirin.

5. Diğer özel etkinlikleri gerçekleştirin.

Bunlardan biri, hizmetinize ait kanal dağıtıcılarının ErrorHandlers özelliğine ekleyerek özel bir hata işleyicisi yükleyebilir.  Birden fazla hata işleyicisi olması mümkündür ve bu koleksiyona eklendikleri sırada çağırılır.

IErrorHandler. ProvideFault istemciye gönderilen hata iletisini denetler. Bu yöntem, hizmetinize bir işlem tarafından oluşturulan özel durumun türünden bağımsız olarak çağrılır. Burada hiçbir işlem gerçekleştirildiyse, WCF varsayılan davranışını varsayar ve yerinde özel hata işleyicileri olmadığı gibi devam eder.

Bu yaklaşımı belki kullanabileceğiniz bir alan, istemciye gönderilmeden önce özel durumları hatalara dönüştürmek için merkezi bir yer oluşturmak istediğinizde (örneğin atılmadığından ve kanalın hatalı duruma taşınmadığından emin olmak).

IErrorHandler. HandleError yöntemi genellikle hata günlüğü, sistem bildirimleri, uygulama kapatma vb. gibi hata ile ilgili davranışları uygulamak için kullanılır. IErrorHandler. HandleError, hizmetin içindeki birden fazla yerde çağrılabilir ve hatanın nerede oluşturulduğuna bağlı olarak, HandleError yöntemi işlemle aynı iş parçacığı tarafından çağrılabilir veya çağrılamaz; Bu şekilde hiçbir garanti yapılmaz.

## <a name="dealing-with-exceptions-outside-wcf"></a>WCF dışındaki özel durumlarla ilgilenme

Genellikle, yapılandırma özel durumları, veritabanı bağlantı dizesi özel durumları ve diğer benzer özel durumlar bir WCF uygulaması bağlamında gerçekleşebilir, ancak bunlar hizmet modeli veya Web hizmeti 'nin kendisinden kaynaklanan özel durum değildir. Bu özel durumlar, Web hizmeti dışında "normal" özel durumlardır ve ortamdaki diğer dış özel durumlar işlenebilmelidir.

## <a name="tracing-exceptions"></a>Özel durumları izleme

Yalnızca birinin tüm özel durumları görebileceği tek "catch-all" konumu izleniyor. İzleme ve günlüğe kaydetme özel durumları hakkında daha fazla bilgi için bkz. Izleme ve günlüğe kaydetme.

## <a name="uri-template-errors-when-using-webgetattribute-and-webinvokeattribute"></a>WebGetAttribute ve Webvokeattribute kullanılırken URI şablonu hataları

WebGet ve Webvoke öznitelikleri, istek adresi bileşenlerini işlem parametrelerine eşleyen bir URI şablonu belirtmenize olanak tanır. Örneğin, "Hava durumu/{State}/{City}" URI şablonu, istek adresini değişmez belirteçlere, durum adlı bir parametreye ve City adlı bir parametreye eşler. Bu parametreler daha sonra, işlemin bazı biçimsel parametrelerine ad ile bağlanabilir.

Türü belirlenmiş bir sözleşmenin biçimsel parametreleri dize olmayan türlerde olabilir, şablon parametreleri URI içindeki dizeler biçiminde görüntülenir. Bu nedenle, işlem çağrılmadan önce dönüştürmenin gerçekleşmesi gerekir. [Dönüştürme biçimleri tablosu](wcf-web-http-programming-model-overview.md) kullanılabilir.

Ancak, dönüştürme başarısız olursa, işlemin yanlış bir şekilde geçmiş olduğunu bilmesini sağlamak için bir yol yoktur. Bir dağıtım hatası biçiminde yüzey yerine tür dönüştürme.

Bir tür dönüştürme gönderimi hatası, hata işleyicisi yükleyerek diğer birçok dağıtım hatası türüyle aynı şekilde incelenebilir. IErrorHandler genişletilebilirlik noktası, hizmet düzeyi özel durumları işlemek için çağrılır. Buradan, çağırana geri gönderilecek yanıt, ve özel görevler ve raporlama gerçekleştirmek için de seçilebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Temel WCF Programlama](../basic-wcf-programming.md)
