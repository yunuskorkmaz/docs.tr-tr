---
title: Özel Kodlayıcılar
ms.date: 03/30/2017
ms.assetid: fa0e1d7f-af36-4bf4-aac9-cd4eab95bc4f
ms.openlocfilehash: 7602e18a03f73f66dfd028d810c003db0b6653bb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59190580"
---
# <a name="custom-encoders"></a>Özel Kodlayıcılar
Bu konu, özel kodlayıcılar oluşturulacağını açıklar.  
  
 Windows Communication Foundation (WCF) kullandığınız bir *bağlama* uç noktaları arasında bir ağ üzerinden veri aktarımı nasıl belirlemek için. Bağlama bir dizi yapılır *bağlama öğelerinin*. Bir bağlama güvenlik, gerekli bir'gibi isteğe bağlı Protokolü bağlama öğeleri içeren *ileti Kodlayıcı* bağlama öğesi ve gerekli aktarım bağlama öğesi. İleti Kodlayıcı, bir ileti kodlama bağlama öğesi tarafından temsil edilir. WCF'de ileti kodlayıcılar üç dahildir: İkili, ileti aktarım en iyi duruma getirme mekanizması (MTOM) ve metin.  
  
 Kodlama bağlama öğesi serileştiren bir giden ileti <xref:System.ServiceModel.Channels.Message> ve aktarım için geçirir veya aktarımdan serileştirilmiş biçiminde bir ileti alır ve protokol katmanında varsa veya uygulamaya geçirir, mevcut değilse.  
  
 İleti Kodlayıcı dönüştürme <xref:System.ServiceModel.Channels.Message> örnekleri hat gösterimine gelen ve giden. Kodlayıcıları oluşturmaması nedeniyle kanal yığınındaki taşıma katmanının olarak açıklanan olsa da, Aktarım katmanı içinde yer alır. Aktarımları (örneğin, HTTP) ileti aktarma standart gereksinimlerine göre biçimlendirin. Kodlayıcıları (örneğin, metin Xml), yalnızca iletisine kodlayın.  
  
 Bir önceden var olan bir istemci veya sunucu bağlanırken bir özel ileti kodlama kullanma hakkında bir seçim olmayabilir. Ancak, WCF hizmetleri birden fazla uç noktası, her biri farklı bir ileti Kodlayıcı üzerinden erişilebilir hale getirilebilir. Tek bir kodlayıcı, hizmetiniz için kitle kapsamaz, birden fazla uç nokta hizmetinize gösterme göz önünde bulundurun. İstemci uygulamaları, daha sonra bunlar için en iyi uç noktayı seçebilirsiniz. Birden çok uç noktalarını kullanarak diğer bağlama öğeleri farklı bir ileti kodlayıcılar avantajları birleştirmek sağlar.  
  
## <a name="system-provided-encoders"></a>Sistem tarafından sağlanan kodlayıcılar  
 WCF en yaygın uygulama senaryolarını kapsayan üzere tasarlanmış birçok sistem tarafından sağlanan bağlamalar sağlar. Bu bağlamalar, her bir aktarım ileti Kodlayıcısı ve diğer seçenekleri (örneğin, güvenlik) birleştirin. Bu konu nasıl genişletileceğini açıklar `Text`, `Binary`, ve `MTOM` ileti WCF'de içerdiği ya da kendi özel bir kodlayıcı oluşturma kodlayıcılar. Metin ileti Kodlayıcı hem bir düz XML kodlama yanı sıra SOAP kodlamaları destekler. Metin ileti Kodlayıcı düz XML kodlama modunu, metin tabanlı SOAP kodlamadan ayırt etmek için ("düz eski XML") POX kodlayıcı olarak adlandırılır.  
  
 Sistem tarafından sağlanan bağlamalar tarafından sağlanan bağlama öğeleri birleşimlerini hakkında daha fazla bilgi için karşılık gelen bölümünde bakın [taşıma seçme](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).  
  
## <a name="how-to-work-with-system-provided-encoders"></a>Sistem tarafından sağlanan kodlayıcılar ile çalışma  
 Türetilen bir sınıf kullanarak bir bağlama için bir kodlama eklenir <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.  
  
 WCF sağlayan aşağıdaki bağlama öğeleri türetilen türde <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> metin, ikili ve ileti aktarım en iyi duruma getirme mekanizması (MTOM) kodlama sağlayabilen sınıf:  
  
-   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>: En birlikte çalışabilir, ancak XML iletileri için en az verimli Kodlayıcı. Genellikle bir Web hizmeti veya Web hizmeti istemcisi metinsel XML anlayabilirsiniz. Ancak, büyük ikili veri olarak metin blokları iletme verimli değildir.  
  
-   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>: Karakter kodlamasını belirtir. bağlama öğesi ve ileti sürüm oluşturmayı ikili tabanlı XML iletileri için kullanılan temsil eder. Bu kodlama seçenekleri, ancak en az çalışabilen en etkili yöntemdir çünkü yalnızca WCF uç noktaları tarafından desteklenir.  
  
