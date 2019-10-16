---
title: Temel Windows Communication Foundation Kavramları
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], concepts
- concepts [WCF]
- fundamentals [WCF]
- Windows Communication Foundation [WCF], concepts
ms.assetid: 3e7e0afd-7913-499d-bafb-eac7caacbc7a
ms.openlocfilehash: 9dcaa5f73dd8a4ec1943cb7fc840feee889563b8
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319842"
---
# <a name="fundamental-windows-communication-foundation-concepts"></a>Temel Windows Communication Foundation Kavramları

Bu belge Windows Communication Foundation (WCF) mimarisinin üst düzey bir görünümünü sağlar. Temel kavramları ve bunların birbirine nasıl uyduğunu açıklamak için tasarlanmıştır. WCF hizmeti ve istemcisinin en basit sürümünü oluşturmaya yönelik bir öğretici için bkz. [Başlangıç Öğreticisi](getting-started-tutorial.md). WCF programlamayı öğrenmek için bkz. [Temel WCF programlama](basic-wcf-programming.md).

## <a name="wcf-fundamentals"></a>WCF temelleri

WCF, hizmetler ve istemciler arasında ileti gönderen sistemler oluşturmak için bir çalışma zamanı ve API kümesidir. Aynı altyapı ve API 'Ler, aynı bilgisayar sistemindeki diğer uygulamalarla ya da başka bir şirkette bulunan ve Internet üzerinden erişilen bir sistemde iletişim kuran uygulamalar oluşturmak için kullanılır.

### <a name="messaging-and-endpoints"></a>Mesajlaşma ve uç noktalar

WCF, ileti tabanlı iletişim kavramının yanı sıra bir ileti olarak modellenebilir (örneğin, bir HTTP isteği veya bir Message Queuing (MSMQ olarak da bilinir) iletisi), programlama modelinde tek bir şekilde temsil edilebilir. Bu, farklı aktarım mekanizmaları genelinde birleştirilmiş bir API sunar.

Model, istemcilerle iletişim kurmasını ve bu iletişime yanıt vermesini bekleyen uygulamalar olan istemcilerle iletişim ve _hizmet_Başlatan uygulamalar olan _istemciler_arasında ayrım yapar. Tek bir uygulama, hem istemci hem de hizmet olarak davranabilir. Örnekler için bkz. [çift yönlü hizmetler](./feature-details/duplex-services.md) ve [eşler arası ağ iletişimi](./feature-details/peer-to-peer-networking.md).

İletiler uç noktalar arasında gönderilir. _Uç noktalar_ , iletilerin gönderileceği veya alındığı, ileti değişimi için gereken tüm bilgileri tanımladıkları yerdir. Bir hizmet, bir veya daha fazla uygulama uç noktası (Ayrıca sıfır veya daha fazla altyapı uç noktası) sunar ve istemci hizmetin uç noktalarından biriyle uyumlu bir uç nokta oluşturur.

Bir _uç nokta_ , iletilerin gönderilmesi gereken, nasıl gönderilmesi gerektiği ve iletilerin nasıl görünebileceği standart tabanlı bir şekilde açıklanmaktadır. Bir hizmet, istemcilerin uygun WCF istemcileri ve iletişim _yığınları_oluşturmak için işleyebilecekleri meta veriler olarak bu bilgileri açığa çıkarır.

### <a name="communication-protocols"></a>İletişim protokolleri

İletişim yığınının gerekli bir öğesi _aktarım protokolüdür_. İletiler, HTTP ve TCP gibi ortak aktarımlar kullanılarak intranetten ve Internet üzerinden gönderilebilir. Eş ağ ağlarında Message Queuing uygulamaları ve düğümleri ile iletişimi destekleyen diğer aktarımlar da dahil edilmiştir. WCF 'nin yerleşik uzantı noktaları kullanılarak daha fazla taşıma mekanizması eklenebilir.

İletişim yığınındaki başka bir gerekli öğe, belirli bir iletinin nasıl biçimlendirildiğini belirten kodlamadır. WCF aşağıdaki kodlamaları sağlar:

- Metin kodlama, birlikte çalışabilen bir kodlama.

- İleti Iletimi Iyileştirme mekanizması (MTOM) kodlaması, bir hizmete veya bir hizmetten yapılandırılmamış ikili verileri etkin bir şekilde göndermek için birlikte çalışabilen bir yoldur.

