---
title: 'Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
ms.openlocfilehash: 495de5a926cfc0c5aab88337f5f33b991c49e71a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184983"
---
# <a name="how-to-create-a-service-that-requires-sessions"></a><span data-ttu-id="8f6be-102">Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8f6be-102">How to: Create a Service That Requires Sessions</span></span>
<span data-ttu-id="8f6be-103">Oturumlar, geri aramalar, çoklu atlama güvenliği ve istemciler ve hizmet örnekleri arasındaki ilişkilendirmeler gibi yararlı özellikleri etkinleştiren iki veya daha fazla uç nokta arasında paylaşılan bir durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8f6be-103">Sessions create a shared state between two or more endpoints that enables useful features such as callbacks, multi-hop security, and associations between clients and service instances.</span></span> <span data-ttu-id="8f6be-104">Windows Communication Foundation (WCF) uygulamalarındaki oturumlar hakkında daha fazla bilgi için, [Bkz. Oturumları Kullanma.](../../../../docs/framework/wcf/using-sessions.md)</span><span class="sxs-lookup"><span data-stu-id="8f6be-104">For more information about sessions in Windows Communication Foundation (WCF) applications, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a><span data-ttu-id="8f6be-105">Bir sözleşmenin oturumları desteklemek için bağlanmasını gerektirdiğini belirtmek için</span><span class="sxs-lookup"><span data-stu-id="8f6be-105">To specify that a contract require its binding to support sessions</span></span>  
  
1. <span data-ttu-id="8f6be-106">En az bir işlemle bir hizmet sözleşmesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8f6be-106">Create a service contract with at least one operation.</span></span> <span data-ttu-id="8f6be-107">Hizmet sözleşmesi oluşturma nın bir örneği için [bkz.](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)</span><span class="sxs-lookup"><span data-stu-id="8f6be-107">For an example of how to create a service contract, see [How to: Define a Service Contract](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span>  
  
2. <span data-ttu-id="8f6be-108"><xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> Özelliği aşağıdakilerden biri için ayarlayarak sözleşmeyi bildiren ibareyi değiştirin: <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="8f6be-108">Modify the <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> that declares the contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> property to either:</span></span>  
  
    - <span data-ttu-id="8f6be-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>bu sözleşmenin bir oturum içinde çalıştırılması gerekiyorsa.</span><span class="sxs-lookup"><span data-stu-id="8f6be-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> if this contract must be run within a session.</span></span>  
  
    - <span data-ttu-id="8f6be-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType>bu sözleşme bir oturum içinde çalıştırılabilirse.</span><span class="sxs-lookup"><span data-stu-id="8f6be-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> if this contract can be run within a session.</span></span>  
  
    - <span data-ttu-id="8f6be-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType>bu sözleşme nin bir oturum içinde çalıştırılmaması gerekiyorsa.</span><span class="sxs-lookup"><span data-stu-id="8f6be-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> if this contract must not be run within a session.</span></span>  
  
3. <span data-ttu-id="8f6be-112">Hizmet bitiş noktanızı oturumları destekleyen bir bağlama kullanacak şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="8f6be-112">Configure your service endpoint to use a binding that supports sessions.</span></span> <span data-ttu-id="8f6be-113">Aşağıdaki yapılandırma <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>örneği, WS`-`ReliableMessaging oturumunu destekleyen ,</span><span class="sxs-lookup"><span data-stu-id="8f6be-113">The following configuration example shows the use of the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, which supports a WS`-`ReliableMessaging session.</span></span>  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="example"></a><span data-ttu-id="8f6be-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="8f6be-114">Example</span></span>  
 <span data-ttu-id="8f6be-115">Aşağıdaki örnek kod, sözleşme düzeyinde oturum gereksiniminin nasıl belirtilen ve <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> bu gereksinimi bağlamayla desteklemek için bir yapılandırma dosyasının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8f6be-115">The following example code shows how to specify a contract-level session requirement and use a configuration file to support that requirement with the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> binding.</span></span>  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)]
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="see-also"></a><span data-ttu-id="8f6be-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f6be-116">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
