---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: özel Ilke onaylamalarını dışarı aktarma'
title: 'Nasıl yapılır: Özel İlke Onaylamalarını Dışarı Aktarma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99030386-43b0-4f7b-866d-17ea307f5cbd
ms.openlocfilehash: b49d5a88809039f59537d79f92e31711085e580a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668941"
---
# <a name="how-to-export-custom-policy-assertions"></a><span data-ttu-id="264d0-103">Nasıl yapılır: Özel İlke Onaylamalarını Dışarı Aktarma</span><span class="sxs-lookup"><span data-stu-id="264d0-103">How to: Export Custom Policy Assertions</span></span>

<span data-ttu-id="264d0-104">İlke onayları bir hizmet uç noktasının yeteneklerini ve gereksinimlerini anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="264d0-104">Policy assertions describe the capabilities and requirements of a service endpoint.</span></span> <span data-ttu-id="264d0-105">Hizmet uygulamaları, uç nokta, bağlama veya sözleşme özelleştirme bilgilerini istemci uygulamasına iletmek için hizmet meta verilerinde özel ilke onayları kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="264d0-105">Service applications can use custom policy assertions in service metadata to communicate endpoint, binding or contract customization information to the client application.</span></span> <span data-ttu-id="264d0-106">İletişim kurduğunuz yeteneklere veya gereksinimlere bağlı olarak, bir uç nokta, işlem veya ileti konusunda WSDL bağlamalarında ekli ilke ifadelerinde onayları dışarı aktarmak için Windows Communication Foundation (WCF) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="264d0-106">You can use Windows Communication Foundation (WCF) to export assertions in policy expressions attached in WSDL bindings at the endpoint, operation, or message subjects, depending upon the capabilities or requirements you are communicating.</span></span>  
  
 <span data-ttu-id="264d0-107">Özel ilke onayları, <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> bir üzerinde arabirimini uygulayarak <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> ve bağlama öğesini doğrudan hizmet uç noktasının bağlamasına veya uygulama yapılandırma dosyanıza kaydederek bağlama öğesini ekleyerek verilir.</span><span class="sxs-lookup"><span data-stu-id="264d0-107">Custom policy assertions are exported by implementing the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface on a <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> and either inserting the binding element directly into the binding of the service endpoint or by registering the binding element in your application configuration file.</span></span> <span data-ttu-id="264d0-108">İlke dışa aktarma uygulamanız, özel ilke onayınız <xref:System.Xml.XmlElement?displayProperty=nameWithType> için yönteme geçirilecek uygun bir örnek olarak eklemesi gerekir <xref:System.ServiceModel.Description.PolicyAssertionCollection?displayProperty=nameWithType> <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> .</span><span class="sxs-lookup"><span data-stu-id="264d0-108">Your policy export implementation should add your custom policy assertion as a <xref:System.Xml.XmlElement?displayProperty=nameWithType> instance to the appropriate <xref:System.ServiceModel.Description.PolicyAssertionCollection?displayProperty=nameWithType> on the <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> passed into the <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> method.</span></span>  
  
 <span data-ttu-id="264d0-109">Ayrıca, <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> sınıfının özelliğini denetlemeniz <xref:System.ServiceModel.Description.WsdlExporter> ve iç içe geçmiş ilke ifadelerini ve ilke çerçevesi özniteliklerini belirtilen ilke sürümüne göre doğru ad alanında dışarı aktarmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="264d0-109">In addition you must check the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property of the <xref:System.ServiceModel.Description.WsdlExporter> class and export nested policy expressions and policy framework attributes in the correct namespace based on the policy version specified.</span></span>  
  
 <span data-ttu-id="264d0-110">Özel ilke onaylamalarını içeri aktarmak için bkz <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> . ve [nasıl yapılır: özel ilke onaylamalarını içeri aktarma](how-to-import-custom-policy-assertions.md).</span><span class="sxs-lookup"><span data-stu-id="264d0-110">To import custom policy assertions, see <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> and [How to: Import Custom Policy Assertions](how-to-import-custom-policy-assertions.md).</span></span>  
  
### <a name="to-export-custom-policy-assertions"></a><span data-ttu-id="264d0-111">Özel ilke onaylamalarını dışarı aktarmak için</span><span class="sxs-lookup"><span data-stu-id="264d0-111">To export custom policy assertions</span></span>  
  