- Etkili aktarım için ikili kodlama.

WCF 'nin yerleşik uzantı noktaları kullanılarak daha fazla kodlama mekanizması (örneğin, bir sıkıştırma kodlaması) eklenebilir.

### <a name="message-patterns"></a>İleti desenleri

WCF, istek-yanıt, tek yönlü ve çift yönlü iletişim dahil olmak üzere çeşitli mesajlaşma düzenlerini destekler. Farklı aktarımlar farklı mesajlaşma düzenlerini destekler ve bu nedenle destekledikleri etkileşimlerin türlerini etkiler. WCF API 'Leri ve çalışma zamanı, iletileri güvenli ve güvenilir bir şekilde göndermenize de yardımcı olur.

## <a name="wcf-terms"></a>WCF koşulları

WCF belgelerinde kullanılan diğer kavramlar ve terimler şunları içerir:

**İleti**  
 Gövde ve üst bilgiler dahil olmak üzere çeşitli bölümlerden oluşabilen, kendi kendine içerilen veri birimi.

**Hizmet**  
 Her uç nokta bir veya daha fazla hizmet işlemini açığa çıkaran bir veya daha fazla uç nokta sunan bir yapı.

**Uç nokta**  
 İletilerin gönderildiği veya alındığı bir yapı (veya her ikisi de). İletilerin nereden gönderilebileceğini tanımlayan bir konum (bir adres), iletilerin nasıl gönderilmesi gerektiğini açıklayan iletişim mekanizması (bağlama) belirtimi ve bu sırada gönderilebilecek veya alınabilecek bir ileti kümesi için tanım (veya her ikisi de) içerir. Hangi iletinin gönderilebileceklerini açıklayan konum (bir hizmet sözleşmesi).

Bir WCF hizmeti, bir uç nokta koleksiyonu olarak dünyaya açıktır.

**Uygulama uç noktası**  
 Uygulama tarafından sunulan ve uygulama tarafından uygulanan bir hizmet sözleşmesine karşılık gelen bir uç nokta.

**Altyapı uç noktası**  
 Bir hizmet sözleşmesiyle ilgisi olmayan hizmet tarafından gerekli veya sağlanmış işlevselliği kolaylaştırmak için altyapı tarafından açığa çıkarılan bir uç nokta. Örneğin, bir hizmette meta veri bilgileri sağlayan bir altyapı uç noktası olabilir.

**Adrestir**  
 İletilerin alındığı konumu belirtir. Tekdüzen Kaynak tanımlayıcısı (URI) olarak belirtilir. URI şeması bölümü, HTTP ve TCP gibi adrese ulaşmak için kullanılacak taşıma mekanizmasını adlandırır. URI 'nin hiyerarşik bölümü, biçimi aktarım mekanizmasına bağlı olan benzersiz bir konum içerir.

Uç nokta adresi, bir hizmette bulunan her bir uç nokta için veya belirli koşullar altında, uç noktalar arasında bir adres paylaşmak için benzersiz uç nokta adresleri oluşturmanızı sağlar. Aşağıdaki örnek, HTTPS protokolünü varsayılan olmayan bir bağlantı noktasıyla kullanan bir adresi gösterir:

```http
HTTPS://cohowinery:8005/ServiceModelSamples/CalculatorService
```

**Bağlama**  
 Bir uç noktanın dünya ile nasıl iletişim kuracağını tanımlar. İletişim altyapısını oluşturmak için diğeri üzerinde "Stack" olan bağlama öğeleri adlı bir bileşen kümesi oluşturulur. En azından, bir bağlama taşıma (HTTP veya TCP gibi) ve kullanılan kodlama (örneğin, metin veya ikili) tanımlar. Bağlama, iletileri güvenli hale getirmek için kullanılan güvenlik mekanizmaları veya bir uç nokta tarafından kullanılan ileti deseninin gibi ayrıntıları belirten bağlama öğeleri içerebilir. Daha fazla bilgi için bkz. [Hizmetleri yapılandırma](configuring-services.md).

**Bağlama öğesi**  
 Bir aktarım, bir kodlama, bir altyapı düzeyi Protokolü (örneğin, WS-ReliableMessaging) veya iletişim yığınının başka bir bileşeni gibi, bağlamanın belirli bir parçasını temsil eder.

