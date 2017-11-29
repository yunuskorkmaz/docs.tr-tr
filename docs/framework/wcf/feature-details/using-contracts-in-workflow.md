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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1c84483b2ca18d63f20e64a62bb757e244db9b24
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-contracts-in-workflow"></a><span data-ttu-id="2654c-102">İş Akışında Sözleşmeleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="2654c-102">Using Contracts in Workflow</span></span>
<span data-ttu-id="2654c-103">Bir hizmet uygularken, bir dizi hizmet ve gönderen ve alan verileri açıklayan sözleşme tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="2654c-103">When implementing a service, you define a number of contracts that describe the service and the data that it sends and receives.</span></span> <span data-ttu-id="2654c-104">Verileri veri sözleşmeleri ve ileti sözleşmeleri temsil edilir; her ikisi de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ve iş akışı Hizmetleri veri sözleşmesi ve ileti sözleşmesi tanımlarını hizmeti açıklamaları bir parçası olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="2654c-104">The data is represented as data contracts and message contracts; both [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and workflow services use data contract and message contract definitions as part of service descriptions.</span></span> <span data-ttu-id="2654c-105">Hizmet, hizmet işlemleri tanımlamak için meta verileri (WSDL biçiminde) gösterir.</span><span class="sxs-lookup"><span data-stu-id="2654c-105">The service itself exposes metadata (in the form of WSDL) in order to describe the operations of the service.</span></span> <span data-ttu-id="2654c-106">İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], hizmet sözleşmeleri ve işlem sözleşmeleri hizmeti ve desteklediği işlemleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="2654c-106">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], service contracts and operation contracts define the service and the operations it supports.</span></span> <span data-ttu-id="2654c-107">Ancak, bir iş akışı hizmetinde bu sözleşmeleri iş sürecinin parçası olan; Bunlar, meta verilerde sözleşme çıkarım adlı bir işlem tarafından sunulur.</span><span class="sxs-lookup"><span data-stu-id="2654c-107">However, in a workflow service, these contracts are part of the business process itself; they are exposed in metadata by a process called contract inference.</span></span>  
  
## <a name="contract-inference"></a><span data-ttu-id="2654c-108">Sözleşme çıkarımı</span><span class="sxs-lookup"><span data-stu-id="2654c-108">Contract Inference</span></span>  
 <span data-ttu-id="2654c-109">Bir iş akışı hizmeti kullanarak barındırıldığında <xref:System.ServiceModel.Activities.WorkflowServiceHost>, iş akışı tanımı incelenir ve bir sözleşme Mesajlaşma etkinlikleriyle iş akışında bulunan kümesini temel alınarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2654c-109">When a workflow service is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, the workflow definition is examined and a contract is generated based on the set of messaging activities found in the workflow.</span></span> <span data-ttu-id="2654c-110">Özellikle aşağıdaki etkinlikleri ve özellikleri sözleşme oluşturmak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="2654c-110">In particular the following activities and properties are used to generate the contract:</span></span>  
  
 <span data-ttu-id="2654c-111"><xref:System.ServiceModel.Activities.Receive>Etkinlik</span><span class="sxs-lookup"><span data-stu-id="2654c-111"><xref:System.ServiceModel.Activities.Receive> Activity</span></span>  
  
-   <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
-   <!--zz <xref:System.ServiceModel.Activities.Receive.OperationContractName%2A>  --> `System.ServiceModel.Activities.Receive.OperationContractName`
  
-   <xref:System.ServiceModel.Activities.Receive.Action%2A>  
  
-   <!--zz <xref:System.ServiceModel.Activities.Receive.ValueType%2A> --> `System.ServiceModel.Activities.Receive.ValueType`
  
 <span data-ttu-id="2654c-112"><xref:System.ServiceModel.Activities.SendReply>Etkinlik</span><span class="sxs-lookup"><span data-stu-id="2654c-112"><xref:System.ServiceModel.Activities.SendReply> Activity</span></span>  
  
-   <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
-   <!--zz <xref:System.ServiceModel.Activities.SendReply.ValueType%2A>-->  `System.ServiceModel.Activities.SendReply.ValueType`
  
 <span data-ttu-id="2654c-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope>Etkinlik</span><span class="sxs-lookup"><span data-stu-id="2654c-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Activity</span></span>  
  
 <span data-ttu-id="2654c-114">Sözleşme çıkarım nihai sonucu WCF hizmeti ve işlem sözleşmeleri aynı veri yapılarını kullanarak hizmet açıklamasıdır.</span><span class="sxs-lookup"><span data-stu-id="2654c-114">The end result of contract inference is a description of the service using the same data structures as WCF service and operation contracts.</span></span> <span data-ttu-id="2654c-115">Bu bilgiler daha sonra WSDL için iş akışı hizmeti kullanıma sunmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2654c-115">This information is then used to expose WSDL for the workflow service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2654c-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2654c-116">See Also</span></span>  
 [<span data-ttu-id="2654c-117">İş akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="2654c-117">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="2654c-118">Mesajlaşma etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="2654c-118">Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/messaging-activities.md)  
 [<span data-ttu-id="2654c-119">Nasıl yapılır: Mesajlaşma etkinlikleriyle iş akışı hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="2654c-119">How to: Create a Workflow Service with Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)  
 [<span data-ttu-id="2654c-120">Nasıl yapılır: varolan bir hizmet sözleşmesini tüketen bir iş akışı hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="2654c-120">How to: Create a workflow service that consumes an existing service contract</span></span>](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
