---
title: Akış Çizelgesi İş Akışları
ms.date: 03/30/2017
ms.assetid: b0a3475c-d22f-49eb-8912-973c960aebf5
ms.openlocfilehash: 1840f677929509e4902498c5aa8920f49cb13496
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773600"
---
# <a name="flowchart-workflows"></a><span data-ttu-id="5deba-102">Akış Çizelgesi İş Akışları</span><span class="sxs-lookup"><span data-stu-id="5deba-102">Flowchart Workflows</span></span>

<span data-ttu-id="5deba-103">Bir akış programları tasarlamak için iyi bilinen bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="5deba-103">A flowchart is a well-known paradigm for designing programs.</span></span> <span data-ttu-id="5deba-104">Akış Çizelgesi etkinlik genellikle sıralı olmayan bir iş akışları uygulamak için kullanılır, ancak hiçbir sıralı iş akışları için kullanılabilir `FlowDecision` düğümleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5deba-104">The Flowchart activity is typically used to implement non-sequential workflows, but can be used for sequential workflows if no `FlowDecision` nodes are used.</span></span>

## <a name="flowchart-workflow-structure"></a><span data-ttu-id="5deba-105">Akış Çizelgesi iş akışı yapısı</span><span class="sxs-lookup"><span data-stu-id="5deba-105">Flowchart workflow structure</span></span>

 <span data-ttu-id="5deba-106">Akış Çizelgesi etkinliğine etkinlikleri yürütülecek bir koleksiyonunu içeren bir etkinliktir.</span><span class="sxs-lookup"><span data-stu-id="5deba-106">A Flowchart activity is an activity that contains a collection of activities to be executed.</span></span>  <span data-ttu-id="5deba-107">Akış çizelgeleri de içeren akış denetimi öğeleri gibi <xref:System.Activities.Statements.FlowDecision> ve <xref:System.Activities.Statements.FlowSwitch%601> yürütme değişkenlerin değerlerini temel alan bağımsız etkinlikler arasında doğrudan.</span><span class="sxs-lookup"><span data-stu-id="5deba-107">Flowcharts also contain flow control elements such as <xref:System.Activities.Statements.FlowDecision> and <xref:System.Activities.Statements.FlowSwitch%601> that direct execution between contained activities based on the values of variables.</span></span>

## <a name="types-of-flow-nodes"></a><span data-ttu-id="5deba-108">Akış düğüm türleri</span><span class="sxs-lookup"><span data-stu-id="5deba-108">Types of flow nodes</span></span>

 <span data-ttu-id="5deba-109">Farklı türde öğeler akış denetimi öğe yürütüldüğünde gerekli türüne bağlı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5deba-109">Different types of elements are used depending on the type of flow control required when the element executes.</span></span> <span data-ttu-id="5deba-110">Akış öğeleri türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5deba-110">Types of flowchart elements include:</span></span>

- <span data-ttu-id="5deba-111">`FlowStep` -Bir adım akış yürütmesinin modeller.</span><span class="sxs-lookup"><span data-stu-id="5deba-111">`FlowStep` - Models one step of execution in the flowchart.</span></span>

- <span data-ttu-id="5deba-112">`FlowDecision` -Bir Boolean koşulu, benzer şekilde temel dalları yürütme <xref:System.Activities.Statements.If>.</span><span class="sxs-lookup"><span data-stu-id="5deba-112">`FlowDecision` - Branches execution based on a Boolean condition, similar to <xref:System.Activities.Statements.If>.</span></span>

- <span data-ttu-id="5deba-113">`FlowSwitch` – Dalları yürütme, benzer özel bir anahtarı temelinde <xref:System.Activities.Statements.Switch%601>.</span><span class="sxs-lookup"><span data-stu-id="5deba-113">`FlowSwitch` – Branches execution based on an exclusive switch, similar to <xref:System.Activities.Statements.Switch%601>.</span></span>

<span data-ttu-id="5deba-114">Her bir bağlantısı olan bir `Action` tanımlayan özellik bir <xref:System.Activities.ActivityAction> alt etkinlikleri ve bir veya daha fazla yürütmek için kullanılabilir `Next` hangi öğe veya öğe geçerli öğe yürütülmesi tamamlandığında yürütülecek tanımlayan özellikleri.</span><span class="sxs-lookup"><span data-stu-id="5deba-114">Each link has an `Action` property that defines a <xref:System.Activities.ActivityAction> that can be used to execute child activities, and one or more `Next` properties that define which element or elements to execute when the current element finishes execution.</span></span>

### <a name="creating-a-basic-activity-sequence-with-a-flowstep-node"></a><span data-ttu-id="5deba-115">Temel etkinlik dizisini FlowStep düğümle oluşturma</span><span class="sxs-lookup"><span data-stu-id="5deba-115">Creating a basic activity sequence with a FlowStep node</span></span>

