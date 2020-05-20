---
title: Başlarken Tutorial2
description: Bu makale, Windows Workflow Foundation uygulamaları programlamayı sağlayan bir dizi öğreticmaya başlar.
ms.date: 03/30/2017
helpviewer_keywords:
- WF [WF], getting started
- Windows Workflow Foundation [WF], getting started
ms.assetid: c2d3585f-6b1a-4d4f-9865-bd7cd31c5d42
ms.openlocfilehash: 148ba77231067bf5f8ff1d8b444b83d951ce8761
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419856"
---
# <a name="getting-started-tutorial"></a><span data-ttu-id="81c23-103">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="81c23-103">Getting Started Tutorial</span></span>
<span data-ttu-id="81c23-104">Bu bölüm, Windows Workflow Foundation (WF) uygulamalarını programlamayı sağlayan bir dizi gözden geçirme konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="81c23-104">This section contains a set of walkthrough topics that introduce you to programming Windows Workflow Foundation (WF) applications.</span></span> <span data-ttu-id="81c23-105">Bu konulardaki yordamları izleyerek, sayı tahmin eden bir oyun olan bir uygulama oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="81c23-105">By following the procedures in these topics, you will build an application that is a number guessing game.</span></span> <span data-ttu-id="81c23-106">Öğreticideki ilk konu, iş akışı için gerekli özel etkinlikleri oluşturma adımlarında size yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="81c23-106">The first topic in the tutorial leads you through the steps to create the custom activities required for the workflow.</span></span> <span data-ttu-id="81c23-107">İkinci konu başlığında, bu etkinlikler yerleşik iş akışı etkinlikleriyle birlikte bir akış çizelgesi iş akışı olarak toplanır.</span><span class="sxs-lookup"><span data-stu-id="81c23-107">In the second topic, these activities are assembled along with built-in workflow activities into a flowchart workflow.</span></span> <span data-ttu-id="81c23-108">Üçüncü konu başlığında, ana bilgisayar uygulaması iş akışını çalıştıracak şekilde yapılandırılmıştır ve son konu başlığında kalıcılığı ortaya çıkartılır.</span><span class="sxs-lookup"><span data-stu-id="81c23-108">In the third topic, the host application is configured to run the workflow, and in the final topic persistence is introduced.</span></span> <span data-ttu-id="81c23-109">Bu işlemdeki her adım önceki adımlara bağlı olduğundan, bunları sırayla tamamlamanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="81c23-109">Each step in this process depends on the previous steps, so we recommend that you complete them in order.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="81c23-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="81c23-110">In This Section</span></span>  
 [<span data-ttu-id="81c23-111">Nasıl Yapılır: Etkinlik Oluşturma</span><span class="sxs-lookup"><span data-stu-id="81c23-111">How to: Create an Activity</span></span>](how-to-create-an-activity.md)  
 <span data-ttu-id="81c23-112">' Dan türetilen özel bir etkinliğin nasıl oluşturulduğunu <xref:System.Activities.NativeActivity%601> ve bu etkinliğin bir yerleşik etkinlik ile birlikte etkinlik tasarımcısını kullanarak bileşik bir etkinliğe nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="81c23-112">Describes how to create a custom activity that derives from <xref:System.Activities.NativeActivity%601>, and how to compose this activity along with a built-in activity into a composite activity using the activity designer.</span></span>  
  
 [<span data-ttu-id="81c23-113">Nasıl yapılır: İş Akışı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="81c23-113">How to: Create a Workflow</span></span>](how-to-create-a-workflow.md)  
 <span data-ttu-id="81c23-114">Yerleşik etkinlikler ve önceki öğreticideki özel etkinlikler kullanılarak akış çizelgesi, sıralı ve durum makinesi iş akışlarının nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="81c23-114">Describes how to create flowchart, sequential, and state machine workflows by using built-in activities and the custom activities from the preceding tutorial.</span></span>  
  
 [<span data-ttu-id="81c23-115">Nasıl yapılır: İş Akışı Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="81c23-115">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)  
 <span data-ttu-id="81c23-116">Bir konak ortamından bir iş akışının nasıl çağırılacağını, verilerin bir iş akışının içine ve dışına nasıl geçirileceğini ve yer işaretlerinin nasıl sürdürüleceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="81c23-116">Describes how to invoke a workflow from a host environment, pass data into and out of a workflow, and how to resume bookmarks.</span></span>  
  
 [<span data-ttu-id="81c23-117">Nasıl yapılır: Uzun Süre Çalışan İş Akışı Oluşturma ve Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="81c23-117">How to: Create and Run a Long Running Workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md)  
 <span data-ttu-id="81c23-118">Bir iş akışı uygulamasına kalıcılığı nasıl ekleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="81c23-118">Describes how to add persistence to a workflow application.</span></span>  
  
 [<span data-ttu-id="81c23-119">Nasıl yapılır: Özel İzleme Katılımcısı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="81c23-119">How to: Create a Custom Tracking Participant</span></span>](how-to-create-a-custom-tracking-participant.md)  
 <span data-ttu-id="81c23-120">Özel izleme katılımcısı ve izleme profili oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="81c23-120">Describes how to create a custom tracking participant and tracking profile.</span></span>  
  
 [<span data-ttu-id="81c23-121">Nasıl yapılır: İş Akışının Birden Fazla Sürümünü Yan Yana Barındırma</span><span class="sxs-lookup"><span data-stu-id="81c23-121">How to: Host Multiple Versions of a Workflow Side-by-Side</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)  
 <span data-ttu-id="81c23-122">`WorkflowIdentity`Bir iş akışının birden çok sürümünü yan yana barındırmak için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="81c23-122">Describes how to use `WorkflowIdentity` to host multiple versions of a workflow side-by-side.</span></span>  
  
 [<span data-ttu-id="81c23-123">Nasıl yapılır: Çalışan İş Akışı Örneğinin Tanımını Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="81c23-123">How to: Update the Definition of a Running Workflow Instance</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md)  
 <span data-ttu-id="81c23-124">Çalışan iş akışı örneklerini değiştirmek için dinamik güncelleştirme 'nin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="81c23-124">Describes how to use dynamic update to modify running workflow instances.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81c23-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81c23-125">See also</span></span>

- [<span data-ttu-id="81c23-126">Windows Workflow Foundation Programlama</span><span class="sxs-lookup"><span data-stu-id="81c23-126">Windows Workflow Foundation Programming</span></span>](programming.md)
