---
title: 'Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
ms.openlocfilehash: c104798fa3ef0e8b9dc43ad9cc68599b71de4011
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140497"
---
# <a name="how-to-create-a-service-that-requires-sessions"></a><span data-ttu-id="b1762-102">Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b1762-102">How to: Create a Service That Requires Sessions</span></span>
<span data-ttu-id="b1762-103">Oturumları, istemcilere hizmet örnekleri arasındaki ilişkilendirmeleri geri çağırmaları ve çok atlamalı güvenlik gibi yararlı özellikleri sağlayan iki veya daha fazla uç noktalar arasında paylaşılan bir durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b1762-103">Sessions create a shared state between two or more endpoints that enables useful features such as callbacks, multi-hop security, and associations between clients and service instances.</span></span> <span data-ttu-id="b1762-104">Windows Communication Foundation (WCF) uygulamalarında oturumları hakkında daha fazla bilgi için bkz. [oturumları kullanarak](../../../../docs/framework/wcf/using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="b1762-104">For more information about sessions in Windows Communication Foundation (WCF) applications, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a><span data-ttu-id="b1762-105">Bir sözleşme bağlamasına oturumları desteklemek gerekli olduğunu belirtmek için</span><span class="sxs-lookup"><span data-stu-id="b1762-105">To specify that a contract require its binding to support sessions</span></span>  
  
1.  <span data-ttu-id="b1762-106">Hizmet Sözleşmesi ile en az bir işlem oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b1762-106">Create a service contract with at least one operation.</span></span> <span data-ttu-id="b1762-107">Hizmet sözleşmesi oluşturma örneği için bkz: [nasıl yapılır: Bir hizmet sözleşmesini tanımlama](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="b1762-107">For an example of how to create a service contract, see [How to: Define a Service Contract](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span>  
  
2.  <span data-ttu-id="b1762-108">Değiştirme <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> ayarlayarak sözleşme bildiren <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> ya da özelliği:</span><span class="sxs-lookup"><span data-stu-id="b1762-108">Modify the <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> that declares the contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> property to either:</span></span>  
  
    -   <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> <span data-ttu-id="b1762-109">Bu sözleşme bir oturumunda çalıştırmanız gerekir</span><span class="sxs-lookup"><span data-stu-id="b1762-109">if this contract must be run within a session.</span></span>  
  
    -   <xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> <span data-ttu-id="b1762-110">Bu sözleşme bir oturumda çalıştırabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="b1762-110">if this contract can be run within a session.</span></span>  
  
    -   <xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> <span data-ttu-id="b1762-111">Bu sözleşme oturum içindeki çalıştırmamalıdır durumunda.</span><span class="sxs-lookup"><span data-stu-id="b1762-111">if this contract must not be run within a session.</span></span>  
  
3.  <span data-ttu-id="b1762-112">Oturumlarının destekleyen bir bağlama kullanmak için hizmet uç noktasını yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="b1762-112">Configure your service endpoint to use a binding that supports sessions.</span></span> <span data-ttu-id="b1762-113">Aşağıdaki yapılandırma örnek kullanımını gösterir <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, bir WS destekleyen`-`ReliableMessaging oturumu.</span><span class="sxs-lookup"><span data-stu-id="b1762-113">The following configuration example shows the use of the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, which supports a WS`-`ReliableMessaging session.</span></span>  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]   
  
## <a name="example"></a><span data-ttu-id="b1762-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="b1762-114">Example</span></span>  
 <span data-ttu-id="b1762-115">Aşağıdaki kod örneği bir sözleşme düzeyi oturumu gereksinim belirtin ve bu gereksinimi desteklemek için bir yapılandırma dosyası kullanma işlemi gösterilmektedir <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> bağlama.</span><span class="sxs-lookup"><span data-stu-id="b1762-115">The following example code shows how to specify a contract-level session requirement and use a configuration file to support that requirement with the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> binding.</span></span>  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)] 
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]      
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]     
  
## <a name="see-also"></a><span data-ttu-id="b1762-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1762-116">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
