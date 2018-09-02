---
title: Bir Uç Noktası Adresi Belirtme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], addressing
ms.assetid: ac24f5ad-9558-4298-b168-c473c68e819b
ms.openlocfilehash: 718a0c086181546ba7b7fb3b31fce0732dd99382
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401773"
---
# <a name="specifying-an-endpoint-address"></a>Bir Uç Noktası Adresi Belirtme
Bir Windows Communication Foundation (WCF) hizmetiyle kurulan tüm iletişimlerde kendi uç noktalar üzerinden gerçekleşir. Her <xref:System.ServiceModel.Description.ServiceEndpoint> içeren bir <xref:System.ServiceModel.Description.ServiceEndpoint.Address%2A>, <xref:System.ServiceModel.Description.ServiceEndpoint.Binding%2A>ve <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A>. Hangi işlemleri kullanılabilir sözleşme belirtir. Bağlama hizmetiyle iletişim kurma ve adresi hizmet nerede bulacağını belirler. Her uç nokta, benzersiz bir adres olmalıdır. Uç nokta adresini tarafından temsil edilen <xref:System.ServiceModel.EndpointAddress> hizmetinin adresini temsil eden bir Tekdüzen Kaynak Tanımlayıcısı (URI) içeren sınıf bir <xref:System.ServiceModel.EndpointAddress.Identity%2A>, hizmetin güvenlik kimliğini ve isteğe bağlı bir koleksiyonunu temsil eden <xref:System.ServiceModel.EndpointAddress.Headers%2A>. İsteğe bağlı üst bilgileri tanımlamak veya uç nokta ile etkileşime geçmek için adresleme daha ayrıntılı bilgi sağlar. Örneğin, gelen iletileri işlemek nasıl, nerede uç nokta bir yanıt iletisi göndermelidir veya birden fazla örneği bulunduğunda, belirli bir kullanıcıdan gelen iletiyi işlemek için kullanılacak bir hizmetin hangi örneğinin üst bilgileri belirtebilir.  
  
## <a name="definition-of-an-endpoint-address"></a>Bir uç nokta adresi tanımı  
 Wcf'de, bir <xref:System.ServiceModel.EndpointAddress> bir uç nokta başvurusu (EPR) WS-Addressing standardında tanımlanan modeller.  
  
 Çoğu taşımalar için URI adresi dört bölümden oluşur. Örneğin, bu URI `http://www.fabrikam.com:322/mathservice.svc/secureEndpoint` aşağıdaki dört bölümden oluşur:  
  
-   Düzen: http:  
  
-   Makine: `www.fabrikam.com`  
  
-   (İsteğe bağlı) Bağlantı noktası: 322  
  
-   Yol: /mathservice.svc/secureEndpoint  
  
 Her uç nokta başvurusu ek tanımlayıcı bilgiler ekleyin bazı başvuru parametreleri gerçekleştirebilirsiniz EPR modelinin bir parçası olan. WCF'de, bu başvuru parametreleri örnekleri olarak modellenir <xref:System.ServiceModel.Channels.AddressHeader> sınıfı.  
  
 Kesin kod kullanarak veya bildirimli olarak yapılandırma yoluyla bir hizmet için uç nokta adresi belirtilebilir. Bağlamalarında ve adreslerinde dağıtılan bir hizmette hizmet geliştirilen kullandığı olanlardan genellikle farklı olduğundan uç noktaları kodda tanımlama genellikle pratik değildir. Genel olarak, kod yerine yapılandırma kullanarak hizmet uç noktaları tanımlamak daha yararlı olur. Bağlama tutulması ve adresleme bilgilerini kodunun dışında yeniden derleyin ve uygulamayı yeniden dağıtmak zorunda kalmadan değiştirmek sağlar. Uç nokta kod veya yapılandırma belirtilirse, çalışma zamanı üzerinde hizmeti tarafından uygulanan her bir sözleşme için her bir temel adres bir varsayılan uç nokta ekler.  
  
 Bir hizmet için uç nokta adresleri WCF'de belirtmenin iki yolu vardır. Hizmetle ilişkili her uç nokta için mutlak bir adres belirtebilirsiniz veya taban adresi sağlayabilir <xref:System.ServiceModel.ServiceHost> bir hizmetin ve ardından bu temel göre tanımlanan bu hizmet ile ilişkili her uç nokta için bir adres belirtin adresi. Bu yordamların her biri, yapılandırma veya kod içinde bir hizmet için uç nokta adresleri belirtmek için kullanabilirsiniz. Göreli Adres belirtmezseniz, hizmeti temel adresi kullanır. Bir hizmet için birden çok taban adresi de sahip olabilir, ancak her hizmetin her aktarım için yalnızca bir temel adres izin verilir. Her biri farklı bir bağlama ile yapılandırılan birden fazla uç nokta varsa adresleri benzersiz olmalıdır. Aynı kullanan uç noktalarda ancak farklı sözleşmeler bağlama aynı adresi kullanabilirsiniz.  
  
 IIS ile barındırırken, yönetmediğiniz <xref:System.ServiceModel.ServiceHost> kendiniz örneği. Taban adresi her zaman IIS'de barındırırken hizmetinin .svc dosyasında belirtilen adrestir. Bu nedenle, göreli bir uç nokta adresleri için IIS tarafından barındırılan hizmet uç noktası kullanmanız gerekir. Tam uç nokta adresi hizmetin dağıtılmasına hatalara neden olabilir. Daha fazla bilgi için [Internet Information Services-Hosted bir WCF Hizmeti dağıtma](../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md).  
  
