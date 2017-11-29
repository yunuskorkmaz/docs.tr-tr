---
title: "Hata işleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c948841a-7db9-40ae-9b78-587d216cbcaf
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 308712ed4c8f44740622c57525f152152f7d6c73
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="error-handling"></a>Hata işleme
## <a name="error-handling-in-windows-communication-foundation"></a>Windows Communication Foundation işleme hatası  
 Bir hizmeti beklenmeyen bir özel durum ya da hata karşılaştığında, bir özel durum işleme çözüm tasarımı için birden çok yolu vardır. Varken hiçbir tek "doğru" veya "en iyi uygulama" hata işleme çözüm, birden çok geçerli yol bir göz önünde bulundurun. Bir WCF uygulama, türünü ve özel durumları, işlenmiş sıklığını karmaşıklığına bağlı olarak, aşağıdaki listeden birden çok yaklaşımlar işlenmemiş yapısını birleştiren bir karma çözümü uygulamak normalde önerilir özel durumlar ve herhangi bir izleme, günlük veya ilke gereksinimleri ilişkilendirilmiş.  
  
 Bu çözümler, bu bölümün geri kalanında daha derine açıklanmıştır.  
  
### <a name="the-microsoft-enterprise-library"></a>Microsoft Enterprise kitaplığı  
 Microsoft Enterprise kitaplığı özel durum işleme uygulama bloğu ortak tasarım desenleri uygulamak ve kurumsal uygulama mimari katmanları tüm oluşan özel durum işleme için tutarlı bir strateji oluşturmak yardımcı olur. Uygulama bileşenleri catch deyimleri bulunan tipik kod desteklemek üzere tasarlanmıştır. Bu kod (örneğin, özel durum bilgilerini kaydeder kodu) bir uygulama boyunca aynı catch blokları içinde yinelenen yerine, özel durum işleme uygulama bloğu geliştiricilerin bu mantığı yeniden kullanılabilir özel durum işleyicileri olarak kapsülleyen olanak tanır.  
  
 Bu kitaplık out-of--box hataya sözleşme özel durum işleyicisi içerir. Bu özel durum işleyici Windows® Communication Foundation (WCF) hizmetini sınırlarında kullanılmak üzere tasarlanmış ve yeni bir arıza sözleşme özel durumu oluşturur.  
  
 Yaygın olarak kullanılan en iyi uygulamaları ekleyebilir ve özel durum uygulamanızın genelinde işleme için ortak bir yaklaşım sağlamak için uygulama blokları hedefleyin. Diğer taraftan, özel hata işleyicileri ve hataya sözleşmeleri birinin üzerinde kendi geliştirilen ayrıca çok kullanışlı olabilir. Örneğin, özel hata işleyicileri FaultExceptions tüm özel durumlar otomatik olarak Yükselt ve günlüğe kaydetme özellikleri uygulamanıza eklemek için mükemmel bir fırsat sağlar.  
  
 Daha fazla bilgi için lütfen bkz [Microsoft Enterprise Kitaplığı](http://msdn.microsoft.com/library/ff632023.aspx).  
  
### <a name="dealing-with-expected-exceptions"></a>Beklenen özel durumlar postalarla  
 Eylem uygun seyri olan her işlem ya da ilgili genişletilebilirlik noktası beklenen özel durumları yakalamak için bunlar veriler kurtarılamaz, uygun özel hataya bir FaultException iade karar verdikten sonra\<T >  
  
### <a name="dealing-with-unexpected-exceptions-using-an-ierrorhandler"></a>Beklenmeyen bir IErrorHandler kullanarak istisnalar ele alma  
 Beklenmeyen durumlarla başa çıkmak için önerilen yol eyleminin "bir IErrorHandler kanca" kullanmamaktır. Hata işleyicileri yalnızca özel durumlarını yakalama WCF çalışma zamanı düzeyinde ("hizmet modeli" katman), kanal katmanında. Çoğu senaryoda önerilmez özel bir kanal oluşturmak için yalnızca bir IErrorHandler kanal düzeyinde kanca şekilde denetleyebilirsiniz.  
  
 "Beklenmeyen bir özel durum" genellikle ne kurtarılamaz bir özel durum, ne de bir işlem özel durumu olan; Bu, bunun yerine, beklenmeyen bir kullanıcı özel durumdur. Kurtarılamaz bir özel durum (bir bellek yetersiz özel durum gibi) – bir genellikle işlenen tarafından [hizmet modeli özel durum işleyicisi](http://msdn.microsoft.com/library/system.servicemodel.dispatcher.exceptionhandler.aspx) otomatik olarak – genellikle düzgün işlenemez ve bu tür özel bir durumu işlemek için yalnızca açıklaması Ek günlük hiç olabilir veya standart bir özel durum istemciye döndürülecek. Genellikle çok erken ya da çok geç hata işleyici tarafından müdahale olduğundan bir işlem özel durum iletisi – işlemde oluşur Örneğin, seri hale getirme, kodlayıcı veya biçimlendirici düzeyinde – genellikle bir IErrorHandler işlenemiyor Bu özel durumları ortaya süre. Benzer şekilde, aktarım özel durumlar bir IErrorHandler işlenemiyor.  
  
 Bir özel durum bir IErrorHandler ile açıkça uygulamanızın davranışını kontrol edebilirsiniz. Görebilirsiniz:  
  
1.  Bir arıza istemciye göndermek isteyip istemediğinizi karar verin  
  
2.  Bir özel durum hatası ile değiştir  
  
3.  Bir hata ile başka bir hataya değiştirin  
  
4.  Günlüğü veya izleme gerçekleştirme  
  
5.  Diğer özel etkinlikleri gerçekleştirmek  
  
 Hizmetiniz için kanal dağıtıcıları ErrorHandlers özelliğine ekleyerek bir özel hata işleyici yükleyebilirsiniz.  Birden fazla hata işleyicisine olması mümkündür ve bu koleksiyona eklendikleri sırayla çağrılır.  
  
 IErrorHandler.ProvideFault istemciye gönderilen hata iletisi denetler. Bu yöntem, hizmetinizde bir işlem tarafından oluşturulan özel durum türü ne olursa olsun çağrılır. Hiçbir işlem burada gerçekleştirilirse, WCF varsayılan davranışını varsayar ve olmamış gibi hiçbir özel hata işleyicileri yerinde devam eder.  
  
 (Örneği değil atıldı ve kanal Faulted durumuna taşınmaz sağlanarak) istemciye gönderilmeden önce hataları için özel durumları dönüştürme için merkezi bir konum oluşturmak istediğinizde bu yaklaşımı belki de kullanabilirsiniz bir alandır.  
  
 IErrorHandler.HandleError yöntemi genellikle hata ile ilgili davranışları hata günlüğü oluşturmayı, gibi kapatılıyor uygulama, vb. Sistem bildirimleri uygulamak için kullanılır. Hizmetin birden fazla yerde IErrorHandler.HandleError çağrılabilir ve burada hata atılır, bağlı olarak HandleError yöntemi olabilir işlemi olarak iş parçacığı tarafından çağrılan değil; veya Bu konuda, hiçbir garanti hale getirilir.  
  
### <a name="dealing-with-exceptions-outside-wcf"></a>Özel durumlar dışında WCF postalarla  
 Genellikle, yapılandırma özel durumları, veritabanı bağlantı dizesi özel durumları ve benzer diğer özel durumlar WCF uygulaması bağlamında oluşabilir, ancak kendileri olmayan nedeni hizmet modeli veya web hizmeti özel durumları. Bu özel durumlar "Normal" özel durumlar web hizmetine dış ve yalnızca ortamında dış diğer özel durumlar işlenecek şekilde yapılması gerekir.  
  
### <a name="tracing-exceptions"></a>Özel durum izleme  
 İzleme, bir olası tüm özel durumları görebileceğiniz yalnızca "catch-tüm" yerdir. İzleme ve kaydetme izleme ve günlük özel durumları hakkında daha fazla bilgi için bkz.  
  
### <a name="uri-template-errors-when-using-webgetattribute-and-webinvokeattribute"></a>WebGetAttribute hem de WebInvokeAttribute kullanırken URI şablonunu hataları  
 WebGet ve Webınvoke öznitelikleri işlemi parametreleri için istek adresi bileşenlerinin eşleştiren bir URI şablonunu belirtmenizi sağlar. Örneğin, URI şablonunu "hava durumu / {state} / {Şehir}" istek adresi değişmez değer belirteçleri, durumu adlı bir parametre ve şehir adlı bir parametre eşler. Bu parametreler sonra adıyla bazı işleminin resmi parametrelerin bağlı.  
  
 Yazılı sözleşme biçimsel parametresi dize olmayan türlerde olabilir şablon parametreleri dizeler URI içindeki biçiminde görünür. Bu nedenle, bir dönüştürme işlemi çağrılabilir önce gerçekleşmesi gerekir. A [dönüştürme biçimleri tablosunun](http://msdn.microsoft.com/library/bb412172.aspx) kullanılabilir.  
  
 Ancak, dönüştürme başarısız olursa, ardından bir şeyler yanlış geçtiğini bilmeniz işlemi olanak yolu yoktur. Tür dönüşümü, bunun yerine bir gönderme hatası biçiminde ortaya çıkarır.  
  
 Tür dönüştürme gönderme hatası olabilir diğer türlerde gönderme hataları gibi aynı hata işleyicisine yükleyerek sahip denetlenir. Hizmet düzeyi özel durumları işleme IErrorHandler genişletilebilirlik noktası çağrıldı. Buradan, geri çağırana – gönderilecek yanıt olarak hem de özel görevler gerçekleştirmek ve raporlama – seçmiş olabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel WCF hata işleme](http://msdn.microsoft.com/library/gg281715.aspx)
