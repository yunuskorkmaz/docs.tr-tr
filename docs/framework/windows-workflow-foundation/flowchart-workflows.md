---
title: "Akış Çizelgesi iş akışları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0a3475c-d22f-49eb-8912-973c960aebf5
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d5975cff014c1d74b9935a7cc95a6b2f25359db5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="flowchart-workflows"></a><span data-ttu-id="2e598-102">Akış Çizelgesi iş akışları</span><span class="sxs-lookup"><span data-stu-id="2e598-102">Flowchart Workflows</span></span>
<span data-ttu-id="2e598-103">Bir akış çizelgesi, programları tasarlamak için iyi bilinen bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="2e598-103">A flowchart is a well-known paradigm for designing programs.</span></span> <span data-ttu-id="2e598-104">Akış etkinliği genellikle sıralı olmayan iş akışları uygulamak için kullanılır, ancak sıralı iş akışları için hiç kullanılabilir `FlowDecision` düğümleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2e598-104">The Flowchart activity is typically used to implement non-sequential workflows, but can be used for sequential workflows if no `FlowDecision` nodes are used.</span></span>  
  
## <a name="flowchart-workflow-structure"></a><span data-ttu-id="2e598-105">Akış iş akışı yapısı</span><span class="sxs-lookup"><span data-stu-id="2e598-105">Flowchart Workflow Structure</span></span>  
 <span data-ttu-id="2e598-106">Bir akış etkinliği yürütülecek etkinlikleri koleksiyonunu içeren bir etkinliktir.</span><span class="sxs-lookup"><span data-stu-id="2e598-106">A Flowchart activity is an activity that contains a collection of activities to be executed.</span></span>  <span data-ttu-id="2e598-107">Akış çizelgeleri de içeren akış denetimi öğeleri gibi <xref:System.Activities.Statements.FlowDecision> ve <xref:System.Activities.Statements.FlowSwitch%601> yürütme değişkenleri değerlerine göre içerilen etkinlikler arasında doğrudan.</span><span class="sxs-lookup"><span data-stu-id="2e598-107">Flowcharts also contain flow control elements such as <xref:System.Activities.Statements.FlowDecision> and <xref:System.Activities.Statements.FlowSwitch%601> that direct execution between contained activities based on the values of variables.</span></span>  
  
## <a name="types-of-flow-nodes"></a><span data-ttu-id="2e598-108">Akış düğüm türleri</span><span class="sxs-lookup"><span data-stu-id="2e598-108">Types of Flow Nodes</span></span>  
 <span data-ttu-id="2e598-109">Farklı türde öğeler öğe yürüttüğünde gerekli akış denetimi türüne bağlı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2e598-109">Different types of elements are used depending on the type of flow control required when the element executes.</span></span> <span data-ttu-id="2e598-110">Akış Çizelgesi öğelerinin türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="2e598-110">Types of flowchart elements include:</span></span>  
  
-   <span data-ttu-id="2e598-111">`FlowStep`-Tek bir adımda akış yürütme modeller.</span><span class="sxs-lookup"><span data-stu-id="2e598-111">`FlowStep` - Models one step of execution in the flowchart.</span></span>  
  
-   <span data-ttu-id="2e598-112">`FlowDecision`-Dalları yürütme temel alarak, benzer Boolean bir koşul <xref:System.Activities.Statements.If>.</span><span class="sxs-lookup"><span data-stu-id="2e598-112">`FlowDecision` - Branches execution based on a Boolean condition, similar to <xref:System.Activities.Statements.If>.</span></span>  
  
