---
title: 'Nasıl yapılır: Oturumlarının gerektiren bir hizmet oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
ms.openlocfilehash: fa151d472dbd27a62f91cd3a43339c66787dc456
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54615448"
---
# <a name="how-to-create-a-service-that-requires-sessions"></a><span data-ttu-id="1ae94-102">Nasıl yapılır: Oturumlarının gerektiren bir hizmet oluşturma</span><span class="sxs-lookup"><span data-stu-id="1ae94-102">How to: Create a Service That Requires Sessions</span></span>
<span data-ttu-id="1ae94-103">Oturumları, istemcilere hizmet örnekleri arasındaki ilişkilendirmeleri geri çağırmaları ve çok atlamalı güvenlik gibi yararlı özellikleri sağlayan iki veya daha fazla uç noktalar arasında paylaşılan bir durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1ae94-103">Sessions create a shared state between two or more endpoints that enables useful features such as callbacks, multi-hop security, and associations between clients and service instances.</span></span> <span data-ttu-id="1ae94-104">Windows Communication Foundation (WCF) uygulamalarında oturumları hakkında daha fazla bilgi için bkz. [oturumları kullanarak](../../../../docs/framework/wcf/using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="1ae94-104">For more information about sessions in Windows Communication Foundation (WCF) applications, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a><span data-ttu-id="1ae94-105">Bir sözleşme bağlamasına oturumları desteklemek gerekli olduğunu belirtmek için</span><span class="sxs-lookup"><span data-stu-id="1ae94-105">To specify that a contract require its binding to support sessions</span></span>  
  
1.  <span data-ttu-id="1ae94-106">Hizmet Sözleşmesi ile en az bir işlem oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1ae94-106">Create a service contract with at least one operation.</span></span> <span data-ttu-id="1ae94-107">Hizmet sözleşmesi oluşturma örneği için bkz: [nasıl yapılır: Bir hizmet sözleşmesini tanımlama](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="1ae94-107">For an example of how to create a service contract, see [How to: Define a Service Contract](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span>  
  
2.  <span data-ttu-id="1ae94-108">Değiştirme <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> ayarlayarak sözleşme bildiren <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> ya da özelliği:</span><span class="sxs-lookup"><span data-stu-id="1ae94-108">Modify the <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> that declares the contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> property to either:</span></span>  
  
    -   <span data-ttu-id="1ae94-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> Bu sözleşme bir oturumunda çalıştırmanız gerekir</span><span class="sxs-lookup"><span data-stu-id="1ae94-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> if this contract must be run within a session.</span></span>  
  
    -   <span data-ttu-id="1ae94-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> Bu sözleşme bir oturumda çalıştırabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="1ae94-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> if this contract can be run within a session.</span></span>  
  
    -   <span data-ttu-id="1ae94-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> Bu sözleşme oturum içindeki çalıştırmamalıdır durumunda.</span><span class="sxs-lookup"><span data-stu-id="1ae94-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> if this contract must not be run within a session.</span></span>  
  
3.  <span data-ttu-id="1ae94-112">Oturumlarının destekleyen bir bağlama kullanmak için hizmet uç noktasını yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="1ae94-112">Configure your service endpoint to use a binding that supports sessions.</span></span> <span data-ttu-id="1ae94-113">Aşağıdaki yapılandırma örnek kullanımını gösterir <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, bir WS destekleyen`-`ReliableMessaging oturumu.</span><span class="sxs-lookup"><span data-stu-id="1ae94-113">The following configuration example shows the use of the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, which supports a WS`-`ReliableMessaging session.</span></span>  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]   
  
## <a name="example"></a><span data-ttu-id="1ae94-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="1ae94-114">Example</span></span>  
 <span data-ttu-id="1ae94-115">Aşağıdaki kod örneği bir sözleşme düzeyi oturumu gereksinim belirtin ve bu gereksinimi desteklemek için bir yapılandırma dosyası kullanma işlemi gösterilmektedir <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> bağlama.</span><span class="sxs-lookup"><span data-stu-id="1ae94-115">The following example code shows how to specify a contract-level session requirement and use a configuration file to support that requirement with the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> binding.</span></span>  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)] 
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]      
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]     
  
## <a name="see-also"></a><span data-ttu-id="1ae94-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ae94-116">See also</span></span>
- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
