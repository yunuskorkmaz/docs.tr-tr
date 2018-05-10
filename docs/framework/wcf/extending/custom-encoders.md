---
title: Özel Kodlayıcılar
ms.date: 03/30/2017
ms.assetid: fa0e1d7f-af36-4bf4-aac9-cd4eab95bc4f
ms.openlocfilehash: ae3904af83452dd76723abb78a7a06fdb0f798cc
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="custom-encoders"></a>Özel Kodlayıcılar
Bu konu özel kodlayıcılar oluşturulacağını açıklar.  
  
 Windows Communication Foundation (WCF) kullandığınız bir *bağlama* uç noktaları arasında bir ağ üzerinden veri aktarımı nasıl belirtmek için. Bir dizi oluşan bir bağlama yapılır *bağlama öğeleri*. İsteğe bağlı Protokolü bağlama öğeleri gibi güvenlik, gerekli bir bağlama içerir *ileti Kodlayıcı* bağlama öğesi ve gerekli aktarım bağlama öğesi. İleti Kodlayıcı bağlama öğesi kodlama bir ileti gösterilir. Üç ileti kodlayıcılar içinde WCF eklenir: ikili, ileti iletim en iyi duruma getirme mekanizmasını (MTOM) ve metin.  
  
 Kodlama bağlama öğesi serileştiren bir giden bir ileti <xref:System.ServiceModel.Channels.Message> ve taşıma için geçirir veya taşımadan serileştirilmiş formun bir ileti alır ve protokol katmanında varsa veya uygulamaya geçirir, yüklü değilse.  
  
 İleti kodlayıcılar dönüştürme <xref:System.ServiceModel.Channels.Message> örnekleri hat gösterimine gelen ve giden. Kodlayıcılar kanal yığınındaki taşıma katmanının bir defada olarak açıklanan rağmen Aktarım katmanı içinde bulundukları. Taşımalar (örneğin HTTP) ileti aktarma standart gereksinimlerine göre biçimlendirin. Kodlayıcılar (örneğin metin Xml), yalnızca ileti kodlayın.  
  
 Bir önceden var olan istemci veya sunucu bağlanırken belirli ileti kodlama kullanma hakkında bir seçenek olmayabilir. Ancak, WCF hizmetleri birden çok uç nokta, her biri farklı ileti Kodlayıcı üzerinden erişilebilir hale getirilebilir. Tek bir kodlayıcı hedef kitle hizmetiniz için kapsamaz, birden çok Uç noktalara hizmetinizi gösterme göz önünde bulundurun. İstemci uygulamaları sonra bunlar için en iyisidir uç noktası seçebilirsiniz. Birden çok uç noktalarını kullanarak diğer bağlama öğeleriyle farklı ileti kodlayıcılar avantajları birleştirmek sağlar.  
  
## <a name="system-provided-encoders"></a>Sistem tarafından sağlanan kodlayıcılar  
 WCF en yaygın uygulama senaryolarını kapsamak üzere tasarlanmış birçok sistem tarafından sağlanan bağlamaları sağlar. Her bu bağlamaların bir aktarım, ileti Kodlayıcı ve diğer seçenekleri (örneğin, güvenlik) birleştirir. Bu konuda nasıl genişletileceğini açıklar `Text`, `Binary`, ve `MTOM` iletisi içinde WCF dahil edilen ya da kendi özel Kodlayıcı oluşturan kodlayıcılar. Metin ileti Kodlayıcı hem bir düz XML kodlama yanı sıra SOAP Kodlamalar destekler. Metin ileti Kodlayıcı düz XML kodlama modunu metin tabanlı SOAP kodlamadan ayırt etmek için POX ("düz eski XML") Kodlayıcı adı verilir.  
  
 Sistem tarafından sağlanan bağlamaları ile sağlanan bağlama öğeleri birleşimlerini hakkında daha fazla bilgi için karşılık gelen bölümüne bakın [taşıma seçme](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).  
  
## <a name="how-to-work-with-system-provided-encoders"></a>Sistem tarafından sağlanan kodlayıcılar ile çalışma  
 Bir kodlama türetilmiş bir sınıf kullanarak bir bağlama eklenir <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.  
  
 WCF sağlayan aşağıdaki türden türetilmiş bağlama öğeleri <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> metin, ikili ve ileti iletim en iyi duruma getirme mekanizmasını (MTOM) kodlama için sağlayabilen sınıfı:  
  
-   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>: En birlikte çalışabilir, ancak XML iletileri için az verimli Kodlayıcı. Genellikle Web hizmeti veya Web hizmeti istemcisi metinsel XML anlayabilirsiniz. Ancak, büyük metin olarak ikili veri blokları iletmek etkili değildir.  
  
-   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>: Karakter kodlamasını belirtir bağlama öğesi ve sürüm oluşturma ikili tabanlı XML iletileri için kullanılan ileti temsil eder. Bu kodlama seçeneklerini, ancak en az çalışabilen en etkili yoldur yalnızca WCF uç noktaları tarafından desteklenmediği için.  
  
