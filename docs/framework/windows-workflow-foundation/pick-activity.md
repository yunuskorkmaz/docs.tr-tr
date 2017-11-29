---
title: "Etkinlik seçin"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3e49b7f-0285-4720-8c09-11ae18f0d53e
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a76b666dde6674740790c161753570193912afd9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="pick-activity"></a><span data-ttu-id="302d4-102">Etkinlik seçin</span><span class="sxs-lookup"><span data-stu-id="302d4-102">Pick Activity</span></span>
<span data-ttu-id="302d4-103"><xref:System.Activities.Statements.Pick> Etkinlik olay tetikleyicileri bunların karşılık gelen işleyiciler tarafından izlenen bir dizi modelleme basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="302d4-103">The <xref:System.Activities.Statements.Pick> activity simplifies the modeling of a set of event triggers followed by their corresponding handlers.</span></span>  <span data-ttu-id="302d4-104">A <xref:System.Activities.Statements.Pick> etkinlik koleksiyonunu içerir <xref:System.Activities.Statements.PickBranch> etkinlikleri, burada her <xref:System.Activities.Statements.PickBranch> arasında eşleştirme olduğu bir <xref:System.Activities.Statements.PickBranch.Trigger%2A> etkinliği ve bir <xref:System.Activities.Statements.PickBranch.Action%2A> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="302d4-104">A <xref:System.Activities.Statements.Pick> activity contains a collection of <xref:System.Activities.Statements.PickBranch> activities, where each <xref:System.Activities.Statements.PickBranch> is a pairing between a <xref:System.Activities.Statements.PickBranch.Trigger%2A> activity and an <xref:System.Activities.Statements.PickBranch.Action%2A> activity.</span></span>  <span data-ttu-id="302d4-105">Yürütme sırasında tüm dalları tetikleyici paralel olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="302d4-105">At execution time, the triggers for all branches are executed in parallel.</span></span>  <span data-ttu-id="302d4-106">Bir tetikleyici tamamlandığında, karşılık gelen eylemi yürütülür ve diğer tüm Tetikleyicileri iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="302d4-106">When one trigger completes, then its corresponding action is executed, and all other triggers are canceled.</span></span>  <span data-ttu-id="302d4-107">Davranışını [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <xref:System.Activities.Statements.Pick> etkinlik benzer [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] <xref:System.Workflow.Activities.ListenActivity> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="302d4-107">The behavior of the [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<xref:System.Activities.Statements.Pick> activity is similar to the [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]<xref:System.Workflow.Activities.ListenActivity> activity.</span></span>  
  
 <span data-ttu-id="302d4-108">Aşağıdaki ekran görüntüsünde [kullanarak çekme etkinliğini](../../../docs/framework/windows-workflow-foundation/samples/using-the-pick-activity.md) SDK'sı örneği iki dalı çekme etkinlikle gösterir.</span><span class="sxs-lookup"><span data-stu-id="302d4-108">The following screenshot from the [Using the Pick Activity](../../../docs/framework/windows-workflow-foundation/samples/using-the-pick-activity.md) SDK sample shows a Pick activity with two branches.</span></span>  <span data-ttu-id="302d4-109">Bir dal adı verilen bir tetikleyici sahip **okuma giriş**, komut satırından giriş okur özel bir etkinlik.</span><span class="sxs-lookup"><span data-stu-id="302d4-109">One branch has a trigger called **Read input**, a custom activity that reads input from the command line.</span></span> <span data-ttu-id="302d4-110">İkinci şube sahip bir <xref:System.Activities.Statements.Delay> etkinlik tetikleyici.</span><span class="sxs-lookup"><span data-stu-id="302d4-110">The second branch has a <xref:System.Activities.Statements.Delay> activity trigger.</span></span> <span data-ttu-id="302d4-111">Varsa **okuma giriş** etkinlik önce verileri alan <xref:System.Activities.Statements.Delay> etkinlik bittiğinde <xref:System.Activities.Statements.Delay> gecikme iptal edilecek ve bir karşılama konsoluna yazılır.</span><span class="sxs-lookup"><span data-stu-id="302d4-111">If the **Read input** activity receives data before the <xref:System.Activities.Statements.Delay> activity finishes, <xref:System.Activities.Statements.Delay> Delay will be canceled and a greeting will be written to the console.</span></span>  <span data-ttu-id="302d4-112">Aksi halde, eğer **okuma giriş** etkinlik ayrılan sürede veri almaz sonra iptal edilecek ve bir zaman aşımı iletisi konsoluna yazılır.</span><span class="sxs-lookup"><span data-stu-id="302d4-112">Otherwise, if the **Read input** activity does not receive data in the allotted time, then it will be canceled and a timeout message will be written to the console.</span></span>  <span data-ttu-id="302d4-113">Zaman aşımı için herhangi bir eylem eklemek için kullanılan genel bir desen budur.</span><span class="sxs-lookup"><span data-stu-id="302d4-113">This is a common pattern used to add a timeout to any action.</span></span>  
  
 <span data-ttu-id="302d4-114">![Etkinlik çekme](../../../docs/framework/windows-workflow-foundation/media/pickconceptual.JPG "PickConceptual")</span><span class="sxs-lookup"><span data-stu-id="302d4-114">![Pick Activity](../../../docs/framework/windows-workflow-foundation/media/pickconceptual.JPG "PickConceptual")</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="302d4-115">Önerilen uygulamalar</span><span class="sxs-lookup"><span data-stu-id="302d4-115">Best practices</span></span>  
 <span data-ttu-id="302d4-116">Çekme kullanırken yürütür şube tetikleyicisini ilk tamamlandıktan dal ' dir.</span><span class="sxs-lookup"><span data-stu-id="302d4-116">When using Pick, the branch that executes is the branch whose trigger completes first.</span></span>  <span data-ttu-id="302d4-117">Kavramsal olarak, tüm Tetikleyicileri paralel olarak yürütün ve başka bir tetikleme tamamlanmasından tarafından iptal etmeden önce bir tetikleyici, mantığını çoğunluğu yürütülen.</span><span class="sxs-lookup"><span data-stu-id="302d4-117">Conceptually, all triggers execute in parallel, and one trigger may have executed the majority of its logic before it is canceled by the completion of another trigger.</span></span>  <span data-ttu-id="302d4-118">Bu aklınızda kullanarak çekme etkinliğini izlemeniz gereken genel kılavuz tetikleyici tek bir olay temsil eden olarak işlemek için mümkün olduğunca az mantığı olarak içine yerleştirilecek ise.</span><span class="sxs-lookup"><span data-stu-id="302d4-118">With this in mind, a general guideline to follow when using the Pick activity is to treat the trigger as representing a single event, and to put as little logic as possible into it.</span></span>  <span data-ttu-id="302d4-119">İdeal olarak, tetikleyici bir olay almak için yeterli mantığının içermelidir ve bu olayın tüm işleme şube eyleme tamamlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="302d4-119">Ideally, the trigger should contain just enough logic to receive an event, and all the processing of that event should go into the action of the branch.</span></span>  <span data-ttu-id="302d4-120">Bu yöntem Tetikleyiciler yürütülmesi arasında örtüşme miktarını azaltır.</span><span class="sxs-lookup"><span data-stu-id="302d4-120">This method minimizes the amount of overlap between the execution of the triggers.</span></span>  <span data-ttu-id="302d4-121">Örneğin, göz önünde bulundurun bir <xref:System.Activities.Statements.Pick> , her tetikleyici içerdiği iki tetikleyici içeren bir <xref:System.ServiceModel.Activities.Receive> etkinlik ek mantığı tarafından izlenen.</span><span class="sxs-lookup"><span data-stu-id="302d4-121">For example, consider a <xref:System.Activities.Statements.Pick> with two triggers, where each trigger contains a <xref:System.ServiceModel.Activities.Receive> activity followed by additional logic.</span></span>  <span data-ttu-id="302d4-122">İlave bir mantık boşta noktanız tanıtır sonra her ikisi de olasılığı varsa <xref:System.ServiceModel.Activities.Receive> başarıyla tamamlayan etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="302d4-122">If the additional logic introduces an idle point, then there is the possibility of both <xref:System.ServiceModel.Activities.Receive> activities completing successfully.</span></span>  <span data-ttu-id="302d4-123">Bir tetikleyici olacak tam olarak başka bir işlem sırasında tam kısmen tamamlanmış.</span><span class="sxs-lookup"><span data-stu-id="302d4-123">One trigger will fully complete, while another will partially complete.</span></span>  <span data-ttu-id="302d4-124">Bazı senaryolarda, bir ileti kabul etmek ve kısmen işlenmesini Tamamlanıyor kabul edilebilir değil.</span><span class="sxs-lookup"><span data-stu-id="302d4-124">In some scenarios, accepting a message, and then partially completing the processing of it is unacceptable.</span></span>  <span data-ttu-id="302d4-125">Bu nedenle, WF yerleşik Mesajlaşma etkinlikleri gibi kullanırken <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply>, sırada <xref:System.ServiceModel.Activities.Receive> tetikleyici, yaygın olarak kullanılan <xref:System.ServiceModel.Activities.SendReply> ve diğer mantığı mümkün olduğunca eylemde sokulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="302d4-125">Therefore, when using WF built-in messaging activities such as <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply>, while <xref:System.ServiceModel.Activities.Receive> is commonly used in the trigger, <xref:System.ServiceModel.Activities.SendReply> and other logic should be put in the action whenever possible.</span></span>  
  
## <a name="using-the-pick-activity-in-the-designer"></a><span data-ttu-id="302d4-126">Çekme Etkinlik Tasarımcısı'nda kullanma</span><span class="sxs-lookup"><span data-stu-id="302d4-126">Using the Pick activity in the designer</span></span>  
 <span data-ttu-id="302d4-127">Çekme Tasarımcısı'nda kullanmak için bulma **çekme** ve **PickBranch** araç kutusunda.</span><span class="sxs-lookup"><span data-stu-id="302d4-127">To use Pick in the designer, find **Pick** and **PickBranch** in the toolbox.</span></span>  <span data-ttu-id="302d4-128">Sürükleme ve bırakma **çekme** tuvale.</span><span class="sxs-lookup"><span data-stu-id="302d4-128">Drag and drop **Pick** onto the canvas.</span></span>  <span data-ttu-id="302d4-129">Varsayılan olarak, yeni bir **çekme** etkinlik Tasarımcısı'nda iki dalı içerir.</span><span class="sxs-lookup"><span data-stu-id="302d4-129">By default, a new **Pick** Activity in the designer will contain two branches.</span></span>  <span data-ttu-id="302d4-130">Ek dalları eklemek için sürükleyin **PickBranch** etkinliği ve varolan dalları yanındaki bırakın.</span><span class="sxs-lookup"><span data-stu-id="302d4-130">To add additional branches, drag the **PickBranch** activity and drop it next to existing branches.</span></span> <span data-ttu-id="302d4-131">Etkinlikler bırakılan üzerine **çekme** ya da etkinliğini **tetikleyici** alan veya **eylem** herhangi bir bölümünü **PickBranch**.</span><span class="sxs-lookup"><span data-stu-id="302d4-131">Activities can be dropped onto the **Pick** Activity into either the **Trigger** area or the **Action** area of any **PickBranch**.</span></span>  
  
## <a name="using-the-pick-activity-in-code"></a><span data-ttu-id="302d4-132">Çekme Etkinlik kod içinde kullanma</span><span class="sxs-lookup"><span data-stu-id="302d4-132">Using the Pick Activity in code</span></span>  
 <span data-ttu-id="302d4-133"><xref:System.Activities.Statements.Pick> Etkinlik doldurarak kullanılır, <xref:System.Activities.Statements.Pick.Branches%2A> koleksiyonuyla <xref:System.Activities.Statements.PickBranch> etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="302d4-133">The <xref:System.Activities.Statements.Pick> activity is used by populating its <xref:System.Activities.Statements.Pick.Branches%2A> collection with <xref:System.Activities.Statements.PickBranch> activities.</span></span> <span data-ttu-id="302d4-134"><xref:System.Activities.Statements.PickBranch> Etkinliklerin her bir <xref:System.Activities.Statements.PickBranch.Trigger%2A> türündeki özelliği <xref:System.Activities.Activity>.</span><span class="sxs-lookup"><span data-stu-id="302d4-134">The <xref:System.Activities.Statements.PickBranch> activities each have a <xref:System.Activities.Statements.PickBranch.Trigger%2A> property of type <xref:System.Activities.Activity>.</span></span> <span data-ttu-id="302d4-135">Belirtilen Etkinlik yürütme tamamlandığında <xref:System.Activities.Statements.PickBranch.Action%2A> yürütür.</span><span class="sxs-lookup"><span data-stu-id="302d4-135">When the specified activity completes execution, the <xref:System.Activities.Statements.PickBranch.Action%2A> executes.</span></span>  
  
 <span data-ttu-id="302d4-136">Aşağıdaki kod örneğinde nasıl kullanılacağını gösteren bir <xref:System.Activities.Statements.Pick> bir satır konsoldan okur bir etkinlik için zaman aşımı uygulamak için etkinlik.</span><span class="sxs-lookup"><span data-stu-id="302d4-136">The following code example demonstrates how to use a <xref:System.Activities.Statements.Pick> activity to implement a timeout for an activity that reads a line from the console.</span></span>  
  
```csharp  
Sequence body = new Sequence()  
{  
    Variables = { name },  
    Activities =   
   {  
       new System.Activities.Statements.Pick  
        {  
           Branches =   
           {  
               new PickBranch  
               {  
                   Trigger = new ReadLine  
                   {  
                      Result = name,  
                      BookmarkName = "name"  
                   },  
                   Action = new WriteLine   
                   {   
                       Text = ExpressionServices.Convert<string>(ctx => "Hello " +   
                           name.Get(ctx))   
                   }  
               },  
               new PickBranch  
               {  
                   Trigger = new Delay  
                   {  
                      Duration = new TimeSpan(0, 0, 5)  
                   },  
                   Action = new WriteLine  
                   {  
                      Text = "Time is up."  
                   }  
               }  
           }  
       }  
   }  
};  
```  
  
```xaml  
<Sequence xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <Variable x:TypeArguments="x:String" Name="username" />  
  </Sequence.Variables>  
  <Pick>  
    <PickBranch>  
      <PickBranch.Trigger>  
        <ReadLine BookmarkName="name" Result="username" />  
      </PickBranch.Trigger>  
      <WriteLine>[String.Concat("Hello ", username)]</WriteLine>  
    </PickBranch>  
    <PickBranch>  
      <PickBranch.Trigger>  
        <Delay>00:00:05</Delay>  
      </PickBranch.Trigger>  
      <WriteLine>Time is up.</WriteLine>  
    </PickBranch>  
  </Pick>  
</Sequence>  
```
