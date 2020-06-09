---
title: İleti Kodlayıcı Seçme
ms.date: 03/30/2017
ms.assetid: 2204d82d-d962-4922-a79e-c9a231604f19
ms.openlocfilehash: dbc5981013fe5e023f1d6d9eaf64b2e1fa18e2df
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84587345"
---
# <a name="choose-a-message-encoder"></a>Ileti Kodlayıcısı seçin

Bu makalede, Windows Communication Foundation (WCF) ' de bulunan ileti kodlayıcıları arasından seçim yapma ölçütleri ele alınmaktadır: ikili, metin ve Ileti Iletimi Iyileştirme mekanizması (MTOM).  
  
 WCF 'de, bir bağlama yoluyla, bir *bağlantı öğelerinden*oluşan bir diziyle oluşturulan *bağlama*aracılığıyla verilerin bir ağ üzerinden nasıl aktarılacağı belirtirsiniz. İleti Kodlayıcısı, bağlama yığınında bir ileti kodlama bağlama öğesi tarafından temsil edilir. Bağlama, bir güvenlik bağlama öğesi veya güvenilir mesajlaşma bağlama öğesi, gerekli bir ileti kodlama bağlama öğesi ve gerekli bir aktarım bağlama öğesi gibi isteğe bağlı protokol bağlama öğeleri içerir.  
  
 İleti kodlama bağlama öğesi, isteğe bağlı protokol bağlama öğelerinin altında ve gerekli aktarım bağlama öğesinin üzerinde bulunur. Giden tarafta, bir ileti Kodlayıcısı giden bir iletiyi serileştirir <xref:System.ServiceModel.Channels.Message> ve aktarıma geçirir. Gelen tarafta bir ileti Kodlayıcısı, aktarımdan bir ' ın serileştirilmiş formunu alır <xref:System.ServiceModel.Channels.Message> ve varsa, daha yüksek protokol katmanına, varsa, ya da uygulamaya geçirir.  
  
 Önceden var olan bir istemciye veya sunucuya bağlanırken, iletilerinizi diğer tarafın beklediği bir şekilde kodlamak gerektiğinden, belirli bir ileti kodlamasının kullanılmasına ilişkin bir seçeneğe sahip olmayabilirsiniz. Ancak, bir WCF hizmeti yazıyorsanız, her biri farklı bir ileti kodlaması kullanan birden fazla uç nokta aracılığıyla hizmetinizi kullanıma sunabilirsiniz. Bu, istemcilerin en iyi bir uç nokta üzerinden hizmetinize konuşmak için en iyi kodlamayı seçmesini ve istemcileriniz için en uygun kodlamayı seçme esnekliği vermeyi sağlar. Birden çok uç nokta kullanmak, farklı ileti kodlamalarının avantajlarını diğer bağlama öğeleriyle birleştirmenize de olanak tanır.  
  
## <a name="system-provided-encoders"></a>Sistem tarafından sunulan kodlayıcılar  
 WCF, aşağıdaki üç sınıf tarafından temsil edilen üç ileti kodlayıcıları içerir:  
  
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>metin iletisi Kodlayıcısı, hem düz XML kodlamasını hem de SOAP kodlamasını destekler. Metin iletisi kodlayıcısından düz XML kodlama moduna, metin tabanlı SOAP kodlamadan ayırt etmek için "düz eski XML" (POX) denir. POX 'i etkinleştirmek için <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement.MessageVersion%2A> özelliğini olarak ayarlayın <xref:System.ServiceModel.Channels.MessageVersion.None%2A> . WCF olmayan uç noktalarla birlikte çalışmak için SMS mesajı Kodlayıcısı 'nı kullanın.  
  
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>ikili ileti Kodlayıcısı, bir Compact ikili biçimi kullanır ve WCF ile WCF iletişimine iyileştirilmiştir ve bu nedenle birlikte çalışabilir. Bu, aynı zamanda tüm kodlayıcılar WCF 'nin sağladığı en performanslı kodlayıcıdır.  
  
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>, Binding öğesi, MTOM kodlaması kullanan iletiler için karakter kodlamasını ve ileti sürüm oluşturmayı belirtir. MTOM, WCF iletilerindeki ikili verileri iletmek için etkili bir teknolojidir. MTOM Kodlayıcısı verimlilik ve birlikte çalışabilirlik arasında bir denge oluşturmaya çalışır. MTOM kodlaması çoğu XML 'i metinsel biçimde iletir, ancak bu verileri,, metne dönüştürülmeksizin olduğu gibi ileterek büyük ikili veri bloklarını iyileştirir. , Kodlayıcılar WCF 'nin sağladığı verimlilik açısından, MTOM, metin (en yavaş) ve ikili (en hızlı) arasındadır.  
  