-   <span data-ttu-id="2e598-113">`FlowSwitch`– Dalları yürütme temel alarak, benzer özel bir anahtar <xref:System.Activities.Statements.Switch%601>.</span><span class="sxs-lookup"><span data-stu-id="2e598-113">`FlowSwitch` – Branches execution based on an exclusive switch, similar to <xref:System.Activities.Statements.Switch%601>.</span></span>  
  
 <span data-ttu-id="2e598-114">Her bir bağlantısı olan bir `Action` tanımlayan özelliğini bir <xref:System.Activities.ActivityAction> alt etkinlikler ve bir veya daha fazla yürütmek için kullanılabilir `Next` hangi öğesi veya öğeleri geçerli öğe yürütme tamamlandığında yürütmek için tanımlayan özellikleri.</span><span class="sxs-lookup"><span data-stu-id="2e598-114">Each link has an `Action` property that defines a <xref:System.Activities.ActivityAction> that can be used to execute child activities, and one or more `Next` properties that define which element or elements to execute when the current element finishes execution.</span></span>  
  
### <a name="creating-a-basic-activity-sequence-with-a-flowstep-node"></a><span data-ttu-id="2e598-115">Temel etkinlik dizisi olan bir FlowStep düğümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="2e598-115">Creating a Basic Activity Sequence with a FlowStep Node</span></span>  
 <span data-ttu-id="2e598-116">İçinde iki etkinlikleri yürütmek sırayla temel sıralı modellemek için `FlowStep` öğe kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2e598-116">To model a basic sequence in which two activities execute in turn, the `FlowStep` element is used.</span></span> <span data-ttu-id="2e598-117">Aşağıdaki örnekte, iki `FlowStep` öğeleri iki etkinlikleri sırayla yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2e598-117">In the following example, two `FlowStep` elements are used to execute two activities in sequence.</span></span>  
  
```xml  
<Flowchart>  
  <FlowStep>      
  <Assign DisplayName="Get Name">  
    <Assign.To>  
      <OutArgument x:TypeArguments="x:String">[result]</OutArgument>  
    </Assign.To>  
    <Assign.Value>  
      <InArgument x:TypeArguments="x:String">["User"]</InArgument>  
    </Assign.Value>  
  </Assign>  
    <FlowStep.Next>  
      <FlowStep>  
        <WriteLine Text="["Hello, " & result]"/>  
</FlowStep>  
    </FlowStep.Next>  
  </FlowStep>  
</Flowchart>  
```  
  
### <a name="creating-a-conditional-flowchart-with-a-flowdecision-node"></a><span data-ttu-id="2e598-118">Koşullu bir akış çizelgesi FlowDecision düğümle oluşturma</span><span class="sxs-lookup"><span data-stu-id="2e598-118">Creating a Conditional Flowchart with a FlowDecision Node</span></span>  
 <span data-ttu-id="2e598-119">Bir akış iş akışı koşullu akışı düğümünde modellemek için (diğer bir deyişle, geleneksel akış grafiği 's karar simgesi olarak işlevleri bir bağlantı oluşturmak için), bir <xref:System.Activities.Statements.FlowDecision> düğümü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2e598-119">To model a conditional flow node in a flowchart workflow (that is, to create a link that functions as a traditional flowchart's decision symbol), a <xref:System.Activities.Statements.FlowDecision> node is used.</span></span> <span data-ttu-id="2e598-120"><xref:System.Activities.Statements.FlowDecision.Condition%2A> Özelliği düğümün durumu tanımlayan bir ifade ayarlanır ve <xref:System.Activities.Statements.FlowDecision.True%2A> ve <xref:System.Activities.Statements.FlowDecision.False%2A> özelliklerinin <xref:System.Activities.Statements.FlowNode> ifade değerlendirilirse yürütülecek örnekleri `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="2e598-120">The <xref:System.Activities.Statements.FlowDecision.Condition%2A> property of the node is set to an expression that defines the condition, and the <xref:System.Activities.Statements.FlowDecision.True%2A> and <xref:System.Activities.Statements.FlowDecision.False%2A> properties are set to <xref:System.Activities.Statements.FlowNode> instances to be executed if the expression evaluates to `true` or `false`.</span></span> <span data-ttu-id="2e598-121">Aşağıdaki örnek kullanan bir iş akışı tanımlamak nasıl gösterir bir <xref:System.Activities.Statements.FlowDecision> düğümü.</span><span class="sxs-lookup"><span data-stu-id="2e598-121">The following example shows how to define a workflow that uses a <xref:System.Activities.Statements.FlowDecision> node.</span></span>  
  
```xml  
<Flowchart>  
  <FlowStep>  
    <Read Result="[s]"/>  
    <FlowStep.Next>  
      <FlowDecision>  
        <IsEmpty Input="[s]" />  
        <FlowDecision.True>  
    <FlowStep>  
            <Write Text="Empty"/>  
    </FlowStep>  
        </FlowDecision.True>  
        <FlowDecision.False>  
    <FlowStep>  
            <Write Text="Non-Empty"/>  
          </FlowStep>  
        </FlowDecision.False>  
      </FlowDecision>  
    </FlowStep.Next>  
  </FlowStep>  