-   <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>: Bir ileti aktarım en iyi duruma getirme mekanizması (MTOM) kodlama kullanılarak bir ileti için kullanılan ileti sürüm oluşturmayı ve karakter kodlamasını belirtir. bağlama öğesi temsil eder. MTOM WCF iletilerinde ikili veri aktarımı için verimli bir teknolojidir. MTOM Kodlayıcısı, verimlilik ve birlikte çalışabilirlik arasında dengeleme dener. MTOM kodlama çoğu XML metin biçiminde aktarır, ancak büyük ikili veri blokları olarak ileterek iyileştirir-olan metin dönüştürme olmadan.  
  
 Bir ikili, MTOM ya da metin bağlama öğesi oluşturur <xref:System.ServiceModel.Channels.MessageEncoderFactory>. Bir ikili, MTOM ya da metin üreteci oluşturur <xref:System.ServiceModel.Channels.MessageEncoderFactory> örneği. Genellikle, yalnızca tek bir örneği yok. Ancak farklı bir kodlayıcı oturumları kullanılıyorsa, her oturum için sağlanabilir. İkili Kodlayıcı sağlar (bkz. XML altyapı) dinamik sözlükleri koordine etmek için bunu kullanın.  
  
 <xref:System.ServiceModel.Channels.MessageEncoder.ReadMessage%2A> Ve <xref:System.ServiceModel.Channels.MessageEncoder.WriteMessage%2A> kodlayıcılarda setinin yöntemlerdir. Bir akış ya da bir ileti okumak için yöntemler sağlar. bir <xref:System.Byte> dizi. Bayt dizileri taşıma arabelleğe alınan modda çalışırken kullanılır. İleti akışları için her zaman yazılır. Aktarım iletisi arabellek gerekir, arabelleğe alma işlemini destekleyen bir akışa sağlar.  
  
 Kalan üyeler destek içerik, medya türleriyle çalışır ve <xref:System.ServiceModel.Channels.MessageEncoder.MessageVersion%2A>. Taşıma tarafından gelen ileti çözülebilir olup olmadığını test etmek için ya da giden ileti bu Kodlayıcı için geçerli olup olmadığını belirlemek için bu Kodlayıcı yöntemleri çağırır.  
  
 Üç Kodlayıcı uygulamaların her biri belirli kodlamaları için uygun olan özellikleri ekler ve tam olarak yapılandırılabilir. Kodlayıcıları güvenli varsayılanlara sahiptir okuyucu kotalar da kullanıma sunar. XML altyapı kotaları hakkında ayrıntılı bilgi için bkz.  
  
## <a name="features-of-system-provided-encoders"></a>Sistem tarafından sağlanan kodlayıcılar özellikleri  
 Sistem tarafından sağlanan kodlayıcılarda tarafından sağlanan özellikleri vardır.  
  
### <a name="pooling"></a>Biriktirme  
 Kodlayıcı uygulamaların her biri, mümkün olduğunca havuzu çalışır. Ayırmaları azaltma yönetilen kod performansını artırmak için önemli bir yoludur. Bu havuzu gerçekleştirmek için uygulamaları kullanın. `SynchronizedPool` sınıfı. C# Dosyası bu sınıf tarafından kullanılan ek iyileştirmeler açıklamasını içerir.  
  
 <xref:System.Xml.XmlDictionaryReader> ve <xref:System.Xml.XmlDictionaryWriter> örnekleri havuza ve yenilerini her ileti için ayırma önlemek için yeniden başlatıldı. Okuyucular için bir `OnClose` geri çağırma geri kazanır, okuyucu olduğunda `Close()` çağrılır. Kodlayıcı Ayrıca iletileri oluştururken kullanılan bazı ileti durumu nesneleri geri dönüştürür. Bu havuzları tarafından yapılandırılabilir boyutlarda `MaxReadPoolSize` ve `MaxWritePoolSize` her üç sınıfın özelliklerini türetilen <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.  
  
### <a name="binary-encoding"></a>İkili kodlama  
 Dinamik sözlük dizesinde ikili zaman kullandığı oturumları kodlama, ileti alıcısı için bildirilmesi gerekir. Bu, dinamik sözlük dizeleri içeren bir ileti ekleyerek gerçekleştirilir. Alıcı dizeleri kaldırır, bunları oturumuna ekler ve iletiyi işler. Doğru sözlük dizeleri taşıma arabelleğe alınıp gerektirir.  
  
 Dizeleri iletiye bir iç tarafından eklenen `AddSessionInformationToMessage` yöntemi. Dizeleri, ön eki uzunlukları ile ileti önüne UTF-8 ekler. Tüm sözlük üst bilgisi, ardından kendi veri uzunluğu ile önekidir. Tersine çevirme işlemi bir iç tarafından gerçekleştirilen `ExtractSessionInformationFromMessage` yöntemi.  
  
 Dinamik sözlük anahtarlarını işleme ek olarak, benzersiz bir yolla kapatamaması arabelleğe alma iletilerinin alınır. Belge üzerinde bir okuyucu oluşturma ve işlemekte yerine ikili Kodlayıcı dahili kullanım `MessagePatterns` ikili akışı ayrıştırma için sınıf. İletilerin çoğu belirli bir dizi WCF tarafından oluşturulmuş bir düzende görünmesini üstbilgileri sahip olur. Düzen sistemi ayırmak, bekliyor üzerinde temel ileti keser. Başarılı olursa, onu başlatır bir <xref:System.ServiceModel.Channels.MessageHeaders> XML Ayrıştırma olmadan nesne. Aksi durumda, standart yöntemin geri döner.  
  