## <a name="defining-endpoint-addresses-in-configuration"></a>Uç nokta adresleri yapılandırmasında tanımlama  
 Bir uç nokta yapılandırma dosyasında tanımlamak için [ \<uç noktası >](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) öğesi.  
  
 [!code-xml[S_UEHelloWorld#5](../../../samples/snippets/common/VS_Snippets_CFX/s_uehelloworld/common/serviceapp2.config#5)]  
  
 Zaman <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> (diğer bir deyişle, barındırma uygulaması hizmeti başlatmayı denediğinde) yöntemi çağrıldığında, sistem arayan bir [ \<hizmet >](../../../docs/framework/configure-apps/file-schema/wcf/service.md) "UE. belirten bir ad özniteliği olan öğe Samples.HelloService". Varsa [ \<hizmet >](../../../docs/framework/configure-apps/file-schema/wcf/service.md) öğe bulundu, Sistem belirtilen sınıf yükler ve yapılandırma dosyasında sağlanan uç nokta tanımlarını kullanarak uç noktaları oluşturur. Bu mekanizma, yükleme ve bağlama ve adresleme bilgilerini kodunuz dışında tutulması sırasında iki kod satırlarını içeren bir hizmet başlatmaya olanak tanır. Bu yaklaşımın avantajı, bu değişiklikleri yeniden derleyin veya uygulama yeniden dağıtmaya gerek kalmadan yapılabilir olmasıdır.  
  
 İsteğe bağlı üst bilgiler bildirilen bir [ \<üstbilgiler >](../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md). Bir hizmet için uç noktalar arasında iki üstbilgi ayıran bir yapılandırma dosyası belirtmek için kullanılan öğelerin bir örneği verilmiştir: "Altın" istemcilerden `http://tempuri1.org/` ve "Standart" istemcilerden `http://tempuri2.org/`. Bu hizmete çağrı yapma istemci uygun olmalıdır [ \<üstbilgiler >](../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md) kendi yapılandırma dosyası.  
  
 [!code-xml[S_UEHelloWorld#1](../../../samples/snippets/common/VS_Snippets_CFX/s_uehelloworld/common/serviceapp.config#1)]  
  
 Üst bilgileri de bir uç noktada tüm iletileri yerine bireysel iletiler (daha önce gösterildiği gibi) ayarlanabilir. Bu kullanılarak yapılır <xref:System.ServiceModel.OperationContextScope> için aşağıdaki örnekte gösterildiği gibi özel bir başlık Giden iletiye eklemek için bir istemci uygulamasında yeni bir bağlam oluşturur.  
  
 [!code-csharp[OperationContextScope#4](../../../samples/snippets/csharp/VS_Snippets_CFX/operationcontextscope/cs/client.cs#4)]
 [!code-vb[OperationContextScope#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/operationcontextscope/vb/client.vb#4)]  
  
## <a name="endpoint-address-in-metadata"></a>Meta veri uç noktası adresi  
 Bir uç nokta adresi, Web Hizmetleri Açıklama Dili (WSDL) WS-Addressing olarak temsil edilen `EndpointReference` (EPR) öğesinde karşılık gelen uç noktanın `wsdl:port` öğesi. EPR uç noktanın adresini ve bunun yanı sıra herhangi bir adres özelliklerini içerir. Unutmayın içinde EPR `wsdl:port` değiştirir `soap:Address` aşağıdaki örnekte görüldüğü gibi.  
  
  
  
## <a name="defining-endpoint-addresses-in-code"></a>Uç nokta adresleri kodda tanımlama  
 Bir uç nokta adresi koduyla oluşturulabilir <xref:System.ServiceModel.EndpointAddress> sınıfı. Uç nokta adresi Belirtilen URI, bir tam yol veya hizmetin taban adresi göreli bir yol olabilir. Aşağıdaki kod örneği nasıl oluşturulacağı <xref:System.ServiceModel.EndpointAddress> ekleyin ve sınıf <xref:System.ServiceModel.ServiceHost> hizmetini barındıran örneği.  
  
 Aşağıdaki örnek kodda tam uç nokta adresi belirtme gösterilmektedir.  
  
 [!code-csharp[S_UEHelloWorld#2](../../../samples/snippets/csharp/VS_Snippets_CFX/s_uehelloworld/cs/snippet.cs#2)]  
  
 Aşağıdaki örnek, hizmet ana bilgisayarı için temel adresini nasıl göreli bir adres ("MyService") ekleneceğini gösterir.  
  
 [!code-csharp[S_UEHelloWorld#3](../../../samples/snippets/csharp/VS_Snippets_CFX/s_uehelloworld/cs/snippet.cs#3)]  
  
> [!NOTE]
>  Özelliklerini <xref:System.ServiceModel.Description.ServiceDescription> hizmetinde uygulama için subsequent değiştirilmemelidir <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> metodunda <xref:System.ServiceModel.ServiceHostBase>. Bazı üyeler gibi <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> özelliği ve `AddServiceEndpoint` yöntemlerde <xref:System.ServiceModel.ServiceHostBase> ve <xref:System.ServiceModel.ServiceHost>, bu noktadan sonra değiştirilirse, bir özel durum. Diğerleri, bunları değiştirmek için izin verir, ancak sonuç tanımsızdır.  
>   
>  Benzer şekilde, istemci üzerinde <xref:System.ServiceModel.Description.ServiceEndpoint> değerlerin değil değiştirilmelidir çağrısından sonra <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> üzerinde <xref:System.ServiceModel.ChannelFactory>. <xref:System.ServiceModel.ChannelFactory.Credentials%2A> Özelliği, bu noktadan sonra değiştirilirse bir özel durum oluşturur. Diğer istemci açıklama değerler hatasız değiştirilebilir, ancak sonuç tanımsızdır.  
>   
>  Hizmet veya istemci için açıklama çağrılmadan önce değiştirmeniz önerilir olmadığını <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.  
  
## <a name="using-default-endpoints"></a>Varsayılan uç noktaları kullanma  
 Uç nokta kod veya yapılandırma belirtilirse çalışma zamanı hizmeti tarafından uygulanan her bir hizmet sözleşmesi için her bir temel adres bir varsayılan uç nokta ekleyerek varsayılan uç noktaları sağlar. Kod veya yapılandırma taban adresi belirtilebilir ve varsayılan uç noktaları eklenip <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> üzerinde çağrılır <xref:System.ServiceModel.ServiceHost>.  
  
 Uç noktalar açıkça verdiyse, varsayılan uç noktaları hala çağırarak eklenebilir <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> üzerinde <xref:System.ServiceModel.ServiceHost> çağırmadan önce <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Varsayılan uç noktaları, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.EndpointAddress>  
 [Kimlik Doğrulama ile Hizmet Kimliği](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Uç Nokta Oluşturmaya Genel Bakış](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Barındırma](../../../docs/framework/wcf/feature-details/hosting.md)