-   <<!--zz xref:System.ServiceModel.Channels.MTOMMessageEncodingBindingElement --> `System.ServiceModel.Channels.MTOMMessageEncodingBindingElement`>: bir ileti iletim en iyi duruma getirme mekanizmasını (MTOM) kodlama kullanılarak bir ileti için kullanılan ileti sürüm oluşturma ve karakter kodlamasını belirtir bağlama öğesi temsil eder. MTOM WCF iletilerindeki ikili veri iletmek için verimli bir teknolojidir. MTOM Kodlayıcısı verimliliği ve birlikte çalışabilirlik arasında dengelemek çalışır. MTOM kodlama çoğu XML metin biçiminde aktarır ancak bunları olarak ileterek büyük ikili veri blokları en iyi duruma getirir-metne dönüştürme olmadan, ise.  
  
 Bir ikili, MTOM veya metin bağlama öğesi oluşturur <xref:System.ServiceModel.Channels.MessageEncoderFactory>. Bir ikili, MTOM veya metin üreteci oluşturur <xref:System.ServiceModel.Channels.MessageEncoderFactory> örneği. Genellikle, yalnızca tek bir örneği yoktur. Ancak oturumları kullandıysanız, farklı bir kodlayıcı her oturuma sağlanabilir. İkili kodlama sağlar (bkz. XML altyapı) dinamik sözlük koordine etmek için bu kullanın.  
  
 <xref:System.ServiceModel.Channels.MessageEncoder.ReadMessage%2A> Ve <xref:System.ServiceModel.Channels.MessageEncoder.WriteMessage%2A> kodlayıcılar çekirdek yöntemleridir. Bir akış ya da bir ileti okumak için yöntemleri sunar bir <xref:System.Byte> dizi. Bayt dizileri taşıma arabelleğe alınan modunda olduğunda kullanılır. İletileri her zaman akışlara yazılır. Taşıma ileti arabellek gerekir, arabelleğe alma yapan bir akış sağlar.  
  
 Kalan üyeleri iş destek içerik, medya türleriyle ve <xref:System.ServiceModel.Channels.MessageEncoder.MessageVersion%2A>. Taşıma tarafından gelen ileti çözülebilir olup olmadığını sınamak için ya da giden ileti bu Kodlayıcı için geçerli olup olmadığını belirlemek için bu Kodlayıcı yöntemleri çağırır.  
  
 Üç Kodlayıcı uygulamaların her biri belirli kodlamaları için uygun olan özellikler ekler ve tam olarak yapılandırılabilir. Kodlayıcılar güvenli varsayılanlar sahip okuyucu kotaları da açın. XML altyapı kotalar bir tartışma için bkz.  
  
## <a name="features-of-system-provided-encoders"></a>Sistem tarafından sağlanan kodlayıcılar özellikleri  
 Sistem tarafından sağlanan kodlayıcılar tarafından sağlanan özellikleri vardır.  
  
### <a name="pooling"></a>Biriktirme  
 Kodlayıcı uygulamaların her biri mümkün olduğunca havuz dener. Ayırmalar azaltma, yönetilen kod performansını artırmak için anahtar bir yoludur. Bu havuzu gerçekleştirmek için uygulamaları kullanır `SynchronizedPool` sınıfı. C# dosyasına bu sınıf tarafından kullanılan ek iyileştirmeler açıklamasını içerir.  
  
 `XmlDictionaryReader` ve `XmlDictionaryWriter` örnekleri havuza ve yenilerini her ileti için ayırma önlemek için yeniden başlatıldı. Okuyucular için bir `OnClose` geri çağırma kaldırsa okuyucu olduğunda `Close()` olarak adlandırılır. Kodlayıcı iletileri oluştururken kullanılan bazı ileti durumu nesneler de geri dönüştürür. Bu havuzları tarafından yapılandırılabilir boyutlarıdır `MaxReadPoolSize` ve `MaxWritePoolSize` her üç sınıfların özelliklerini türetilen <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.  
  
### <a name="binary-encoding"></a>İkili kodlama  
 Dinamik sözlük dize ikili zaman kullandığı oturumları kodlama, ileti alıcısı için bildirilmesi gerekir. Bu, dinamik sözlük dizeleri iletisiyle ekleyerek yapılır. Alıcı dizeleri kaldırır, oturumuna ekler ve iletiyi işler. Sözlük dizeler doğru geçirme taşıma arabelleğe alınıp gerektirir.  
  
 Dizeleri iletiye iç tarafından eklenen `AddSessionInformationToMessage` yöntemi. Dizeleri, kendi uzunluğunda önekli ileti önüne UTF-8 olarak ekler. Tüm sözlük üst bilgisi sonra kendi veri uzunluğu olan öneki. Tersine çevirme işlemi bir iç tarafından gerçekleştirilen `ExtractSessionInformationFromMessage` yöntemi.  
  
 Dinamik sözlük anahtarları işleme ek olarak, arabelleğe alınan süre sonuyla iletileri benzersiz bir şekilde alınır. Belge üzerinde bir okuyucu oluşturma ve işlemeyi yerine ikili kodlama dahili kullanım `MessagePatterns` ikili akış deconstruct sınıfı. Çoğu iletileri WCF tarafından oluşturulan, belirli bir sipariş görünmesini üstbilgileri belirli kümesine sahip olur. Desen sistem parçalayın bunu beklediği üzerinde temel ileti keser. Başarılı olursa, başlatır bir <xref:System.ServiceModel.Channels.MessageHeaders> XML Ayrıştırma olmadan nesnesi. Aksi durumda, standart yöntemi geri döner.  
  
