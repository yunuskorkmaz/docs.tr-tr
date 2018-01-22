---
title: "Temel Windows Communication Foundation Kavramları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF [WCF], concepts
- concepts [WCF]
- fundamentals [WCF]
- Windows Communication Foundation [WCF], concepts
ms.assetid: 3e7e0afd-7913-499d-bafb-eac7caacbc7a
caps.latest.revision: "39"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 651515095a0c9f9e970fff2d77421cfa804fa701
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="fundamental-windows-communication-foundation-concepts"></a>Temel Windows Communication Foundation Kavramları
Bu belge üst düzey bir görünümünü sağlar [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] mimarisi. Temel kavramları ve onların birlikte nasıl uyduğunu açıklamak üzere tasarlanmıştır. En basit sürümü oluşturma bir öğretici için bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet ve istemci, bkz: [başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md). Bilgi edinmek için [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] programlama, bkz: [temel WCF programlama](../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="wcf-fundamentals"></a>WCF temelleri  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]bir çalışma zamanı ve bir dizi API Hizmetleri ve istemciler arasında iletileri gönder sistemleri oluşturmak üzere kullanılır. Aynı altyapı ve API'leri, diğer uygulamalarla aynı bilgisayar sisteminde veya başka bir şirket içinde bulunur ve Internet üzerinden erişilen bir sistemde, iletişim kuran uygulamaları oluşturmak için kullanılır.  
  
