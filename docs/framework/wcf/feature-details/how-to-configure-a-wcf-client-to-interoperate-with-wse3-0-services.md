---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: WCF Istemcisini WVAW 3.0 hizmetleriyle birlikte çalışmak üzere yapılandırma'
title: 'Nasıl yapılır: WCF İstemcisini WSE3.0 Hizmetleriyle Çalışacak Şekilde Yapılandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3dadd7f1-d207-4ea5-a73b-3e8aa44407f8
ms.openlocfilehash: 97de90c491a29cdacf881a92013a11db6aea416f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780134"
---
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a><span data-ttu-id="04a11-103">Nasıl yapılır: WCF İstemcisini WSE3.0 Hizmetleriyle Çalışacak Şekilde Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="04a11-103">How to: Configure a WCF Client to interoperate with WSE3.0 Services</span></span>

<span data-ttu-id="04a11-104">Windows Communication Foundation (WCF) istemcileri, WCF istemcileri WS-Addressing belirtim 'in 2004 Ağustos sürümünü kullanacak şekilde yapılandırıldığında Microsoft .NET (WVACE) Hizmetleri için Web Hizmetleri geliştirmeleri 3,0 ile uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="04a11-104">Windows Communication Foundation (WCF) clients are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) services when WCF clients are configured to use the August 2004 version of the WS-Addressing specification.</span></span>  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a><span data-ttu-id="04a11-105">Bir WCF istemcisini bir WVA3,0 Web hizmeti ile birlikte çalışmak üzere yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="04a11-105">To configure a WCF client to interoperate with a WSE 3.0 Web service</span></span>  
  
1. <span data-ttu-id="04a11-106">WVA3,0 Web hizmeti için bir WCF istemcisi oluşturmak üzere [ServiceModel meta veri yardımcı programı aracını (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="04a11-106">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to create a WCF client for the WSE 3.0 Web service.</span></span>  
  
     <span data-ttu-id="04a11-107">Bir Wo Web hizmeti için bir WCF istemci sınıfı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="04a11-107">For a WSE Web service, a WCF client class is created.</span></span>  
  
     <span data-ttu-id="04a11-108">WCF istemcisi oluşturma hakkında ayrıntılı bilgi için bkz. [nasıl yapılır: Istemci oluşturma](../how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="04a11-108">For details about creating a WCF client, see the [How to: Create a Client](../how-to-create-a-wcf-client.md).</span></span>  
  
2. <span data-ttu-id="04a11-109">WVA3,0 Web hizmetleriyle iletişim kurabilen bir bağlamayı temsil eden bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="04a11-109">Create a class that represents a binding that can communicate with WSE 3.0 Web services.</span></span>  
  
     <span data-ttu-id="04a11-110">Aşağıdaki sınıf, [Wo örneği ile birlikte çalışma](/previous-versions/dotnet/netframework-3.5/ms752257(v=vs.90)) 'nin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="04a11-110">The following class is part of the [Interoperating with WSE](/previous-versions/dotnet/netframework-3.5/ms752257(v=vs.90)) sample.</span></span>  
  
    1. <span data-ttu-id="04a11-111">Sınıfından türeten bir sınıf oluşturun <xref:System.ServiceModel.Channels.Binding> .</span><span class="sxs-lookup"><span data-stu-id="04a11-111">Create a class that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         <span data-ttu-id="04a11-112">Aşağıdaki kod örneği, sınıfından türetilen adlı bir sınıf oluşturur `WseHttpBinding` <xref:System.ServiceModel.Channels.Binding> .</span><span class="sxs-lookup"><span data-stu-id="04a11-112">The following code example creates a class named `WseHttpBinding` that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2. <span data-ttu-id="04a11-113">Wo anahtar onaylama onayını belirten sınıfa, türetilmiş anahtarların gerekli olup olmadığına, güvenli oturumların kullanılıp kullanılmadığını, imza onaylarının gerekli olup olmadığına ve ileti koruma ayarlarına yönelik özellikler ekleyin.</span><span class="sxs-lookup"><span data-stu-id="04a11-113">Add properties to the class that specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings.</span></span>  
  
         <span data-ttu-id="04a11-114">Aşağıdaki kod örneği,,, `SecurityAssertion` `RequireDerivedKeys` `EstablishSecurityContext` ve `MessageProtectionOrder` özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="04a11-114">The following code example defines the `SecurityAssertion`, `RequireDerivedKeys`, `EstablishSecurityContext`, and `MessageProtectionOrder` properties.</span></span> <span data-ttu-id="04a11-115">Bunlar, türetilmiş anahtarların gerekli olup olmadığını, güvenli oturumların kullanılıp kullanılmadığını, imza onaylarının gerekli olup olmadığını ve ileti koruma ayarlarını sırasıyla belirler.</span><span class="sxs-lookup"><span data-stu-id="04a11-115">They specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings, respectively.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3. <span data-ttu-id="04a11-116"><xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A>Bağlama özelliklerini ayarlamak için yöntemini geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="04a11-116">Override the <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> method to set the binding properties.</span></span>  
  
         <span data-ttu-id="04a11-117">Aşağıdaki kod örneği, ve özelliklerinin değerlerini alarak aktarım, ileti kodlama ve ileti koruma ayarlarını belirtir `SecurityAssertion` `MessageProtectionOrder` .</span><span class="sxs-lookup"><span data-stu-id="04a11-117">The following code example specifies the transport, message encoding, and message protection settings by getting the values of the `SecurityAssertion` and `MessageProtectionOrder` properties.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3. <span data-ttu-id="04a11-118">İstemci uygulama kodunda, bağlama özelliklerini ayarlamak için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="04a11-118">In the client application code, add code to set the binding properties.</span></span>  
  
     <span data-ttu-id="04a11-119">Aşağıdaki kod örneği, WCF istemcisinin WVA3,0 anahtar güvenlik onayı tarafından tanımlanan ileti koruması ve kimlik doğrulaması kullanması gerektiğini belirtir `AnonymousForCertificate` .</span><span class="sxs-lookup"><span data-stu-id="04a11-119">The following code example specifies that the WCF client must use message protection and authentication as defined by the WSE 3.0 `AnonymousForCertificate` turnkey security assertion.</span></span> <span data-ttu-id="04a11-120">Ayrıca, güvenli oturumlar ve türetilmiş anahtarlar gereklidir.</span><span class="sxs-lookup"><span data-stu-id="04a11-120">Additionally, secure sessions and derived keys are required.</span></span>  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="04a11-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="04a11-121">Example</span></span>  

 <span data-ttu-id="04a11-122">Aşağıdaki kod örneği, bir WSE 3,0 anahtar güvenlik onaylaması özelliklerine karşılık gelen özellikleri kullanıma sunan özel bir bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="04a11-122">The following code example defines a custom binding that exposes properties that correspond to the properties of a WSE 3.0 turnkey security assertion.</span></span> <span data-ttu-id="04a11-123">Adlı özel bağlama `WseHttpBinding` daha sonra BIR WCF istemcisinin bağlama özelliklerini belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="04a11-123">The custom binding, which is named `WseHttpBinding`, is then used to specify the binding properties for a WCF client.</span></span>  

[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="04a11-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04a11-124">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <span data-ttu-id="04a11-125">[Wo ile birlikte çalışma](/previous-versions/dotnet/netframework-3.5/ms752257(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="04a11-125">[Interoperating with WSE](/previous-versions/dotnet/netframework-3.5/ms752257(v=vs.90))</span></span>
