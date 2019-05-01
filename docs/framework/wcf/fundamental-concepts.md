---
title: Temel Windows Communication Foundation Kavramları
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], concepts
- concepts [WCF]
- fundamentals [WCF]
- Windows Communication Foundation [WCF], concepts
ms.assetid: 3e7e0afd-7913-499d-bafb-eac7caacbc7a
ms.openlocfilehash: f0802365ed07bdb57111d1b28e8d7ddfd800d41b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61929603"
---
# <a name="fundamental-windows-communication-foundation-concepts"></a>Temel Windows Communication Foundation Kavramları
Bu belge, Windows Communication Foundation (WCF) mimarisinin üst düzey bir görünümünü sağlar. Temel kavramları ve bunların birbirine nasıl uyduğunu açıklamak için tasarlanmıştır. Basit bir WCF hizmeti ve istemci sürümü oluşturmaya ilişkin öğretici için bkz: [başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md). WCF programlama bilgi edinmek için [temel WCF programlama](../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="wcf-fundamentals"></a>WCF ile ilgili temel bilgiler  
 WCF hizmet ve istemcileri arasında iletileri gönderen sistemleri oluşturmak için bir çalışma zamanı ve bir API kümesi bir işlemdir. Aynı altyapı ve API'leri, aynı bilgisayar üzerinde veya başka bir şirketteki bulunan ve Internet üzerinden erişilen bir sistemde, diğer uygulamalarla iletişim kuran uygulamaları oluşturmak için kullanılır.  
  
### <a name="messaging-and-endpoints"></a>Mesajlaşma ve uç noktaları  
 WCF programlama modeli Tekdüzen bir yolla (örneğin, bir HTTP isteği veya bir Message Queuing (MSMQ olarak da bilinir) iletisi) bir ileti temsil edilen, modellenebilir kavramı ileti tabanlı iletişim ve herhangi bir temel alır. Bu, farklı taşıma mekanizmaları arasında birleştirilmiş bir API sağlar.  
  
 Model ayırt *istemcileri*, iletişimi, uygulamaları olan ve *Hizmetleri*, istemcilerin onlarla iletişim ve yanıt için beklemek uygulamaları olduğu iletişim. Tek bir uygulama, hem istemci hem de bir hizmet görev yapabilir. Örnekler için bkz [çift yönlü Hizmetler](../../../docs/framework/wcf/feature-details/duplex-services.md) ve [eşler arası ağ](../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
 Uç noktalar arasında iletileri gönderilir. *Uç noktaları* iletileri burada gönderilen veya alınan basamak (veya her ikisi de) ve ileti değişimi için gerekli tüm bilgileri tanımlarlar. Bir veya daha fazla uygulama uç noktası (sıfır veya daha fazla altyapı uç noktaları için olduğu gibi) bir hizmet sunar ve istemci bir hizmet uç noktaları ile uyumlu bir uç nokta oluşturur.  
  
 Bir *uç nokta* standart tabanlı bir yolla iletileri gibi görünmelidir iletileri nereye gönderileceğini ve nasıl gönderileceğini açıklar. Bir hizmet, bu bilgileri istemcilerin uygun WCF istemcileri ve iletişimi oluşturmak için işleme meta veri olarak getirebilir *yığınları*.  
  
### <a name="communication-protocols"></a>İletişim protokolleri  
 Bir gerekli iletişim yığını öğesidir *Aktarım Protokolü*. İletiler, intranetler ve HTTP ve TCP gibi ortak taşımaları kullanarak Internet üzerinden gönderilebilir. Diğer taşımalar içerdiği eş ağ bir ağ üzerinde Message Queuing uygulama ve düğümleri ile iletişimi destekler. Daha fazla taşıma mekanizmaları WCF yerleşik uzantı noktaları kullanılarak eklenebilir.  
  
 Başka bir iletişim yığını öğesinde belirli bir ileti nasıl biçimlendirildiğini belirten kodlama gereklidir. WCF aşağıdaki kodlamalarda sağlar:  
  
- Metin kodlama, kodlama birlikte çalışabilir.  
  
- İleti Aktarım en iyi duruma getirme mekanizması (kodlama, için ve bir hizmetten yapılandırılmamış ikili verileri verimli bir şekilde göndermek için birlikte çalışabilen bir yolu olan MTOM).  
  
- İkili kodlama verimli aktarım için.  
  
 WCF yerleşik uzantı noktaları kullanarak (örneğin, bir sıkıştırma kodlaması) daha kodlama mekanizmaları eklenebilir.  
  
### <a name="message-patterns"></a>İleti desenleri  
 WCF istek-yanıt, tek yönlü ve çift yönlü iletişimi dahil olmak üzere birden çok Mesajlaşma düzenini destekler. Farklı taşımalar farklı Mesajlaşma düzenini destekler ve böylece destekledikleri etkileşimleri türlerini etkiler. WCF API'leri ve çalışma zamanı Ayrıca, güvenli ve güvenilir bir şekilde göndermek için yardımcı olur.  
  
## <a name="wcf-terms"></a>WCF koşulları  
 Diğer kavramlar ve terimler için WCF belgelerinde kullanılan aşağıda verilmiştir.  
  
  iletisi  
 Gövde ve üst bilgiler dahil olmak üzere birkaç bölümden oluşabilir veri müstakil birimi.  
  
 hizmet  
 Bir veya daha fazla uç noktaları, bir veya daha fazla hizmet işlemleri ifşa eden her bir uç noktasıyla sunan bir yapısı.  
  
 uç noktası  
 Bir yapı hangi iletileri gönderilen veya alınan (ya da her ikisi de). Bu nerede iletileri, ileti gönderilmesi gerektiğini nasıl, açıklar iletişim mekanizması (bağlama) belirtimi gönderilebilir tanımlayan bir konum (adres) ve bir dizi gönderilen veya alınan ileti için bir tanım (veya her ikisi) oluşur hangi ileti gönderilebilir açıklar (bir hizmet sözleşmesini) konumu.  
  
 Bir WCF Hizmeti uç noktaları koleksiyonu olarak tüm dünyada kullanıma sunulur.  
  
 Uygulama uç noktası  
 Uygulama tarafından uygulanan bir hizmet sözleşmesini uygulama ve, tarafından sunulan bir uç noktaya karşılık gelir.  
  
 Altyapı uç noktası  
 Gerekli veya bir hizmet sözleşmesine ilişkili değil hizmeti tarafından sağlanan işlevselliği kolaylaştırmak için altyapı tarafından sunulan bir uç nokta. Örneğin, bir hizmeti meta veri bilgileri sağlayan altyapı uç noktası olabilir.  
  
 adres  
 Burada mesajların alındığı konumu belirtir. Bu bir Tekdüzen Kaynak Tanımlayıcısı (URI) olarak belirtilir. URI şeması bölümü HTTP ve TCP gibi adresi ulaşmak için kullanılacak aktarım mekanizması olarak adlandırır. Hiyerarşik bir URI parçası biçimini aktarma mekanizması bağımlı olan benzersiz bir konumu içerir.  
  
 Uç nokta adresi, hizmet içinde veya uç noktalar genelinde bir adresi paylaşmak için belirli koşullar altında her uç nokta için benzersiz uç nokta adresleri oluşturmanıza olanak sağlar. Aşağıdaki örnek, varsayılan olmayan bağlantı noktası ile HTTPS protokolünü kullanarak bir adres gösterir:  
  
```  
HTTPS://cohowinery:8005/ServiceModelSamples/CalculatorService  
```  
  
 bağlama  
 Bir uç nokta dünya nasıl iletişim kurduğu tanımlar. Bileşenleri "iletişim altyapısı oluşturmak için diğerinin en üstünde bir yığın" bağlama öğeleri adı verilen bir dizi oluşturulur. En azından bir bağlama (örneğin, HTTP veya TCP) taşıma ve kodlama (metin veya ikili gibi) kullanılan tanımlar. Bağlama, iletileri ya da bir uç nokta tarafından kullanılan ileti deseni güvenliğini sağlamak için kullanılan güvenlik mekanizmaları gibi ayrıntılarını belirtin bağlama öğelerini içerebilir. Daha fazla bilgi için [Hizmetleri'ni Yapılandırma](../../../docs/framework/wcf/configuring-services.md).  
  
 bağlama öğesi  
 Bağlama, kodlama, bir altyapı düzeyinde Protokolü (örneğin, WS-ReliableMessaging) uygulaması veya herhangi bir iletişim yığını bileşeninin bir taşıma gibi belirli bir parçasını temsil eder.  
  
 davranışlar  
 Bir hizmet, bir uç nokta, belirli bir işlem veya bir istemci çeşitli çalışma zamanı yönlerini denetleyen bir bileşen. Davranışlar, kapsam göre gruplandırılır: ortak davranışlarını etkileyen tüm uç noktalar genel olarak, hizmet davranışlarını etkileyen yalnızca hizmetle ilgili özellikleri, uç nokta davranışları etkileyen yalnızca uç noktası ile ilgili özellikler ve işlem düzeyinde davranışlarını etkileyen belirli işlemler. Örneğin, bir hizmet davranışı, işleme özelliklerini doldurmak için tehdit tepki verdiğini iletilerin bir aşırı zaman bir hizmetin nasıl belirten azaltıyor. Bir uç nokta davranışı, diğer taraftan, nasıl gibi uç noktaları ve güvenlik kimlik bilgisi nerede bulacağını ilgili olan yalnızca yönü denetler.  
  
 sistem tarafından sağlanan bağlamalar  
 WCF sistem tarafından sağlanan bağlamalar içerir. Bu bağlama belirli senaryolar için iyileştirilen öğelerinin koleksiyonlarıdır. Örneğin, <xref:System.ServiceModel.WSHttpBinding> çeşitli WS - uygulama hizmetleri ile birlikte çalışabilirlik için tasarlanmış * belirtimleri. Önceden tanımlanmış bu bağlamaları, yalnızca belirli bir senaryoyu doğru şekilde uygulanabilir seçenekleri sunarak zamandan tasarruf edin. Önceden tanımlanmış bir bağlama gereksinimlerinizi karşılamıyorsa, kendi özel bağlama oluşturabilirsiniz.  
  
 kodlama ile yapılandırma  
 Denetim bir uygulamanın ya da ile yapılandırma, veya her ikisinin bir birleşimi yoluyla kodlama yapılabilir. Yapılandırma, birisi dışındaki kod yazıldıktan sonra istemci ve hizmet parametrelerini ayarlamak için geliştirici (örneğin, bir ağ yöneticisi) ve yeniden derlemenize gerek kalmadan zorlu avantajına sahiptir. Yapılandırma yalnızca, uç nokta adresleri gibi değerler oluşturmanıza olanak tanır, ancak ayrıca uç noktaları, bağlamalar ve davranışları eklemenize olanak sağlayarak daha fazla denetim sağlar. Kodlama, hizmet veya istemci bileşenlerinin tümünü üzerinde kesin denetim korumak Geliştirici sağlar ve aracılığıyla yapılandırmada gerçekleştirilen herhangi bir ayarı inceledi ve gerekirse kod tarafından geçersiz kılındı.  
  
 hizmet işlemi  
 Bir işlem için işlevselliğini uygulayan bir hizmetin kod içinde tanımlanan bir yordam. Bu işlem, istemcilere bir WCF istemcisi yöntemi olarak sunulur. Yöntemi bir değer döndürmesi bir isteğe bağlı sayıda bağımsız değişken, veya bağımsız değişken almaz ve hiç yanıt döndürür. Örneğin, basit bir "Merhaba" işlevleri bir işlem bir bildirim istemcinin bulunma ve bir dizi işlem başlamak için kullanılabilir.  
  
 Hizmet Sözleşmesi  
 Tek bir işlevsel birim ilgili işlemlere birden çok bağdaştırabilir. Sözleşme ad alanı hizmeti, karşılık gelen bir geri çağırma anlaşması ve diğer tür ayarları gibi hizmet düzeyi ayarlarını tanımlayabilirsiniz. Çoğu durumda, sözleşmenin kendi seçtiğiniz programlama dilinde bir arabirim oluşturma ve uygulama tarafından tanımlanan <xref:System.ServiceModel.ServiceContractAttribute> özniteliği için arabirim. Arabirimi uygulama tarafından gerçek hizmetinin kod sonuçları.  
  
 işlem anlaşması  
 Bir işlem anlaşması, parametreler ve dönüş türü bir işlemi tanımlar. Hizmet sözleşmesini tanımlayan bir arabirim oluştururken, bir işlem anlaşması uygulayarak geldiğiniz <xref:System.ServiceModel.OperationContractAttribute> sözleşmesinin bir parçası olan her yöntem tanımını özniteliği. İşlemleri, tek bir ileti alma ve tek bir ileti döndürerek veya bir dizi türleri alma ve bir tür döndüren olarak modellenebilir. İkinci durumda, sistem bu işlem için değiştirilecek gereken iletilerin biçimini belirler.  
  
 ileti sözleşmesi  
 Bir ileti biçimini tanımlar. Örneğin, hangi güvenlik düzeyinin hangi ileti vb. öğelere uygulanmalıdır iletinin gövdesi karşı üst bilgilerinde gitmesi gereken olup olmadığını bildirir.  
  
 hatalı sözleşme  
 Çağırana döndürülen hatalar belirtmek için bir hizmet işlemi ile ilişkili olabilir. Bir işlem ile ilişkili sıfır veya daha fazla hataları olabilir. Bu hatalar, programlama modeli içinde özel durumlar olarak modellenir SOAP hatalarıdır.  
  
 veri sözleşmesi  
 Bir hizmetin kullandığı veri türlerinin açıklamaları meta verilerinde. Bu hizmetle birlikte çalışmak diğer sağlar. Veri türleri, herhangi bir ileti bölümünde Örneğin, parametre olarak kullanılabilir veya dönüş türleri. Yalnızca basit türler hizmeti kullanıyorsanız, veri sözleşmeleri açıkça kullanmaya gerek yoktur.  
  
 barındırma  
 Bir hizmet bazı işlem içinde barındırılması gerekir. A *konak* hizmet ömrü denetleyen bir uygulamadır. Hizmetleri, şirket içinde barındırılan veya mevcut bir barındırma işlemi tarafından yönetiliyor.  
  
 kendini barındıran hizmet  
 Geliştirici oluşturan bir işlem uygulama içinde çalışan bir hizmet. Geliştirici ömrü denetimleri, hizmet özelliklerini ayarlar, (dinleme moduna ayarlanır) hizmetinin açar ve hizmet kapatır.  
  
 barındırma işlemi  
 Uygulama hizmetlerini barındırmak için tasarlanmıştır. Bunlar, Internet Information Services (IIS), Windows Etkinleştirme Hizmeti (WAS) ve Windows Hizmetleri içerir. Bu barındırılan senaryolarda, ana bilgisayar hizmeti kullanım ömrü denetler. Örneğin, IIS kullanarak hizmet ve yapılandırma dosyasını içeren bir sanal dizin ayarlayabilirsiniz. Bir ileti alındığında, IIS hizmetini başlatır ve yaşam süresi denetler.  
  
 örnek oluşturma  
 Bir hizmet bir örneklemesini modeline sahiptir. Üç örneklemesini modeli vardır: "tek tek bir CLR nesnesi tüm istemciler; Hizmetleri," " her istemci çağrısı işlemek için yeni bir CLR nesne oluşturulduğu çağrı başına,"; ve "her oturum," CLR bir dizi oluşturulur, her ayrı bir oturum için hangi nesneleri içinde. Uygulama gereksinimleri ve beklediğiniz kullanım modelini hizmetinin örneklemesini bir model seçimi bağlıdır.  
  
 İstemci uygulaması  
 Bir veya daha fazla uç noktası ile iletileri birbiriyle değiştirir program. İstemci uygulaması, WCF istemcisini yöntemlerini çağırmak ve bir WCF istemcisi örneği oluşturma ile başlar. Tek bir uygulama hem istemci hem de hizmet olabileceğine dikkat edin önemlidir.  
  
 Kanal  
 Bir bağlama öğesi, somut bir uygulama. Bağlama yapılandırmasını temsil eder ve bu yapılandırma ile ilişkili uygulama kanalıdır. Bu nedenle, her bir bağlama öğesi ile ilişkili bir kanal yoktur. Kanal bağlama somut uygulaması oluşturmak için birbirinin yığın: kanal yığını.  
  
 WCF istemcisi  
 Yöntemler olarak hizmet işlemini kullanıma sunar bir istemci uygulaması yapısı (içinde [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Visual Basic veya Visual C# gibi tercih ettiğiniz dil programlama). Herhangi bir uygulama, bir hizmeti barındıran bir uygulama da dahil olmak üzere bir WCF istemcisi barındırabilirsiniz. Bu nedenle, başka bir hizmetler WCF istemcileri içeren bir hizmet oluşturmak mümkündür.  
  
 Bir WCF istemcisi kullanarak otomatik olarak oluşturulabilir [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ve meta verilerini yayımlayan bir çalışan hizmeti işaret.  
  
 meta veriler  
 Bir hizmette bir dış varlığı hizmetiyle iletişim kurmak için anlamanız gereken hizmet özellikleri açıklanmaktadır. Meta verileri tarafından kullanılabilir [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) bir WCF istemcisi ve bir istemci uygulaması hizmetiyle etkileşim kurmak için kullanabileceğiniz eşlik eden yapılandırma oluşturulacak.  
  
 Hizmet veri sözleşme tanımlama, XML şema belgeleri ve hizmet yöntemleri açıklayan WSDL belgeleri hizmet tarafından sunulan meta veriler içerir.  
  
 Etkin olduğunda, hizmet için meta verileri otomatik olarak WCF tarafından hizmet ve kendi uç inceleyerek oluşturulur. Hizmet meta verileri yayımlamak için meta verileri davranışı açıkça etkinleştirmeniz gerekir.  
  
 güvenlik  
 WCF'de, gizliliği (şifreleme ileti gizlice önlemek için) bütünlük (anlamına gelir iletinin oynama algılanması için), (anlamına gelir sunucular ve istemciler doğrulanması için) kimlik doğrulaması ve yetkilendirme (erişimi denetlemek için içerir. Kaynaklar). Bu işlevler, ya da yararlanarak mevcut güvenlik mekanizmaları, TLS üzerinden HTTP (HTTPS olarak da bilinir) gibi veya bir veya daha fazlasını çeşitli WS - uygulama tarafından sağlanan * güvenlik belirtimleri.  
  
 Aktarım güvenlik modu  
 Gizlilik, bütünlük ve kimlik doğrulaması (Örneğin HTTPS) aktarım katmanı düzenekleri tarafından sağlanan belirtir. HTTPS gibi bir aktarım kullanırken, bu mod, yaygınlık internetteki nedeniyle, performans açısından verimlidir ve iyi anlaşılan olma avantajına sahiptir. Olumsuz yönüyse, bu tür bir güvenlik her atlama iletişimi maruz bir "ortadaki adam" saldırılarına açık hale getirme iletişim yolunun üzerinde ayrı ayrı uygulanır ' dir.  
  
 ileti güvenlik modu  
 Belirtimi adlı gibi güvenlik bir veya daha fazla güvenlik belirtimleri uygulayarak sağlandığını belirtir [Web Hizmetleri güvenlik: SOAP ileti güvenliği](https://go.microsoft.com/fwlink/?LinkId=94684). Her ileti, iletim sırasında güvenliğini sağlamak ve izinsiz algılamak ve iletilerin şifresini çözmek için alıcılar etkinleştirmek için gerekli mekanizmalarını içerir. Bu anlamda, güvenlik, birden çok atlama arasında uçtan uca güvenlik sağlama, her ileti içinde kapsüllenir. Güvenlik bilgileri iletisinin bir parçası olur çünkü da birden çok türde ileti kimlik bilgilerini dahil etmek mümkündür (bunlar olarak adlandırılır *talep*). Bu yaklaşım, ayrıca, kaynak ve hedef arasında birden çok aktarımı dahil olmak üzere herhangi bir aktarım üzerinden güvenli bir şekilde seyahat ileti etkinleştirme avantajına sahiptir. Bu yaklaşımın bir dezavantajı, performans etkilerini elde edilen işe, şifreleme mekanizmasıyla karmaşıklığını olur.  
  
 ileti kimlik bilgisi güvenlik moduyla taşıma  
 Her ileti iletinin alıcılar tarafından gereken birden çok kimlik bilgilerini (talep) içerebilir ancak gizliliği, kimlik doğrulama ve iletileri bütünlüğünü sağlamak için Aktarım katmanı belirtir.  
  
 WS-*  
 WCF'de uygulanan Web hizmeti (WS) belirtimleri, WS-güvenlik WS-ReliableMessaging ve benzeri gibi gittikçe artan için Toplu özellik.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Communication Foundation nedir?](../../../docs/framework/wcf/whats-wcf.md)
- [Windows Communication Foundation Mimarisi](../../../docs/framework/wcf/architecture.md)
