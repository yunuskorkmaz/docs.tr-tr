---
title: İleti Kodlayıcı Seçme
ms.date: 03/30/2017
ms.assetid: 2204d82d-d962-4922-a79e-c9a231604f19
ms.openlocfilehash: d93d7039d034262cd47edd437d5d7d8d63890f02
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635771"
---
# <a name="choose-a-message-encoder"></a>İleti Kodlayıcısı Seçin

Bu makalede, Windows Communication Foundation (WCF) içinde yer alan ileti kodlayıcıları arasında seçim yapmak için ölçütler açıklanmaktadır: ikili, metin ve İleti Iletimi Optimizasyon Mekanizması (MTOM).  
  
 WCF'de, *bağlayıcı öğeler*den oluşan *bir*bağlama yoluyla uç noktalar arasında bir ağ üzerinden nasıl veri aktarılabildiğini belirtirsiniz. İleti kodlayıcısı, bağlama yığınındaki bağlama öğesini kodlayan bir ileti ilemi ile temsil edilir. Bağlama, güvenlik bağlama öğesi veya güvenilir ileti bağlama öğesi, gerekli ileti kodlama bağlayıcı öğesi ve gerekli aktarım bağlama öğesi gibi isteğe bağlı iletişim bağlama öğelerini içerir.  
  
 İleti kodlama bağlama öğesi isteğe bağlı protokol bağlama öğelerinin altında ve gerekli aktarım bağlama öğesinin üzerinde yer almaktadır. Giden tarafta, bir ileti kodlayıcısı giden <xref:System.ServiceModel.Channels.Message> idizine serileştirir ve taşımaya geçirir. Gelen tarafta, ileti kodlayıcısı aktarımdan serileştirilmiş bir <xref:System.ServiceModel.Channels.Message> form alır ve varsa daha yüksek protokol katmanına veya yoksa uygulamaya geçirir.  
  
 Önceden varolan bir istemciye veya sunucuya bağlanırken, iletilerinizi diğer tarafın beklediği şekilde kodlamanız gerektiğinden, belirli bir ileti kodlaması hakkında seçeneğiniz olmayabilir. Ancak, bir WCF hizmeti yazıyorsanız, her biri farklı bir ileti kodlaması kullanarak hizmetinizi birden çok uç nokta üzerinden ortaya çıkarabilirsiniz. Bu, istemcilerin kendileri için en iyi olan bitiş noktası üzerinden hizmetinizle konuşmak için en iyi kodlamayı seçmelerine ve müşterilerinize kendileri için en iyi kodlamayı seçme esnekliği ni seçmelerine olanak tanır. Birden çok uç nokta kullanmak, farklı ileti kodlamalarının avantajlarını diğer bağlama öğeleriyle birleştirmenize de olanak tanır.  
  
## <a name="system-provided-encoders"></a>Sistem Destekli Kodlayıcılar  
 WCF, aşağıdaki üç sınıf tarafından temsil edilen üç ileti kodlayıcıiçerir:  
  
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>, metin iletisi kodlayıcı, hem düz XML kodlama ve SOAP kodlama destekler. Metin iletisi kodlayıcısının düz XML kodlama modu, metin tabanlı SOAP kodlamasından ayırt etmek için "düz eski XML" (POX) olarak adlandırılır. POX'u etkinleştirmek <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement.MessageVersion%2A> için <xref:System.ServiceModel.Channels.MessageVersion.None%2A>özelliği ' ye göre ayarlayın. WCF olmayan uç noktalarıyla birlikte çalışmak için metin iletisi kodlayıcısını kullanın.  
  
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>, ikili mesaj kodlayıcısı, kompakt ikili bir biçim kullanır ve WCF ile WCF iletişimi için optimize edilmiştir ve bu nedenle birlikte çalışabilir değildir. Bu aynı zamanda WCF'nin sağladığı tüm kodlayıcıların en çok performans gösteren kodlayıcısıdır.  
  
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>, bağlama öğesi, MTOM kodlama kullanarak iletiler için karakter kodlama ve ileti sürümü belirtir. MTOM, WCF iletilerinde ikili veri aktarımı için etkili bir teknolojidir. MTOM kodlayıcısı verimlilik ve birlikte çalışabilirlik arasında bir denge oluşturmaya çalışır. MTOM kodlaması çoğu XML'i metin biçiminde iletir, ancak büyük ikili veri bloklarını metne dönüştürmeden olduğu gibi ileterek optimize eder. Verimlilik açısından, WCF sağlar kodlayıcılar arasında, MTOM metin (en yavaş) ve ikili (en hızlı) arasında.  
  
