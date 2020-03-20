---
title: Pick Etkinliği
ms.date: 03/30/2017
ms.assetid: b3e49b7f-0285-4720-8c09-11ae18f0d53e
ms.openlocfilehash: 672de5fd3df5e8dde6c54118503bf2a11353b116
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182901"
---
# <a name="pick-activity"></a><span data-ttu-id="d1f7c-102">Pick Etkinliği</span><span class="sxs-lookup"><span data-stu-id="d1f7c-102">Pick Activity</span></span>
<span data-ttu-id="d1f7c-103">Etkinlik, <xref:System.Activities.Statements.Pick> ilgili işleyicileri tarafından izlenen olay tetikleyicileri kümesinin modelliğini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="d1f7c-103">The <xref:System.Activities.Statements.Pick> activity simplifies the modeling of a set of event triggers followed by their corresponding handlers.</span></span>  <span data-ttu-id="d1f7c-104">Bir <xref:System.Activities.Statements.Pick> etkinlik, her <xref:System.Activities.Statements.PickBranch> <xref:System.Activities.Statements.PickBranch> bir <xref:System.Activities.Statements.PickBranch.Trigger%2A> etkinlik ve bir <xref:System.Activities.Statements.PickBranch.Action%2A> etkinlik arasında bir eşleştirme olduğu bir etkinlik koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="d1f7c-104">A <xref:System.Activities.Statements.Pick> activity contains a collection of <xref:System.Activities.Statements.PickBranch> activities, where each <xref:System.Activities.Statements.PickBranch> is a pairing between a <xref:System.Activities.Statements.PickBranch.Trigger%2A> activity and an <xref:System.Activities.Statements.PickBranch.Action%2A> activity.</span></span>  <span data-ttu-id="d1f7c-105">Yürütme sırasında, tüm dalların tetikleyicileri paralel olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="d1f7c-105">At execution time, the triggers for all branches are executed in parallel.</span></span>  <span data-ttu-id="d1f7c-106">Bir tetikleyici tamamlandığında, karşılık gelen eylemi yürütülür ve diğer tüm tetikleyiciler iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="d1f7c-106">When one trigger completes, then its corresponding action is executed, and all other triggers are canceled.</span></span>  <span data-ttu-id="d1f7c-107">Etkinliğin davranışı [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] .NET Framework 3.5 <xref:System.Workflow.Activities.ListenActivity> etkinliğine benzer. <xref:System.Activities.Statements.Pick></span><span class="sxs-lookup"><span data-stu-id="d1f7c-107">The behavior of the [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<xref:System.Activities.Statements.Pick> activity is similar to the .NET Framework 3.5 <xref:System.Workflow.Activities.ListenActivity> activity.</span></span>  
  
 <span data-ttu-id="d1f7c-108">[Seçme Etkinliği](./samples/using-the-pick-activity.md) SDK örneğinden aşağıdaki ekran görüntüsü, iki dallı bir Çekme etkinliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="d1f7c-108">The following screenshot from the [Using the Pick Activity](./samples/using-the-pick-activity.md) SDK sample shows a Pick activity with two branches.</span></span>  <span data-ttu-id="d1f7c-109">Bir dalda **Okuma girişi**adlı bir tetikleyici vardır, komut satırından girişi okuyan özel bir etkinlik.</span><span class="sxs-lookup"><span data-stu-id="d1f7c-109">One branch has a trigger called **Read input**, a custom activity that reads input from the command line.</span></span> <span data-ttu-id="d1f7c-110">İkinci dalda <xref:System.Activities.Statements.Delay> bir etkinlik tetikleyicisi vardır.</span><span class="sxs-lookup"><span data-stu-id="d1f7c-110">The second branch has a <xref:System.Activities.Statements.Delay> activity trigger.</span></span> <span data-ttu-id="d1f7c-111">Okundu **girişi** etkinliği etkinlik bitmeden <xref:System.Activities.Statements.Delay> önce <xref:System.Activities.Statements.Delay> veri alırsa, Gecikme iptal edilir ve konsola bir karşılama yazılır.</span><span class="sxs-lookup"><span data-stu-id="d1f7c-111">If the **Read input** activity receives data before the <xref:System.Activities.Statements.Delay> activity finishes, <xref:System.Activities.Statements.Delay> Delay will be canceled and a greeting will be written to the console.</span></span>  <span data-ttu-id="d1f7c-112">Aksi takdirde, **Read girişi** etkinliği ayrılan süre içinde veri almazsa, iptal edilir ve konsola bir zaman ekme iletisi yazılır.</span><span class="sxs-lookup"><span data-stu-id="d1f7c-112">Otherwise, if the **Read input** activity does not receive data in the allotted time, then it will be canceled and a timeout message will be written to the console.</span></span>  <span data-ttu-id="d1f7c-113">Bu, herhangi bir eyleme zaman aşındırmak için kullanılan yaygın bir desendir.</span><span class="sxs-lookup"><span data-stu-id="d1f7c-113">This is a common pattern used to add a timeout to any action.</span></span>  
  
 ![Pick Etkinliği](./media/pick-activity/pick-activity-two-branches.jpg)  
  
## <a name="best-practices"></a><span data-ttu-id="d1f7c-115">En iyi uygulamalar</span><span class="sxs-lookup"><span data-stu-id="d1f7c-115">Best practices</span></span>  
 <span data-ttu-id="d1f7c-116">Çekme'yi kullanırken, çalıştıran dal, tetikleyicisi ilk tamamlanan daldır.</span><span class="sxs-lookup"><span data-stu-id="d1f7c-116">When using Pick, the branch that executes is the branch whose trigger completes first.</span></span>  <span data-ttu-id="d1f7c-117">Kavramsal olarak, tüm tetikleyiciler paralel olarak yürütülür ve bir tetikleyici, başka bir tetikleyicinin tamamlanmasıyla iptal edilmeden önce mantığının büyük bir kısmını yürütülmüş olabilir.</span><span class="sxs-lookup"><span data-stu-id="d1f7c-117">Conceptually, all triggers execute in parallel, and one trigger may have executed the majority of its logic before it is canceled by the completion of another trigger.</span></span>  <span data-ttu-id="d1f7c-118">Bunu göz önünde bulundurarak, Çekme etkinliğini kullanırken izninizlen genel bir kılavuz, tetikleyiciyi tek bir olayı temsil ediyor gibi ele almak ve mümkün olduğunca az mantık koymaktır.</span><span class="sxs-lookup"><span data-stu-id="d1f7c-118">With this in mind, a general guideline to follow when using the Pick activity is to treat the trigger as representing a single event, and to put as little logic as possible into it.</span></span>  <span data-ttu-id="d1f7c-119">İdeal olarak, tetikleyici bir olay almak için yeterli mantık içermelidir ve bu olayın tüm işleme dalı eyleme gitmeli.</span><span class="sxs-lookup"><span data-stu-id="d1f7c-119">Ideally, the trigger should contain just enough logic to receive an event, and all the processing of that event should go into the action of the branch.</span></span>  <span data-ttu-id="d1f7c-120">Bu yöntem, tetikleyicilerin yürütülmesi arasındaki çakışma miktarını en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="d1f7c-120">This method minimizes the amount of overlap between the execution of the triggers.</span></span>  <span data-ttu-id="d1f7c-121">Örneğin, her <xref:System.Activities.Statements.Pick> tetikleyiciek mantık ardından bir <xref:System.ServiceModel.Activities.Receive> etkinlik içeren iki tetikleyici ile a düşünün.</span><span class="sxs-lookup"><span data-stu-id="d1f7c-121">For example, consider a <xref:System.Activities.Statements.Pick> with two triggers, where each trigger contains a <xref:System.ServiceModel.Activities.Receive> activity followed by additional logic.</span></span>  <span data-ttu-id="d1f7c-122">Ek mantık boşta bir nokta tanıtırsa, <xref:System.ServiceModel.Activities.Receive> her iki faaliyetin de başarıyla tamamlanması olasılığı vardır.</span><span class="sxs-lookup"><span data-stu-id="d1f7c-122">If the additional logic introduces an idle point, then there is the possibility of both <xref:System.ServiceModel.Activities.Receive> activities completing successfully.</span></span>  <span data-ttu-id="d1f7c-123">Bir tetikleyici tamamen tamamlanacak, diğeri ise kısmen tamamlanacak.</span><span class="sxs-lookup"><span data-stu-id="d1f7c-123">One trigger will fully complete, while another will partially complete.</span></span>  <span data-ttu-id="d1f7c-124">Bazı senaryolarda, bir iletiyi kabul etmek ve sonra kısmen işlemeyi tamamlamak kabul edilemez.</span><span class="sxs-lookup"><span data-stu-id="d1f7c-124">In some scenarios, accepting a message, and then partially completing the processing of it is unacceptable.</span></span>  <span data-ttu-id="d1f7c-125">Bu nedenle, WF dahili mesajlaşma etkinlikleri <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply>kullanırken <xref:System.ServiceModel.Activities.Receive> ve , genellikle tetikleyici <xref:System.ServiceModel.Activities.SendReply> kullanılır ken, ve diğer mantık mümkün olduğunca eylem koymak gerekir.</span><span class="sxs-lookup"><span data-stu-id="d1f7c-125">Therefore, when using WF built-in messaging activities such as <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply>, while <xref:System.ServiceModel.Activities.Receive> is commonly used in the trigger, <xref:System.ServiceModel.Activities.SendReply> and other logic should be put in the action whenever possible.</span></span>  
  
## <a name="using-the-pick-activity-in-the-designer"></a><span data-ttu-id="d1f7c-126">Tasarımcıda Çekme etkinliğini kullanma</span><span class="sxs-lookup"><span data-stu-id="d1f7c-126">Using the Pick activity in the designer</span></span>  
 <span data-ttu-id="d1f7c-127">Tasarımcıda Seç'i kullanmak için araç kutusunda **Pick** ve **PickBranch'ı** bulun.</span><span class="sxs-lookup"><span data-stu-id="d1f7c-127">To use Pick in the designer, find **Pick** and **PickBranch** in the toolbox.</span></span>  <span data-ttu-id="d1f7c-128">**Sürükle** ve tuval üzerine Pick bırakın.</span><span class="sxs-lookup"><span data-stu-id="d1f7c-128">Drag and drop **Pick** onto the canvas.</span></span>  <span data-ttu-id="d1f7c-129">Varsayılan olarak, tasarımcıda yeni bir **Çekme** Etkinliği iki dal içerir.</span><span class="sxs-lookup"><span data-stu-id="d1f7c-129">By default, a new **Pick** Activity in the designer will contain two branches.</span></span>  <span data-ttu-id="d1f7c-130">Ek dallar eklemek için **PickBranch** etkinliğini sürükleyin ve varolan dalların yanına bırakın.</span><span class="sxs-lookup"><span data-stu-id="d1f7c-130">To add additional branches, drag the **PickBranch** activity and drop it next to existing branches.</span></span> <span data-ttu-id="d1f7c-131">Etkinlikler, **Tetikleyici** alanına veya herhangi bir **PickBranch'ın** **Eylem** alanına **Çekme** Etkinliği'ne bırakılabilir.</span><span class="sxs-lookup"><span data-stu-id="d1f7c-131">Activities can be dropped onto the **Pick** Activity into either the **Trigger** area or the **Action** area of any **PickBranch**.</span></span>  
  
## <a name="using-the-pick-activity-in-code"></a><span data-ttu-id="d1f7c-132">Kodda Çekme Etkinliği'ni kullanma</span><span class="sxs-lookup"><span data-stu-id="d1f7c-132">Using the Pick Activity in code</span></span>  
 <span data-ttu-id="d1f7c-133">Etkinlik, <xref:System.Activities.Statements.Pick> <xref:System.Activities.Statements.Pick.Branches%2A> koleksiyonunu etkinliklerle <xref:System.Activities.Statements.PickBranch> doldurarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d1f7c-133">The <xref:System.Activities.Statements.Pick> activity is used by populating its <xref:System.Activities.Statements.Pick.Branches%2A> collection with <xref:System.Activities.Statements.PickBranch> activities.</span></span> <span data-ttu-id="d1f7c-134">Etkinliklerin <xref:System.Activities.Statements.PickBranch> her <xref:System.Activities.Statements.PickBranch.Trigger%2A> biri bir <xref:System.Activities.Activity>tür özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d1f7c-134">The <xref:System.Activities.Statements.PickBranch> activities each have a <xref:System.Activities.Statements.PickBranch.Trigger%2A> property of type <xref:System.Activities.Activity>.</span></span> <span data-ttu-id="d1f7c-135">Belirtilen etkinlik yürütmeyi tamamladığında, yürütülür. <xref:System.Activities.Statements.PickBranch.Action%2A></span><span class="sxs-lookup"><span data-stu-id="d1f7c-135">When the specified activity completes execution, the <xref:System.Activities.Statements.PickBranch.Action%2A> executes.</span></span>  
  
 <span data-ttu-id="d1f7c-136">Aşağıdaki kod örneği, konsoldan <xref:System.Activities.Statements.Pick> bir satır okuyan bir etkinlik için zaman arasını uygulamak için bir etkinliğin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d1f7c-136">The following code example demonstrates how to use a <xref:System.Activities.Statements.Pick> activity to implement a timeout for an activity that reads a line from the console.</span></span>  
  
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
