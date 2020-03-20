---
title: İş Akışında Sözleşmeleri Kullanma
ms.date: 03/30/2017
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
ms.openlocfilehash: 9f967d75a8e9d24fcfac8b7376a3d4840fba52f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184268"
---
# <a name="using-contracts-in-workflow"></a><span data-ttu-id="63a59-102">İş Akışında Sözleşmeleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="63a59-102">Using Contracts in Workflow</span></span>
<span data-ttu-id="63a59-103">Bir hizmeti uygularken, hizmeti ve gönderdiği ve aldığı verileri açıklayan bir dizi sözleşme tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="63a59-103">When implementing a service, you define a number of contracts that describe the service and the data that it sends and receives.</span></span> <span data-ttu-id="63a59-104">Veriler veri sözleşmeleri ve ileti sözleşmeleri olarak temsil edilir; hem WCF hem de iş akışı hizmetleri, hizmet açıklamalarının bir parçası olarak veri sözleşmesi ve ileti sözleşmesi tanımlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="63a59-104">The data is represented as data contracts and message contracts; both WCF and workflow services use data contract and message contract definitions as part of service descriptions.</span></span> <span data-ttu-id="63a59-105">Hizmetin kendisi, hizmetin işlemlerini açıklamak için meta verileri (WSDL biçiminde) ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="63a59-105">The service itself exposes metadata (in the form of WSDL) in order to describe the operations of the service.</span></span> <span data-ttu-id="63a59-106">WCF'de hizmet sözleşmeleri ve işletme sözleşmeleri hizmeti ve desteklediği işlemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="63a59-106">In WCF, service contracts and operation contracts define the service and the operations it supports.</span></span> <span data-ttu-id="63a59-107">Ancak, bir iş akışı hizmetinde, bu sözleşmeler iş sürecinin bir parçasıdır; sözleşme çıkarımı adı verilen bir işlemle meta verilerde ortaya çıkarlar.</span><span class="sxs-lookup"><span data-stu-id="63a59-107">However, in a workflow service, these contracts are part of the business process itself; they are exposed in metadata by a process called contract inference.</span></span>  
  
## <a name="contract-inference"></a><span data-ttu-id="63a59-108">Sözleşme Çıkarımı</span><span class="sxs-lookup"><span data-stu-id="63a59-108">Contract Inference</span></span>  
 <span data-ttu-id="63a59-109">İş akışı hizmeti kullanılarak <xref:System.ServiceModel.Activities.WorkflowServiceHost>barındırıldığında, iş akışı tanımı incelenir ve iş akışında bulunan ileti etkinlikleri kümesine göre bir sözleşme oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="63a59-109">When a workflow service is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, the workflow definition is examined and a contract is generated based on the set of messaging activities found in the workflow.</span></span> <span data-ttu-id="63a59-110">Özellikle aşağıdaki faaliyetler ve özellikler sözleşme oluşturmak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="63a59-110">In particular the following activities and properties are used to generate the contract:</span></span>  
  
 <span data-ttu-id="63a59-111"><xref:System.ServiceModel.Activities.Receive>Etkinlik</span><span class="sxs-lookup"><span data-stu-id="63a59-111"><xref:System.ServiceModel.Activities.Receive> Activity</span></span>  
  
- <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
- <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
- <xref:System.ServiceModel.Activities.Receive.Action%2A>

 <span data-ttu-id="63a59-112"><xref:System.ServiceModel.Activities.SendReply>Etkinlik</span><span class="sxs-lookup"><span data-stu-id="63a59-112"><xref:System.ServiceModel.Activities.SendReply> Activity</span></span>  
  
- <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <span data-ttu-id="63a59-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope>Etkinlik</span><span class="sxs-lookup"><span data-stu-id="63a59-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Activity</span></span>  
  
 <span data-ttu-id="63a59-114">Sözleşme çıkarımının sonucu, WCF hizmeti ve işlem sözleşmeleri ile aynı veri yapılarını kullanan hizmetin açıklamasıdır.</span><span class="sxs-lookup"><span data-stu-id="63a59-114">The end result of contract inference is a description of the service using the same data structures as WCF service and operation contracts.</span></span> <span data-ttu-id="63a59-115">Bu bilgiler daha sonra iş akışı hizmeti için WSDL'yi ortaya çıkarmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="63a59-115">This information is then used to expose WSDL for the workflow service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63a59-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63a59-116">See also</span></span>

- [<span data-ttu-id="63a59-117">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="63a59-117">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="63a59-118">Mesajlaşma Etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="63a59-118">Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
- [<span data-ttu-id="63a59-119">Nasıl yapılır: Mesajlaşma Etkinlikleriyle İş Akışı Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="63a59-119">How to: Create a Workflow Service with Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)
- [<span data-ttu-id="63a59-120">Nasıl yapılır: Var olan hizmet anlaşmasını kullanan iş akışı hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="63a59-120">How to: Create a workflow service that consumes an existing service contract</span></span>](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
