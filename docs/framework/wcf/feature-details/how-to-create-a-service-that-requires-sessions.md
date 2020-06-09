---
title: 'Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
ms.openlocfilehash: 29c2a87daaf763a50aa657c9badc002ff2fa27e1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593340"
---
# <a name="how-to-create-a-service-that-requires-sessions"></a><span data-ttu-id="a8ee6-102">Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a8ee6-102">How to: Create a Service That Requires Sessions</span></span>
<span data-ttu-id="a8ee6-103">Oturumlar, geri çağrılar, çok duraklı güvenlik ve istemciler ile hizmet örnekleri arasındaki ilişkilendirmeler gibi faydalı özellikleri sağlayan iki veya daha fazla uç nokta arasında paylaşılan bir durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a8ee6-103">Sessions create a shared state between two or more endpoints that enables useful features such as callbacks, multi-hop security, and associations between clients and service instances.</span></span> <span data-ttu-id="a8ee6-104">Windows Communication Foundation (WCF) uygulamalarındaki oturumlar hakkında daha fazla bilgi için bkz. [oturumları kullanma](../using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="a8ee6-104">For more information about sessions in Windows Communication Foundation (WCF) applications, see [Using Sessions](../using-sessions.md).</span></span>  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a><span data-ttu-id="a8ee6-105">Bir sözleşmenin, oturumları desteklemek için bağlamasını gerektirdiğini belirtmek için</span><span class="sxs-lookup"><span data-stu-id="a8ee6-105">To specify that a contract require its binding to support sessions</span></span>  
  
1. <span data-ttu-id="a8ee6-106">En az bir işlemle bir hizmet sözleşmesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a8ee6-106">Create a service contract with at least one operation.</span></span> <span data-ttu-id="a8ee6-107">Hizmet sözleşmesinin nasıl oluşturulacağı hakkında bir örnek için bkz. [nasıl yapılır: bir hizmet sözleşmesi tanımlama](../how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="a8ee6-107">For an example of how to create a service contract, see [How to: Define a Service Contract](../how-to-define-a-wcf-service-contract.md).</span></span>  
  
2. <span data-ttu-id="a8ee6-108">Özelliği şu <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> şekilde ayarlayarak sözleşmeyi bildiren ' i değiştirin <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="a8ee6-108">Modify the <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> that declares the contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> property to either:</span></span>  
  
    - <span data-ttu-id="a8ee6-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>Bu sözleşmenin bir oturum içinde çalıştırılması gerekiyorsa.</span><span class="sxs-lookup"><span data-stu-id="a8ee6-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> if this contract must be run within a session.</span></span>  
  
    - <span data-ttu-id="a8ee6-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType>Bu sözleşme bir oturum içinde çalıştırılabilirler.</span><span class="sxs-lookup"><span data-stu-id="a8ee6-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> if this contract can be run within a session.</span></span>  
  
    - <span data-ttu-id="a8ee6-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType>Bu sözleşmenin bir oturum içinde çalıştırılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a8ee6-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> if this contract must not be run within a session.</span></span>  
  
3. <span data-ttu-id="a8ee6-112">Hizmet uç noktanızı oturumları destekleyen bir bağlama kullanacak şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="a8ee6-112">Configure your service endpoint to use a binding that supports sessions.</span></span> <span data-ttu-id="a8ee6-113">Aşağıdaki yapılandırma örneği, <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> BIR WS ReliableMessaging oturumunu destekleyen öğesinin kullanımını gösterir `-` .</span><span class="sxs-lookup"><span data-stu-id="a8ee6-113">The following configuration example shows the use of the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, which supports a WS`-`ReliableMessaging session.</span></span>  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="example"></a><span data-ttu-id="a8ee6-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="a8ee6-114">Example</span></span>  
 <span data-ttu-id="a8ee6-115">Aşağıdaki örnek kod, bir sözleşme düzeyi oturum gereksinimini belirtmeyi ve bağlamakla bu gereksinimi desteklemek için bir yapılandırma dosyası kullanmayı gösterir <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="a8ee6-115">The following example code shows how to specify a contract-level session requirement and use a configuration file to support that requirement with the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> binding.</span></span>  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)]
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="see-also"></a><span data-ttu-id="a8ee6-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8ee6-116">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
