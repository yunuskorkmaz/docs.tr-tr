---
title: İleti Kodlayıcı Seçme
ms.date: 03/30/2017
ms.assetid: 2204d82d-d962-4922-a79e-c9a231604f19
ms.openlocfilehash: bf40d31e3ee04136a094b5045f2502e29caceec8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494868"
---
# <a name="choosing-a-message-encoder"></a>İleti Kodlayıcı Seçme
Bu konuda Windows Communication Foundation (WCF) dahil edilen ileti kodlayıcılar arasından seçim ölçütleri ele alınmıştır: ikili, metin ve ileti iletim en iyi duruma getirme mekanizmasını (MTOM).  
  
 WCF'de, belirttiğiniz yoluyla uç noktaları arasında bir ağ üzerinden veri aktarımı nasıl bir *bağlama*, hangi oluşur bir dizi *bağlama öğeleri*. İleti Kodlayıcı bağlama öğesi bağlama yığınında kodlama bir ileti gösterilir. Bir bağlama güvenlik bağlama öğesi veya güvenilir Mesajlaşma bağlama öğesi, bağlama öğesi ve gerekli aktarım bağlama öğesi kodlama gerekli bir ileti gibi isteğe bağlı Protokolü bağlama öğeleri içerir.  
  
 İleti kodlama bağlama öğesi, isteğe bağlı Protokolü bağlama öğeleri altında ve gerekli aktarım bağlama öğesi üstünde bulunur. Giden ileti Kodlayıcı giden tarafında serileştiren <xref:System.ServiceModel.Channels.Message> ve aktarıma geçirir. Gelen tarafında bir ileti Kodlayıcı serileştirilmiş biçiminde alır. bir <xref:System.ServiceModel.Channels.Message> taşıma ve daha yüksek protokolü için katman, varsa geçişleri ya da uygulamaya, aksi takdirde.  
  
 Bir önceden var olan istemci veya sunucu bağlanırken iletilerinizi, diğer taraftaki bekleniyor şekilde kodlamak gerektiğinden bir belirli ileti kodlama kullanılarak hakkında bir seçim olmayabilir. Ancak, bir WCF Hizmeti yazıyorsanız, her farklı ileti kodlama kullanılarak hizmetinizi birden fazla uç noktası aracılığıyla ortaya çıkarabilirsiniz. Bu istemciler istemcileriniz kodlama kendileri için en iyi seçim yapma esnekliği vermiş yanı sıra bunları için en iyisidir uç nokta üzerinden hizmetinize Konuşmayı için en iyi kodlama seçmenize olanak sağlar. Birden çok uç noktalarını kullanarak diğer bağlama öğeleriyle farklı ileti Kodlamalar avantajları birleştirmek sağlar.  
  
## <a name="system-provided-encoders"></a>Sistem tarafından sağlanan kodlayıcılar  
 WCF aşağıdaki üç sınıfları tarafından temsil edilen üç ileti kodlayıcılar içerir:  
  
-   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>, metin ileti Kodlayıcı hem düz XML kodlama ve kodlama SOAP destekler. Metin ileti Kodlayıcı düz XML kodlama modunu "düz eski XML" olarak adlandırılır (POX SOAP metin tabanlı kodlamadan ayırt etmek için). POX etkinleştirmek için ayarlanmış <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement.MessageVersion%2A> özelliğine <xref:System.ServiceModel.Channels.MessageVersion.None%2A>. WCF olmayan uç ile birlikte çalışmak için metin ileti Kodlayıcı kullanın.  
  
-   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>, ikili ileti Kodlayıcı sıkıştırılmış bir ikili biçimi kullanır ve WCF için WCF iletişimi için optimize edilmiştir ve bu nedenle birlikte çalışabilir değil. WCF sağlayan tüm kodlayıcılar, çoğu kullanıcı Kodlayıcı de budur.  
  
