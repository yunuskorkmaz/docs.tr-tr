---
title: 'Nasıl yapılır: Belirtilen Bir Kimlik Doğrulama Modu için SecurityBindingElement Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a7c7747a-5b8c-463f-8493-7266dac75066
ms.openlocfilehash: 6466d218ca21e7d2ee4f01f079f308348469fd97
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934339"
---
# <a name="how-to-create-a-securitybindingelement-for-a-specified-authentication-mode"></a><span data-ttu-id="d2152-102">Nasıl yapılır: Belirtilen Bir Kimlik Doğrulama Modu için SecurityBindingElement Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d2152-102">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>
<span data-ttu-id="d2152-103">Windows Communication Foundation (WCF), istemcilerin ve hizmetlerin bir diğeri üzerinde kimlik doğrulaması yaptığı çeşitli modlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="d2152-103">Windows Communication Foundation (WCF) provides several modes by which clients and services authenticate to one another.</span></span> <span data-ttu-id="d2152-104">Aşağıdaki örnekte gösterildiği gibi, <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıftaki statik yöntemleri kullanarak veya yapılandırma yoluyla bu kimlik doğrulama modları için güvenlik bağlama öğeleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2152-104">You can create security binding elements for these authentication modes by using static methods on the <xref:System.ServiceModel.Channels.SecurityBindingElement> class or through configuration, as shown in the following example.</span></span>  
  
 <span data-ttu-id="d2152-105">18 kimlik doğrulama modları hakkında daha fazla bilgi için bkz. [SecurityBindingElement Kimlik doğrulama modları](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).</span><span class="sxs-lookup"><span data-stu-id="d2152-105">For more information about the 18 authentication modes, see [SecurityBindingElement Authentication Modes](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2152-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="d2152-106">Example</span></span>  
 <span data-ttu-id="d2152-107">Aşağıdaki kod örneği, çeşitli kimlik doğrulama modları için bağlama oluşturma yöntemlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2152-107">The following code example shows methods for creating bindings for the various authentication modes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d2152-108"><xref:System.ServiceModel.Channels.SecurityBindingElement> Nesne örneği oluşturulduktan sonra, <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> ve <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>gibi birçok özellik sabittir.</span><span class="sxs-lookup"><span data-stu-id="d2152-108">Once an instance of the <xref:System.ServiceModel.Channels.SecurityBindingElement> object is created, a number of properties are immutable, such as <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> and <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>.</span></span> <span data-ttu-id="d2152-109">Bu `set` tür özellikleri çağırmak bunları değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="d2152-109">Calling `set` on such properties does not change them.</span></span>  
  
 [!code-csharp[c_CustomBindingsAuthMode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#2)]
 [!code-vb[c_CustomBindingsAuthMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d2152-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2152-110">See also</span></span>

- [<span data-ttu-id="d2152-111">SecurityBindingElement Kimlik Doğrulama Modları</span><span class="sxs-lookup"><span data-stu-id="d2152-111">SecurityBindingElement Authentication Modes</span></span>](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)
- [<span data-ttu-id="d2152-112">Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="d2152-112">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
