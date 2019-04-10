---
title: 'Nasıl yapılır: WCF İstemcisini WSE3.0 Hizmetleriyle Çalışacak Şekilde Yapılandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3dadd7f1-d207-4ea5-a73b-3e8aa44407f8
ms.openlocfilehash: 62642651516274a27c44abfc19e94dc529690ea9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59304551"
---
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a><span data-ttu-id="d2340-102">Nasıl yapılır: WCF İstemcisini WSE3.0 Hizmetleriyle Çalışacak Şekilde Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d2340-102">How to: Configure a WCF Client to interoperate with WSE3.0 Services</span></span>
<span data-ttu-id="d2340-103">WCF istemcileri belirtiminin WS-Addressing Ağustos 2004 sürümü kullanmak için yapılandırıldığı zaman Windows Communication Foundation (WCF) istemcileri hat düzeyinde Web Hizmetleri iyileştirmeleri 3.0 ile Microsoft .NET (WSE) Hizmetleri için uyumludur.</span><span class="sxs-lookup"><span data-stu-id="d2340-103">Windows Communication Foundation (WCF) clients are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) services when WCF clients are configured to use the August 2004 version of the WS-Addressing specification.</span></span>  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a><span data-ttu-id="d2340-104">WSE 3.0 Web hizmetiyle çalışmak için WCF istemcisini yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="d2340-104">To configure a WCF client to interoperate with a WSE 3.0 Web service</span></span>  
  
1. <span data-ttu-id="d2340-105">Çalıştırma [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) WSE 3.0 Web hizmeti için bir WCF istemcisi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="d2340-105">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to create a WCF client for the WSE 3.0 Web service.</span></span>  
  
     <span data-ttu-id="d2340-106">WSE Web hizmeti, bir WCF istemcisi sınıfı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d2340-106">For a WSE Web service, a WCF client class is created.</span></span>  
  
     <span data-ttu-id="d2340-107">Bir WCF istemcisi oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir istemci oluşturmanız](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="d2340-107">For details about creating a WCF client, see the [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
2. <span data-ttu-id="d2340-108">WSE 3.0 Web Hizmetleri ile iletişim kurabilen bir bağlama temsil eden bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d2340-108">Create a class that represents a binding that can communicate with WSE 3.0 Web services.</span></span>  
  
     <span data-ttu-id="d2340-109">Aşağıdaki sınıf parçasıdır [WSE ile birlikte](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29) örnek.</span><span class="sxs-lookup"><span data-stu-id="d2340-109">The following class is part of the [Interoperating with WSE](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29) sample.</span></span>  
  
    1.  <span data-ttu-id="d2340-110">Türetilen bir sınıf oluşturmanız <xref:System.ServiceModel.Channels.Binding> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d2340-110">Create a class that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         <span data-ttu-id="d2340-111">Aşağıdaki kod örneğinde adlı bir sınıf oluşturur `WseHttpBinding` türetilen <xref:System.ServiceModel.Channels.Binding> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d2340-111">The following code example creates a class named `WseHttpBinding` that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  <span data-ttu-id="d2340-112">Özellikleri WSE anahtar teslimi onaylama, türetilen anahtarlar gerekli olup, güvenli oturumlar kullanılıp, imza onayı gerekli olup ve ileti koruma ayarlarını belirten sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d2340-112">Add properties to the class that specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings.</span></span>  
  
         <span data-ttu-id="d2340-113">Aşağıdaki kod örneği tanımlar `SecurityAssertion`, `RequireDerivedKeys`, `EstablishSecurityContext`, ve `MessageProtectionOrder` özellikleri.</span><span class="sxs-lookup"><span data-stu-id="d2340-113">The following code example defines the `SecurityAssertion`, `RequireDerivedKeys`, `EstablishSecurityContext`, and `MessageProtectionOrder` properties.</span></span> <span data-ttu-id="d2340-114">Bunlar WSE anahtar teslimi onaylama, türetilen anahtarlar gerekli olup, güvenli oturumlar kullanılıp, imza onayı gerekli olup ve ileti koruma ayarları sırasıyla belirtin.</span><span class="sxs-lookup"><span data-stu-id="d2340-114">They specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings, respectively.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  <span data-ttu-id="d2340-115">Geçersiz kılma <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> bağlama özellikleri ayarlamak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d2340-115">Override the <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> method to set the binding properties.</span></span>  
  
         <span data-ttu-id="d2340-116">Aşağıdaki kod örneğinde taşıma, ileti kodlama ve ileti koruma ayarları değerlerini alarak belirtir `SecurityAssertion` ve `MessageProtectionOrder` özellikleri.</span><span class="sxs-lookup"><span data-stu-id="d2340-116">The following code example specifies the transport, message encoding, and message protection settings by getting the values of the `SecurityAssertion` and `MessageProtectionOrder` properties.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3. <span data-ttu-id="d2340-117">İstemci uygulama kodunda bağlama özellikleri ayarlamak için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d2340-117">In the client application code, add code to set the binding properties.</span></span>  
  
     <span data-ttu-id="d2340-118">Aşağıdaki kod örneği WCF istemcisini iletisi koruma ve kimlik doğrulaması WSE 3.0 tarafından tanımlandığı şekilde kullanması gerektiğini belirtir `AnonymousForCertificate` kullanıma hazır güvenlik onaylama işlemi.</span><span class="sxs-lookup"><span data-stu-id="d2340-118">The following code example specifies that the WCF client must use message protection and authentication as defined by the WSE 3.0 `AnonymousForCertificate` turnkey security assertion.</span></span> <span data-ttu-id="d2340-119">Ayrıca, güvenli oturumlar ve türetilen anahtarlar gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d2340-119">Additionally, secure sessions and derived keys are required.</span></span>  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="d2340-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="d2340-120">Example</span></span>  
 <span data-ttu-id="d2340-121">Aşağıdaki kod örneği bir WSE 3.0 kullanıma hazır güvenlik onaylama işlemi özelliklerine karşılık gelen özelliklerle sunan özel bir bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d2340-121">The following code example defines a custom binding that exposes properties that correspond to the properties of a WSE 3.0 turnkey security assertion.</span></span> <span data-ttu-id="d2340-122">Olarak adlandırılan özel bağlama `WseHttpBinding`, ardından bir WCF istemcisi için bağlama özelliklerini belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d2340-122">The custom binding, which is named `WseHttpBinding`, is then used to specify the binding properties for a WCF client.</span></span>  

[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="d2340-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2340-123">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- [<span data-ttu-id="d2340-124">WSE ile birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="d2340-124">Interoperating with WSE</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29)