## <a name="how-to-choose-a-message-encoder"></a>İleti Kodlayıcısı Nasıl Seçilir?  
 Aşağıdaki tabloda ileti kodlayıcısı seçmek için kullanılan yaygın etkenler açıklanmaktadır. Uygulamanız için önemli olan etkenlere öncelik verin ve ardından bu etkenlerle en iyi şekilde çalışan ileti kodlayıcılarını seçin. Bu tabloda listelenmemiş ek faktörleri ve uygulamanızda gerekli olabilecek özel ileti kodlayıcılarını göz önünde bulundurun.  
  
|Faktörü|Açıklama|Bu faktörü destekleyen kodlayıcılar|  
|------------|-----------------|---------------------------------------|  
|Desteklenen Karakter Setleri|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>ve <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> sadece UTF8 ve UTF16 Unicode *(büyük-endian* ve *little-endian)* kodlamaları destekler. UTF7 veya ASCII gibi başka kodlamalar gerekiyorsa, özel bir kodlayıcı kullanılmalıdır. Örnek özel kodlayıcı için [Bkz. Özel İleti Kodlayıcısı.](https://docs.microsoft.com/dotnet/framework/wcf/samples/custom-message-encoder-custom-text-encoder)|Metin|  
|Denetim|Denetim, iletim sırasında iletileri inceleyebilme yeteneğidir. SABUN'un kullanımı olsun veya olmasın, metin kodlamaları, iletilerin özel araçlar kullanılmadan birçok uygulama tarafından incelenmesine ve analiz edilmesine olanak sağlar. İleti veya aktarım düzeyinde aktarım güvenliğinin kullanımı, iletileri inceleme yeteneğinizi etkiler. Gizlilik, bir iletiyi incelenmekten korur ve bütünlük bir iletiyi değiştirilmekten korur.|Metin|  
|Güvenilirlik|Güvenilirlik, bir kodlayıcının iletim hatalarına karşı dayanıklılığıdır. İleti, aktarım veya uygulama katmanında güvenilirlik de sağlanabilir. Tüm standart WCF kodlayıcıları başka bir katmanın güvenilirlik sağladığını varsayar. Kodlayıcının iletim hatasını kurtarma yeteneği çok azdır.|None|  
|Sade -lik|Basitlik, kodlama belirtimi için kodlayıcılar ve kod çözücüler oluşturabileceğiniz kolaylığı temsil eder. Metin kodlamaları özellikle basitlik açısından avantajlıdır ve POX metin kodlaması SOAP'ın işlenmesi için destek gerektirmeme avantajına sahiptir.|Metin (POX)|  
|Boyut|Kodlama, içeriğe uygulanan ek yük miktarını belirler. Kodlanmış iletilerin boyutu, hizmet işlemlerinin maksimum verimi ile doğrudan ilişkilidir. İkili kodlamalar genellikle metin kodlamalarından daha kompakttır. İleti boyutu çok yüksekolduğunda, kodlama sırasında ileti içeriğini sıkıştırmayı da düşünün. Ancak, sıkıştırma hem ileti gönderen hem de alıcı için işlem maliyetleri ekler.|İkili|  
|Akış|Akış, uygulamaların iletinin tamamı gelmeden önce bir iletiyi işlemeye başlamasını sağlar. Akış'ı etkin bir şekilde kullanmak, iletinin önemli verilerinin iletinin başında kullanılabilir olmasını gerektirir, böylece alıcı uygulamanın ulaşmasını beklemesi gerekmez. Ayrıca, akışlı aktarım kullanan uygulamaların, içeriğin iletme bağımlılıkları olmaması için iletideki verileri aşamalı olarak düzenlemesi gerekir. Çoğu durumda, içerik akışı ile bu içerik için mümkün olan en küçük aktarım boyutuna sahip olmak arasında uzlaşma nız gerekir.|None|  
|Üçüncü Taraf Araç Desteği|Kodlama için destek alanları geliştirme ve tanı içerir. Üçüncü taraf geliştiriciler, POX biçiminde kodlanmış iletileri işlemek için kitaplıklara ve araç kitlerine büyük bir yatırım yaptı.|Metin (POX)|  
|Birlikte Çalışabilirlik|Bu faktör, bir WCF kodlayıcısının WCF olmayan hizmetlerle birlikte çalışabilme yeteneğini ifade eder.|Metin<br /><br /> MTOM (kısmi)|  
  
Not: İkili Kodlayıcı'yı kullanırken, XMLReader oluştururken IgnoreWhitespace ayarını kullanmak hiçbir etki yaratmaz.  Örneğin, bir hizmet işlemi içinde aşağıdakileri yaparsanız:  

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
  
YokSaybeyaz boşluk ayarı yoksayılır.  
  
## <a name="compression-and-the-binary-encoder"></a>Sıkıştırma ve İkili Kodlayıcı

WCF 4.5 ile başlayarak WCF ikili kodlayıcı sıkıştırma desteği ekler. Bu, bir WCF istemcisinden sıkıştırılmış iletigöndermek için gzip/deflate algoritmasını kullanmanıza ve aynı zamanda kendi barındırılan bir WCF hizmetinden sıkıştırılmış iletilerle yanıt vermenize olanak tanır. Bu özellik, hem HTTP hem de TCP aktarımlarında sıkıştırmasağlar. IIS barındırılan bir WCF hizmeti, IIS ana bilgisayar sunucusunu yapılandırarak sıkıştırılmış yanıt göndermek için her zaman etkinleştirilebilir. Sıkıştırma türü <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A?displayProperty=nameWithType> özelliği ile yapılandırılır. Bu özellik <xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType> enum değerlerinden birine ayarlanır:

- <xref:System.ServiceModel.Channels.CompressionFormat.Deflate>
- <xref:System.ServiceModel.Channels.CompressionFormat.GZip>
- <xref:System.ServiceModel.Channels.CompressionFormat.None>
  
Bu özellik yalnızca binaryMessageEncodingBindingElement'de açıkta olduğundan, bu özelliği kullanmak için aşağıdaki gibi özel bir bağlama oluşturmanız gerekir:

 ```xml
 <customBinding>
   <binding name="BinaryCompressionBinding">
     <binaryMessageEncoding compressionFormat ="GZip" />
     <httpTransport />
  </binding>
</customBinding>
 ```

Hem istemci hem de hizmetin sıkıştırılmış iletiler göndermeyi ve almayı kabul etmesi gerekir ve bu nedenle sıkıştırmaBiçimi özelliği hem istemci hem de hizmetteki binaryMessageEncoding öğesi üzerinde yapılandırılmalıdır. Hizmet veya istemci sıkıştırma için yapılandırılmamışsa, ancak diğer taraf bir ProtocolException atılır. Sıkıştırmayı etkinleştirme dikkatle düşünülmelidir. Ağ bant genişliği bir darboğaz ise sıkıştırma çoğunlukla yararlıdır. CPU'nun darboğaz olduğu durumlarda, sıkıştırma iş buzunu azaltır. Bunun uygulamaya fayda sağp sağlamaması için simüle edilmiş bir ortamda uygun test yapılmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlamalar](../../../../docs/framework/wcf/feature-details/bindings.md)
