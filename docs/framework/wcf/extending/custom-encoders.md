---
title: Özel Kodlayıcılar
ms.date: 03/30/2017
ms.assetid: fa0e1d7f-af36-4bf4-aac9-cd4eab95bc4f
ms.openlocfilehash: 586207af0bfbe106512dfb61ee7439d4f5ce64c6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797212"
---
# <a name="custom-encoders"></a>Özel Kodlayıcılar
Bu konu başlığında özel kodlayıcılar oluşturma konusu ele alınmaktadır.  
  
 Windows Communication Foundation (WCF) ' de, bir ağ üzerinden uç noktalar arasında veri aktarımını belirtmek için bir *bağlama* kullanırsınız. Bağlama *öğelerinden*oluşan bir sıralama oluşur. Bağlama, güvenlik, gerekli bir *Ileti Kodlayıcısı* bağlama öğesi ve gerekli bir aktarım bağlama öğesi gibi isteğe bağlı protokol bağlama öğelerini içerir. İleti Kodlayıcısı bir ileti kodlama bağlama öğesiyle temsil edilir. WCF 'ye üç ileti kodlayıcıları dahildir: İkili, Ileti Iletimi Iyileştirme mekanizması (MTOM) ve metin.  
  
 Bir ileti kodlama bağlama öğesi, bir bağlantıyı serileştirir <xref:System.ServiceModel.Channels.Message> ve aktarıma geçirir ya da aktarımdan bir iletinin seri hale getirilmiş formunu alır ve varsa bunu, varsa protokol katmanına geçirir.  
  
 İleti kodlayıcıları, <xref:System.ServiceModel.Channels.Message> bir tel gösterimden ve bu örneklere örnek dönüştürür. Kodlayıcılar kanal yığınındaki aktarım katmanının üzerinde oturmuş gibi açıklansa da, bunlar aktarım katmanının içinde yer alır. Aktarımlar (örneğin, HTTP), aktarım standardının gereksinimlerine göre iletiyi biçimlendirir. Kodlayıcılar (örneğin, metin XML) yalnızca iletiyi kodlayın.  
  
 Önceden var olan bir istemciye veya sunucuya bağlanırken, belirli bir ileti kodlamasının kullanılmasıyla ilgili bir seçeneğe sahip olmayabilirsiniz. Ancak, WCF Hizmetleri, her biri farklı ileti Kodlayıcısı olan birden fazla uç nokta aracılığıyla erişilebilir hale getirilebilir. Tek bir kodlayıcı hizmetinize ilişkin tüm hedef kitlesini kapsamadığı zaman, hizmetinizi birden fazla uç nokta üzerinden kullanıma sunar. İstemci uygulamaları daha sonra kendileri için en iyi uç noktayı seçebilir. Birden çok bitiş noktası kullanmak, farklı ileti Kodlayıcılarının avantajlarını diğer bağlama öğeleriyle birleştirmenize olanak tanır.  
  
## <a name="system-provided-encoders"></a>Sistem tarafından sunulan kodlayıcılar  
 WCF, en yaygın uygulama senaryolarını kapsayacak şekilde tasarlanan çeşitli sistem tarafından sağlanan bağlamalar sağlar. Bu bağlamalardan her biri bir aktarım, ileti Kodlayıcısı ve diğer seçenekleri (örneğin, güvenlik) birleştirir. Bu konuda, WCF 'ye dahil edilen `Text`, `Binary`, ve `MTOM` ileti kodlayıcıların nasıl genişletileceği veya kendi özel kodlayıcılarınızın nasıl oluşturulduğu açıklanmaktadır. Kısa mesaj Kodlayıcısı hem düz XML kodlamasının hem de SOAP kodlamaları destekler. Metin iletisi kodlayıcısından düz XML kodlama moduna, metin tabanlı SOAP kodlamadan ayırt etmek için POX ("düz eski XML") kodlayıcı adı verilir.  
  
 Sistem tarafından belirtilen bağlamalar tarafından sunulan bağlama öğelerinin birleşimleri hakkında daha fazla bilgi için, [Taşıma Seçme](../feature-details/choosing-a-transport.md)konusunun ilgili bölümüne bakın.  
  