**Davranışlar**  
 Bir hizmetin, bir uç noktanın, belirli bir işlemin veya bir istemcinin çeşitli çalışma zamanı yönlerini denetleyen bir bileşen. Davranışlar, kapsama göre gruplandırılır: ortak davranışlar tüm uç noktaları küresel olarak etkiler, hizmet davranışları, yalnızca hizmetle ilgili özellikleri etkiler, uç nokta davranışları yalnızca uç noktayla ilgili özellikleri etkiler ve işlem düzeyi davranışları özel olarak etkiler operasyonları. Örneğin, bir hizmet davranışı, bir hizmetin çok fazla sayıda ileti işleme yeteneklerini yoğun bir şekilde tehdit eden bir hizmetin nasıl tepki verdiğini belirten azaltmadır. Diğer yandan bir uç nokta davranışı, bir güvenlik kimlik bilgisinin nasıl ve nerede bulunacağı gibi yalnızca uç noktalarla ilgili olan yönleri denetler.

**Sistem tarafından sağlanmış bağlamalar**  
 WCF, bir dizi sistem tarafından sağlanmış bağlamaları içerir. Bunlar, belirli senaryolar için iyileştirilmiş bağlama öğelerinin koleksiyonlarıdır. Örneğin <xref:System.ServiceModel.WSHttpBinding>, çeşitli WS-\* belirtimleri uygulayan hizmetlerle birlikte çalışabilirlik için tasarlanmıştır. Bu ön tanımlı bağlamalar, yalnızca belirli senaryoya doğru şekilde uygulanabilen seçenekleri sunarak zamandan tasarruf sağlar. Önceden tanımlanmış bir bağlama gereksinimlerinizi karşılamıyorsa, kendi özel bağlamalarınızı oluşturabilirsiniz.

**Yapılandırma ve kodlamaya karşı**  
 Bir uygulamanın denetimi, kodlama veya yapılandırma yoluyla ya da her ikisinin bir birleşimi aracılığıyla yapılabilir. Yapılandırma, geliştirici dışındaki birinin (örneğin, bir ağ yöneticisi) kod yazıldıktan ve yeniden derlenmeden sonra istemci ve hizmet parametrelerini ayarlayabilmesini sağlar. Yapılandırma yalnızca uç nokta adresleri gibi değerleri ayarlamanıza imkan tanır, ancak uç noktalar, bağlamalar ve davranışlar eklemenize olanak tanıyarak daha fazla denetime de izin verir. Kodlama, geliştiricinin hizmet veya istemcinin tüm bileşenleri üzerinde katı denetimi korumasını sağlar ve yapılandırma aracılığıyla yapılan tüm ayarlar denetlenir ve kod tarafından geçersiz kılınır.

**Hizmet işlemi**  
 Bir işlemin işlevlerini uygulayan bir hizmetin kodunda tanımlanan yordam. Bu işlem, istemcilere bir WCF istemcisinde yöntemler olarak sunulur. Yöntemi bir değer döndürebilir ve isteğe bağlı sayıda bağımsız değişken alabilir ya da hiçbir bağımsız değişkeni alabilir ve yanıt vermez. Örneğin, basit bir "Hello" olarak işlev gören bir işlem, bir istemcinin varlığına yönelik bildirim olarak kullanılabilir ve bir dizi işlem başlatabilir.

**Hizmet sözleşmesi**  
 , Birden çok ilgili işlemi tek bir işlevsel birimde birleştirir. Sözleşme, hizmetin ad alanı, buna karşılık gelen bir geri çağırma anlaşması ve diğer ayarları gibi hizmet düzeyi ayarları tanımlayabilir. Çoğu durumda, sözleşme tercih ettiğiniz programlama dilinde bir arabirim oluşturularak ve <xref:System.ServiceModel.ServiceContractAttribute> özniteliğini arabirimine uygulayarak tanımlanır. Gerçek hizmet kodu, arabirimini uygulayarak oluşur.

**İşlem sözleşmesi**  
 Bir işlem sözleşmesi, bir işlemin parametrelerini ve dönüş türünü tanımlar. Hizmet sözleşmesini tanımlayan bir arabirim oluştururken, sözleşmenin bir parçası olan her yöntem tanımına <xref:System.ServiceModel.OperationContractAttribute> özniteliğini uygulayarak bir işlem sözleşmesini işaret edersiniz. İşlemler tek bir ileti alarak ve tek bir ileti döndürerek veya bir tür kümesi alarak ve bir tür döndürdüğünde modellenebilir. İkinci durumda, sistem söz konusu işlem için alışverişi gereken iletilerin biçimini saptacaktır.

