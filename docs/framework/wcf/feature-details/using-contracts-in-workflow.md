---
title: İş Akışında Sözleşmeleri Kullanma
ms.date: 03/30/2017
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
ms.openlocfilehash: dd35766011c412acc937eed75d523a0574f6b9cb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61918547"
---
# <a name="using-contracts-in-workflow"></a><span data-ttu-id="e870c-102">İş Akışında Sözleşmeleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="e870c-102">Using Contracts in Workflow</span></span>
<span data-ttu-id="e870c-103">Bir hizmet uygularken, bir dizi hizmet ve veri gönderen ve alan açıklayan sözleşme tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="e870c-103">When implementing a service, you define a number of contracts that describe the service and the data that it sends and receives.</span></span> <span data-ttu-id="e870c-104">Verileri veri sözleşmeleri ve ileti sözleşmeleri temsil edilir; WCF hem iş akışı Hizmetleri, veri sözleşme ve ileti anlaşması tanımlarını hizmet açıklamaları bir parçası olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="e870c-104">The data is represented as data contracts and message contracts; both WCF and workflow services use data contract and message contract definitions as part of service descriptions.</span></span> <span data-ttu-id="e870c-105">Hizmet, hizmet işlemleri tanımlamak için meta verileri (WSDL biçiminde) kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="e870c-105">The service itself exposes metadata (in the form of WSDL) in order to describe the operations of the service.</span></span> <span data-ttu-id="e870c-106">WCF'de, hizmet sözleşmeleri ve işlem sözleşmeleri hizmeti ve desteklediği işlemleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="e870c-106">In WCF, service contracts and operation contracts define the service and the operations it supports.</span></span> <span data-ttu-id="e870c-107">Ancak, bir iş akışı hizmetinde, bu sözleşme iş işleminin bir parçası olan; Bunlar, meta verilerde sözleşme çıkarımı olarak adlandırılan bir işlem tarafından sunulur.</span><span class="sxs-lookup"><span data-stu-id="e870c-107">However, in a workflow service, these contracts are part of the business process itself; they are exposed in metadata by a process called contract inference.</span></span>  
  
## <a name="contract-inference"></a><span data-ttu-id="e870c-108">Sözleşme çıkarımı</span><span class="sxs-lookup"><span data-stu-id="e870c-108">Contract Inference</span></span>  
 <span data-ttu-id="e870c-109">Bir iş akışı hizmeti kullanarak barındırıldığında <xref:System.ServiceModel.Activities.WorkflowServiceHost>, iş akışı tanımı incelenir ve sözleşme Mesajlaşma etkinlikleriyle iş akışında bulunan kümesi temel alınarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e870c-109">When a workflow service is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, the workflow definition is examined and a contract is generated based on the set of messaging activities found in the workflow.</span></span> <span data-ttu-id="e870c-110">Özellikle aşağıdaki etkinlikleri ve özellikleri sözleşme oluşturmak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="e870c-110">In particular the following activities and properties are used to generate the contract:</span></span>  
  
 <span data-ttu-id="e870c-111"><xref:System.ServiceModel.Activities.Receive> Etkinlik</span><span class="sxs-lookup"><span data-stu-id="e870c-111"><xref:System.ServiceModel.Activities.Receive> Activity</span></span>  
  
- <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
- <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
- <xref:System.ServiceModel.Activities.Receive.Action%2A>   
 
 <span data-ttu-id="e870c-112"><xref:System.ServiceModel.Activities.SendReply> Etkinlik</span><span class="sxs-lookup"><span data-stu-id="e870c-112"><xref:System.ServiceModel.Activities.SendReply> Activity</span></span>  
  
- <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <span data-ttu-id="e870c-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Etkinlik</span><span class="sxs-lookup"><span data-stu-id="e870c-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Activity</span></span>  
  
 <span data-ttu-id="e870c-114">Sözleşme çıkarımı nihai sonucu WCF hizmeti ve işlem sözleşmeleri aynı veri yapılarını kullanarak hizmeti açıklamasıdır.</span><span class="sxs-lookup"><span data-stu-id="e870c-114">The end result of contract inference is a description of the service using the same data structures as WCF service and operation contracts.</span></span> <span data-ttu-id="e870c-115">Bu bilgiler, sonra iş akışı hizmeti için WSDL göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e870c-115">This information is then used to expose WSDL for the workflow service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e870c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e870c-116">See also</span></span>

- [<span data-ttu-id="e870c-117">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="e870c-117">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="e870c-118">Mesajlaşma Etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="e870c-118">Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
- [<span data-ttu-id="e870c-119">Nasıl yapılır: Mesajlaşma etkinlikleriyle iş akışı hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="e870c-119">How to: Create a Workflow Service with Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)
- [<span data-ttu-id="e870c-120">Nasıl yapılır: Mevcut bir hizmet anlaşmasını kullanan iş akışı hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="e870c-120">How to: Create a workflow service that consumes an existing service contract</span></span>](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