<span data-ttu-id="5deba-116">İçinde iki etkinlikleri yürütmek sırayla, temel bir sıralı model `FlowStep` öğe kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5deba-116">To model a basic sequence in which two activities execute in turn, the `FlowStep` element is used.</span></span> <span data-ttu-id="5deba-117">Aşağıdaki örnekte, iki `FlowStep` öğeleri iki etkinlikleri sırayla yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5deba-117">In the following example, two `FlowStep` elements are used to execute two activities in sequence.</span></span>

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

### <a name="creating-a-conditional-flowchart-with-a-flowdecision-node"></a><span data-ttu-id="5deba-118">FlowDecision düğümle koşullu bir akış oluşturma</span><span class="sxs-lookup"><span data-stu-id="5deba-118">Creating a conditional flowchart with a FlowDecision node</span></span>

<span data-ttu-id="5deba-119">Bir akış çizelgesi iş akışı koşullu akış düğümünde modellemek için (diğer bir deyişle, geleneksel bir akış kişinin kararı simgesi olarak işlevleri bir bağlantı oluşturmak için), <xref:System.Activities.Statements.FlowDecision> düğümü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5deba-119">To model a conditional flow node in a flowchart workflow (that is, to create a link that functions as a traditional flowchart's decision symbol), a <xref:System.Activities.Statements.FlowDecision> node is used.</span></span> <span data-ttu-id="5deba-120"><xref:System.Activities.Statements.FlowDecision.Condition%2A> Düğümün özelliği koşulu tanımlayan bir ifade kümesi ve <xref:System.Activities.Statements.FlowDecision.True%2A> ve <xref:System.Activities.Statements.FlowDecision.False%2A> özelliklerinin <xref:System.Activities.Statements.FlowNode> ifade değerlendirilirse yürütülecek örnekleri `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="5deba-120">The <xref:System.Activities.Statements.FlowDecision.Condition%2A> property of the node is set to an expression that defines the condition, and the <xref:System.Activities.Statements.FlowDecision.True%2A> and <xref:System.Activities.Statements.FlowDecision.False%2A> properties are set to <xref:System.Activities.Statements.FlowNode> instances to be executed if the expression evaluates to `true` or `false`.</span></span> <span data-ttu-id="5deba-121">Aşağıdaki örnek, kullanan bir iş akışı tanımlamak gösterilmiştir bir <xref:System.Activities.Statements.FlowDecision> düğümü.</span><span class="sxs-lookup"><span data-stu-id="5deba-121">The following example shows how to define a workflow that uses a <xref:System.Activities.Statements.FlowDecision> node.</span></span>

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

### <a name="creating-an-exclusive-switch-with-a-flowswitch-node"></a><span data-ttu-id="5deba-122">FlowSwitch düğümle bir özel anahtarı oluşturma</span><span class="sxs-lookup"><span data-stu-id="5deba-122">Creating an exclusive switch with a FlowSwitch node</span></span>

<span data-ttu-id="5deba-123">Bir akış içinde bir özel yol seçili temel üzerinde eşleşen bir değeri, model <xref:System.Activities.Statements.FlowSwitch%601> düğümü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5deba-123">To model a flowchart in which one exclusive path is selected based on a matching value, the <xref:System.Activities.Statements.FlowSwitch%601> node is used.</span></span> <span data-ttu-id="5deba-124"><xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> Özelliği bir <xref:System.Activities.Activity%601> bir tür parametresi ile <xref:System.Object> karşı seçenek değerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5deba-124">The <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> property is set to a <xref:System.Activities.Activity%601> with a type parameter of <xref:System.Object> that defines the value to match choices against.</span></span> <span data-ttu-id="5deba-125"><xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> Özelliği anahtarları sözlüğü tanımlar ve <xref:System.Activities.Statements.FlowNode> koşullu ifadesi ve bir dizi karşı eşleştirilecek nesneleri <xref:System.Activities.Statements.FlowNode> verilen durumu koşullu ifade eşleşiyorsa yürütme nasıl akışını tanımlayan nesne.</span><span class="sxs-lookup"><span data-stu-id="5deba-125">The <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> property defines a dictionary of keys and <xref:System.Activities.Statements.FlowNode> objects to match against the conditional expression, and a set of <xref:System.Activities.Statements.FlowNode> objects that define how execution should flow if the given case matches the conditional expression.</span></span> <span data-ttu-id="5deba-126"><xref:System.Activities.Statements.FlowSwitch%601> Ayrıca tanımlayan bir <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> hiçbir servis talebi koşul ifadesi eşleşiyorsa yürütme nasıl akışını tanımlayan özellik.</span><span class="sxs-lookup"><span data-stu-id="5deba-126">The <xref:System.Activities.Statements.FlowSwitch%601> also defines a <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> property that defines how execution should flow if no cases match the condition expression.</span></span> <span data-ttu-id="5deba-127">Aşağıdaki örnek, kullanan bir iş akışı tanımlamak gösterilmiştir bir <xref:System.Activities.Statements.FlowSwitch%601> öğesi.</span><span class="sxs-lookup"><span data-stu-id="5deba-127">The following example demonstrates how to define a workflow that uses a <xref:System.Activities.Statements.FlowSwitch%601> element.</span></span>

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