**İleti sözleşmesi**  
 Bir iletinin biçimini açıklar. Örneğin, ileti öğelerinin üstbilgiye ve gövdeye, hangi güvenlik düzeyinin ileti öğelerine uygulanacağını ve bu şekilde ilgili olduğunu bildirir.

**Hata sözleşmesi**  
 Çağırana döndürülebilecek hataları göstermek için bir hizmet işlemiyle ilişkilendirilebilir. Bir işlem ile ilişkili sıfır veya daha fazla hata olabilir. Bu hatalar, programlama modelinde özel durum olarak modellenen SOAP hatalarıdır.

**Veri sözleşmesi**  
 Bir hizmetin kullandığı veri türlerinin meta verilerindeki açıklamalar. Bu, başkalarının hizmetle birlikte çalışabilmesine olanak sağlar. Veri türleri, bir iletinin herhangi bir bölümünde, örneğin, parametreler veya dönüş türleri olarak kullanılabilir. Hizmet yalnızca basit türler kullanıyorsa, veri sözleşmelerini açık bir şekilde kullanmaya gerek yoktur.

**Barındırma**  
 Bir hizmetin bazı süreçte barındırılması gerekir. _Ana bilgisayar_ , hizmetin ömrünü denetleyen bir uygulamadır. Hizmetler, mevcut bir barındırma işlemi tarafından kendiliğinden barındırılabilir veya yönetilebilir.

**Şirket içinde barındırılan hizmet**  
 Geliştiricinin oluşturduğu bir işlem uygulaması içinde çalışan bir hizmet. Geliştirici ömrünü denetler, hizmetin özelliklerini ayarlar, hizmeti açar (bunu bir dinleme moduna dönüştürür) ve hizmeti kapatır.

**Barındırma işlemi**  
 Hizmetleri barındırmak için tasarlanan bir uygulama. Bunlara Internet Information Services (IIS), Windows Etkinleştirme Hizmetleri (WAS) ve Windows hizmetleri dahildir. Bu barındırılan senaryolarda, konak hizmetin ömrünü denetler. Örneğin, IIS kullanarak hizmet derlemesini ve yapılandırma dosyasını içeren bir sanal dizin ayarlayabilirsiniz. Bir ileti alındığında IIS, hizmeti başlatır ve ömrünü denetler.

**Örnek Oluşturma**  
 Hizmetin bir örnek oluşturma modeli vardır. Üç örnek oluşturma modeli vardır: tek bir CLR nesnesinin tüm istemcilere hizmet veren "tek" Her bir istemci çağrısını işlemek için yeni bir CLR nesnesi oluşturulduğu çağrı başına, " ve her ayrı oturum için bir CLR nesneleri kümesinin oluşturulduğu "oturum başına". Bir örnek oluşturma modeli seçimi, uygulamanın gereksinimlerine ve hizmetin beklenen kullanım düzenine bağlıdır.

**İstemci uygulaması**  
 Bir veya daha fazla uç nokta ile ileti alışverişi yapan bir program. İstemci uygulaması, WCF istemcisinin bir örneğini oluşturarak ve WCF istemcisinin çağırma yöntemlerine başlar. Tek bir uygulamanın hem istemci hem de hizmet olabileceğini göz önünde bulundurulmamak önemlidir.

**Kanalla**  
 Bağlama öğesinin somut bir uygulamasıdır. Bağlama yapılandırmayı temsil eder ve kanal bu yapılandırmayla ilişkili bir uygulama olur. Bu nedenle, her bağlama öğesiyle ilişkili bir kanal vardır. Bağlama somut uygulamasını oluşturmak için her birinin üst kısmında kanallar yığını: kanal yığını.