## <a name="how-to-choose-a-message-encoder"></a>Ileti Kodlayıcısı seçme  
 Aşağıdaki tabloda bir ileti Kodlayıcısı seçmek için kullanılan yaygın faktörler açıklanmaktadır. Uygulamanız için önemli olan faktörleri önceliklendirin ve ardından bu faktörlerle en iyi şekilde çalışan ileti kodlayıcıları ' nı seçin. Bu tabloda listelenmeyen ek faktörleri ve uygulamanızda gerekebilecek tüm özel ileti kodlayıcıları göz önünde bulundurduğunuzdan emin olun.  
  
|Çarpan|Açıklama|Bu faktörü destekleyen kodlayıcılar|  
|------------|-----------------|---------------------------------------|  
|Desteklenen karakter kümeleri|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>ve <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> yalnızca UTF8 ve UTF16 Unicode (*Big-endian* ve *little-endian*) kodlamalarını destekler. UTF7 veya ASCII gibi diğer kodlamalar gerekliyse, özel bir kodlayıcı kullanılmalıdır. Örnek özel bir kodlayıcı için bkz. [özel Ileti Kodlayıcısı](https://docs.microsoft.com/dotnet/framework/wcf/samples/custom-message-encoder-custom-text-encoder).|Metin|  
|İncelemesi|İnceleme, iletim sırasında iletileri incelemenize olanak sağlar. SOAP kullanımı olmadan veya kullanmadan metin kodlamaları, özel araçların kullanılması gerekmeden iletilerin birçok uygulama tarafından İncelenme ve çözümlenme izni verir. Aktarım güvenliği 'nin ileti veya Aktarım düzeyinde kullanımı, iletileri İnceleme yeteneğinizi etkiler. Gizlilik bir iletinin incelenmeden korunmasını sağlar ve bütünlüğü bir iletinin değiştirilmesini önler.|Metin|  
|Güvenilirlik|Güvenilirlik, bir kodlayıcı için hata aktarma esnekliği sağlar. Güvenilirlik ileti, taşıma veya uygulama katmanında de belirtilebilir. Standart WCF kodlayıcılarıyla, başka bir katmanın güvenilirlik sağladığını varsayalım. Kodlayıcı bir iletim hatasından kurtulacak.|Yok|  
|Olması|Basitlik, kodlama belirtimi için kodlayıcılar ve kod çözücüleri oluşturabileceğiniz kolaylığınızı temsil eder. Metin kodlamaları basitlik için özellikle avantajlıdır ve POX metin kodlaması SOAP işleme desteğinin gerekli olmadığı ek avantajlara sahiptir.|Metin (POX)|  
|Boyut|Kodlama, içerikte uygulanan ek yükün miktarını belirler. Kodlanmış iletilerin boyutu, hizmet işlemlerinin en yüksek aktarım hızı ile doğrudan ilgilidir. İkili kodlamalar genellikle metin kodlamasından daha küçüktür. İleti boyutu Premium olduğunda, kodlama sırasında ileti içeriğini de sıkıştırmayı göz önünde bulundurun. Ancak, sıkıştırma ileti gönderici ve alıcı için işleme maliyetlerini ekler.|İkili|  
|Akış|Akış, tüm ileti alınmadan önce uygulamaların bir iletiyi işlemeye başlamasını sağlar. Akış kullanımı etkin olarak, ileti için önemli verilerin iletinin başlangıcında kullanılabilmesi için, alıcı uygulamanın gelmesi beklemek zorunda olmaması gerekir. Ayrıca, akışlı aktarım kullanan uygulamaların, içerikte ileri doğru bağımlılıklara sahip olmaması için iletideki verileri artımlı olarak düzenlemesi gerekir. Çoğu durumda, akış içeriği arasında uzlaşmak ve bu içerik için olası en küçük aktarım boyutuna sahip olmanız gerekir.|Yok|  
|Üçüncü taraf araç desteği|Bir kodlamaya yönelik destek alanı geliştirme ve tanılama 'yı içerir. Üçüncü taraf geliştiriciler, POX biçiminde kodlanmış iletileri işlemeye yönelik kitaplıklarda ve araç setlerine büyük bir yatırım yaptı.|Metin (POX)|  
|Birlikte çalışabilirlik|Bu faktör, WCF Kodlayıcısı 'nın WCF olmayan hizmetlerle birlikte çalışabilme yeteneğini ifade eder.|Metin<br /><br /> MTOM (kısmi)|  
  
Note: BINARY Encoder kullanılırken, XMLReader oluşturma sırasında IgnoreWhitespace ayarının kullanılması hiçbir etkiye sahip olmayacaktır.  Örneğin, bir hizmet işlemi içinde aşağıdakileri yaparsanız:  

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
  
IgnoreWhitespace ayarı yok sayılır.  
  
## <a name="compression-and-the-binary-encoder"></a>Sıkıştırma ve Ikili kodlayıcı

WCF ikili Kodlayıcısı 4,5 ile başlayarak sıkıştırma için destek ekler. Bu, bir WCF istemcisinden sıkıştırılmış iletiler göndermek için gzip/söndür algoritmasını kullanmanızı ve ayrıca şirket içinde barındırılan bir WCF hizmetinden sıkıştırılmış iletilerle yanıt vermesini sağlar. Bu özellik hem HTTP hem de TCP aktarımlarında sıkıştırmayı sunar. IIS konak sunucusunu yapılandırarak, IIS tarafından barındırılan bir WCF hizmeti her zaman sıkıştırılmış yanıtları göndermek için etkinleştirilebilir. Sıkıştırma türü, özelliği ile yapılandırılır <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A?displayProperty=nameWithType> . Bu özellik, <xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType> Enum değerlerinden birine ayarlanır:

- <xref:System.ServiceModel.Channels.CompressionFormat.Deflate>
- <xref:System.ServiceModel.Channels.CompressionFormat.GZip>
- <xref:System.ServiceModel.Channels.CompressionFormat.None>
  
Bu özellik yalnızca binaryMessageEncodingBindingElement üzerinde kullanıma sunulduğundan, bu özelliği kullanmak için aşağıdaki gibi bir özel bağlama oluşturmanız gerekecektir:

 ```xml
 <customBinding>
   <binding name="BinaryCompressionBinding">
     <binaryMessageEncoding compressionFormat ="GZip" />
     <httpTransport />
  </binding>
</customBinding>
 ```

Hem istemci hem de hizmetin sıkıştırılmış iletiler göndermesini ve almasını kabul etmesi ve bu nedenle, hem istemci hem de hizmette bulunan binaryMessageEncoding öğesinde compressionFormat özelliğinin yapılandırılması gerekir. Hizmet veya istemci sıkıştırma için yapılandırılmamışsa ancak diğer taraf ise ProtocolException oluşur. Sıkıştırmanın etkinleştirilmesi dikkatle düşünülmelidir. Sıkıştırma, ağ bant genişliği bir performans sorunu olduğunda yararlıdır. CPU 'nun performans sorunu olduğu durumlarda, sıkıştırma işlemi performansı düşürür. Uygulamanın avantaja sahip olup olmadığını öğrenmek için, bir sanal ortamda uygun test yapılmalıdır  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlamalar](bindings.md)
