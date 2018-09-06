---
title: İleti Kodlayıcı Seçme
ms.date: 03/30/2017
ms.assetid: 2204d82d-d962-4922-a79e-c9a231604f19
ms.openlocfilehash: 5d2b55f04954cdd855ff9e224d2bc0405919f7a3
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43773113"
---
# <a name="choosing-a-message-encoder"></a>İleti Kodlayıcı Seçme
Windows Communication Foundation (WCF) dahil edilen ileti kodlayıcılarda arasından seçim ölçütleri bu konuda ele alınmıştır: ikili ve metin iletisi iletim en iyi duruma getirme mekanizması (MTOM).  
  
 WCF'de, belirttiğiniz yoluyla uç noktalar arasında bir ağ üzerinden veri aktarmak nasıl bir *bağlama*, bir dizi yapılan *bağlama öğelerinin*. İleti Kodlayıcı bağlama öğesi bağlama yığınında kodlama bir ileti gösterilir. Bir bağlama güvenlik bağlama öğesi veya güvenilir Mesajlaşma bağlama öğesi, bağlama öğesi ve gerekli aktarım bağlama öğesinin kodlama gerekli bir ileti gibi isteğe bağlı Protokolü bağlama öğeleri içerir.  
  
 İleti kodlama bağlama öğesi, isteğe bağlı Protokolü bağlama öğeleri altında ve gerekli aktarım bağlama öğesi üstünde bulunur. Giden ileti Kodlayıcı giden tarafında serileştiren <xref:System.ServiceModel.Channels.Message> ve aktarmaya geçirir. Gelen tarafında ileti Kodlayıcı seri hala getirilmiş biçimini alır. bir <xref:System.ServiceModel.Channels.Message> taşıma ve daha yüksek protokolü için katman, varsa, geçiş veya uygulamaya, aksi takdirde.  
  
 Bir önceden var olan bir istemci veya sunucu bağlanırken iletilerinizi diğer tarafı bekleniyor bir şekilde kodlama olması gerektiğinden bir özel ileti kodlama kullanma hakkında bir seçim olmayabilir. Ancak, bir WCF Hizmeti yazıyorsanız, her bir farklı ileti kodlama kullanılarak hizmetinizi birden çok uç noktaları aracılığıyla kullanıma sunabilirsiniz. Bu istemciler, istemciler kendileri için en iyi seçeneği kodlamayı esnekliğini yanı sıra kendileri için en iyi uç nokta üzerinden hizmetinize konuşmak için en iyi kodlama seçmenizi sağlar. Birden fazla uç nokta kullanarak, farklı ileti Kodlamalar avantajlarını diğer bağlama öğeleri ile birleştirmek de sağlar.  
  
## <a name="system-provided-encoders"></a>Sistem tarafından sağlanan kodlayıcılar  
 WCF aşağıdaki üç sınıf tarafından temsil edilen üç ileti kodlayıcılar içerir:  
  
-   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>, metin ileti Kodlayıcı hem düz XML kodlama ve SOAP kodlamasına destekler. Metin ileti Kodlayıcı düz XML kodlama modunu "düz eski XML" olarak adlandırılır (POX metin tabanlı SOAP kodlamadan diğerine ayırt etmek için). POX etkinleştirmek için <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement.MessageVersion%2A> özelliğini <xref:System.ServiceModel.Channels.MessageVersion.None%2A>. Metin ileti Kodlayıcı olmayan WCF uç noktaları ile çalışmak için kullanın.  
  
-   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>, ikili ileti Kodlayıcısı, sıkıştırılmış bir ikili biçimini kullanır ve WCF için WCF iletişim için optimize edilmiştir ve bu nedenle birlikte çalışabilir değil. En yüksek performanslı Kodlayıcı WCF sağlar kodlayıcıların karşılaştırılması de budur.  
  