### <a name="mtom-encoding"></a>MTOM Kodlama  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> Sınıfında adlı bir ek yapılandırma özelliği <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement.MaxBufferSize%2A>. Bu, bir üst sınır ne kadar veri bir ileti okuma işlemi sırasında arabelleğe almak için izin veriliyorsa üzerinde yerleştirir. XML bilgi kümesi (bilgi kümesi) veya diğer MIME bölümü, tüm MIME bölümleri tek bir iletiye yeniden birleştirmek için arabelleğe alınan gerekebilir.  
  
 HTTP ile düzgün çalışmak için bazı iç API'ler için iç MTOM ileti Kodlayıcı sınıfı sağlar `GetContentType` (olduğu da iç) ve `WriteMessage`, genel ve geçersiz kılınabilir. Daha fazla iletişim MIME üstbilgi değerleri ile HTTP üstbilgileri değerleri kabul emin olmak için gerçekleşmelidir.  
  
 Dahili olarak MTOM ileti Kodlayıcı WCF'ın metin okuyucular kullanır ve metin Kodlayıcı için benzer. İkisi arasındaki temel fark büyük ikili veya "Büyük ikili nesneler" (BLOB) parçalarını iyileştirir bunları ileti baytlarının katıştırılmış önce 64 tabanlı kodlama değil dönüştürmektir. Bunun yerine, bu Bloblarda ayıklanan ve başvurulan MIME ek olarak tutulur.  
  
## <a name="writing-your-own-encoder"></a>Kendi Kodlayıcı yazma  
 Kendi özel ileti Kodlayıcı uygulamak için aşağıdaki soyut temel sınıflar, özel uygulamalar sağlamalıdır:  
  
-   <xref:System.ServiceModel.Channels.MessageEncoder>  
  
-   <xref:System.ServiceModel.Channels.MessageEncoderFactory>  
  
-   <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
  
 Bir iletinin bellek içi gösteriminden bir akışa yazılabilir bir temsili dönüştürme saklanmış olduğu içinde <xref:System.ServiceModel.Channels.MessageEncoder> XML okuyucular ve belirli türlerdeki XML kodlamaları destekleyen XML yazıcılar için bir üreteci hizmet veren sınıf.  
  
-   Geçersiz kılmanız gerekir, bu sınıfın temel yöntemler şunlardır:  
  
-   <xref:System.ServiceModel.Channels.MessageEncoder.WriteMessage%2A> hangi alır bir <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> nesne ve içine Yazar bir <xref:System.IO.Stream> nesne.  
  
-   <xref:System.ServiceModel.Channels.MessageEncoder.ReadMessage%2A> hangi alır bir <xref:System.IO.Stream> nesne ve en fazla üstbilgi boyutu ve döndürür bir <xref:System.ServiceModel.Channels.Message> nesne.  
  
 Buna standart aktarım protokolünü ve özelleştirilmiş kodlama arasında dönüştürme işleyen bu yöntemleri yazdığınız kodu var.  
  
 Ardından, özel bir kodlayıcı oluşturan bir Üreteç sınıfını kod gerekir. Geçersiz kılma <xref:System.ServiceModel.Channels.MessageEncoderFactory.Encoder%2A> özel örneğini döndürülecek <xref:System.ServiceModel.Channels.MessageEncoder>.  
  
 Ardından özel bağlanma <xref:System.ServiceModel.Channels.MessageEncoderFactory> geçersiz kılarak, hizmet veya istemcinin yapılandırmak için kullanılan bağlama öğesi yığınına <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> yöntemi bu üretecin bir örneğini döndürür.  
  
 Örnek kod ile bu işlemi canlandırmak adına WCF ile sağlanan iki örnekleri vardır: [Özel ileti Kodlayıcı: Özel metin Kodlayıcı](../../../../docs/framework/wcf/samples/custom-message-encoder-custom-text-encoder.md) ve [özel ileti Kodlayıcı: Sıkıştırma Kodlayıcısı](../../../../docs/framework/wcf/samples/custom-message-encoder-compression-encoder.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MessageEncoderFactory>
- <xref:System.ServiceModel.Channels.MessageEncoder>
- [Veri Aktarımı Mimarisi Genel Bakış](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)
- [İleti Kodlayıcı Seçme](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [Taşıma Seçme](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