-   <<!--zz xref:System.ServiceModel.Channels.MTOMMessageEncodingBindingElement --> `System.ServiceModel.Channels.MTOMMessageEncodingBindingElement`>, bağlama öğesi karakter kodlamasını belirtir ve ileti sürüm oluşturma için iletileri MTOM kodlama kullanılarak. MTOM WCF iletilerindeki ikili veri iletmek için verimli bir teknolojidir. MTOM Kodlayıcısı verimliliği ve birlikte çalışabilirlik arasında bir denge oluşturmaya çalışır. MTOM kodlama çoğu XML metin biçiminde aktarır ancak bunları olarak ileterek büyük ikili veri blokları en iyi duruma getirir-metne dönüştürme olmadan, ise. WCF sağlar, kodlayıcılar arasında verimliliği açısından MTOM (yavaş) ortası metin ve ikili (hızlı) olur.  
  
## <a name="how-to-choose-a-message-encoder"></a>İleti Kodlayıcı seçme  
 Aşağıdaki tabloda bir ileti Kodlayıcı seçmek için kullanılan ortak faktörde açıklanmaktadır. Uygulamanız için önemli olan ve ileti kodlayıcılar o iş en iyi seçin faktörlerin faktörleriyle öncelik verin. Bu tabloyu ve uygulamanızı gerekli tüm özel ileti kodlayıcılar listelenmeyen herhangi bir ek etken dikkate aldığınızdan emin olun.  
  
