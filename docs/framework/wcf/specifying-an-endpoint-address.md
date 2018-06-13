---
title: Bir Uç Noktası Adresi Belirtme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], addressing
ms.assetid: ac24f5ad-9558-4298-b168-c473c68e819b
ms.openlocfilehash: f7e2253c527cbb2b6f21b222b1e9691c2ecff01f
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809124"
---
# <a name="specifying-an-endpoint-address"></a>Bir Uç Noktası Adresi Belirtme
Windows Communication Foundation (WCF) hizmetiyle kurulan tüm iletişimlerde kendi bitiş noktalarından oluşur. Her <xref:System.ServiceModel.Description.ServiceEndpoint> içeren bir <xref:System.ServiceModel.Description.ServiceEndpoint.Address%2A>, <xref:System.ServiceModel.Description.ServiceEndpoint.Binding%2A>ve bir <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A>. Hangi işlemleri kullanılabilir sözleşme belirtir. Bağlama hizmetiyle iletişim kurma ve hizmet nerede bulacağını adresini belirtir. Her uç noktası benzersiz bir adres olmalıdır. Uç nokta adresi tarafından temsil edilen <xref:System.ServiceModel.EndpointAddress> hizmetinin adresini gösteren bir Tekdüzen Kaynak Tanımlayıcısı (URI) içeren sınıf bir <xref:System.ServiceModel.EndpointAddress.Identity%2A>, hizmet güvenlik kimliğini ve isteğe bağlı bir topluluğu gösterir <xref:System.ServiceModel.EndpointAddress.Headers%2A>. İsteğe bağlı üstbilgi tanımlamak veya uç noktasıyla etkileşim için adresleme daha ayrıntılı bilgi sağlar. Örneğin, üstbilgileri gelen iletiyi işlemeye nasıl, burada uç nokta bir yanıt iletisi göndermesi gerekir veya birden çok örneği kullanılamadığında belirli bir kullanıcıdan gelen iletiyi işlemek için kullanılacak bir hizmetin hangi örneğinin gösterebilir.  
  
## <a name="definition-of-an-endpoint-address"></a>Bir uç nokta adresi tanımı  
 Wcf'de, bir <xref:System.ServiceModel.EndpointAddress> bir uç nokta başvurusu (EPR) WS adresleme standardında tanımlanan modeller.  
  
 Çoğu taşıma için URI adresi dört bölümden oluşur. Örneğin, bu URI "http://www.fabrikam.com:322/mathservice.svc/secureEndpoint" aşağıdaki dört bölümden oluşur:  
  
-   Düzen: http:  
  
-   Makine: www.fabrikam.com  
  
-   (İsteğe bağlı) Bağlantı noktası: 322  
  
-   Yol: /mathservice.svc/secureEndpoint  
  
 Her bitiş noktası başvurusu fazladan tanımlama bilgilerini eklemek bazı başvuru parametreleri taşıyabilir EPR modelin parçası olur. Örnekleri olarak Modellenen WCF, bu başvuru parametreleri <xref:System.ServiceModel.Channels.AddressHeader> sınıfı.  
  
 Kod kullanarak imperatively ya da bildirimli olarak yapılandırma yoluyla bir hizmet uç noktası adresi belirtilebilir. Bağlamalar ve dağıtılmış bir hizmet için adresleri hizmet geliştirildiği sırada kullanılan olanlardan genellikle farklı olduğu için uç noktalar kodda tanımlama genellikle pratik değildir. Genellikle, kod yerine Yapılandırması kullanılarak hizmet uç noktaları tanımlamak daha pratik olur. Bağlama tutulması ve kod dışında bilgisine derlenir ve uygulamayı yeniden dağıtmak zorunda kalmadan değiştirmek için bunları sağlar. Uç nokta yok kod veya yapılandırma belirttiyseniz, çalışma zamanı hizmeti tarafından uygulanan her sözleşme için temel her adresinde bir varsayılan uç nokta ekler.  
  
 WCF'de bir hizmeti için uç nokta adresleri belirtmek için iki yolu vardır. Taban adresi sağlayabilir veya hizmetle ilişkilendirilmiş her uç noktası için mutlak bir adres belirtebilirsiniz <xref:System.ServiceModel.ServiceHost> bir hizmetin ve ardından bu temel göre tanımlanan bu hizmeti ile ilişkili her uç nokta için bir adres belirtin adresi. Bu yordamların her biri, yapılandırma ve kodun içerisinde bir hizmeti için uç nokta adresleri belirtmek için kullanabilirsiniz. Göreli bir Adres belirtmezseniz, hizmetin taban adresi kullanır. Ayrıca bir hizmet için birden çok taban adresi olabilir ancak her hizmetin her aktarım için yalnızca bir taban adresi izin verilir. Her biri farklı bir bağlama ile yapılandırılan birden çok uç nokta varsa adresleri benzersiz olmalıdır. Aynı kullanan uç ancak farklı sözleşmeleri bağlama aynı adres kullanabilirsiniz.  
  
 IIS ile barındırdığında değil yönettiğiniz <xref:System.ServiceModel.ServiceHost> kendiniz örneği. Temel adres, her zaman IIS'de barındırdığında hizmeti .svc dosyasında belirtilen adrestir. Bu nedenle, göreli uç nokta adresleri IIS tarafından barındırılan hizmet uç noktaları için kullanmanız gerekir. Tam uç noktası adresi biri hizmet dağıtımı hatalara yol açabilir. Daha fazla bilgi için bkz: [Internet Information Services-Hosted WCF Hizmeti dağıtma](../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md).  
  
