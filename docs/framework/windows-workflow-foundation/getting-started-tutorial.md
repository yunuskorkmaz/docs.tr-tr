---
title: Tutorial2 Başlarken
ms.date: 03/30/2017
helpviewer_keywords:
- WF [WF], getting started
- Windows Workflow Foundation [WF], getting started
ms.assetid: c2d3585f-6b1a-4d4f-9865-bd7cd31c5d42
ms.openlocfilehash: 540765c09dceef583798ceaf1abf9f191f444697
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59217438"
---
# <a name="getting-started-tutorial"></a><span data-ttu-id="8a7bf-102">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="8a7bf-102">Getting Started Tutorial</span></span>
<span data-ttu-id="8a7bf-103">Bu bölüm, Windows Workflow Foundation (WF) uygulama programlama tanıtan izlenecek yol konuları kümesi içerir.</span><span class="sxs-lookup"><span data-stu-id="8a7bf-103">This section contains a set of walkthrough topics that introduce you to programming Windows Workflow Foundation (WF) applications.</span></span> <span data-ttu-id="8a7bf-104">Aşağıdaki konulardaki yordamları izleyerek, bir sayı tahminiyle gerçekleştirilen saldırı oyun bir uygulama oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="8a7bf-104">By following the procedures in these topics, you will build an application that is a number guessing game.</span></span> <span data-ttu-id="8a7bf-105">Öğreticinin ilk konu, iş akışı için gereken özel etkinlikler oluşturma adımlarında yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="8a7bf-105">The first topic in the tutorial leads you through the steps to create the custom activities required for the workflow.</span></span> <span data-ttu-id="8a7bf-106">İkinci konusunda bu etkinlikler, bir akış çizelgesi iş akışınıza yerleşik iş akışı etkinlikleri ve birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8a7bf-106">In the second topic, these activities are assembled along with built-in workflow activities into a flowchart workflow.</span></span> <span data-ttu-id="8a7bf-107">Üçüncü bölümüne ana uygulama iş akışı çalıştırmak için yapılandırılır ve son konu başlığında, Kalıcılık sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="8a7bf-107">In the third topic, the host application is configured to run the workflow, and in the final topic persistence is introduced.</span></span> <span data-ttu-id="8a7bf-108">Bu işlemin her adımından önceki adımları, bağlıdır, bu nedenle bunları sırada tamamlamanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="8a7bf-108">Each step in this process depends on the previous steps, so we recommend that you complete them in order.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8a7bf-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8a7bf-109">In This Section</span></span>  
 [<span data-ttu-id="8a7bf-110">Nasıl yapılır: Bir etkinlik oluşturma</span><span class="sxs-lookup"><span data-stu-id="8a7bf-110">How to: Create an Activity</span></span>](how-to-create-an-activity.md)  
 <span data-ttu-id="8a7bf-111">Öğesinden türetilen özel etkinlik oluşturma işlemini açıklamaktadır <xref:System.Activities.NativeActivity%601>ve nasıl etkinlik Tasarımcısı'nı kullanarak, bileşik bir etkinlik içinde yerleşik bir etkinlik ile birlikte bu etkinlik oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8a7bf-111">Describes how to create a custom activity that derives from <xref:System.Activities.NativeActivity%601>, and how to compose this activity along with a built-in activity into a composite activity using the activity designer.</span></span>  
  
 [<span data-ttu-id="8a7bf-112">Nasıl yapılır: Bir iş akışı oluşturma</span><span class="sxs-lookup"><span data-stu-id="8a7bf-112">How to: Create a Workflow</span></span>](how-to-create-a-workflow.md)  
 <span data-ttu-id="8a7bf-113">Yerleşik etkinlikler ve önceki öğreticide özel etkinlikler kullanarak akış çizelgesi, sıralı ve durum makine iş akışları oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="8a7bf-113">Describes how to create flowchart, sequential, and state machine workflows by using built-in activities and the custom activities from the preceding tutorial.</span></span>  
  
 [<span data-ttu-id="8a7bf-114">Nasıl yapılır: İş akışı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="8a7bf-114">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)  
 <span data-ttu-id="8a7bf-115">Nasıl bir iş akışı konak Ortamı'ndan çağırmak, veri ekleme çıkarma iş akışı iletmek ve yer işaretleri devam etme açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8a7bf-115">Describes how to invoke a workflow from a host environment, pass data into and out of a workflow, and how to resume bookmarks.</span></span>  
  
 [<span data-ttu-id="8a7bf-116">Nasıl yapılır: Oluşturma ve uzun süre çalışan iş akışı</span><span class="sxs-lookup"><span data-stu-id="8a7bf-116">How to: Create and Run a Long Running Workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md)  
 <span data-ttu-id="8a7bf-117">Bir iş akışı uygulamasını kalıcı eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="8a7bf-117">Describes how to add persistence to a workflow application.</span></span>  
  
 [<span data-ttu-id="8a7bf-118">Nasıl yapılır: Özel İzleme Katılımcısı oluşturma</span><span class="sxs-lookup"><span data-stu-id="8a7bf-118">How to: Create a Custom Tracking Participant</span></span>](how-to-create-a-custom-tracking-participant.md)  
 <span data-ttu-id="8a7bf-119">Özel İzleme katılımcı ve izleme profili oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="8a7bf-119">Describes how to create a custom tracking participant and tracking profile.</span></span>  
  
 [<span data-ttu-id="8a7bf-120">Nasıl yapılır: Birden çok sürümünü bir iş akışı yan yana barındırma</span><span class="sxs-lookup"><span data-stu-id="8a7bf-120">How to: Host Multiple Versions of a Workflow Side-by-Side</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)  
 <span data-ttu-id="8a7bf-121">Nasıl kullanılacağını açıklar `WorkflowIdentity` bir iş akışı yan yana birden çok sürümünü barındırmak için.</span><span class="sxs-lookup"><span data-stu-id="8a7bf-121">Describes how to use `WorkflowIdentity` to host multiple versions of a workflow side-by-side.</span></span>  
  
 [<span data-ttu-id="8a7bf-122">Nasıl yapılır: Bir çalışan iş akışı örneğinin tanımını güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="8a7bf-122">How to: Update the Definition of a Running Workflow Instance</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md)  
 <span data-ttu-id="8a7bf-123">Çalışan iş akışı örnekleri değiştirmek için dinamik güncelleştirme kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="8a7bf-123">Describes how to use dynamic update to modify running workflow instances.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a7bf-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a7bf-124">See also</span></span>

- [<span data-ttu-id="8a7bf-125">Windows Workflow Foundation Programlama</span><span class="sxs-lookup"><span data-stu-id="8a7bf-125">Windows Workflow Foundation Programming</span></span>](programming.md)