</Flowchart>  
```  
  
### <a name="creating-an-exclusive-switch-with-a-flowswitch-node"></a><span data-ttu-id="2e598-122">Bir özel anahtarı olan bir FlowSwitch düğümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="2e598-122">Creating an Exclusive Switch with a FlowSwitch Node</span></span>  
 <span data-ttu-id="2e598-123">İçinde bir özel yol seçili dayalı eşleşen bir değeri bir akış çizelgesi modellemek için <xref:System.Activities.Statements.FlowSwitch%601> düğümü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2e598-123">To model a flowchart in which one exclusive path is selected based on a matching value, the <xref:System.Activities.Statements.FlowSwitch%601> node is used.</span></span> <span data-ttu-id="2e598-124"><xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> Özelliği ayarlanmış bir <xref:System.Activities.Activity%601> bir tür parametresi ile <xref:System.Object> karşı seçimler eşleşecek değer tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2e598-124">The <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> property is set to a <xref:System.Activities.Activity%601> with a type parameter of <xref:System.Object> that defines the value to match choices against.</span></span> <span data-ttu-id="2e598-125"><xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> Özellik anahtarları sözlüğü tanımlar ve <xref:System.Activities.Statements.FlowNode> koşullu ifade ve bir dizi karşı eşleşecek şekilde nesneleri <xref:System.Activities.Statements.FlowNode> verilen durumu koşullu ifade eşleşirse yürütme nasıl gerçekleştiğini tanımlayan nesneleri.</span><span class="sxs-lookup"><span data-stu-id="2e598-125">The <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> property defines a dictionary of keys and <xref:System.Activities.Statements.FlowNode> objects to match against the conditional expression, and a set of <xref:System.Activities.Statements.FlowNode> objects that define how execution should flow if the given case matches the conditional expression.</span></span> <span data-ttu-id="2e598-126"><xref:System.Activities.Statements.FlowSwitch%601> De tanımlayan bir <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> hiçbir örnek koşul ifadesi eşleşiyorsa yürütme nasıl gerçekleştiğini tanımlar özelliği.</span><span class="sxs-lookup"><span data-stu-id="2e598-126">The <xref:System.Activities.Statements.FlowSwitch%601> also defines a <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> property that defines how execution should flow if no cases match the condition expression.</span></span> <span data-ttu-id="2e598-127">Aşağıdaki örnek kullanan bir iş akışı tanımlamak gösterilmiştir bir <xref:System.Activities.Statements.FlowSwitch%601> öğesi.</span><span class="sxs-lookup"><span data-stu-id="2e598-127">The following example demonstrates how to define a workflow that uses a <xref:System.Activities.Statements.FlowSwitch%601> element.</span></span>  
  
```xml  
<Flowchart>  
    <FlowSwitch>  
      <FlowStep x:Key="Red">  
        <WriteRed/>  
      </FlowStep>  
      <FlowStep x:Key="Blue">  
        <WriteBlue/>  
      </FlowStep>  
      <FlowStep x:Key="Green">  
        <WriteGreen/>  
      </FlowStep>  
    </FlowSwitch>  
</Flowchart>  
```
