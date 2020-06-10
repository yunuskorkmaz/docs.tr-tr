---
title: 'Nasıl yapılır: WCF İstemcisini WSE3.0 Hizmetleriyle Çalışacak Şekilde Yapılandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3dadd7f1-d207-4ea5-a73b-3e8aa44407f8
ms.openlocfilehash: 7dd50fcc07c6c090042cf87acb4aa5d2b5321a68
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579585"
---
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a><span data-ttu-id="a07a4-102">Nasıl yapılır: WCF İstemcisini WSE3.0 Hizmetleriyle Çalışacak Şekilde Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a07a4-102">How to: Configure a WCF Client to interoperate with WSE3.0 Services</span></span>
<span data-ttu-id="a07a4-103">Windows Communication Foundation (WCF) istemcileri, WCF istemcileri WS-Addressing belirtiminin 2004 Ağustos sürümünü kullanacak şekilde yapılandırıldığında, Microsoft .NET (WVACE) Hizmetleri için Web Hizmetleri geliştirmeleri 3,0 ile kablo düzeyinde uyumludur.</span><span class="sxs-lookup"><span data-stu-id="a07a4-103">Windows Communication Foundation (WCF) clients are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) services when WCF clients are configured to use the August 2004 version of the WS-Addressing specification.</span></span>  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a><span data-ttu-id="a07a4-104">Bir WCF istemcisini bir WVA3,0 Web hizmeti ile birlikte çalışmak üzere yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="a07a4-104">To configure a WCF client to interoperate with a WSE 3.0 Web service</span></span>  
  
1. <span data-ttu-id="a07a4-105">WVA3,0 Web hizmeti için bir WCF istemcisi oluşturmak üzere [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a07a4-105">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to create a WCF client for the WSE 3.0 Web service.</span></span>  
  
     <span data-ttu-id="a07a4-106">Bir Wo Web hizmeti için bir WCF istemci sınıfı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a07a4-106">For a WSE Web service, a WCF client class is created.</span></span>  
  
     <span data-ttu-id="a07a4-107">WCF istemcisi oluşturma hakkında ayrıntılı bilgi için bkz. [nasıl yapılır: Istemci oluşturma](../how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="a07a4-107">For details about creating a WCF client, see the [How to: Create a Client](../how-to-create-a-wcf-client.md).</span></span>  
  
2. <span data-ttu-id="a07a4-108">WVA3,0 Web hizmetleriyle iletişim kurabilen bir bağlamayı temsil eden bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a07a4-108">Create a class that represents a binding that can communicate with WSE 3.0 Web services.</span></span>  
  
     <span data-ttu-id="a07a4-109">Aşağıdaki sınıf, [Wo örneği ile birlikte çalışma](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29) 'nin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="a07a4-109">The following class is part of the [Interoperating with WSE](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29) sample.</span></span>  
  
    1. <span data-ttu-id="a07a4-110">Sınıfından türeten bir sınıf oluşturun <xref:System.ServiceModel.Channels.Binding> .</span><span class="sxs-lookup"><span data-stu-id="a07a4-110">Create a class that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         <span data-ttu-id="a07a4-111">Aşağıdaki kod örneği, sınıfından türetilen adlı bir sınıf oluşturur `WseHttpBinding` <xref:System.ServiceModel.Channels.Binding> .</span><span class="sxs-lookup"><span data-stu-id="a07a4-111">The following code example creates a class named `WseHttpBinding` that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2. <span data-ttu-id="a07a4-112">Wo anahtar onaylama onayını belirten sınıfa, türetilmiş anahtarların gerekli olup olmadığına, güvenli oturumların kullanılıp kullanılmadığını, imza onaylarının gerekli olup olmadığına ve ileti koruma ayarlarına yönelik özellikler ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a07a4-112">Add properties to the class that specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings.</span></span>  
  
         <span data-ttu-id="a07a4-113">Aşağıdaki kod örneği,,, `SecurityAssertion` `RequireDerivedKeys` `EstablishSecurityContext` ve `MessageProtectionOrder` özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a07a4-113">The following code example defines the `SecurityAssertion`, `RequireDerivedKeys`, `EstablishSecurityContext`, and `MessageProtectionOrder` properties.</span></span> <span data-ttu-id="a07a4-114">Bunlar, türetilmiş anahtarların gerekli olup olmadığını, güvenli oturumların kullanılıp kullanılmadığını, imza onaylarının gerekli olup olmadığını ve ileti koruma ayarlarını sırasıyla belirler.</span><span class="sxs-lookup"><span data-stu-id="a07a4-114">They specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings, respectively.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3. <span data-ttu-id="a07a4-115"><xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A>Bağlama özelliklerini ayarlamak için yöntemini geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="a07a4-115">Override the <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> method to set the binding properties.</span></span>  
  
         <span data-ttu-id="a07a4-116">Aşağıdaki kod örneği, ve özelliklerinin değerlerini alarak aktarım, ileti kodlama ve ileti koruma ayarlarını belirtir `SecurityAssertion` `MessageProtectionOrder` .</span><span class="sxs-lookup"><span data-stu-id="a07a4-116">The following code example specifies the transport, message encoding, and message protection settings by getting the values of the `SecurityAssertion` and `MessageProtectionOrder` properties.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3. <span data-ttu-id="a07a4-117">İstemci uygulama kodunda, bağlama özelliklerini ayarlamak için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a07a4-117">In the client application code, add code to set the binding properties.</span></span>  
  
     <span data-ttu-id="a07a4-118">Aşağıdaki kod örneği, WCF istemcisinin WVA3,0 anahtar güvenlik onayı tarafından tanımlanan ileti koruması ve kimlik doğrulaması kullanması gerektiğini belirtir `AnonymousForCertificate` .</span><span class="sxs-lookup"><span data-stu-id="a07a4-118">The following code example specifies that the WCF client must use message protection and authentication as defined by the WSE 3.0 `AnonymousForCertificate` turnkey security assertion.</span></span> <span data-ttu-id="a07a4-119">Ayrıca, güvenli oturumlar ve türetilmiş anahtarlar gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a07a4-119">Additionally, secure sessions and derived keys are required.</span></span>  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="a07a4-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="a07a4-120">Example</span></span>  
 <span data-ttu-id="a07a4-121">Aşağıdaki kod örneği, bir WSE 3,0 anahtar güvenlik onaylaması özelliklerine karşılık gelen özellikleri kullanıma sunan özel bir bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a07a4-121">The following code example defines a custom binding that exposes properties that correspond to the properties of a WSE 3.0 turnkey security assertion.</span></span> <span data-ttu-id="a07a4-122">Adlı özel bağlama `WseHttpBinding` daha sonra BIR WCF istemcisinin bağlama özelliklerini belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a07a4-122">The custom binding, which is named `WseHttpBinding`, is then used to specify the binding properties for a WCF client.</span></span>  

[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="a07a4-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a07a4-123">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- [<span data-ttu-id="a07a4-124">Wo ile birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="a07a4-124">Interoperating with WSE</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29)
