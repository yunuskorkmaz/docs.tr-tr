---
title: 'Nasıl yapılır: Hizmet Sözleşmelerinde Hata Bildirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e8da98e7-d22f-4f60-ac82-3fb0928a353f
ms.openlocfilehash: 6f08ef6eb62b31b0969779d51d0a068145a23fc0
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971962"
---
# <a name="how-to-declare-faults-in-service-contracts"></a><span data-ttu-id="1ea7f-102">Nasıl yapılır: Hizmet Sözleşmelerinde Hata Bildirme</span><span class="sxs-lookup"><span data-stu-id="1ea7f-102">How to: Declare Faults in Service Contracts</span></span>

<span data-ttu-id="1ea7f-103">Yönetilen kodda, hata koşulları oluştuğunda özel durumlar oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1ea7f-103">In managed code, exceptions are thrown when error conditions occur.</span></span> <span data-ttu-id="1ea7f-104">Ancak Windows Communication Foundation (WCF) uygulamalarında, hizmet sözleşmeleri, hizmet sözleşmesinde SOAP hataları bildirerek istemcilere hangi hata bilgilerinin döndürüleceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1ea7f-104">In Windows Communication Foundation (WCF) applications, however, service contracts specify what error information is returned to clients by declaring SOAP faults in the service contract.</span></span> <span data-ttu-id="1ea7f-105">Özel durumlar ve hatalar arasındaki ilişkiye genel bakış için bkz. [anlaşmalar ve hizmetlerde hataları belirtme ve işleme](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="1ea7f-105">For an overview of the relationship between exceptions and faults, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>

## <a name="create-a-service-contract-that-specifies-a-soap-fault"></a><span data-ttu-id="1ea7f-106">SOAP hatası belirten bir hizmet sözleşmesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="1ea7f-106">Create a service contract that specifies a SOAP fault</span></span>

1. <span data-ttu-id="1ea7f-107">En az bir işlem içeren bir hizmet sözleşmesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1ea7f-107">Create a service contract that contains at least one operation.</span></span> <span data-ttu-id="1ea7f-108">Bir örnek için bkz [. nasıl yapılır: Bir hizmet sözleşmesi](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="1ea7f-108">For an example, see [How to: Define a Service Contract](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span>

2. <span data-ttu-id="1ea7f-109">Hangi istemcilere bildirilmesi beklendiğini belirten bir hata koşulu içerebilen bir işlem seçin.</span><span class="sxs-lookup"><span data-stu-id="1ea7f-109">Select an operation that can specify an error condition about which clients can expect to be notified.</span></span> <span data-ttu-id="1ea7f-110">İstemcilere SOAP hataları döndürmekte olan hata koşullarının belirlenmesi için bkz. [anlaşmalar ve hizmetlerde hataları belirtme ve işleme](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="1ea7f-110">To decide which error conditions justify returning SOAP faults to clients, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>

3. <span data-ttu-id="1ea7f-111"><xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> Seçili işleme uygulayın ve oluşturucuya seri hale getirilebilir bir hata türü geçirin.</span><span class="sxs-lookup"><span data-stu-id="1ea7f-111">Apply a <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> to the selected operation and pass a serializable fault type to the constructor.</span></span> <span data-ttu-id="1ea7f-112">Serileştirilebilir türler oluşturma ve kullanma hakkında ayrıntılı bilgi için bkz. [hizmet sözleşmeleri içinde veri aktarımı belirtme](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="1ea7f-112">For details about creating and using serializable types, see [Specifying Data Transfer in Service Contracts](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).</span></span> <span data-ttu-id="1ea7f-113">Aşağıdaki örnekte, `SampleMethod` işlemin bir `GreetingFault`ile sonuçlanabileceğini belirtme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1ea7f-113">The following example shows how to specify that the `SampleMethod` operation can result in a `GreetingFault`.</span></span>

     [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
     [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]

4. <span data-ttu-id="1ea7f-114">Sözleşmede hata koşullarını ileten tüm işlemler için adım 2 ve 3 ' ü tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="1ea7f-114">Repeat steps 2 and 3 for all operations in the contract that communicate error conditions to clients.</span></span>

## <a name="implementing-an-operation-to-return-a-specified-soap-fault"></a><span data-ttu-id="1ea7f-115">Belirtilen SOAP hatasını döndürmek için bir Işlem uygulama</span><span class="sxs-lookup"><span data-stu-id="1ea7f-115">Implementing an Operation to Return a Specified SOAP Fault</span></span>
 <span data-ttu-id="1ea7f-116">Bir işlem, bir hata koşulunu çağıran bir uygulamayla iletmek için belirli bir SOAP hatasının döndürülüp döndürülmeyeceğini (önceki yordamda olduğu gibi) belirledikten sonra, bir sonraki adım bu belirtimi uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="1ea7f-116">Once an operation has specified that a specific SOAP fault can be returned (such as in the preceding procedure) to communicate an error condition to a calling application, the next step is to implement that specification.</span></span>

### <a name="throw-the-specified-soap-fault-in-the-operation"></a><span data-ttu-id="1ea7f-117">İşlemde belirtilen SOAP hatasını oluştur</span><span class="sxs-lookup"><span data-stu-id="1ea7f-117">Throw the specified SOAP fault in the operation</span></span>

1. <span data-ttu-id="1ea7f-118">Bir işlemde <xref:System.ServiceModel.FaultContractAttribute>belirtilen bir hata koşulu oluştuğunda, belirtilen SOAP hatasının tür parametresi olduğu <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> yeni bir oluştur.</span><span class="sxs-lookup"><span data-stu-id="1ea7f-118">When a <xref:System.ServiceModel.FaultContractAttribute>-specified error condition occurs in an operation, throw a new <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> where the specified SOAP fault is the type parameter.</span></span> <span data-ttu-id="1ea7f-119">Aşağıdaki örnek, bir önceki yordamda ve aşağıdaki `GreetingFault` kod bölümünde `SampleMethod` gösterildiği içindeki ' ın nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1ea7f-119">The following example shows how to throw the `GreetingFault` in the `SampleMethod` shown in the preceding procedure and in the following Code section.</span></span>

     [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
     [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]

## <a name="example"></a><span data-ttu-id="1ea7f-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="1ea7f-120">Example</span></span>

<span data-ttu-id="1ea7f-121">Aşağıdaki kod örneği, `GreetingFault` `SampleMethod` işlem için bir öğesini belirten tek bir işlemin bir uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1ea7f-121">The following code example shows an implementation of a single operation that specifies a `GreetingFault` for the `SampleMethod` operation.</span></span>

[!code-csharp[FaultContractAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#1)]
[!code-vb[FaultContractAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#1)]

## <a name="see-also"></a><span data-ttu-id="1ea7f-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ea7f-122">See also</span></span>

- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
