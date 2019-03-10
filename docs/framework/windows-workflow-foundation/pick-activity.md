---
title: Pick etkinliği
ms.date: 03/30/2017
ms.assetid: b3e49b7f-0285-4720-8c09-11ae18f0d53e
ms.openlocfilehash: 7626dda3689f89831d98ad484d7eab62c25def5b
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717953"
---
# <a name="pick-activity"></a><span data-ttu-id="4f552-102">Pick etkinliği</span><span class="sxs-lookup"><span data-stu-id="4f552-102">Pick Activity</span></span>
<span data-ttu-id="4f552-103"><xref:System.Activities.Statements.Pick> Modelleme olay tetikleyicilerini karşılık gelen işleyicilerini tarafından izlenen bir dizi etkinlik basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="4f552-103">The <xref:System.Activities.Statements.Pick> activity simplifies the modeling of a set of event triggers followed by their corresponding handlers.</span></span>  <span data-ttu-id="4f552-104">A <xref:System.Activities.Statements.Pick> etkinliği içeren bir koleksiyonu <xref:System.Activities.Statements.PickBranch> etkinlikleri, burada her <xref:System.Activities.Statements.PickBranch> arasında eşleştirme olduğu bir <xref:System.Activities.Statements.PickBranch.Trigger%2A> etkinliği ve bir <xref:System.Activities.Statements.PickBranch.Action%2A> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="4f552-104">A <xref:System.Activities.Statements.Pick> activity contains a collection of <xref:System.Activities.Statements.PickBranch> activities, where each <xref:System.Activities.Statements.PickBranch> is a pairing between a <xref:System.Activities.Statements.PickBranch.Trigger%2A> activity and an <xref:System.Activities.Statements.PickBranch.Action%2A> activity.</span></span>  <span data-ttu-id="4f552-105">Yürütme sırasında tüm dallar için Tetikleyiciler paralel olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="4f552-105">At execution time, the triggers for all branches are executed in parallel.</span></span>  <span data-ttu-id="4f552-106">Bir tetikleyici tamamlandığında, karşılık gelen eylemi yürütülür ve diğer tüm tetikleyiciler iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="4f552-106">When one trigger completes, then its corresponding action is executed, and all other triggers are canceled.</span></span>  <span data-ttu-id="4f552-107">Davranışını [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <xref:System.Activities.Statements.Pick> etkinlik benzer [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] <xref:System.Workflow.Activities.ListenActivity> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="4f552-107">The behavior of the [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<xref:System.Activities.Statements.Pick> activity is similar to the [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]<xref:System.Workflow.Activities.ListenActivity> activity.</span></span>  
  
 <span data-ttu-id="4f552-108">Aşağıdaki ekran görüntüsünden [çekme etkinliğini kullanarak](./samples/using-the-pick-activity.md) SDK'sı örneği bir Pick etkinliği iki dal ile gösterir.</span><span class="sxs-lookup"><span data-stu-id="4f552-108">The following screenshot from the [Using the Pick Activity](./samples/using-the-pick-activity.md) SDK sample shows a Pick activity with two branches.</span></span>  <span data-ttu-id="4f552-109">Bir dal olarak adlandırılan bir tetikleyici sahip **okuma giriş**, komut satırından giriş okuyan özel bir etkinlik.</span><span class="sxs-lookup"><span data-stu-id="4f552-109">One branch has a trigger called **Read input**, a custom activity that reads input from the command line.</span></span> <span data-ttu-id="4f552-110">İkinci dalında olan bir <xref:System.Activities.Statements.Delay> etkinlik tetikleyici.</span><span class="sxs-lookup"><span data-stu-id="4f552-110">The second branch has a <xref:System.Activities.Statements.Delay> activity trigger.</span></span> <span data-ttu-id="4f552-111">Varsa **okuma giriş** etkinlik önce veri aldığında <xref:System.Activities.Statements.Delay> etkinlik bittiğinde <xref:System.Activities.Statements.Delay> gecikme iptal edildi ve bir karşılama konsoluna yazılır.</span><span class="sxs-lookup"><span data-stu-id="4f552-111">If the **Read input** activity receives data before the <xref:System.Activities.Statements.Delay> activity finishes, <xref:System.Activities.Statements.Delay> Delay will be canceled and a greeting will be written to the console.</span></span>  <span data-ttu-id="4f552-112">Aksi takdirde **okuma giriş** etkinlik ayrılan sürede veri almaz sonra iptal edilecek ve bir zaman aşımı iletisi konsoluna yazılır.</span><span class="sxs-lookup"><span data-stu-id="4f552-112">Otherwise, if the **Read input** activity does not receive data in the allotted time, then it will be canceled and a timeout message will be written to the console.</span></span>  <span data-ttu-id="4f552-113">Bu, bir zaman aşımı için herhangi bir eylem eklemek için kullanılan ortak bir desendir.</span><span class="sxs-lookup"><span data-stu-id="4f552-113">This is a common pattern used to add a timeout to any action.</span></span>  
  
 <span data-ttu-id="4f552-114">![Pick etkinliği](./media/pickconceptual.JPG "PickConceptual")</span><span class="sxs-lookup"><span data-stu-id="4f552-114">![Pick Activity](./media/pickconceptual.JPG "PickConceptual")</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="4f552-115">Önerilen uygulamalar</span><span class="sxs-lookup"><span data-stu-id="4f552-115">Best practices</span></span>  
 <span data-ttu-id="4f552-116">Seçim kullanırken, yürütülen dal tetikleyicisini ilk tamamlandıktan daldır.</span><span class="sxs-lookup"><span data-stu-id="4f552-116">When using Pick, the branch that executes is the branch whose trigger completes first.</span></span>  <span data-ttu-id="4f552-117">Kavramsal olarak, tüm tetikleyiciler paralel olarak yürütmek ve başka bir tetikleyici tamamlanmasından tarafından iptal edilmeden önce bir tetikleyici mantığını çoğunu yürütülen.</span><span class="sxs-lookup"><span data-stu-id="4f552-117">Conceptually, all triggers execute in parallel, and one trigger may have executed the majority of its logic before it is canceled by the completion of another trigger.</span></span>  <span data-ttu-id="4f552-118">Tetikleyici temsil eden tek bir olay olarak kabul ve mümkün olduğunca az mantıksal olarak içine yerleştirmek için bunu aklınızda Pick etkinliği kullanma değiştirirken izlemeniz gereken genel kılavuz sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="4f552-118">With this in mind, a general guideline to follow when using the Pick activity is to treat the trigger as representing a single event, and to put as little logic as possible into it.</span></span>  <span data-ttu-id="4f552-119">İdeal olarak, tetikleyici olaya almak için yeterli mantıksal içermelidir ve bu olayın tüm işleme dalın eylemlere tamamlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="4f552-119">Ideally, the trigger should contain just enough logic to receive an event, and all the processing of that event should go into the action of the branch.</span></span>  <span data-ttu-id="4f552-120">Bu yöntem Tetikleyiciler yürütülmesi arasında çakışma miktarını en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="4f552-120">This method minimizes the amount of overlap between the execution of the triggers.</span></span>  <span data-ttu-id="4f552-121">Örneğin, göz önünde bulundurun bir <xref:System.Activities.Statements.Pick> burada her tetikleyicisi içeren iki tetikleyicilerle bir <xref:System.ServiceModel.Activities.Receive> etkinliği izleyen tarafından ilave bir mantık.</span><span class="sxs-lookup"><span data-stu-id="4f552-121">For example, consider a <xref:System.Activities.Statements.Pick> with two triggers, where each trigger contains a <xref:System.ServiceModel.Activities.Receive> activity followed by additional logic.</span></span>  <span data-ttu-id="4f552-122">İlave bir mantık boşta noktanız tanıtır sonra her ikisi de olasılığı yoktur <xref:System.ServiceModel.Activities.Receive> tamamlanmasıyla etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="4f552-122">If the additional logic introduces an idle point, then there is the possibility of both <xref:System.ServiceModel.Activities.Receive> activities completing successfully.</span></span>  <span data-ttu-id="4f552-123">Bir tetikleyici olacak tam olarak tam, başka bir işlem sırasında kısmen tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="4f552-123">One trigger will fully complete, while another will partially complete.</span></span>  <span data-ttu-id="4f552-124">Bazı senaryolarda, bir ileti kabul etmek ve kısmen işlenmesini Tamamlanıyor kabul edilebilir değil.</span><span class="sxs-lookup"><span data-stu-id="4f552-124">In some scenarios, accepting a message, and then partially completing the processing of it is unacceptable.</span></span>  <span data-ttu-id="4f552-125">Bu nedenle, WF yerleşik Mesajlaşma etkinlikleri gibi kullanırken <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply>, ancak <xref:System.ServiceModel.Activities.Receive> tetikleyici, yaygın olarak kullanılan <xref:System.ServiceModel.Activities.SendReply> ve başka bir mantık eylemi mümkün olduğunca koymanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4f552-125">Therefore, when using WF built-in messaging activities such as <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply>, while <xref:System.ServiceModel.Activities.Receive> is commonly used in the trigger, <xref:System.ServiceModel.Activities.SendReply> and other logic should be put in the action whenever possible.</span></span>  
  
## <a name="using-the-pick-activity-in-the-designer"></a><span data-ttu-id="4f552-126">Tasarımcıda Pick etkinliği kullanma</span><span class="sxs-lookup"><span data-stu-id="4f552-126">Using the Pick activity in the designer</span></span>  
 <span data-ttu-id="4f552-127">Çekme Tasarımcısı'nda kullanmak için bulma **çekme** ve **PickBranch** araç.</span><span class="sxs-lookup"><span data-stu-id="4f552-127">To use Pick in the designer, find **Pick** and **PickBranch** in the toolbox.</span></span>  <span data-ttu-id="4f552-128">Sürükle ve bırak **çekme** tuvale.</span><span class="sxs-lookup"><span data-stu-id="4f552-128">Drag and drop **Pick** onto the canvas.</span></span>  <span data-ttu-id="4f552-129">Varsayılan olarak, yeni bir **çekme** etkinlik Tasarımcısı'nda iki dal içerir.</span><span class="sxs-lookup"><span data-stu-id="4f552-129">By default, a new **Pick** Activity in the designer will contain two branches.</span></span>  <span data-ttu-id="4f552-130">Ek dalları eklemek için sürükleyin **PickBranch** etkinlik ve var olan dalların yanındaki bırakın.</span><span class="sxs-lookup"><span data-stu-id="4f552-130">To add additional branches, drag the **PickBranch** activity and drop it next to existing branches.</span></span> <span data-ttu-id="4f552-131">Etkinlikler bırakılan üzerine **çekme** ya da etkinliğini **tetikleyici** alan veya **eylem** herhangi bir bölümünü **PickBranch**.</span><span class="sxs-lookup"><span data-stu-id="4f552-131">Activities can be dropped onto the **Pick** Activity into either the **Trigger** area or the **Action** area of any **PickBranch**.</span></span>  
  
## <a name="using-the-pick-activity-in-code"></a><span data-ttu-id="4f552-132">Kodda çekme etkinliği kullanma</span><span class="sxs-lookup"><span data-stu-id="4f552-132">Using the Pick Activity in code</span></span>  
 <span data-ttu-id="4f552-133"><xref:System.Activities.Statements.Pick> Etkinliği doldurarak kullanılır, <xref:System.Activities.Statements.Pick.Branches%2A> koleksiyonuyla <xref:System.Activities.Statements.PickBranch> etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="4f552-133">The <xref:System.Activities.Statements.Pick> activity is used by populating its <xref:System.Activities.Statements.Pick.Branches%2A> collection with <xref:System.Activities.Statements.PickBranch> activities.</span></span> <span data-ttu-id="4f552-134"><xref:System.Activities.Statements.PickBranch> Etkinliklerin her bir <xref:System.Activities.Statements.PickBranch.Trigger%2A> türünün özelliği <xref:System.Activities.Activity>.</span><span class="sxs-lookup"><span data-stu-id="4f552-134">The <xref:System.Activities.Statements.PickBranch> activities each have a <xref:System.Activities.Statements.PickBranch.Trigger%2A> property of type <xref:System.Activities.Activity>.</span></span> <span data-ttu-id="4f552-135">Belirtilen Etkinlik yürütme tamamlandığında <xref:System.Activities.Statements.PickBranch.Action%2A> yürütür.</span><span class="sxs-lookup"><span data-stu-id="4f552-135">When the specified activity completes execution, the <xref:System.Activities.Statements.PickBranch.Action%2A> executes.</span></span>  
  
 <span data-ttu-id="4f552-136">Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir. bir <xref:System.Activities.Statements.Pick> konsoldan bir satır okur bir etkinlik için bir zaman aşımı uygulamak için etkinlik.</span><span class="sxs-lookup"><span data-stu-id="4f552-136">The following code example demonstrates how to use a <xref:System.Activities.Statements.Pick> activity to implement a timeout for an activity that reads a line from the console.</span></span>  
  
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
