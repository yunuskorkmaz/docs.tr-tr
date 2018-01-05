---
title: "İş Akışında Sözleşmeleri Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ff40241bd48a4355738ca93ef2c80ceec55db11
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="using-contracts-in-workflow"></a><span data-ttu-id="e4593-102">İş Akışında Sözleşmeleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="e4593-102">Using Contracts in Workflow</span></span>
<span data-ttu-id="e4593-103">Bir hizmet uygularken, bir dizi hizmet ve gönderen ve alan verileri açıklayan sözleşme tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="e4593-103">When implementing a service, you define a number of contracts that describe the service and the data that it sends and receives.</span></span> <span data-ttu-id="e4593-104">Verileri veri sözleşmeleri ve ileti sözleşmeleri temsil edilir; her ikisi de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ve iş akışı Hizmetleri veri sözleşmesi ve ileti sözleşmesi tanımlarını hizmeti açıklamaları bir parçası olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="e4593-104">The data is represented as data contracts and message contracts; both [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and workflow services use data contract and message contract definitions as part of service descriptions.</span></span> <span data-ttu-id="e4593-105">Hizmet, hizmet işlemleri tanımlamak için meta verileri (WSDL biçiminde) gösterir.</span><span class="sxs-lookup"><span data-stu-id="e4593-105">The service itself exposes metadata (in the form of WSDL) in order to describe the operations of the service.</span></span> <span data-ttu-id="e4593-106">İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], hizmet sözleşmeleri ve işlem sözleşmeleri hizmeti ve desteklediği işlemleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="e4593-106">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], service contracts and operation contracts define the service and the operations it supports.</span></span> <span data-ttu-id="e4593-107">Ancak, bir iş akışı hizmetinde bu sözleşmeleri iş sürecinin parçası olan; Bunlar, meta verilerde sözleşme çıkarım adlı bir işlem tarafından sunulur.</span><span class="sxs-lookup"><span data-stu-id="e4593-107">However, in a workflow service, these contracts are part of the business process itself; they are exposed in metadata by a process called contract inference.</span></span>  
  
## <a name="contract-inference"></a><span data-ttu-id="e4593-108">Sözleşme çıkarımı</span><span class="sxs-lookup"><span data-stu-id="e4593-108">Contract Inference</span></span>  
 <span data-ttu-id="e4593-109">Bir iş akışı hizmeti kullanarak barındırıldığında <xref:System.ServiceModel.Activities.WorkflowServiceHost>, iş akışı tanımı incelenir ve bir sözleşme Mesajlaşma etkinlikleriyle iş akışında bulunan kümesini temel alınarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e4593-109">When a workflow service is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, the workflow definition is examined and a contract is generated based on the set of messaging activities found in the workflow.</span></span> <span data-ttu-id="e4593-110">Özellikle aşağıdaki etkinlikleri ve özellikleri sözleşme oluşturmak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="e4593-110">In particular the following activities and properties are used to generate the contract:</span></span>  
  
 <span data-ttu-id="e4593-111"><xref:System.ServiceModel.Activities.Receive>Etkinlik</span><span class="sxs-lookup"><span data-stu-id="e4593-111"><xref:System.ServiceModel.Activities.Receive> Activity</span></span>  
  
-   <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
-   <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
-   <xref:System.ServiceModel.Activities.Receive.Action%2A>   
 
 <span data-ttu-id="e4593-112"><xref:System.ServiceModel.Activities.SendReply>Etkinlik</span><span class="sxs-lookup"><span data-stu-id="e4593-112"><xref:System.ServiceModel.Activities.SendReply> Activity</span></span>  
  
-   <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <span data-ttu-id="e4593-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope>Etkinlik</span><span class="sxs-lookup"><span data-stu-id="e4593-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Activity</span></span>  
  
 <span data-ttu-id="e4593-114">Sözleşme çıkarım nihai sonucu WCF hizmeti ve işlem sözleşmeleri aynı veri yapılarını kullanarak hizmet açıklamasıdır.</span><span class="sxs-lookup"><span data-stu-id="e4593-114">The end result of contract inference is a description of the service using the same data structures as WCF service and operation contracts.</span></span> <span data-ttu-id="e4593-115">Bu bilgiler daha sonra WSDL için iş akışı hizmeti kullanıma sunmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e4593-115">This information is then used to expose WSDL for the workflow service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4593-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e4593-116">See Also</span></span>  
 [<span data-ttu-id="e4593-117">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="e4593-117">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="e4593-118">Mesajlaşma Etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="e4593-118">Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/messaging-activities.md)  
 [<span data-ttu-id="e4593-119">Nasıl yapılır: Mesajlaşma Etkinlikleriyle İş Akışı Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e4593-119">How to: Create a Workflow Service with Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)  
 [<span data-ttu-id="e4593-120">Nasıl yapılır: Var olan hizmet anlaşmasını kullanan iş akışı hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="e4593-120">How to: Create a workflow service that consumes an existing service contract</span></span>](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
