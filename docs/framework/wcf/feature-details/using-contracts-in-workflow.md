---
title: İş Akışında Sözleşmeleri Kullanma
ms.date: 03/30/2017
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
ms.openlocfilehash: def100f9483ea9ac8bf1aa3285d76edccffb030a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595017"
---
# <a name="using-contracts-in-workflow"></a><span data-ttu-id="1ffde-102">İş Akışında Sözleşmeleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="1ffde-102">Using Contracts in Workflow</span></span>
<span data-ttu-id="1ffde-103">Bir hizmet uygularken, hizmeti ve gönderdiği verileri tanımlayan bir dizi sözleşme tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="1ffde-103">When implementing a service, you define a number of contracts that describe the service and the data that it sends and receives.</span></span> <span data-ttu-id="1ffde-104">Veriler veri sözleşmeleri ve ileti sözleşmeleri olarak temsil edilir; WCF ve Workflow Hizmetleri, hizmet açıklamalarının parçası olarak veri sözleşmesi ve ileti sözleşmesi tanımlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="1ffde-104">The data is represented as data contracts and message contracts; both WCF and workflow services use data contract and message contract definitions as part of service descriptions.</span></span> <span data-ttu-id="1ffde-105">Hizmet, hizmetin işlemlerini anlatmak için meta verileri (WSDL biçiminde) kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="1ffde-105">The service itself exposes metadata (in the form of WSDL) in order to describe the operations of the service.</span></span> <span data-ttu-id="1ffde-106">WCF 'de hizmet sözleşmeleri ve işlem sözleşmeleri, hizmeti ve desteklediği işlemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1ffde-106">In WCF, service contracts and operation contracts define the service and the operations it supports.</span></span> <span data-ttu-id="1ffde-107">Ancak, bir iş akışı hizmetinde, bu sözleşmeler iş sürecinin bir parçasıdır; Bunlar, anlaşma çıkarımı adlı bir işlem tarafından meta verilerde kullanıma sunulur.</span><span class="sxs-lookup"><span data-stu-id="1ffde-107">However, in a workflow service, these contracts are part of the business process itself; they are exposed in metadata by a process called contract inference.</span></span>  
  
## <a name="contract-inference"></a><span data-ttu-id="1ffde-108">Sözleşme çıkarımı</span><span class="sxs-lookup"><span data-stu-id="1ffde-108">Contract Inference</span></span>  
 <span data-ttu-id="1ffde-109">Bir iş akışı hizmeti kullanılarak barındırıldığı zaman, iş akışı <xref:System.ServiceModel.Activities.WorkflowServiceHost> tanımı incelenir ve iş akışında bulunan mesajlaşma etkinlikleri kümesine göre bir sözleşme oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1ffde-109">When a workflow service is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, the workflow definition is examined and a contract is generated based on the set of messaging activities found in the workflow.</span></span> <span data-ttu-id="1ffde-110">Aşağıdaki etkinlikler ve özellikler, sözleşmeyi oluşturmak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="1ffde-110">In particular the following activities and properties are used to generate the contract:</span></span>  
  
 <span data-ttu-id="1ffde-111"><xref:System.ServiceModel.Activities.Receive>Etkinlik</span><span class="sxs-lookup"><span data-stu-id="1ffde-111"><xref:System.ServiceModel.Activities.Receive> Activity</span></span>  
  
- <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
- <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
- <xref:System.ServiceModel.Activities.Receive.Action%2A>

 <span data-ttu-id="1ffde-112"><xref:System.ServiceModel.Activities.SendReply>Etkinlik</span><span class="sxs-lookup"><span data-stu-id="1ffde-112"><xref:System.ServiceModel.Activities.SendReply> Activity</span></span>  
  
- <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <span data-ttu-id="1ffde-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope>Etkinlik</span><span class="sxs-lookup"><span data-stu-id="1ffde-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Activity</span></span>  
  
 <span data-ttu-id="1ffde-114">Sözleşme çıkarımı nihai sonucu, WCF hizmeti ve işlem sözleşmeleri ile aynı veri yapılarını kullanan hizmetin bir açıklamasıdır.</span><span class="sxs-lookup"><span data-stu-id="1ffde-114">The end result of contract inference is a description of the service using the same data structures as WCF service and operation contracts.</span></span> <span data-ttu-id="1ffde-115">Bu bilgiler daha sonra iş akışı hizmeti için WSDL 'yi göstermek üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1ffde-115">This information is then used to expose WSDL for the workflow service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ffde-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ffde-116">See also</span></span>

- [<span data-ttu-id="1ffde-117">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="1ffde-117">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="1ffde-118">Mesajlaşma Etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="1ffde-118">Messaging Activities</span></span>](messaging-activities.md)
- [<span data-ttu-id="1ffde-119">Nasıl yapılır: Mesajlaşma Etkinlikleriyle İş Akışı Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1ffde-119">How to: Create a Workflow Service with Messaging Activities</span></span>](how-to-create-a-workflow-service-with-messaging-activities.md)
- [<span data-ttu-id="1ffde-120">Nasıl yapılır: Var olan hizmet anlaşmasını kullanan iş akışı hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="1ffde-120">How to: Create a workflow service that consumes an existing service contract</span></span>](../../windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
