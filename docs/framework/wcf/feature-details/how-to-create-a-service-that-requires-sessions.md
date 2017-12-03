---
title: "Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8f9cff53b598d4e477488bcb5b5e87be62e78bb9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-service-that-requires-sessions"></a><span data-ttu-id="773e0-102">Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="773e0-102">How to: Create a Service That Requires Sessions</span></span>
<span data-ttu-id="773e0-103">Oturumları geri aramalar, çoklu atlamalı güvenlik ve istemciler ve hizmet örnekleri arasındaki ilişkileri gibi yararlı özellikleri etkinleştirir iki veya daha fazla uç noktalar arasında paylaşılan bir durum oluşturun.</span><span class="sxs-lookup"><span data-stu-id="773e0-103">Sessions create a shared state between two or more endpoints that enables useful features such as callbacks, multi-hop security, and associations between clients and service instances.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="773e0-104">oturumlarında [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] uygulamalar, bkz [kullanarak oturumları](../../../../docs/framework/wcf/using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="773e0-104"> sessions in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] applications, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a><span data-ttu-id="773e0-105">Bir sözleşme bağlamasına oturumları desteklemek gerekli olduğunu belirtmek için</span><span class="sxs-lookup"><span data-stu-id="773e0-105">To specify that a contract require its binding to support sessions</span></span>  
  
1.  <span data-ttu-id="773e0-106">Hizmet sözleşmesi en az bir işlem ile oluşturun.</span><span class="sxs-lookup"><span data-stu-id="773e0-106">Create a service contract with at least one operation.</span></span> <span data-ttu-id="773e0-107">Hizmet sözleşmesi oluşturma örneği için bkz: [nasıl yapılır: bir hizmet sözleşmesini tanımlama](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="773e0-107">For an example of how to create a service contract, see [How to: Define a Service Contract](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span>  
  
2.  <span data-ttu-id="773e0-108">Değiştirme <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> ayarlayarak sözleşme bildiren <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> ya da özellik:</span><span class="sxs-lookup"><span data-stu-id="773e0-108">Modify the <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> that declares the contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> property to either:</span></span>  
  
    -   <span data-ttu-id="773e0-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>Bu sözleşme bir oturumunda çalıştırmanız gerekir</span><span class="sxs-lookup"><span data-stu-id="773e0-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> if this contract must be run within a session.</span></span>  
  
    -   <span data-ttu-id="773e0-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType>Bu sözleşme bir oturumda çalıştırabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="773e0-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> if this contract can be run within a session.</span></span>  
  
    -   <span data-ttu-id="773e0-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType>Bu sözleşme bir oturumda çalıştırılmamalıdır durumunda.</span><span class="sxs-lookup"><span data-stu-id="773e0-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> if this contract must not be run within a session.</span></span>  
  
3.  <span data-ttu-id="773e0-112">Oturumları destekleyen bir bağlama kullanmak için hizmet uç noktası yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="773e0-112">Configure your service endpoint to use a binding that supports sessions.</span></span> <span data-ttu-id="773e0-113">Aşağıdaki yapılandırma örneği kullanımı gösterilmiştir <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, bir WS destekleyen`-`ReliableMessaging oturumu.</span><span class="sxs-lookup"><span data-stu-id="773e0-113">The following configuration example shows the use of the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, which supports a WS`-`ReliableMessaging session.</span></span>  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]   
  
## <a name="example"></a><span data-ttu-id="773e0-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="773e0-114">Example</span></span>  
 <span data-ttu-id="773e0-115">Aşağıdaki kod örneği, bir sözleşme düzeyi oturum gereksinimi belirtmek ve bu gereksinimi desteklemek için bir yapılandırma dosyası kullanmak gösterilmiştir <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> bağlama.</span><span class="sxs-lookup"><span data-stu-id="773e0-115">The following example code shows how to specify a contract-level session requirement and use a configuration file to support that requirement with the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> binding.</span></span>  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)] 
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]      
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]     
  
## <a name="see-also"></a><span data-ttu-id="773e0-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="773e0-116">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>  
 <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
