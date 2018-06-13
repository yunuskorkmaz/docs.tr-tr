---
title: 'Nasıl yapılır: WCF İstemcisini WSE3.0 Hizmetleriyle Çalışacak Şekilde Yapılandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3dadd7f1-d207-4ea5-a73b-3e8aa44407f8
ms.openlocfilehash: e30403f9c97f31e93c22a9658ffb74d4d02a49ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490649"
---
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a><span data-ttu-id="67447-102">Nasıl yapılır: WCF İstemcisini WSE3.0 Hizmetleriyle Çalışacak Şekilde Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="67447-102">How to: Configure a WCF Client to interoperate with WSE3.0 Services</span></span>
<span data-ttu-id="67447-103">WCF istemcileri WS adresleme belirtimi Ağustos 2004 sürümünü kullanacak şekilde yapılandırıldıklarında Windows Communication Foundation (WCF) istemcileri hat düzeyinde Web Hizmetleri geliştirmeleri 3.0 ile Microsoft .NET (WSE) Hizmetleri için uyumludur.</span><span class="sxs-lookup"><span data-stu-id="67447-103">Windows Communication Foundation (WCF) clients are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) services when WCF clients are configured to use the August 2004 version of the WS-Addressing specification.</span></span>  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a><span data-ttu-id="67447-104">WSE 3.0 Web hizmeti ile birlikte çalışmak için WCF istemcisini yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="67447-104">To configure a WCF client to interoperate with a WSE 3.0 Web service</span></span>  
  
1.  <span data-ttu-id="67447-105">Çalıştırma [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) WSE 3.0 Web hizmeti için bir WCF istemcisi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="67447-105">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to create a WCF client for the WSE 3.0 Web service.</span></span>  
  
     <span data-ttu-id="67447-106">WSE Web hizmeti için bir WCF istemcisi sınıfı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="67447-106">For a WSE Web service, a WCF client class is created.</span></span>  
  
     <span data-ttu-id="67447-107">Bir WCF istemcisi oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir istemci oluşturmak](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="67447-107">For details about creating a WCF client, see the [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
2.  <span data-ttu-id="67447-108">WSE 3.0 Web Hizmetleri ile iletişim kurabilen bir bağlama temsil eden bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="67447-108">Create a class that represents a binding that can communicate with WSE 3.0 Web services.</span></span>  
  
     <span data-ttu-id="67447-109">Aşağıdaki sınıf parçası olan [WSE ile birlikte](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41) örnek.</span><span class="sxs-lookup"><span data-stu-id="67447-109">The following class is part of the [Interoperating with WSE](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41) sample.</span></span>  
  
    1.  <span data-ttu-id="67447-110">Türeyen bir sınıf oluşturun <xref:System.ServiceModel.Channels.Binding> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="67447-110">Create a class that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         <span data-ttu-id="67447-111">Aşağıdaki kod örneğinde adlı bir sınıf oluşturur `WseHttpBinding` , türetilen <xref:System.ServiceModel.Channels.Binding> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="67447-111">The following code example creates a class named `WseHttpBinding` that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  <span data-ttu-id="67447-112">Özellikler WSE anahtar teslimi onaylama, türetilmiş anahtar gerekli olup, güvenli oturumlar kullanılıp, imza onayı gerekli olup olmadığı ve ileti koruma ayarlarını belirtin sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="67447-112">Add properties to the class that specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings.</span></span>  
  
         <span data-ttu-id="67447-113">Aşağıdaki kod örneğinde tanımlar `SecurityAssertion,``RequireDerivedKeys, EstablishSecurityContext, MessageProtectionOrder` WSE anahtar teslimi onaylama, türetilmiş anahtar gerekli olup, güvenli oturumlar kullanılıp, imza onayı gerekli olup ve ileti koruma ayarlarını belirten özellikleri sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="67447-113">The following code example defines `SecurityAssertion,``RequireDerivedKeys, EstablishSecurityContext, MessageProtectionOrder` properties that specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings, respectively.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  <span data-ttu-id="67447-114">Geçersiz kılma <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> yöntemi bağlama özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="67447-114">Override the <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> method to set the binding properties.</span></span>  
  
         <span data-ttu-id="67447-115">Aşağıdaki kod örneğinde taşıma, ileti kodlama ve ileti koruma ayarları değerleri alma belirtir `SecurityAssertion` ve `MessageProtectionOrder` özellikleri.</span><span class="sxs-lookup"><span data-stu-id="67447-115">The following code example specifies the transport, message encoding, and message protection settings by getting the values of the `SecurityAssertion` and `MessageProtectionOrder` properties.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3.  <span data-ttu-id="67447-116">İstemci uygulaması kodu bağlama özelliklerini ayarlamak için kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="67447-116">In the client application code, add code to set the binding properties.</span></span>  
  
     <span data-ttu-id="67447-117">Aşağıdaki kod örneğinde WCF istemcisini ileti koruma ve kimlik doğrulama WSE 3.0 tarafından tanımlandığı şekilde kullanması gerektiğini belirtir `AnonymousForCertificate` anahtar teslimi güvenlik onaylama işlemi.</span><span class="sxs-lookup"><span data-stu-id="67447-117">The following code example specifies that the WCF client must use message protection and authentication as defined by the WSE 3.0 `AnonymousForCertificate` turnkey security assertion.</span></span> <span data-ttu-id="67447-118">Ayrıca, güvenli oturumlar ve türetilmiş anahtar gereklidir.</span><span class="sxs-lookup"><span data-stu-id="67447-118">Additionally, secure sessions and derived keys are required.</span></span>  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="67447-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="67447-119">Example</span></span>  
 <span data-ttu-id="67447-120">Aşağıdaki kod örneğinde WSE 3.0 anahtar teslimi güvenlik onaylama işlemi özelliklerine karşılık özellikleri kullanıma sunan özel bir bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="67447-120">The following code example defines a custom binding that exposes properties that correspond to the properties of a WSE 3.0 turnkey security assertion.</span></span> <span data-ttu-id="67447-121">Adlı özel bağlama `WseHttpBinding`, ardından bağlama özellikleri için bir WCF istemcisi belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="67447-121">The custom binding, which is named `WseHttpBinding`, is then used to specify the binding properties for a WCF client.</span></span>  
  
  
[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="67447-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="67447-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 [<span data-ttu-id="67447-123">WSE ile birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="67447-123">Interoperating with WSE</span></span>](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41)