### <a name="messaging-and-endpoints"></a>İleti ve uç noktaları  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]programlama modeli Tekdüzen bir yolla bir ileti (örneğin, bir HTTP isteği veya bir Message Queuing (MSMQ olarak da bilinir) ileti) belirtildiği şekilde, modellenebilir kavramı ileti tabanlı iletişim ve herhangi bir şey dayanır. Bu birleşik API farklı taşıma mekanizmaları sağlar.  
  
 Model arasında ayırt *istemcileri*, iletişim, başlatmayı uygulamaları olan ve *Hizmetleri*, istemcilerin onlarla iletişim ve için yanıt beklemek uygulamaları olduğu iletişim. Tek bir uygulama hem istemci hem de bir hizmet olarak davranamaz. Örnekler için bkz: [çift yönlü Hizmetler](../../../docs/framework/wcf/feature-details/duplex-services.md) ve [eşler arası ağ](../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
 Uç noktaları arasında gönderilen iletileri. *Uç noktaları* iletileri burada gönderilen veya alınan basamak (veya her ikisi de) ve ileti değişimi için gerekli tüm bilgileri tanımlayın. Bir veya daha fazla uygulama uç (sıfır veya daha fazla altyapı uç noktaları için olduğu gibi) bir hizmet sunar ve istemci bir hizmetin uç noktaları ile uyumlu bir uç noktası oluşturur.  
  
 Bir *endpoint* standart tabanlı bir yolla iletileri burada gönderilmesi gerektiğini, nasıl gönderileceğini ve iletileri aşağıdaki gibi görünmelidir açıklanmaktadır. Bir hizmeti bu bilgileri istemcilerin uygun oluşturmak için işleyebilmesi için meta veri olarak kullanıma [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemcilerin ve iletişim *yığınları*.  
  
### <a name="communication-protocols"></a>İletişim protokolleri  
 Bir gerekli iletişim yığını öğesidir *Taşıma Protokolü*. İletiler, intranetler ve HTTP ve TCP gibi ortak taşımaları kullanarak Internet üzerinden gönderilebilir. Diğer taşımaları dahil edilen eş ağı kafes üzerinde Message Queuing uygulamaları ve düğümler iletişim destekler. Daha fazla aktarım mekanizmaları yerleşik uzantısı noktalarının kullanılarak eklenebilir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
 Başka bir iletişim yığını öğesinde belirli bir ileti nasıl biçimlendirilmiş belirtir kodlama gereklidir. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]Aşağıdaki Kodlamalar sağlar:  
  
-   Metin kodlama, birlikte çalışabilen kodlama.  
  
-   İleti iletim en iyi duruma getirme mekanizmasını (kodlama, verimli bir şekilde yapılandırılmamış ikili veriler için hizmet göndermek için birlikte çalışabilir bir yolu olan MTOM).  
  
-   İkili verimli aktarımı için kodlama.  
  
 Daha fazla kodlama mekanizmaları (örneğin, bir sıkıştırma kodlama), yerleşik uzantısı noktalarının kullanılarak eklenebilir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
### <a name="message-patterns"></a>İleti desenleri  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]İstek-yanıt, tek yönlü ve çift yönlü iletişimi de dahil olmak üzere birkaç Mesajlaşma düzenini destekler. Farklı taşımaları farklı Mesajlaşma düzenini destekler ve böylece destekledikleri etkileşimleri türlerini etkiler. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] API'leri ve çalışma zamanı de yardımcı güvenli ve güvenilir bir şekilde iletileri göndermek için.  
  
## <a name="wcf-terms"></a>WCF koşulları  
 Diğer kavramlar ve terimler kullanılan [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] belgeleri aşağıdakileri içerir.  
  
 iletisi  
 Gövde ve üstbilgileri dahil çeşitli bölümlerini oluşabilir veri, bağımsız bir birim.  
  
 hizmet  
 Bir veya daha fazla uç noktaları, bir veya daha fazla hizmet işlemleri gösterme her uç noktası ile kullanıma sunan bir yapısı.  
  
 uç noktası  
 Bir yapı hangi iletilerin gönderilen veya alınan (ya da her ikisi de). Bu burada iletiler, iletilerin nasıl gönderilmesini, açıklanan iletişim mekanizması (bağlama) belirtimi gönderilebilir tanımlayan bir konum (bir adresi) ve gönderilen veya alınan iletileri kümesi için bir tanım (veya her ikisi de) oluşur hangi ileti gönderilebilir açıklar (bir hizmet sözleşmesini) konumu.  
  
 A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet uç noktaları koleksiyonu olarak dünya gösterilir.  
  
 Uygulama uç noktası  
 Uygulama ve, tarafından kullanıma sunulan bir uç nokta uygulaması tarafından uygulanan bir hizmet sözleşmesini karşılık gelir.  
  
 Altyapı uç noktası  
 Gerekli veya bir hizmet sözleşmesini ilgili değildir hizmeti tarafından sağlanan işlevselliği kolaylaştırmak için altyapı tarafından sunulan bir uç nokta. Örneğin, bir hizmeti meta veri bilgileri sağlayan bir altyapı uç noktası olabilir.  
  
 adres  
 Burada iletileri alınan konumunu belirtir. Bir Tekdüzen Kaynak Tanımlayıcısı (URI) olarak belirtilir. URI şeması bölümü HTTP ve TCP gibi adresine erişmek için kullanılacak aktarım mekanizması adları. URI hiyerarşik parçası biçimini bir aktarım mekanizması bağımlı benzersiz bir konuma içerir.  
  
 Uç nokta adresi benzersiz uç nokta adresleri her bitiş noktasıyla ilgili bir hizmetinde veya bir adresi uç noktalar arasında paylaşmak için belirli koşullar altında oluşturmanıza olanak sağlar. Aşağıdaki örnek, bir varsayılan olmayan bağlantı noktası ile HTTPS protokolünü kullanarak bir adres gösterir:  
  
```  
HTTPS://cohowinery:8005/ServiceModelSamples/CalculatorService  
```  
  
 bağlama  
 Bir uç nokta dünyasına nasıl iletişim kuracağını tanımlar. "Bir iletişim altyapısı oluşturmak için diğer üstünde yığın" bağlama öğeleri adlı bileşenler kümesinin oluşturulur. En azından bir bağlama (örneğin, HTTP veya TCP) taşıma ve kodlama (metin veya ikili gibi) kullanılan tanımlar. Bir bağlama iletileri ya da bir uç nokta tarafından kullanılan ileti deseni güvenliğini sağlamak için kullanılan güvenlik mekanizmaları gibi ayrıntılarını belirtin bağlama öğeleri içerebilir. Daha fazla bilgi için bkz: [Hizmetleri'ni Yapılandırma](../../../docs/framework/wcf/configuring-services.md).  
  
 bağlama öğesi  
 Bir kodlama, bir altyapı düzeyi Protokolü (örneğin, WS-ReliableMessaging) uygulaması ya da herhangi bir bileşeni iletişim yığınının bir taşıma gibi bağlama belirli bir parçasını temsil eder.  
  
 davranışlar  
 Bir hizmeti, bir uç nokta, belirli bir işlem veya bir istemci çeşitli çalışma zamanı yönlerini denetleyen bir bileşeni. Davranışları kapsam göre gruplandırılır: ortak davranışları etkileyen tüm uç noktaları genel olarak, hizmet davranışları etkiler yalnızca hizmeti ile ilgili konuları, uç nokta davranışları etkileyen yalnızca uç noktası ile ilgili özellikler ve işlem düzeyi davranışları etkileyen belirli işlemler. Örneğin, bir hizmet davranışı işleme yeteneklerini doldurmaya iletilerinin bir aşırı zaman tepki verdiğini tehdit bir hizmetin nasıl belirten azaltmadır. Bir uç nokta davranışını diğer taraftan, nasıl gibi uç noktaları ve bir güvenlik kimlik bilgisi nerede bulacağını ilgili yalnızca yönünü denetler.  
  
 sistem tarafından sağlanan bağlamalar  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]Sistem tarafından sağlanan bağlamalar sayısını içerir. Bu bağlama belirli senaryolar için iyileştirilen öğelerinin koleksiyonlarıdır. Örneğin, <xref:System.ServiceModel.WSHttpBinding> çeşitli WS - uygulama hizmetleri ile birlikte çalışabilirlik için tasarlanmış * belirtimleri. Bu önceden tanımlanmış bağlamaları, yalnızca belirli bir senaryoyu doğru uygulanabilir seçenekleri sunarak zaman kazandırır. Önceden tanımlanmış bir bağlama gereksinimlerinizi karşılamıyorsa, kendi özel bağlama oluşturabilirsiniz.  
  
 kodlama ve yapılandırma  
 Denetim bir uygulama ya da aracılığıyla, yapılandırma, veya ikisinin birleşimi yoluyla kodlama yapılabilir. Yapılandırma birisi kodu yazıldıktan sonra istemci ve hizmet parametrelerini ayarlamak için (örneğin, bir ağ yöneticisi) Geliştirici dışındaki ve yeniden derleyin gerek kalmadan izin vererek avantajına sahiptir. Yapılandırma yalnızca, uç nokta adresleri gibi değerlerini ayarlamak sağlar, ancak aynı zamanda uç noktaları, bağlamaları ve davranışları eklemenize olanak sağlayarak daha fazla denetim sağlar. Kodlama, hizmet veya istemci bileşenlerinin tümünü üzerinde tam denetimi korumak Geliştirici sağlar ve yapılandırma aracılığıyla yapılan herhangi bir ayarı Denetlenmekte ve gerekirse kod tarafından geçersiz kılındı.  
  
 hizmet işlemi  
 Bir işlem işlevselliğini hayata geçiren bir hizmetin kodda tanımlanan bir yordamdır. Bu işlem, üzerinde yöntemleri olarak istemcilerine sunulur bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci. Yöntemi bir değer döndürmesi ve isteğe bağlı bir bağımsız değişken sayısı ayırın veya bağımsız değişkenler almayan ve hiçbir yanıt döndürür. Örneğin, bir basit "Hello"ifadesini işlev bir işlem bir bildirim bir istemcinin varlık ve işlemleri, bir dizi başlamak için kullanılabilir.  
  
 service contract  
 Tek bir işlev birime birden fazla ilgili işlemleri birbirine bağlar. Sözleşme ad alanı hizmeti, karşılık gelen bir geri çağırma sözleşme ve diğer tür ayarları gibi hizmet düzeyi ayarlarını tanımlayabilirsiniz. Çoğu durumda, sözleşmenin tercih ettiğiniz programlama dilinde bir arabirim oluşturma ve uygulama tarafından tanımlanan <xref:System.ServiceModel.ServiceContractAttribute> özniteliği için arabirim. Arabirimi uygulama tarafından gerçek hizmet kod sonuçları.  
  
 işlem Sözleşmesi  
 Bir işlem sözleşmesi parametreler ve dönüş türü bir işlemi tanımlar. Hizmet sözleşmesini tanımlayan bir arabirim oluştururken, bir işlem sözleşmesi uygulayarak belirtmek <xref:System.ServiceModel.OperationContractAttribute> özniteliği sözleşmesinin bir parçası olan her yöntem tanımını ekleyin. İşlemler, tek bir ileti alma ve tek bir ileti döndürerek veya türleri kümesi alma ve bir tür döndüren olarak modellenebilir. İkinci durumda, sistem bu işlemi için değiştirilebilmesi için gereken iletilerin biçimini belirler.  
  
 ileti sözleşmesi  
 Bir ileti biçimi açıklar. Örneğin, ileti öğeleri gövdesi karşı üstbilgilerindeki gitmesi gereken olup olmadığını hangi güvenlik düzeyini ileti ve benzeri hangi öğelerine uygulanan bildirir.  
  
 hatalı sözleşme  
 Çağırana döndürülen hatalar belirtmek için bir hizmet işlemi ile ilişkili olabilir. Bir işlem, kendisiyle ilişkilendirilmiş sıfır veya daha fazla hataları olabilir. Bu hatalar programlama modeli, özel durumlar olarak Modellenen SOAP hatalarıdır.  
  
 veri sözleşmesi  
 Meta veri açıklamasında veri türlerinin bir hizmet kullanır. Bu hizmet ile birlikte çalışmak başkalarına sağlar. Veri türleri dönüş türleri veya herhangi bir kısmını bir ileti Örneğin, parametre olarak kullanılabilir. Yalnızca basit türler hizmeti kullanıyorsanız, veri sözleşmeleri açıkça kullanmaya gerek yoktur.  
  
 barındırma  
 Bir hizmet bazı işleminde barındırılması gerekir. A *konak* hizmet ömrü denetleyen bir uygulamadır. Hizmetleri otomatik olarak barındırılan veya varolan bir barındırma işlemi tarafından yönetiliyor.  
  
 kendini barındıran hizmet  
 Geliştirici oluşturulan işlem uygulama içinde çalışan bir hizmet. Geliştirici yaşam denetimleri, hizmet özelliklerini ayarlar, (dinleme moduna ayarlar) hizmetini açar ve hizmet kapatır.  
  
 barındırma işlemi  
 Ana Bilgisayar Hizmetleri için tasarlanmış bir uygulama. Bu, Internet Information Services (IIS), Windows Etkinleştirme Hizmetleri (WAS) ve Windows Hizmetleri içerir. Barındırılan bu senaryolarda, ana bilgisayar hizmeti ömrü denetler. Örneğin, IIS kullanarak hizmet ve yapılandırma dosyasını içeren bir sanal dizin ayarlayabilirsiniz. Bir ileti alındığında, IIS hizmetini başlatır ve yaşam süresi denetler.  
  
 örnek oluşturma  
 Bir hizmet bir örneklemesini modeli vardır. Üç örneklemesini modeli vardır: "tek tek bir CLR nesnesi tüm istemciler için; Hizmetleri," " her istemci çağrısını işlemek için yeni bir CLR nesnesi oluşturulduğu çağrı,"; ve "her oturum," CLR kümesi oluşturulur, ayrı her oturum için bir tane nesneleri içinde. Uygulama gereksinimleri ve beklediğiniz kullanım modelini hizmetinin örneklemesini model seçimi bağlıdır.  
  
 istemci uygulaması  
 Bir veya daha fazla uç noktaları iletileri alış verişleri program. İstemci uygulaması örneğini oluşturarak başlar bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci ve yöntemleri çağırma [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci. Tek bir uygulama hem istemci hem de bir hizmet olabilir dikkate almak önemlidir.  
  
 Kanal  
 Bir bağlama öğesi somut bir uygulamasıdır. Bağlama yapılandırmasını temsil eder ve kanal bu yapılandırmasıyla ilişkili uygulamasıdır. Bu nedenle her bağlama öğesi ile ilişkili bir kanalı yok. Kanal bağlama somut uygulaması oluşturmak için birbirinin yığın: kanal yığını.  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]İstemci  
 Yöntemleri olarak hizmet işlemini kullanıma sunar bir istemci uygulaması yapısı (içinde [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] programlama dili Visual Basic veya Visual C# gibi tercih ettiğiniz). Herhangi bir uygulama barındırabilen bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] bir hizmeti barındıran bir uygulama da dahil olmak üzere istemci. Bu nedenle, içeren bir hizmet oluşturmak mümkün [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] diğer hizmetlerin istemciler.  
  
 A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci otomatik olarak oluşturulabilir kullanarak [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ve meta verilerini yayımlayan bir çalışan hizmetine işaret.  
  
 meta veriler  
 Bir hizmeti, bir dış varlık hizmetiyle iletişim kurmak için anlamanız gereken hizmet özelliklerini açıklar. Meta veriler tüketilen tarafından [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) oluşturmak için bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci ve istemci uygulamanın hizmetiyle etkileşim kurmak için kullanabileceği eşlik eden yapılandırma.  
  
 Hizmet tarafından kullanıma sunulan meta veri hizmetinin veri sözleşmesi tanımlayın, XML Şeması belgeleri ve hizmet yöntemleri açıklayan WSDL belgelerini içerir.  
  
 Etkinleştirildiğinde, hizmet için meta verileri otomatik olarak tarafından oluşturulan [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmeti ve kendi uç noktaları inceleme tarafından. Bir hizmeti meta verilerini yayımlamak için meta veri davranışı açıkça etkinleştirmelisiniz.  
  
 güvenlik  
 İçinde [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], gizliliği (şifreleme gizlice Dinlemenin önlenmesi iletilerinin), bütünlük (anlamına gelir iletiyle oynama algılanamadı için), kimlik doğrulama (anlamına gelir sunucularını ve istemcilerini doğrulanması için) ve yetkilendirme (içerir Denetim kaynaklarına erişimi). Bu işlevler ya da yararlanmayı mevcut güvenlik mekanizmaları, HTTP (HTTPS olarak da bilinir) üzerinden TLS gibi veya bir veya daha fazlasını çeşitli WS - uygulama tarafından sağlanan * güvenlik özellikleri.  
  
 Aktarım güvenlik modu  
 Gizlilik, bütünlük ve kimlik doğrulaması için Aktarım katmanı mekanizmaları (Örneğin HTTPS) tarafından sağlanan belirtir. HTTPS gibi bir aktarım kullanırken bu modda kendi yaygınlığını Internet'te nedeniyle verimli, performans ve iyi anlaşılan olma avantajına sahiptir. Dezavantajı, bu tür bir güvenlik iletişim "ortadaki adam" saldırıya açıktır yapmadan iletişim yolundaki her atlama üzerinde ayrı olarak uygulandığını ' dir.  
  
 ileti güvenlik modu  
 Belirtimi adlı gibi güvenlik bir veya daha fazla güvenlik özellikleri, uygulama tarafından sağlandığını belirtir [Web Hizmetleri güvenlik: SOAP iletisi Güvenlik](http://go.microsoft.com/fwlink/?LinkId=94684). Her ileti, aktarım sırasında güvenliği sağlamak için ve izinsiz algılamak ve iletilerin şifresini çözmek için alıcıları etkinleştirmek için gerekli mekanizmalar içerir. Bu anlamda güvenlik birden çok atlama arasında uçtan uca güvenlik sağlayan her ileti içinde kapsüllenir. Güvenlik bilgileri iletinin bir parçası haline gelir olduğundan, ayrıca kimlik bilgileri iletisi ile birden çok türde içerecek şekilde mümkündür (bunlar denir *talep*). Bu yaklaşım, ayrıca kaynak ve hedef arasındaki birden çok aktarımı dahil olmak üzere herhangi bir aktarım üzerinden güvenli bir şekilde hareket etmek ileti etkinleştirme avantajına sahiptir. Bu yaklaşımın bir dezavantajı performans etkileri kaynaklanan işe, şifreleme mekanizmaları karmaşıklığını ' dir.  
  
 ileti kimlik bilgileri güvenlik moduyla taşıma  
 Her ileti bir ileti alıcı tarafından birden çok kimlik bilgileri gerekli (talep) içerebilir ancak gizlilik, kimlik doğrulama ve iletileri bütünlüğünü sağlamak için Aktarım katmanı kullanımını belirtir.  
  
 WS-*  
 WS güvenliği, WS-ReliableMessaging ve içinde uygulanan vb. gibi Web hizmeti (WS) belirtim büyüyen kümesi için kestirme [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Communication Foundation nedir?](../../../docs/framework/wcf/whats-wcf.md)  
 [Windows Communication Foundation Mimarisi](../../../docs/framework/wcf/architecture.md)  
 [Güvenlik mimarisi](http://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