## <a name="how-to-work-with-system-provided-encoders"></a>Sistem tarafından sunulan kodlayıcılarla çalışma  
 Bir kodlama, öğesinden <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>türetilmiş bir sınıf kullanılarak bağlamaya eklenir.  
  
 WCF, metin, ikili ve ileti iletimi iyileştirme mekanizması ( <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> MTOM) kodlaması için sağlayabileceğiniz sınıftan türetilmiş aşağıdaki bağlama öğesi türlerini sağlar:  
  
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>: En çok çalışabilen, ancak XML iletileri için en az verimli kodlayıcı. Bir Web hizmeti veya Web hizmeti istemcisi, genellikle metinsel XML 'i anlayabilir. Ancak, büyük ikili veri bloklarını metin olarak iletmek verimli değildir.  
  
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>: İkili tabanlı XML iletileri için kullanılan karakter kodlamasını ve ileti sürüm oluşturmayı belirten bağlama öğesini temsil eder. Bu, kodlama seçeneklerinin en etkilidir, ancak yalnızca WCF uç noktaları tarafından desteklendiğinden, en az birlikte kullanılabilir.  
  
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>: Ileti Iletimi Iyileştirme mekanizması (MTOM) kodlaması kullanan bir ileti için kullanılan karakter kodlamasını ve ileti sürüm oluşturmayı belirten bağlama öğesini temsil eder. MTOM, WCF iletilerindeki ikili verileri iletmek için etkili bir teknolojidir. MTOM Kodlayıcısı verimlilik ve birlikte çalışabilirlik arasında denge kurmaya çalışır. MTOM kodlaması çoğu XML 'i metinsel biçimde iletir, ancak bu verileri,, metne dönüştürülmeksizin olduğu gibi ileterek büyük ikili veri bloklarını iyileştirir.  
  
 Binding öğesi bir ikili, MTOM veya metin <xref:System.ServiceModel.Channels.MessageEncoderFactory>oluşturur. Fabrika bir ikili, MTOM veya metin <xref:System.ServiceModel.Channels.MessageEncoderFactory> örneği oluşturur. Genellikle yalnızca tek bir örnek vardır. Ancak oturumlar kullanılıyorsa, her oturuma farklı bir kodlayıcı istenebilir. Ikili kodlayıcı, dinamik sözlükleri koordine etmek için bunu kullanır (bkz. XML altyapısı).  
  
 <xref:System.ServiceModel.Channels.MessageEncoder.ReadMessage%2A> Ve<xref:System.ServiceModel.Channels.MessageEncoder.WriteMessage%2A> yöntemleri, kodlayıcıların çekirdekleridir. Yöntemler bir akıştan veya bir <xref:System.Byte> diziden bir ileti okumayı sağlar. Aktarım, arabelleğe alınmış modda çalışırken bayt dizileri kullanılır. Mesajlar her zaman akışlara yazılır. Taşıma iletiyi arabelleğe alıyorsa, arabelleğe alma yapan bir akış sağlar.  
  
 Üyelerin geri kalanı destek içeriği, medya türleri ve <xref:System.ServiceModel.Channels.MessageEncoder.MessageVersion%2A>desteğiyle çalışır. Taşıma bu kodlayıcı yöntemlerini, gelen iletinin onun tarafından çözülip çözülmeyeceğini test etmek veya giden iletinin bu kodlayıcı için geçerli olup olmadığını anlamak için çağırır.  
  
 Üç kodlayıcı uygulamasının her biri, belirli kodlayıcılara uygun özellikleri ekler ve tamamen yapılandırılabilir. Kodlayıcılar Ayrıca güvenli varsayılanlara sahip okuyucu kotaları sunar. Kotaların bir tartışması için bkz. XML altyapısı.  
  