-   <<!--zz xref:System.ServiceModel.Channels.MTOMMessageEncodingBindingElement --> `System.ServiceModel.Channels.MTOMMessageEncodingBindingElement`> ileti sürüm oluşturma için iletileri MTOM kodlama kullanılarak ve bağlama öğesi, karakter kodlamasını belirtir. MTOM WCF iletilerinde ikili veri aktarımı için verimli bir teknolojidir. MTOM Kodlayıcısı verimliliği ve birlikte çalışabilirlik arasında bir denge oluşturmaya çalışır. MTOM kodlama çoğu XML metin biçiminde aktarır, ancak büyük ikili veri blokları olarak ileterek iyileştirir-olan metin dönüştürme olmadan. WCF sağlar, kodlayıcılarda arasında verimliliği açısından MTOM (yavaş) raflarının metin ve ikili (hızlı) var.  
  
## <a name="how-to-choose-a-message-encoder"></a>İleti Kodlayıcı seçme  
 Aşağıdaki tabloda, bir ileti Kodlayıcı seçmek için kullanılan ortak faktörleri anlatılmaktadır. Uygulamanız için önemlidir ve ileti kodlayıcılarda en iyi çalışan seçin faktörlerin faktörlerle öncelik verin. Bu tabloda ve uygulamanızı gerekli tüm özel ileti kodlayıcılar listelenmeyen ek faktörleri dikkate aldığınızdan emin olun.  
  
