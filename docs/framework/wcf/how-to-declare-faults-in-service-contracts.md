---
title: "Nasıl yapılır: Hizmet Sözleşmelerinde Hata Bildirme"
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
ms.assetid: e8da98e7-d22f-4f60-ac82-3fb0928a353f
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1ebfe56a0e073534840ce81eebb64ce3f5db48a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-faults-in-service-contracts"></a><span data-ttu-id="42555-102">Nasıl yapılır: Hizmet Sözleşmelerinde Hata Bildirme</span><span class="sxs-lookup"><span data-stu-id="42555-102">How to: Declare Faults in Service Contracts</span></span>
<span data-ttu-id="42555-103">Hata koşullarını ortaya çıktığında yönetilen kodda özel durumlar.</span><span class="sxs-lookup"><span data-stu-id="42555-103">In managed code, exceptions are thrown when error conditions occur.</span></span> <span data-ttu-id="42555-104">İçinde [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] uygulamalar, Bununla birlikte, hizmet sözleşmelerini belirtin hangi hata bilgilerini hizmet sözleşmesi SOAP Hataları bildirerek istemcilere gönderilir.</span><span class="sxs-lookup"><span data-stu-id="42555-104">In [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] applications, however, service contracts specify what error information is returned to clients by declaring SOAP faults in the service contract.</span></span> <span data-ttu-id="42555-105">Özel durum ve hataları arasındaki ilişkiyi genel bakış için bkz: [belirtme ve işleme hataları sözleşme ve hizmetlerde](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="42555-105">For an overview of the relationship between exceptions and faults, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
### <a name="create-a-service-contract-that-specifies-a-soap-fault"></a><span data-ttu-id="42555-106">Bir SOAP hatasını belirtir bir hizmet sözleşmesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="42555-106">Create a service contract that specifies a SOAP fault</span></span>  
  
1.  <span data-ttu-id="42555-107">En az bir işlem içeren bir hizmet sözleşmesini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="42555-107">Create a service contract that contains at least one operation.</span></span> <span data-ttu-id="42555-108">Bir örnek için bkz: [nasıl yapılır: bir hizmet sözleşmesini tanımlama](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="42555-108">For an example, see [How to: Define a Service Contract](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span>  
  
2.  <span data-ttu-id="42555-109">Bir hata durumu hakkında bildirim almak istemcileri bekleyebilirsiniz belirtebilirsiniz bir işlem seçin.</span><span class="sxs-lookup"><span data-stu-id="42555-109">Select an operation that can specify an error condition about which clients can expect to be notified.</span></span> <span data-ttu-id="42555-110">İstemcilere SOAP hataları döndürüyor, hata koşullarını justify karar vermek için bkz: [belirtme ve işleme hataları sözleşme ve hizmetlerde](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="42555-110">To decide which error conditions justify returning SOAP faults to clients, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
3.  <span data-ttu-id="42555-111">Geçerli bir <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> seçili işlemi ve Oluşturucusu geçişine seri hale getirilebilir bir arıza yazın.</span><span class="sxs-lookup"><span data-stu-id="42555-111">Apply a <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> to the selected operation and pass a serializable fault type to the constructor.</span></span> <span data-ttu-id="42555-112">Oluşturma ve seri hale getirilebilir türler kullanma hakkında daha fazla bilgi için bkz [hizmet sözleşmelerinde veri aktarımı belirtme](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="42555-112">For details about creating and using serializable types, see [Specifying Data Transfer in Service Contracts](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).</span></span> <span data-ttu-id="42555-113">Aşağıdaki örnek, belirten gösterilmektedir `SampleMethod` işlemi sonuçlanabilir bir `GreetingFault`.</span><span class="sxs-lookup"><span data-stu-id="42555-113">The following example shows how to specify that the `SampleMethod` operation can result in a `GreetingFault`.</span></span>  
  
     [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
     [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]  
  
4.  <span data-ttu-id="42555-114">Hata koşulları istemcilere iletişim kuran tüm işlemleri sözleşmesindeki için 2 ve 3. adımları yineleyin.</span><span class="sxs-lookup"><span data-stu-id="42555-114">Repeat steps 2 and 3 for all operations in the contract that communicate error conditions to clients.</span></span>  
  
## <a name="implementing-an-operation-to-return-a-specified-soap-fault"></a><span data-ttu-id="42555-115">Belirtilen bir SOAP hatası döndürmek için bir işlem uygulama</span><span class="sxs-lookup"><span data-stu-id="42555-115">Implementing an Operation to Return a Specified SOAP Fault</span></span>  
 <span data-ttu-id="42555-116">Bir işlem belirli bir SOAP hatası (yukarıdaki yordamı olduğu gibi) çağıran bir uygulama bir hata koşuluna iletişim kurmak için döndürülebilecek olduğunu belirttiğinde, sonraki adım, belirtimi uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="42555-116">Once an operation has specified that a specific SOAP fault can be returned (such as in the preceding procedure) to communicate an error condition to a calling application, the next step is to implement that specification.</span></span>  
  
#### <a name="throw-the-specified-soap-fault-in-the-operation"></a><span data-ttu-id="42555-117">Belirtilen bir SOAP hatası işlemde throw</span><span class="sxs-lookup"><span data-stu-id="42555-117">Throw the specified SOAP fault in the operation</span></span>  
  
1.  <span data-ttu-id="42555-118">Zaman bir <xref:System.ServiceModel.FaultContractAttribute>-yeni bir durum, bir işlem içinde belirtilen hata koşulu ortaya <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> burada belirtilen bir SOAP hatası, tür parametresi.</span><span class="sxs-lookup"><span data-stu-id="42555-118">When a <xref:System.ServiceModel.FaultContractAttribute>-specified error condition occurs in an operation, throw a new <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> where the specified SOAP fault is the type parameter.</span></span> <span data-ttu-id="42555-119">Aşağıdaki örnek throw gösterilmektedir `GreetingFault` içinde `SampleMethod` önceki yordamda ve aşağıdaki kod bölümünde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="42555-119">The following example shows how to throw the `GreetingFault` in the `SampleMethod` shown in the preceding procedure and in the following Code section.</span></span>  
  
     [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
     [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="42555-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="42555-120">Example</span></span>  
 <span data-ttu-id="42555-121">Aşağıdaki kod örneğinde belirten tek bir işlem uygulaması gösterir bir `GreetingFault` için `SampleMethod` işlemi.</span><span class="sxs-lookup"><span data-stu-id="42555-121">The following code example shows an implementation of a single operation that specifies a `GreetingFault` for the `SampleMethod` operation.</span></span>  
  
 [!code-csharp[FaultContractAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#1)]
 [!code-vb[FaultContractAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="42555-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="42555-122">See Also</span></span>  
 <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>  
 <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