## <a name="defining-endpoint-addresses-in-configuration"></a>Uç nokta adresleri yapılandırmasında tanımlama  
 Bir yapılandırma dosyasında bir uç nokta tanımlamak için [ \<uç noktası >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) öğesi.  
  
 [!code-xml[S_UEHelloWorld#5](../../../samples/snippets/common/VS_Snippets_CFX/s_uehelloworld/common/serviceapp2.config#5)]  
  
 Zaman <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> yöntemi (diğer bir deyişle, barındırma uygulama hizmetini başlatmak çalıştığında) çağrılır, sistem arar bir [ \<hizmet >](../../../docs/framework/configure-apps/file-schema/wcf/service.md) "UE. belirten bir ad özniteliği olan öğe Samples.HelloService". Varsa [ \<hizmet >](../../../docs/framework/configure-apps/file-schema/wcf/service.md) öğe bulundu, Sistem belirtilen sınıf yükler ve uç noktaları yapılandırma dosyasında sağlanan uç nokta tanımları kullanarak oluşturur. Bu düzenek, yüklemek ve bağlama ve adresleme bilgilerini kodunuzu dışında tutulması sırasında iki kod satırı ile bir hizmeti başlatmak sağlar. Bu yaklaşımın avantajı, bu değişiklikleri yeniden derleyin veya uygulamayı yeniden dağıtmak zorunda kalmadan yapılabilir ' dir.  
  
 İsteğe bağlı üstbilgi içinde bildirilen bir [ \<üstbilgiler >](../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md). Bir hizmeti için uç noktalar arasında iki üstbilgi ayıran bir yapılandırma dosyası belirtmek için kullanılan öğelerinin bir örneği şudur: "Altın" istemcilerden http://tempuri1.org/ ve "Standart" istemcilerden http://tempuri2.org/. Bu hizmet çağırma istemci uygun olmalıdır [ \<üstbilgiler >](../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md) yapılandırma dosyası.  
  
 [!code-xml[S_UEHelloWorld#1](../../../samples/snippets/common/VS_Snippets_CFX/s_uehelloworld/common/serviceapp.config#1)]  
  
 Üst bilgileri de bir uç noktada tüm iletileri yerine tek bir ileti üzerinde (daha önce gösterildiği gibi) ayarlanabilir. Bu kullanılarak yapılır <xref:System.ServiceModel.OperationContextScope> aşağıdaki örnekte gösterildiği gibi bir özel üst bilgi Giden iletiye eklemek için bir istemci uygulamasında yeni bir bağlam oluşturmak için.  
  
 [!code-csharp[OperationContextScope#4](../../../samples/snippets/csharp/VS_Snippets_CFX/operationcontextscope/cs/client.cs#4)]
 [!code-vb[OperationContextScope#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/operationcontextscope/vb/client.vb#4)]  
  
## <a name="endpoint-address-in-metadata"></a>Meta veri uç noktası adresi  
 Bir uç noktası adresi, Web Hizmetleri Açıklama Dili (WSDL) WS-adresleme olarak temsil edilir `EndpointReference` (EPR) öğesi içinde karşılık gelen uç noktanın `wsdl:port` öğesi. EPR, uç noktanın adresi herhangi bir adres özelliği içerir. Unutmayın içinde EPR `wsdl:port` değiştirir `soap:Address` aşağıdaki örnekte görüldüğü gibi.  
  
  
  
## <a name="defining-endpoint-addresses-in-code"></a>Uç nokta adresleri kodda tanımlama  
 Bir uç nokta adresi koduyla oluşturulabilir <xref:System.ServiceModel.EndpointAddress> sınıfı. Uç nokta adres için belirtilen URI, bir tam yol veya hizmetin taban adresi göreli bir yol olabilir. Aşağıdaki kod örneği oluşturmak nasıl gösterir <xref:System.ServiceModel.EndpointAddress> sınıfı ve ekleyin <xref:System.ServiceModel.ServiceHost> barındırma hizmeti örneği.  
  
 Aşağıdaki örnek kodda tam uç noktası adresi belirtme gösterilmiştir.  
  
 [!code-csharp[S_UEHelloWorld#2](../../../samples/snippets/csharp/VS_Snippets_CFX/s_uehelloworld/cs/snippet.cs#2)]  
  
 Aşağıdaki örnekte bir göreli adresi ("MyService") eklemek hizmet ana bilgisayarını temel adresine gösterilmiştir.  
  
 [!code-csharp[S_UEHelloWorld#3](../../../samples/snippets/csharp/VS_Snippets_CFX/s_uehelloworld/cs/snippet.cs#3)]  
  
> [!NOTE]
>  Özelliklerini <xref:System.ServiceModel.Description.ServiceDescription> hizmetinde uygulama subsequent için değiştirilmemelidir <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> yöntemi <xref:System.ServiceModel.ServiceHostBase>. Bazı üyeler gibi <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> özelliği ve `AddServiceEndpoint` yöntemlere <xref:System.ServiceModel.ServiceHostBase> ve <xref:System.ServiceModel.ServiceHost>, bu noktadan sonra değiştirilirse bir özel durum. Başkalarının, bunları değiştirmek için izin verme, ancak sonuç tanımlanmadı.  
>   
>  Benzer şekilde, istemci üzerinde <xref:System.ServiceModel.Description.ServiceEndpoint> değerleri değil değiştirilmelidir çağrısından sonra <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> üzerinde <xref:System.ServiceModel.ChannelFactory>. <xref:System.ServiceModel.ChannelFactory.Credentials%2A> Özelliği, bu noktadan sonra değiştirilirse bir özel durum oluşturur. Bir istemci açıklama değerleri hatasız değiştirilebilir, ancak sonuç tanımlanmadı.  
>   
>  Hizmet veya istemci için açıklama çağrılmadan önce değiştirmeniz önerilir olup olmadığını <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.  
  
## <a name="using-default-endpoints"></a>Varsayılan uç noktaları kullanma  
 Uç nokta yok kod veya yapılandırma belirtilmezse, çalışma zamanı her taban adresi hizmeti tarafından uygulanan her hizmet sözleşmesi için bir varsayılan uç nokta ekleyerek varsayılan uç noktaları sağlar. Kod veya yapılandırma taban adresi belirtilebilir ve varsayılan uç noktaları eklenip <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> üzerinde adlı <xref:System.ServiceModel.ServiceHost>.  
  
 Uç noktalar açıkça verdiyse, varsayılan uç noktalar hala çağırarak eklenebilir <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> üzerinde <xref:System.ServiceModel.ServiceHost> çağırmadan önce <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Varsayılan uç noktalar, bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.EndpointAddress>  
 [Kimlik Doğrulama ile Hizmet Kimliği](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Uç Nokta Oluşturmaya Genel Bakış](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Barındırma](../../../docs/framework/wcf/feature-details/hosting.md)