1. <span data-ttu-id="264d0-112"><xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType>Arabirimini bir üzerinde uygulayın <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="264d0-112">Implement the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface on a <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>.</span></span> <span data-ttu-id="264d0-113">Aşağıdaki kod örneği, bağlama düzeyinde özel bir ilke onaylama uygulamasının uygulanmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="264d0-113">The following code example shows the implementation of a custom policy assertion at the binding level.</span></span>  
  
     [!code-csharp[CustomPolicySample#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyexporter.cs#14)]
     [!code-vb[CustomPolicySample#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyexporter.vb#14)]  
  
2. <span data-ttu-id="264d0-114">Bağlama öğesini program aracılığıyla veya bir uygulama yapılandırma dosyası kullanarak uç nokta bağlamaya ekleyin.</span><span class="sxs-lookup"><span data-stu-id="264d0-114">Insert the binding element into the endpoint binding either programmatically or using an application configuration file.</span></span> <span data-ttu-id="264d0-115">Aşağıdaki yordamlara bakın.</span><span class="sxs-lookup"><span data-stu-id="264d0-115">See the following procedures.</span></span>  
  
### <a name="to-insert-a-binding-element-using-an-application-configuration-file"></a><span data-ttu-id="264d0-116">Bir uygulama yapılandırma dosyası kullanarak bir bağlama öğesi eklemek için</span><span class="sxs-lookup"><span data-stu-id="264d0-116">To insert a binding element using an application configuration file</span></span>  
  
1. <span data-ttu-id="264d0-117"><xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>Özel ilke onaylama bağlama öğesi için uygulayın.</span><span class="sxs-lookup"><span data-stu-id="264d0-117">Implement <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType> for your custom policy assertion binding element.</span></span>  
  
2. <span data-ttu-id="264d0-118">Bağlama öğesi uzantısını öğesini kullanarak yapılandırma dosyasına ekleyin [\<bindingElementExtensions>](../../configure-apps/file-schema/wcf/bindingelementextensions.md) .</span><span class="sxs-lookup"><span data-stu-id="264d0-118">Add the binding element extension to the configuration file using the [\<bindingElementExtensions>](../../configure-apps/file-schema/wcf/bindingelementextensions.md) element.</span></span>  
  
3. <span data-ttu-id="264d0-119">Kullanarak özel bir bağlama oluşturun <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="264d0-119">Build a custom binding using the <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-insert-a-binding-element-programmatically"></a><span data-ttu-id="264d0-120">Programlı olarak bir bağlama öğesi eklemek için</span><span class="sxs-lookup"><span data-stu-id="264d0-120">To insert a binding element programmatically</span></span>  
  
1. <span data-ttu-id="264d0-121">Yeni bir oluşturun <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> ve ' a ekleyin <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="264d0-121">Create a new <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> and add it to a <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.</span></span>  
  
2. <span data-ttu-id="264d0-122">Adım 1 ' den özel bağlamayı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="264d0-122">Add the custom binding from step 1.</span></span> <span data-ttu-id="264d0-123">Yeni bir uç noktaya ekleyin ve yöntemini çağırarak bu yeni hizmet uç noktasını öğesine ekleyin <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> .</span><span class="sxs-lookup"><span data-stu-id="264d0-123">to a new endpoint and add that new service endpoint to the <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> by calling the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
3. <span data-ttu-id="264d0-124"><xref:System.ServiceModel.ServiceHost>uygulamasını açın.</span><span class="sxs-lookup"><span data-stu-id="264d0-124">Open the <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="264d0-125">Aşağıdaki kod örneği, özel bir bağlamanın oluşturulmasını ve bağlama öğelerinin programlı olarak eklenmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="264d0-125">The following code example shows the creation of a custom binding and the programmatic insertion of binding elements.</span></span>  
  
     [!code-csharp[s_imperative#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_imperative/cs/service.cs#1)]
     [!code-vb[s_imperative#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_imperative/vb/service.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="264d0-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="264d0-126">See also</span></span>

- <xref:System.ServiceModel.Description.IPolicyImportExtension>
- <xref:System.ServiceModel.Description.IPolicyExportExtension>
- [<span data-ttu-id="264d0-127">Nasıl yapılır: Özel İlke Onaylamalarını İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="264d0-127">How to: Import Custom Policy Assertions</span></span>](how-to-import-custom-policy-assertions.md)