### <a name="mtom-encoding"></a>MTOM Kodlama  
 <<!--zz xref:System.ServiceModel.Channels.MTOMMessageEncodingBindingElement --> `System.ServiceModel.Channels.MTOMMessageEncodingBindingElement`> Sınıfı adlı bir ek yapılandırma özelliği vardır <<!--zz xref:System.ServiceModel.Channels.MTOMMessageEncodingBindingElement --> `System.ServiceModel.Channels.MTOMMessageEncodingBindingElement`. MaxBufferSize % 2A >. Bu, bir üst sınır ne kadar veri bir ileti okuma işlemi sırasında arabellek etmesine izin verilen üzerinde yerleştirir. XML bilgi ayarlayın (bilgi) veya diğer MIME bölümleri, tek bir iletiye tüm MIME bölümleri yeniden birleştirmek için arabelleğe gerekebilir.  
  
 HTTP ile düzgün çalışması için bazı iç API'ler iç MTOM ileti Kodlayıcı sınıfı sağlar `GetContentType` (olduğu de dahili) ve `WriteMessage`, ortak ve geçersiz kılınabilir. Daha fazla iletişim MIME Üstbilgileri değerleriyle HTTP üstbilgileri değerleri kabul emin olmak üzere yapılmalıdır.  
  
 Dahili olarak, MTOM ileti Kodlayıcı WCF'ın metin okuyucu kullanır ve metin Kodlayıcı benzer. İkisi arasındaki temel fark ikili veya "İkili büyük nesneler" (BLOB) büyük parçalarını iyileştirir bunları ileti baytlarının katıştırılmış önce 64 tabanlı kodlama için değil dönüştürmektir. Bunun yerine, bu BLOB'lar ayıklanan ve başvurulan MIME ek olarak tutulur.  
  
## <a name="writing-your-own-encoder"></a>Kendi Kodlayıcı yazma  
 Kendi özel ileti Kodlayıcı uygulamak için aşağıdaki soyut taban sınıfları özel uygulamaları sağlamanız gerekir:  
  
-   <xref:System.ServiceModel.Channels.MessageEncoder>  
  
-   <xref:System.ServiceModel.Channels.MessageEncoderFactory>  
  
-   <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
  
 Bellek içi gösteriminden bir iletinin bir akış yazılabilir bir gösterimi dönüştürme kapsüllenmiş içinde <xref:System.ServiceModel.Channels.MessageEncoder> XML okuyucular ve XML Kodlamalar belirli türlerini desteklemek XML yazarları için bir üreteci olarak hizmet veren sınıfı.  
  
-   Geçersiz kılmanız gerekir bu sınıfın anahtar yöntemler şunlardır:  
  
-   <xref:System.ServiceModel.Channels.MessageEncoder.WriteMessage%2A> hangi alır bir <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> nesne ve içine Yazar bir <xref:System.IO.Stream> nesnesi.  
  
-   <xref:System.ServiceModel.Channels.MessageEncoder.ReadMessage%2A> hangi alır bir <xref:System.IO.Stream> nesne ve en fazla üstbilgi boyutu ve döndürür bir <xref:System.ServiceModel.Channels.Message> nesnesi.  
  
 Bu yöntemleri yazma standart Aktarım Protokolü ve özelleştirilmiş kodlama arasında dönüştürme işleyen kodu değil.  
  
 Ardından özel kodlayıcıyı oluşturan bir Üreteç sınıfını kod gerekir. Geçersiz kılma <xref:System.ServiceModel.Channels.MessageEncoderFactory.Encoder%2A> özel bir örneğini döndürmek için <xref:System.ServiceModel.Channels.MessageEncoder>.  
  
 Özel bağlanma <xref:System.ServiceModel.Channels.MessageEncoderFactory> hizmet veya istemci geçersiz kılarak yapılandırmak için kullanılan bağlama öğesi yığınına <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> yöntemi bu üretecin bir örneğini döndürür.  
  
 Bu işlem örnek kodu göstermeye WCF ile sağlanan iki örnek vardır: [özel ileti Kodlayıcı: özel metin Kodlayıcı](../../../../docs/framework/wcf/samples/custom-message-encoder-custom-text-encoder.md) ve [özel ileti Kodlayıcı: sıkıştırma Kodlayıcısı](../../../../docs/framework/wcf/samples/custom-message-encoder-compression-encoder.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.MessageEncoderFactory>  
 <xref:System.ServiceModel.Channels.MessageEncoder>  
 [Veri Aktarımı Mimarisi Genel Bakış](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)  
 [İleti Kodlayıcı Seçme](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [Taşıma Seçme](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
