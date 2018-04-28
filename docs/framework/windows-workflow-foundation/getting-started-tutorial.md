---
title: Öğretici2 Başlarken
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WF [WF], getting started
- Windows Workflow Foundation [WF], getting started
ms.assetid: c2d3585f-6b1a-4d4f-9865-bd7cd31c5d42
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1be017762ed64f61516216c9d103547f88598254
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="getting-started-tutorial"></a><span data-ttu-id="c7cec-102">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="c7cec-102">Getting Started Tutorial</span></span>
<span data-ttu-id="c7cec-103">Bu bölüm, Windows Workflow Foundation (WF) uygulama programlama tanıtmak gözden geçirme konuları kümesi içerir.</span><span class="sxs-lookup"><span data-stu-id="c7cec-103">This section contains a set of walkthrough topics that introduce you to programming Windows Workflow Foundation (WF) applications.</span></span> <span data-ttu-id="c7cec-104">Aşağıdaki konulardaki yordamları izleyerek, numara tahmin eden oyun bir uygulama oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="c7cec-104">By following the procedures in these topics, you will build an application that is a number guessing game.</span></span> <span data-ttu-id="c7cec-105">Öğreticinin ilk konusunda iş akışı için gereken özel etkinlikler oluşturmak için aşağıdaki adımları size yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7cec-105">The first topic in the tutorial leads you through the steps to create the custom activities required for the workflow.</span></span> <span data-ttu-id="c7cec-106">İkinci konuda bu etkinlikleri yerleşik iş akışı etkinlikleri ile birlikte bir akış iş akışı ile birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c7cec-106">In the second topic, these activities are assembled along with built-in workflow activities into a flowchart workflow.</span></span> <span data-ttu-id="c7cec-107">Üçüncü konusunda konak uygulama iş akışını çalıştırmak için yapılandırılmış ve son konusunda Kalıcılık sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="c7cec-107">In the third topic, the host application is configured to run the workflow, and in the final topic persistence is introduced.</span></span> <span data-ttu-id="c7cec-108">Bunları sırayla tamamlamanızı öneririz şekilde bu işlemdeki her adım önceki adımları, bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c7cec-108">Each step in this process depends on the previous steps, so we recommend that you complete them in order.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c7cec-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c7cec-109">In This Section</span></span>  
 [<span data-ttu-id="c7cec-110">Nasıl Yapılır: Etkinlik Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c7cec-110">How to: Create an Activity</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 <span data-ttu-id="c7cec-111">Türetilen özel bir aktivite oluşturmayı açıklar <xref:System.Activities.NativeActivity%601>ve yerleşik bir etkinlik Tasarımcısı'nı kullanarak bileşik bir etkinlik etkinliğini birlikte bu etkinlik oluşturmak nasıl.</span><span class="sxs-lookup"><span data-stu-id="c7cec-111">Describes how to create a custom activity that derives from <xref:System.Activities.NativeActivity%601>, and how to compose this activity along with a built-in activity into a composite activity using the activity designer.</span></span>  
  
 [<span data-ttu-id="c7cec-112">Nasıl yapılır: İş Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c7cec-112">How to: Create a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)  
 <span data-ttu-id="c7cec-113">Akış Çizelgesi, sıralı ve Durum makinesi iş akışları yerleşik etkinlikler ve önceki öğretici özel etkinliklerden kullanarak nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c7cec-113">Describes how to create flowchart, sequential, and state machine workflows by using built-in activities and the custom activities from the preceding tutorial.</span></span>  
  
 [<span data-ttu-id="c7cec-114">Nasıl yapılır: İş Akışı Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c7cec-114">How to: Run a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)  
 <span data-ttu-id="c7cec-115">Bir ana bilgisayar ortamından bir iş akışının çağırmak, içine ve dışına bir iş akışı veri iletmek ve yer işaretleri sürdürmeye açıklar.</span><span class="sxs-lookup"><span data-stu-id="c7cec-115">Describes how to invoke a workflow from a host environment, pass data into and out of a workflow, and how to resume bookmarks.</span></span>  
  
 [<span data-ttu-id="c7cec-116">Nasıl yapılır: Uzun Süre Çalışan İş Akışı Oluşturma ve Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c7cec-116">How to: Create and Run a Long Running Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md)  
 <span data-ttu-id="c7cec-117">Bir iş akışı uygulamaya Kalıcılık eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="c7cec-117">Describes how to add persistence to a workflow application.</span></span>  
  
 [<span data-ttu-id="c7cec-118">Nasıl yapılır: Özel İzleme Katılımcısı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c7cec-118">How to: Create a Custom Tracking Participant</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md)  
 <span data-ttu-id="c7cec-119">Özel İzleme katılımcı ve izleme profili nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c7cec-119">Describes how to create a custom tracking participant and tracking profile.</span></span>  
  
 [<span data-ttu-id="c7cec-120">Nasıl yapılır: İş Akışının Birden Fazla Sürümünü Yan Yana Barındırma</span><span class="sxs-lookup"><span data-stu-id="c7cec-120">How to: Host Multiple Versions of a Workflow Side-by-Side</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md)  
 <span data-ttu-id="c7cec-121">Nasıl kullanılacağını açıklar `WorkflowIdentity` bir iş akışı yan yana birden fazla sürümünü barındırmak için.</span><span class="sxs-lookup"><span data-stu-id="c7cec-121">Describes how to use `WorkflowIdentity` to host multiple versions of a workflow side-by-side.</span></span>  
  
 [<span data-ttu-id="c7cec-122">Nasıl yapılır: Çalışan İş Akışı Örneğinin Tanımını Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="c7cec-122">How to: Update the Definition of a Running Workflow Instance</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md)  
 <span data-ttu-id="c7cec-123">Çalışan iş akışı örnekleri değiştirmek için dinamik güncelleştirme kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="c7cec-123">Describes how to use dynamic update to modify running workflow instances.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7cec-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c7cec-124">See Also</span></span>  
 [<span data-ttu-id="c7cec-125">Windows Workflow Foundation Programlama</span><span class="sxs-lookup"><span data-stu-id="c7cec-125">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)
