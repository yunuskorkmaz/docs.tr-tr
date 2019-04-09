---
title: 'Nasıl yapılır: Hizmet Sözleşmelerinde Hata Bildirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e8da98e7-d22f-4f60-ac82-3fb0928a353f
ms.openlocfilehash: 90abb29550ce7e027244b220f30e9fe46e282ff3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129499"
---
# <a name="how-to-declare-faults-in-service-contracts"></a><span data-ttu-id="3c45b-102">Nasıl yapılır: Hizmet Sözleşmelerinde Hata Bildirme</span><span class="sxs-lookup"><span data-stu-id="3c45b-102">How to: Declare Faults in Service Contracts</span></span>
<span data-ttu-id="3c45b-103">Hata koşullarını ortaya çıktığında yönetilen kodda özel durumlar.</span><span class="sxs-lookup"><span data-stu-id="3c45b-103">In managed code, exceptions are thrown when error conditions occur.</span></span> <span data-ttu-id="3c45b-104">Windows Communication Foundation (WCF) uygulamalar, ancak hangi hata bilgilerini hizmet sözleşmesi, SOAP Hataları bildirerek istemcilere döndürülen hizmet sözleşmelerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="3c45b-104">In Windows Communication Foundation (WCF) applications, however, service contracts specify what error information is returned to clients by declaring SOAP faults in the service contract.</span></span> <span data-ttu-id="3c45b-105">Özel durumlar ve hatalar arasındaki ilişkiyi genel bakış için bkz. [belirtme ve işleme hataları sözleşme ve hizmetlerde](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="3c45b-105">For an overview of the relationship between exceptions and faults, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
### <a name="create-a-service-contract-that-specifies-a-soap-fault"></a><span data-ttu-id="3c45b-106">Bir SOAP hatasını belirten bir hizmet sözleşmesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="3c45b-106">Create a service contract that specifies a SOAP fault</span></span>  
  
1.  <span data-ttu-id="3c45b-107">En az bir işlem içeren bir hizmet sözleşmesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3c45b-107">Create a service contract that contains at least one operation.</span></span> <span data-ttu-id="3c45b-108">Bir örnek için bkz [nasıl yapılır: Bir hizmet sözleşmesini tanımlama](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="3c45b-108">For an example, see [How to: Define a Service Contract](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span>  
  
2.  <span data-ttu-id="3c45b-109">Bir hata durumu hakkında bildirim almak istemcileri bekleyebileceğiniz belirtebileceğiniz bir işlem seçin.</span><span class="sxs-lookup"><span data-stu-id="3c45b-109">Select an operation that can specify an error condition about which clients can expect to be notified.</span></span> <span data-ttu-id="3c45b-110">Hangi hata koşulları istemcilere SOAP hataları döndürüyor Yasla karar vermek için bkz: [belirtme ve işleme hataları sözleşme ve hizmetlerde](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="3c45b-110">To decide which error conditions justify returning SOAP faults to clients, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
3.  <span data-ttu-id="3c45b-111">Geçerli bir <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> seçili işlemi ve oluşturucuya seri hale getirilebilir bir hata türü geçişi.</span><span class="sxs-lookup"><span data-stu-id="3c45b-111">Apply a <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> to the selected operation and pass a serializable fault type to the constructor.</span></span> <span data-ttu-id="3c45b-112">Oluşturma ve serializable türler kullanma hakkında daha fazla ayrıntı için bkz. [hizmet sözleşmelerinde veri aktarımı belirtme](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="3c45b-112">For details about creating and using serializable types, see [Specifying Data Transfer in Service Contracts](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).</span></span> <span data-ttu-id="3c45b-113">Aşağıdaki örnek olduğunu belirtmek gösterilmektedir `SampleMethod` işlemi sonuçlanabilir bir `GreetingFault`.</span><span class="sxs-lookup"><span data-stu-id="3c45b-113">The following example shows how to specify that the `SampleMethod` operation can result in a `GreetingFault`.</span></span>  
  
     [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
     [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]  
  
4.  <span data-ttu-id="3c45b-114">Sözleşme istemcilere hata koşulları iletişim kuran tüm işlemler için 2 ve 3. adımları tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="3c45b-114">Repeat steps 2 and 3 for all operations in the contract that communicate error conditions to clients.</span></span>  
  
## <a name="implementing-an-operation-to-return-a-specified-soap-fault"></a><span data-ttu-id="3c45b-115">Belirtilen SOAP hatası döndürmek için bir işlem uygulama</span><span class="sxs-lookup"><span data-stu-id="3c45b-115">Implementing an Operation to Return a Specified SOAP Fault</span></span>  
 <span data-ttu-id="3c45b-116">Bir işlemi belirli bir SOAP hatası (yukarıdaki yordamı gibi) bir hata koşulu çağıran bir uygulama için iletişim kurmak için döndürülebilir olduğunu belirttiğinde, sonraki adımda bu belirtimini uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="3c45b-116">Once an operation has specified that a specific SOAP fault can be returned (such as in the preceding procedure) to communicate an error condition to a calling application, the next step is to implement that specification.</span></span>  
  
#### <a name="throw-the-specified-soap-fault-in-the-operation"></a><span data-ttu-id="3c45b-117">Belirtilen bir SOAP hatası işlem içinde özel durum</span><span class="sxs-lookup"><span data-stu-id="3c45b-117">Throw the specified SOAP fault in the operation</span></span>  
  
1.  <span data-ttu-id="3c45b-118">Olduğunda bir <xref:System.ServiceModel.FaultContractAttribute>-yeni bir durum, bir işlem belirtilen hata koşulu ortaya <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> tür parametresi olduğu belirtilen bir SOAP hatası.</span><span class="sxs-lookup"><span data-stu-id="3c45b-118">When a <xref:System.ServiceModel.FaultContractAttribute>-specified error condition occurs in an operation, throw a new <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> where the specified SOAP fault is the type parameter.</span></span> <span data-ttu-id="3c45b-119">Aşağıdaki örnekte throw gösterilmektedir `GreetingFault` içinde `SampleMethod` önceki yordamdaki ve aşağıdaki kod bölümünde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="3c45b-119">The following example shows how to throw the `GreetingFault` in the `SampleMethod` shown in the preceding procedure and in the following Code section.</span></span>  
  
     [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
     [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="3c45b-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="3c45b-120">Example</span></span>  
 <span data-ttu-id="3c45b-121">Aşağıdaki kod örneği belirten tek bir işlem uygulaması gösterir bir `GreetingFault` için `SampleMethod` işlemi.</span><span class="sxs-lookup"><span data-stu-id="3c45b-121">The following code example shows an implementation of a single operation that specifies a `GreetingFault` for the `SampleMethod` operation.</span></span>  
  
 [!code-csharp[FaultContractAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#1)]
 [!code-vb[FaultContractAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3c45b-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c45b-122">See also</span></span>

- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