## <a name="features-of-system-provided-encoders"></a>Sistem tarafından sunulan kodlayıcılara ait özellikler  
 Sistem tarafından sunulan kodlayıcılar tarafından sunulan birçok özellik vardır.  
  
### <a name="pooling"></a>Biriktirme  
 Kodlayıcı uygulamalarının her biri, mümkün olduğunca çok havuzu oluşturmaya çalışır. Ayırmaları azaltmak, yönetilen kodun performansını artırmanın önemli bir yoludur. Bu havuzlamayı başarmak için uygulamalar `SynchronizedPool` sınıfını kullanır. Dosya C# , bu sınıf tarafından kullanılan ek iyileştirmelerin bir açıklamasını içerir.  
  
 <xref:System.Xml.XmlDictionaryReader>ve <xref:System.Xml.XmlDictionaryWriter> örnekleri havuza alınır ve her ileti için yeni bir ayırma yapılmasını engellemek için yeniden başlatılır. Okuyucular için, çağrıldığında `OnClose` `Close()` okuyucu geri kazanır bir geri çağırma işlemi. Kodlayıcı Ayrıca ileti oluştururken kullanılan bazı ileti durum nesnelerini de geri dönüştürür. Bu havuzların boyutları, `MaxReadPoolSize` öğesinden <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>türetilmiş üç sınıfın her `MaxWritePoolSize` birinde ve özellikleri tarafından yapılandırılabilir.  
  
### <a name="binary-encoding"></a>İkili kodlama  
 İkili kodlama oturumları kullandığında, dinamik sözlük dizesinin ileti alıcısına bildirilmesi gerekir. Bu, iletiyi dinamik sözlük dizelerine önek olarak çağırarak yapılır. Alıcı dizelerin dışına şeritler, bunları oturuma ekler ve iletiyi işler. Sözlük dizelerini doğru şekilde geçirmek, taşımanın arabelleğe alınmasının yapılmasını gerektirir.  
  
 Dizeler bir iç `AddSessionInformationToMessage` yöntem tarafından iletiye eklenir. Bu, dizeleri UTF-8 olarak önek ön eki olan iletinin önüne ekler. Tüm sözlük üst bilgisi daha sonra verilerinin uzunluğuna önek olarak eklenir. Ters işlem, bir iç `ExtractSessionInformationFromMessage` yöntem tarafından gerçekleştirilir.  
  
 Dinamik sözlük anahtarlarını işlemenin yanı sıra, ara belleğe alınmış oturumsuz iletiler benzersiz bir şekilde alınır. Belge üzerinde bir okuyucu oluşturmak ve onu işlemek yerine ikili kodlayıcı, ikili akışı oluşturmak için iç `MessagePatterns` sınıfı kullanır. Bu düşünce, çoğu iletinin WCF tarafından oluşturulan belirli bir sırada görüntülenen belirli bir başlık kümesine sahip olması fikrindedir. Model sistemi, beklediği işe göre iletiyi ayırır. Başarılı olursa, bir <xref:System.ServiceModel.Channels.MessageHeaders> nesneyi XML ayrıştırmadan başlatır. Aksi takdirde, standart yönteme geri döner.  
  