**WCF istemcisi**  
 Hizmet işlemlerini yöntemler olarak sunan bir istemci-uygulama yapısı (Visual Basic veya görsel C#gibi tercih ettiğiniz .NET Framework programlama dilinde). Herhangi bir uygulama, bir hizmeti barındıran uygulama dahil olmak üzere bir WCF istemcisi barındırabilir. Bu nedenle, diğer hizmetlerin WCF istemcilerini içeren bir hizmet oluşturmak mümkündür.

Bir WCF istemcisi, [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) kullanılarak otomatik olarak oluşturulabilir ve meta verileri yayımlayan çalışan bir hizmete işaret edebilir.

**Meta Veriler**  
 Bir hizmette, bir dış varlığın hizmetle iletişim kurmak için anlaşılması gereken hizmetin özelliklerini açıklar. Meta veriler, bir WCF istemcisi oluşturmak için [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) tarafından ve bir istemci uygulamasının hizmetle etkileşimde bulunmak için kullanabileceği bir yapılandırma ile tüketilebilir.

Hizmet tarafından kullanıma sunulan meta veriler, hizmetin veri sözleşmesini ve hizmetin yöntemlerini açıklayan WSDL belgelerini tanımlayan XML şema belgelerini içerir.

Etkinleştirildiğinde hizmetin meta verileri, hizmet ve uç noktaları incelenerek WCF tarafından otomatik olarak oluşturulur. Meta verileri bir hizmetten yayımlamak için meta veri davranışını açıkça etkinleştirmeniz gerekir.

**Security**  
 WCF 'de Gizlilik (gizlice dinleme işleminin önlenmesi için iletilerin şifrelenmesi), bütünlük (iletiyle birlikte izinsiz değişiklik algılama anlamına gelir), kimlik doğrulaması (sunucu ve istemci doğrulaması için yol) ve yetkilendirme (erişim denetimi) dahildir. Kaynaklar). Bu işlevler, HTTP üzerinden TLS (HTTPS olarak da bilinir) veya çeşitli WS-\* güvenlik belirtimlerinden birini uygulayarak mevcut güvenlik mekanizmalarından yararlanarak sağlanır.

**Taşıma güvenlik modu**  
 Gizli, bütünlük ve kimlik doğrulamanın aktarım katmanı mekanizmaları (HTTPS gibi) tarafından sağlandığını belirtir. HTTPS gibi bir taşıma kullanırken, bu mod performansından verimli olmasının ve Internet 'teki ön sürümü nedeniyle iyi anlaşılmıştır. Bu tür güvenlik, iletişim yolundaki her bir atlama için ayrı olarak uygulanan iletişim, iletişimin "ortadaki adam" saldırısından etkilenir hale getirilmesi olur.

**İleti güvenlik modu**  
 [Web Hizmetleri güvenliği: SOAP Iletisi güvenliği](https://go.microsoft.com/fwlink/?LinkId=94684)adında bir belirtim gibi bir veya daha fazla güvenlik belirtimlerinin uygulanarak güvenliğin sağlandığını belirtir. Her ileti, geçişi sırasında güvenlik sağlamak için gereken mekanizmaları içerir ve alıcıların izinsiz değişiklik algılamasına ve iletilerin şifresini çözmesine olanak tanır. Bu anlamda, güvenlik, her ileti içinde kapsüllenir ve birden çok atlama arasında uçtan uca güvenlik sağlar. Güvenlik bilgileri iletinin bir parçası haline geldiği için, ileti ile birden çok kimlik bilgisi türü eklemek de mümkündür (bunlar _talepler_olarak adlandırılır). Bu yaklaşım ayrıca, kaynağı ve hedefi arasında birden fazla taşıma da dahil olmak üzere, iletinin herhangi bir aktarımdan güvenli bir şekilde gezinmesinin avantajına sahiptir. Bu yaklaşımın dezavantajı, kullanılan şifreleme mekanizmalarının karmaşıklıkdır ve performans etkilerine neden olur.

**İleti kimlik bilgileri güvenlik modu ile taşıma**  
 Mesajların gizlilik, kimlik doğrulaması ve bütünlüğünü sağlamak için aktarım katmanının kullanımını belirtir, ancak her ileti, ileti alıcıları için gereken birden çok kimlik bilgisi (talep) içerebilir.

**WS-\***  
 WCF 'de uygulanan WS-Security, WS-ReliableMessaging, vb. gibi artan Web hizmeti (WS) belirtimleri kümesi için toplu değer.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Communication Foundation nedir?](whats-wcf.md)
- [Windows Communication Foundation Mimarisi](architecture.md)
