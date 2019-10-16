---
title: Bir Uç Noktası Adresi Belirtme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], addressing
ms.assetid: ac24f5ad-9558-4298-b168-c473c68e819b
ms.openlocfilehash: 47a7bb42ea2441ffef2fd27f26a20beceb871173
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321127"
---
# <a name="specifying-an-endpoint-address"></a>Bir Uç Noktası Adresi Belirtme

Bir Windows Communication Foundation (WCF) hizmeti ile tüm iletişim uç noktaları aracılığıyla oluşur. Her <xref:System.ServiceModel.Description.ServiceEndpoint> <xref:System.ServiceModel.Description.ServiceEndpoint.Address%2A>, <xref:System.ServiceModel.Description.ServiceEndpoint.Binding%2A> ve <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> içerir. Sözleşme hangi işlemlerin kullanılabilir olduğunu belirtir. Bağlama, hizmetle nasıl iletişim kurabileceğinizi belirtir ve adres hizmetin nerede bulunacağını belirtir. Her uç noktanın benzersiz bir adresi olmalıdır. Uç nokta adresi, hizmetin adresini temsil eden bir Tekdüzen Kaynak tanımlayıcısı (URI) ve hizmetin güvenlik kimliğini temsil eden bir <xref:System.ServiceModel.EndpointAddress.Identity%2A> ve isteğe bağlı <xref:System.ServiceModel.EndpointAddress.Headers%2A> koleksiyonu içeren <xref:System.ServiceModel.EndpointAddress> sınıfı tarafından temsil edilir. İsteğe bağlı üstbilgiler, uç noktayı tanımlamak veya ile etkileşimde bulunmak için daha ayrıntılı adresleme bilgileri sağlar. Örneğin, üst bilgilerin bir yanıt iletisi gönderebilmesi veya birden çok örnek kullanılabilir olduğunda belirli bir kullanıcıdan gelen bir iletiyi işlemek için kullanılacak bir hizmet örneği olan gelen bir iletiyi nasıl işleyeceğini belirtebilir.

## <a name="definition-of-an-endpoint-address"></a>Bir uç nokta adresinin tanımı

WCF 'de <xref:System.ServiceModel.EndpointAddress>, WS-Addressing standardında tanımlanan bir uç nokta başvurusunu (EPR) modeller.

Çoğu taşımanın adres URI 'sinin dört bölümü vardır. Örneğin, bu URI `http://www.fabrikam.com:322/mathservice.svc/secureEndpoint` aşağıdaki dört parçaya sahiptir:

- Düzen: http:

- Makine: `www.fabrikam.com`

- Seçim Bağlantı noktası: 322

- Yol:/mathservice.svc/secureEndpoint

EPR modelinin bir parçası olan her bir uç nokta başvurusunun, ek tanımlayıcı bilgi ekleyen bazı başvuru parametrelerini taşıyacağından emin olur. WCF 'de, bu başvuru parametreleri <xref:System.ServiceModel.Channels.AddressHeader> sınıfının örnekleri olarak modellenir.

Bir hizmet için uç nokta adresi, kod kullanılarak veya bildirimli olarak yapılandırma yoluyla imperatively belirtilebilir. Dağıtılmış bir hizmetin bağlamaları ve adresleri genellikle hizmet geliştirildiğinde kullanılanlardan farklı olduğundan, koddaki uç noktaların tanımlanması genellikle pratik değildir. Genellikle, kod yerine yapılandırma kullanarak hizmet uç noktaları tanımlamak daha pratik bir yapılandırmadır. Bağlama ve adresleme bilgilerinin koddan tutulması, uygulamayı yeniden derlemek ve yeniden dağıtmak zorunda kalmadan değiştirilmesine izin verir. Kodda veya yapılandırmada hiçbir uç nokta belirtilmemişse, çalışma zamanı, hizmet tarafından uygulanan her bir sözleşmenin her bir temel adresine bir varsayılan uç nokta ekler.