### <a name="mtom-encoding"></a>MTOM Kodlama  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> Sınıfında adlı<xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement.MaxBufferSize%2A>ek bir yapılandırma özelliği bulunur. Bu, bir iletiyi okuma işlemi sırasında arabelleğe izin verilen veri miktarına bağlı olarak bir üst sınır koyar. Tüm MIME parçalarını tek bir ileti halinde yeniden birleştirmek için XML bilgi kümesi (Infoset) veya diğer MIME bölümlerinin ara belleğe alınmış olması gerekebilir.  
  
 HTTP ile doğru şekilde çalışmak için, iç MTOM ileti Kodlayıcısı sınıfı, için `GetContentType` bazı iç API 'ler (Ayrıca, iç) sağlar ve `WriteMessage`bu genel ve geçersiz kılınabilir. HTTP başlıklarındaki değerlerin MIME başlıklarındaki değerlerle uyumlu olduğundan emin olmak için daha fazla iletişim oluşması gerekir.  
  
 Dahili olarak, MTOM ileti Kodlayıcısı WCF 'nin metin okuyucularını kullanır ve metin kodlayıcıyla benzerdir. Ana fark, büyük ölçekli ikilinin veya "Ikili büyük nesneler" (blob 'Lar), ileti baytlarına katıştırmadan önce Base-64 kodlamaya dönüştürmeden en iyi duruma getirmektedir. Bunun yerine, bu Bloblar ayıklanmakta tutulur ve MIME ekleri olarak başvurulur.  
  
## <a name="writing-your-own-encoder"></a>Kendi kodlayıcınızı yazma  
 Kendi özel ileti kodlayıcıınızı uygulamak için aşağıdaki soyut temel sınıfların özel uygulamalarını sağlamanız gerekir:  
  
- <xref:System.ServiceModel.Channels.MessageEncoder>  
  
- <xref:System.ServiceModel.Channels.MessageEncoderFactory>  
  
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
  
 Bir iletinin bellek içi gösteriminden bir akışa yazılabilen bir gösterime dönüştürme, XML okuyucuları ve belirli XML kodlamaları türlerini destekleyen XML yazarları <xref:System.ServiceModel.Channels.MessageEncoder> için bir fabrika görevi gören sınıfı içinde kapsüllenir.  
  
- Bu sınıfın geçersiz kılmanız gereken anahtar yöntemleri şunlardır:  
  
- <xref:System.ServiceModel.Channels.MessageEncoder.WriteMessage%2A>bir <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> nesnesi alır ve bir <xref:System.IO.Stream> nesnesine yazar.  
  
- <xref:System.ServiceModel.Channels.MessageEncoder.ReadMessage%2A>bir <xref:System.IO.Stream> nesne ve en büyük üst bilgi boyutu alır ve bir <xref:System.ServiceModel.Channels.Message> nesne döndürür.  
  
 Bu yöntemler, standart Aktarım Protokolü ve özelleştirilmiş kodunuzla dönüştürmeyi işleyen bu yöntemlere yazdığınız koddur.  
  
 Ardından, özel kodlayıcıyı oluşturan bir fabrika sınıfını kodlarınızın olması gerekir. <xref:System.ServiceModel.Channels.MessageEncoderFactory.Encoder%2A> Özel<xref:System.ServiceModel.Channels.MessageEncoder>bir örneğini döndürmek için öğesini geçersiz kılın.  
  
 Ardından, <xref:System.ServiceModel.Channels.MessageEncoderFactory> <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> bu fabrikasının bir örneğini döndürmek için yöntemini geçersiz kılarak hizmeti veya istemciyi yapılandırmak için kullanılan bağlama öğesi yığınına özel ' i bağlayın.  
  
 Bu işlemi örnek kodla gösteren WCF ile birlikte sağlanan iki örnek vardır: [Özel Ileti Kodlayıcısı: Özel metin Kodlayıcısı](../samples/custom-message-encoder-custom-text-encoder.md) ve [özel ileti Kodlayıcısı: Sıkıştırma Kodlayıcısı](../samples/custom-message-encoder-compression-encoder.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MessageEncoderFactory>
- <xref:System.ServiceModel.Channels.MessageEncoder>
- [Veri Aktarımı Mimarisi Genel Bakış](../feature-details/data-transfer-architectural-overview.md)
- [İleti Kodlayıcı Seçme](../feature-details/choosing-a-message-encoder.md)
- [Taşıma Seçme](../feature-details/choosing-a-transport.md)