|faktörü|Açıklama|Bu destek kodlayıcılar|  
|------------|-----------------|---------------------------------------|  
|Desteklenen karakter kümeleri|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> ve <<!--zz xref:System.ServiceModel.Channels.MTOMMessageEncodingBindingElement --> `System.ServiceModel.Channels.MTOMMessageEncodingBindingElement`> yalnızca UTF8 ve UTF16 Unicode desteği (*büyük endian* ve *endian*) kodlamaları. Diğer Kodlamalar, UTF7 veya ASCII gibi gerekiyorsa, özel bir kodlayıcı kullanılması gerekir. Örnek özel bir kodlayıcı için bkz: [özel ileti Kodlayıcı](https://go.microsoft.com/fwlink/?LinkId=119857).|Metin|  
|İnceleme|İnceleme aktarım sırasında iletilerini incelemek için yeteneğidir. Metin kodlamalarını ile veya SOAP kullanmadan inceledi ve birçok uygulamasında özel araçlar tarafından kullanmadan analiz iletileri sağlar. Aktarım güvenliği, ileti veya aktarım düzeyinde kullanımını iletileri İnceleme olanağınız etkilediğini unutmayın. İncelenmekte olan bir ileti gizliliğini korur ve değiştirilmesini bir ileti bütünlüğü korur.|Metin|  
|Güvenilirlik|Güvenilirlik, bir kodlayıcının iletim hatalara dayanıklılıktır. Güvenilirlik, message, taşıma veya uygulama katmanı sağlanabilir. Tüm standart WCF kodlayıcılarda başka bir katmanı güvenilirlik sağladığını varsayalım. Kodlayıcı iletim hatadan kurtarmak için çok az özelliğine sahiptir.|Yok.|  
|Basitliği|Basitlik, ile Kodlayıcıları ve kod çözücüleri bir kodlama belirtimi için oluşturabileceğiniz bir kolayca temsil eder. Metin kodlamalarını kolaylık olması için özellikle yararlı ve POX metin kodlaması SOAP işlemek için destek gerektirmeyen ek avantajı vardır.|Metin (POX)|  
|Boyut|Kodlama, içerik uygulanan ek yükü miktarını belirler. Kodlanan ileti boyutu, hizmet işlemleri en fazla aktarım hızı için doğrudan ilgilidir. İkili Kodlamalar genellikle metin kodlamalarını daha küçük. İleti boyutu bir premium olduğunda, ayrıca ileti içeriği kodlama sırasında sıkıştırma göz önünde bulundurun. Ancak, sıkıştırma ileti gönderen ve alıcı için işlem maliyetleri ekler.|İkili|  
|Akış|Akış, iletinin tamamı edinildi önce bir iletiyi işlemesi uygulamalar sağlar. Etkili bir şekilde akış'ı kullanarak, böylece alıcı uygulama gelmesi için beklenecek gerekli değildir önemli verileri bir ileti için ileti başında kullanılabilir olmasını gerektirir. Ayrıca, içerik İleri bağımlılıklar yok. böylece akış aktarım kullanan uygulamalar verileri artımlı olarak düzenlemelisiniz. Çoğu durumda, içerik akışı yapmak ve içerik için en küçük olası Aktarım boyutu arasındaki tehlikeye gerekir.|Yok.|  
|3. taraf araç desteğini|Destek alanları bir kodlama için geliştirme ve tanılama içerir. Üçüncü taraf geliştiriciler, kitaplıkları ve araç Setleri POX biçiminde kodlanmış iletileri işlemek için büyük bir yatırım yaptık.|Metin (POX)|  
|Birlikte Çalışabilirlik|Bu faktör olmayan WCF hizmetleri ile çalışmak için bir WCF Kodlayıcısı yeteneğini gösterir.|Metin<br /><br /> MTOM (kısmi)|  
  
Not: ikili Kodlayıcı kullanırken bir XMLReader oluştururken IgnoreWhitespace ayarıyla hiçbir etkisi olmaz.  Örneğin, aşağıdakileri bir hizmet işlemi içinde:  

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
  
## <a name="compression-and-the-binary-encoder"></a>Sıkıştırma ve ikili kodlayıcı

WCF 4.5 ile başlayarak WCF ikili Kodlayıcı sıkıştırma desteği ekler. Bu, bir WCF istemciden sıkıştırılmış iletileri göndermek için gzip nebo deflate algoritmasını kullanmanızı sağlar ve ayrıca şirket içinde barındırılan bir WCF hizmetinden sıkıştırılmış ileti ile yanıt. Bu özellik hem HTTP hem de TCP taşımalar sıkıştırmayı sağlar. Bir IIS barındırılan WCF hizmeti her zaman etkinleştirilebilir IIS konak sunucusunu yapılandırarak sıkıştırılmış yanıtlar göndermek için. Sıkıştırma türünü yapılandırılmış <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A?displayProperty=nameWithType> özelliği. Bu özellik, birine ayarlanır <xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType> enum değerleri:

* `CompressionFormat.Deflate`
* `CompressionFormat.GZip`
* `CompressionFormat.None`
  
Bu özellik yalnızca binaryMessageEncodingBindingElement üstündeki açık olduğundan, bu özelliği kullanmak için aşağıdaki gibi özel bir bağlama oluşturmak ihtiyacınız olacak:

 ```xml
 <customBinding>
   <binding name="BinaryCompressionBinding">
     <binaryMessageEncoding compressionFormat ="GZip" />
     <httpTransport />
  </binding>
</customBinding>
 ```

Hem istemci hem de hizmet sıkıştırılmış iletileri gönderip kabul etmeniz gerekir ve bu nedenle compressionformat'ı özelliği binaryMessageEncoding öğesinde hem istemci hem de hizmet yapılandırılması gerekir. Bir ProtocolException ya da hizmet veya istemcinin sıkıştırma için yapılandırılmamış ancak diğer taraf oluşturulur. Sıkıştırmayı etkinleştirme dikkatle düşünülmelidir. Sıkıştırma, çoğunlukla ağ bant genişliği bir performans sorunu oluşturuyorsa yararlıdır. CPU performans sorunu olduğu durumlarda, sıkıştırma, aktarım hızı azaltır. Bu uygulama avantajlar öğrenmek için sanal bir ortamda uygun sınama gerçekleştirilmelidir  
  
## <a name="see-also"></a>Ayrıca Bkz.

[Bağlamalar](../../../../docs/framework/wcf/feature-details/bindings.md)