WCF 'de bir hizmet için uç nokta adreslerini belirtmenin iki yolu vardır. Hizmetle ilişkili her bir uç nokta için mutlak bir adres belirtebilir veya bir hizmetin <xref:System.ServiceModel.ServiceHost> ' ı için bir temel adres sağlayabilir ve bu hizmetle ilişkili olan her bitiş noktası için bu temel adrese göre tanımlanan bir adres belirtebilirsiniz. Yapılandırma veya koddaki bir hizmetin uç nokta adreslerini belirtmek için bu yordamların her birini kullanabilirsiniz. Göreli bir adres belirtmezseniz, hizmet temel adresi kullanır. Ayrıca, bir hizmet için birden fazla temel adrese sahip olabilirsiniz, ancak her bir hizmet için her bir aktarım için yalnızca bir temel adrese izin verilir. Her biri farklı bir bağlama ile yapılandırılan birden fazla uç noktalarınız varsa, bunların adresleri benzersiz olmalıdır. Aynı bağlamayı kullanan uç noktalar, ancak farklı sözleşmeler aynı adresi kullanabilir.

IIS ile barındırırken, <xref:System.ServiceModel.ServiceHost> örneğini kendiniz yönetmeyin. Temel adres, IIS 'de barındırırken hizmetin. svc dosyasında her zaman belirtilen adrestir. Bu nedenle, IIS tarafından barındırılan hizmet uç noktaları için göreli uç nokta adreslerini kullanmanız gerekir. Tam bir uç nokta adresi sağlamak, hizmetin dağıtımındaki hatalara neden olabilir. Daha fazla bilgi için bkz. [Internet Information Services barındırılan BIR WCF hizmetini dağıtma](./feature-details/deploying-an-internet-information-services-hosted-wcf-service.md).

## <a name="defining-endpoint-addresses-in-configuration"></a>Yapılandırmada uç nokta adreslerini tanımlama

Bir yapılandırma dosyasında bir uç nokta tanımlamak için [\<endpoint >](../configure-apps/file-schema/wcf/endpoint-element.md) öğesini kullanın.