|Faktörü|Açıklama|Bu faktör destek kodlayıcılar|  
|------------|-----------------|---------------------------------------|  
|Desteklenen karakter kümeleri|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> ve <<!--zz xref:System.ServiceModel.Channels.MTOMMessageEncodingBindingElement --> `System.ServiceModel.Channels.MTOMMessageEncodingBindingElement`> yalnızca UTF8 ve UTF16 Unicode desteği (*big endian* ve *little endian*) kodlaması. Diğer Kodlamalar, UTF7 veya ASCII gibi gerekirse, özel bir kodlayıcı kullanılması gerekir. Özel bir örnek Kodlayıcısı için bkz: [özel ileti Kodlayıcı](http://go.microsoft.com/fwlink/?LinkId=119857).|Metin|  
|Denetleme|Denetleme iletilerini iletim sırasında inceleyin yeteneğidir. Metin kodlamalarını, ile veya SOAP, kullanmadan Denetlenmekte ve birçok uygulama özelleştirilmiş araçları tarafından kullanmadan analiz için iletilerini izin verin. İleti veya aktarım düzeyinde aktarımı güvenlik kullanımını iletileri inceleyin yeteneğinizi etkilediğini unutmayın. İncelenmesi gelen ileti gizliliği korur ve değiştirilmesini bir ileti bütünlüğünü korur.|Metin|  
|Güvenilirlik|Güvenilirlik bir kodlayıcı iletim hatalara esnekliğini ' dir. Güvenilirlik, ileti, taşıma veya uygulama katmanı sağlanabilir. Tüm standart WCF kodlayıcılar başka bir katmana güvenilirlik sağlayan varsayılır. Kodlayıcı iletim hatadan kurtarmak için çok az özelliğine sahiptir.|Yok.|  
|Basitlik|Basitlik ile Kodlayıcıları ve kod çözücüleri bir kodlama belirtimi için oluşturmanın kolaylığı temsil eder. Metin kodlamalarını kolaylık sağlamak için özellikle yararlı ve POX metin kodlaması SOAP işlemek için destek gerektirmeyen ek avantajı vardır.|Metin (POX)|  
|Boyut|Kodlama içerik uygulanan ek yük miktarı belirler. Kodlanmış iletilerin boyutunu hizmet işlemleri için en yüksek verimlilik doğrudan ilişkilidir. İkili kodlamaları genellikle metin kodlamalarını daha küçük. İleti boyutu premium olduğunda, ileti içeriği kodlama sırasında da sıkıştırmayı göz önünde bulundurun. Ancak, sıkıştırma ileti gönderici ve alıcı için işlem maliyetleri ekler.|İkili|  
|Akış|Akış uygulamalarının tüm ileti geldi önce bir iletiyi işlemesi olanak sağlar. Akış etkili şekilde kullanma böylece alıcı uygulama gelmesini bekleyin için gerekli olmayan bir ileti için önemli verileri ileti başında kullanılabilir olmasını gerektirir. Böylece içeriği İleri bağımlılıklar yok Ayrıca, akış aktarımı kullanan uygulamalar veri iletisi artımlı olarak düzenlemeniz gerekir. Çoğu durumda, içerik akışı ve içerik için en küçük olası transfer boyuta sahip arasında tehlikeye gerekir.|Yok.|  
|3 parti aracı desteği|Bir kodlama için destek alanları geliştirme ve tanılama içerir. Üçüncü taraf geliştiriciler kitaplıkları ve POX biçimde kodlanmış iletileri işlemek için araç takımları büyük yatırım yaptık.|Metin (POX)|  
|Birlikte Çalışabilirlik|Bu faktör bir WCF Kodlayıcısı WCF olmayan hizmetleriyle yeteneğini gösterir.|Metin<br /><br /> MTOM (kısmi)|  
  
Not: ikili kodlama kullanırken, bir XMLReader oluştururken IgnoreWhitespace ayarı kullanarak hiçbir etkisi olmaz.  Örneğin, aşağıdakileri bir hizmet işlemi içinde:  

```csharp
public void OperationContract(XElement input)
{
    Console.WriteLine("{0}", input.Value);
    int counter = 0;
    var xreader = input.CreateReader();
    var reader = XmlReader.Create(xreader, new XmlReaderSettings() { IgnoreWhitespace = true });
    while (reader.Read())
    {
        counter++;
    }

    Console.WriteLine("Read {0} lines with reader", counter);
}
```  
  
IgnoreWhitespace ayar yok sayılır.  
  
## <a name="compression-and-the-binary-encoder"></a>Sıkıştırma ve ikili kodlama

WCF ikili kodlama WCF 4.5 ile başlayan sıkıştırma desteği ekler. Bu, gzip ve deflate algoritması WCF istemciden sıkıştırılmış ileti göndermek için kullanmanıza olanak sağlar ve ayrıca bir kendi kendini barındıran WCF hizmetinden sıkıştırılmış iletileriyle yanıt. Bu özellik hem HTTP hem de TCP taşımaları sıkıştırmayı sağlar. Bir IIS barındırılan WCF hizmeti her zaman etkinleştirilebilir IIS ana bilgisayar sunucusunu yapılandırarak sıkıştırılmış yanıtlar göndermek için. Sıkıştırma türünü ile yapılandırılmış <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A?displayProperty=nameWithType> özelliği. Bu özellik, birine ayarlandığında <xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType> enum değerleri:

* `CompressionFormat.Deflate`
* `CompressionFormat.GZip`
* `CompressionFormat.None`
  
Bu özellik yalnızca binaryMessageEncodingBindingElement üstündeki açık olduğundan, bu özelliği kullanmak için aşağıdaki gibi özel bağlama oluşturmanız gerekir:

 ```xml
 <customBinding>
   <binding name="BinaryCompressionBinding">
     <binaryMessageEncoding compressionFormat ="GZip" />
     <httpTransport />
  </binding>
</customBinding>
 ```

Hem istemci hem de hizmet sıkıştırılmış ileti gönderme ve alma kabul etmeniz ve bu nedenle compressionFormat özelliği hem istemci hem de hizmet binaryMessageEncoding öğede yapılandırılması gerekir. Bir ProtocolException ya da hizmet ya da istemci sıkıştırma yapılandırılmamış ancak diğer taraf atılır. Sıkıştırmayı etkinleştirme dikkatle düşünülmelidir. Sıkıştırma, çoğunlukla ağ bant genişliği tıkanıklık olması durumunda faydalıdır. CPU performans sorunu olduğu durumda sıkıştırma verimliliği azaltır. Bu uygulama avantaj öğrenmek için sanal bir ortamda uygun test yapılmalıdır  
  
## <a name="see-also"></a>Ayrıca Bkz.

[Bağlamalar](../../../../docs/framework/wcf/feature-details/bindings.md)
