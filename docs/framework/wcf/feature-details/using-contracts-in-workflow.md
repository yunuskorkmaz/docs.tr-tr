---
title: İş Akışında Sözleşmeleri Kullanma
ms.date: 03/30/2017
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
ms.openlocfilehash: dd35766011c412acc937eed75d523a0574f6b9cb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150065"
---
# <a name="using-contracts-in-workflow"></a><span data-ttu-id="d2592-102">İş Akışında Sözleşmeleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="d2592-102">Using Contracts in Workflow</span></span>
<span data-ttu-id="d2592-103">Bir hizmet uygularken, bir dizi hizmet ve veri gönderen ve alan açıklayan sözleşme tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="d2592-103">When implementing a service, you define a number of contracts that describe the service and the data that it sends and receives.</span></span> <span data-ttu-id="d2592-104">Verileri veri sözleşmeleri ve ileti sözleşmeleri temsil edilir; WCF hem iş akışı Hizmetleri, veri sözleşme ve ileti anlaşması tanımlarını hizmet açıklamaları bir parçası olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2592-104">The data is represented as data contracts and message contracts; both WCF and workflow services use data contract and message contract definitions as part of service descriptions.</span></span> <span data-ttu-id="d2592-105">Hizmet, hizmet işlemleri tanımlamak için meta verileri (WSDL biçiminde) kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="d2592-105">The service itself exposes metadata (in the form of WSDL) in order to describe the operations of the service.</span></span> <span data-ttu-id="d2592-106">WCF'de, hizmet sözleşmeleri ve işlem sözleşmeleri hizmeti ve desteklediği işlemleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="d2592-106">In WCF, service contracts and operation contracts define the service and the operations it supports.</span></span> <span data-ttu-id="d2592-107">Ancak, bir iş akışı hizmetinde, bu sözleşme iş işleminin bir parçası olan; Bunlar, meta verilerde sözleşme çıkarımı olarak adlandırılan bir işlem tarafından sunulur.</span><span class="sxs-lookup"><span data-stu-id="d2592-107">However, in a workflow service, these contracts are part of the business process itself; they are exposed in metadata by a process called contract inference.</span></span>  
  
## <a name="contract-inference"></a><span data-ttu-id="d2592-108">Sözleşme çıkarımı</span><span class="sxs-lookup"><span data-stu-id="d2592-108">Contract Inference</span></span>  
 <span data-ttu-id="d2592-109">Bir iş akışı hizmeti kullanarak barındırıldığında <xref:System.ServiceModel.Activities.WorkflowServiceHost>, iş akışı tanımı incelenir ve sözleşme Mesajlaşma etkinlikleriyle iş akışında bulunan kümesi temel alınarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d2592-109">When a workflow service is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, the workflow definition is examined and a contract is generated based on the set of messaging activities found in the workflow.</span></span> <span data-ttu-id="d2592-110">Özellikle aşağıdaki etkinlikleri ve özellikleri sözleşme oluşturmak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="d2592-110">In particular the following activities and properties are used to generate the contract:</span></span>  
  
 <xref:System.ServiceModel.Activities.Receive> <span data-ttu-id="d2592-111">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="d2592-111">Activity</span></span>  
  
-   <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
-   <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
-   <xref:System.ServiceModel.Activities.Receive.Action%2A>   
 
 <xref:System.ServiceModel.Activities.SendReply> <span data-ttu-id="d2592-112">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="d2592-112">Activity</span></span>  
  
-   <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope> <span data-ttu-id="d2592-113">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="d2592-113">Activity</span></span>  
  
 <span data-ttu-id="d2592-114">Sözleşme çıkarımı nihai sonucu WCF hizmeti ve işlem sözleşmeleri aynı veri yapılarını kullanarak hizmeti açıklamasıdır.</span><span class="sxs-lookup"><span data-stu-id="d2592-114">The end result of contract inference is a description of the service using the same data structures as WCF service and operation contracts.</span></span> <span data-ttu-id="d2592-115">Bu bilgiler, sonra iş akışı hizmeti için WSDL göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d2592-115">This information is then used to expose WSDL for the workflow service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2592-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2592-116">See also</span></span>

- [<span data-ttu-id="d2592-117">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="d2592-117">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="d2592-118">Mesajlaşma Etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="d2592-118">Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
- [<span data-ttu-id="d2592-119">Nasıl yapılır: Mesajlaşma Etkinlikleriyle İş Akışı Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d2592-119">How to: Create a Workflow Service with Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)
- [<span data-ttu-id="d2592-120">Nasıl yapılır: Var olan hizmet anlaşmasını kullanan iş akışı hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="d2592-120">How to: Create a workflow service that consumes an existing service contract</span></span>](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