[!code-xml[S_UEHelloWorld#5](../../../samples/snippets/common/VS_Snippets_CFX/s_uehelloworld/common/serviceapp2.config#5)]

@No__t-0 yöntemi çağrıldığında (yani, barındırma uygulaması hizmeti başlatmaya çalıştığında), sistem "UE" belirten bir ad özniteliği olan bir [\<service >](../configure-apps/file-schema/wcf/service.md) öğesi arar. Samples. HelloService ". [@No__t-1Service >](../configure-apps/file-schema/wcf/service.md) öğesi bulunursa, sistem belirtilen sınıfı yükler ve yapılandırma dosyasında sağlanmış olan uç nokta tanımlarını kullanarak uç noktalar oluşturur. Bu mekanizma, koddan bağlama ve adresleme bilgilerini korurken iki satırlık kodla bir hizmeti yükleyip başlatabilmeniz için izin verir. Bu yaklaşımın avantajı, bu değişikliklerin uygulamayı yeniden derlemek veya yeniden dağıtmak zorunda kalmadan yapılabilmesine neden olur.

İsteğe bağlı üstbilgiler [\<headers >](../configure-apps/file-schema/wcf/headers-element.md)olarak belirtilir. Aşağıda iki üst bilgi arasında ayrım yapan bir yapılandırma dosyasındaki bir hizmetin uç noktalarını belirtmek için kullanılan öğelerin bir örneği verilmiştir: "altın" istemcileri `http://tempuri1.org/` ve "standart" istemcilerinden `http://tempuri2.org/`. Bu hizmeti çağıran istemci, yapılandırma dosyasında uygun [\<Üst bilgi >](../configure-apps/file-schema/wcf/headers-element.md) sahip olmalıdır.

[!code-xml[S_UEHelloWorld#1](../../../samples/snippets/common/VS_Snippets_CFX/s_uehelloworld/common/serviceapp.config#1)]

Üst bilgiler, bir uç noktasındaki tüm iletiler yerine tek tek iletilerde de ayarlanabilir (daha önce gösterildiği gibi). Bu işlem, aşağıdaki örnekte gösterildiği gibi, Giden iletiye özel bir üst bilgi eklemek üzere bir istemci uygulamasında yeni bir bağlam oluşturmak için <xref:System.ServiceModel.OperationContextScope> kullanılarak yapılır.

[!code-csharp[OperationContextScope#4](../../../samples/snippets/csharp/VS_Snippets_CFX/operationcontextscope/cs/client.cs#4)]
[!code-vb[OperationContextScope#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/operationcontextscope/vb/client.vb#4)]

## <a name="endpoint-address-in-metadata"></a>Meta verilerde uç nokta adresi

Bir uç nokta adresi, Web Hizmetleri Açıklama Dili (WSDL) ile ilgili uç noktanın `wsdl:port` öğesinin içinde WS-Addressing `EndpointReference` (EPR) öğesi olarak temsil edilir. EPR, uç noktanın adresini ve tüm adres özelliklerini içerir. @No__t-0 içindeki EPR 'nin `soap:Address` ' i aşağıdaki örnekte görüldüğü gibi değiştirdiğine unutmayın.

## <a name="defining-endpoint-addresses-in-code"></a>Koddaki Endpoint adreslerini tanımlama

@No__t-0 sınıfıyla kodda bir uç nokta adresi oluşturulabilir. Uç nokta adresi için belirtilen URI, tam nitelenmiş bir yol veya hizmetin temel adresine göreli bir yol olabilir. Aşağıdaki kod, <xref:System.ServiceModel.EndpointAddress> sınıfının bir örneğinin nasıl oluşturulacağını ve hizmetin barındırıldığı <xref:System.ServiceModel.ServiceHost> örneğine nasıl ekleneceğini gösterir.

Aşağıdaki örnekte, kodda tam uç nokta adresinin nasıl belirtileceği gösterilmektedir.

[!code-csharp[S_UEHelloWorld#2](../../../samples/snippets/csharp/VS_Snippets_CFX/s_uehelloworld/cs/snippet.cs#2)]

Aşağıdaki örnek, hizmet ana bilgisayarının temel adresine göreli bir adresin ("hizmetim") nasıl ekleneceğini gösterir.

[!code-csharp[S_UEHelloWorld#3](../../../samples/snippets/csharp/VS_Snippets_CFX/s_uehelloworld/cs/snippet.cs#3)]

> [!NOTE]
> Hizmet uygulamasındaki <xref:System.ServiceModel.Description.ServiceDescription> ' ın özellikleri, daha sonra <xref:System.ServiceModel.ServiceHostBase> ' deki <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> yöntemine değiştirilmemelidir. @No__t-0 özelliği ve <xref:System.ServiceModel.ServiceHostBase> ve <xref:System.ServiceModel.ServiceHost> üzerindeki `AddServiceEndpoint` yöntemleri gibi bazı üyeler, bu noktadan sonra değiştirilirse bir özel durum oluşturur. Diğerleri bunları değiştirmenize izin verir, ancak sonuç tanımsızdır.
>
> Benzer şekilde, istemcide <xref:System.ServiceModel.Description.ServiceEndpoint> değerleri <xref:System.ServiceModel.ChannelFactory> ' de <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> ' e çağrıdan sonra değiştirilmemelidir. @No__t-0 özelliği, bu noktadan sonra değiştirilirse bir özel durum oluşturur. Diğer istemci açıklama değerleri hata olmadan değiştirilebilir, ancak sonuç tanımsızdır.
>
> Hizmet veya istemci için, <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> çağrılmadan önce açıklamayı değiştirmeniz önerilir.

## <a name="using-default-endpoints"></a>Varsayılan uç noktaları kullanma

Kodda veya yapılandırmada hiçbir uç nokta belirtilmemişse, çalışma zamanı, hizmet tarafından uygulanan her bir hizmet sözleşmesinin her bir temel adresine bir varsayılan uç nokta ekleyerek varsayılan uç noktaları sağlar. Temel adres kodda veya yapılandırmada belirtilebilir ve varsayılan uç noktalar <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> <xref:System.ServiceModel.ServiceHost> ' de çağrıldığında eklenir.

Uç noktalar açıkça sağlanmışsa, <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> çağrılmadan önce <xref:System.ServiceModel.ServiceHost> ' de <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> çağırarak varsayılan uç noktalar eklenebilir. Varsayılan uç noktalar, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](./samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](simplified-configuration.md) ve Basitleştirilmiş yapılandırma.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.EndpointAddress>
- [Kimlik Doğrulama ile Hizmet Kimliği](./feature-details/service-identity-and-authentication.md)
- [Uç Nokta Oluşturmaya Genel Bakış](endpoint-creation-overview.md)
- [Barındırma](./feature-details/hosting.md)
