---
title: Akış Çizelgesi İş Akışları
description: Bu makalede, genellikle Workflow Foundation 'da ardışık olmayan iş akışlarını uygulamak için kullanılan akış çizelgesi etkinliği açıklanmaktadır.
ms.date: 03/30/2017
ms.assetid: b0a3475c-d22f-49eb-8912-973c960aebf5
ms.openlocfilehash: ce0661653a1d50b3f7264246b810faabbd12bf5f
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419921"
---
# <a name="flowchart-workflows"></a><span data-ttu-id="538c5-103">Akış Çizelgesi İş Akışları</span><span class="sxs-lookup"><span data-stu-id="538c5-103">Flowchart Workflows</span></span>

<span data-ttu-id="538c5-104">Akış çizelgesi, programları tasarlamak için iyi bilinen bir paradigdır.</span><span class="sxs-lookup"><span data-stu-id="538c5-104">A flowchart is a well-known paradigm for designing programs.</span></span> <span data-ttu-id="538c5-105">Akış çizelgesi etkinliği genellikle sıralı olmayan iş akışlarını uygulamak için kullanılır, ancak hiçbir düğüm kullanılmazsa sıralı iş akışları için kullanılabilir `FlowDecision` .</span><span class="sxs-lookup"><span data-stu-id="538c5-105">The Flowchart activity is typically used to implement non-sequential workflows, but can be used for sequential workflows if no `FlowDecision` nodes are used.</span></span>

## <a name="flowchart-workflow-structure"></a><span data-ttu-id="538c5-106">Akış çizelgesi iş akışı yapısı</span><span class="sxs-lookup"><span data-stu-id="538c5-106">Flowchart workflow structure</span></span>

 <span data-ttu-id="538c5-107">Akış çizelgesi etkinliği, yürütülecek etkinlik koleksiyonunu içeren bir etkinliktir.</span><span class="sxs-lookup"><span data-stu-id="538c5-107">A Flowchart activity is an activity that contains a collection of activities to be executed.</span></span>  <span data-ttu-id="538c5-108">Akış çizelgeleri Ayrıca gibi akış denetim öğelerini <xref:System.Activities.Statements.FlowDecision> ve <xref:System.Activities.Statements.FlowSwitch%601> bağımsız etkinlikler arasında değişken değerlerine göre doğrudan yürütmeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="538c5-108">Flowcharts also contain flow control elements such as <xref:System.Activities.Statements.FlowDecision> and <xref:System.Activities.Statements.FlowSwitch%601> that direct execution between contained activities based on the values of variables.</span></span>

## <a name="types-of-flow-nodes"></a><span data-ttu-id="538c5-109">Akış düğümleri türleri</span><span class="sxs-lookup"><span data-stu-id="538c5-109">Types of flow nodes</span></span>

 <span data-ttu-id="538c5-110">Farklı öğe türleri, öğe yürütüldüğünde gereken akış denetimi türüne bağlı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="538c5-110">Different types of elements are used depending on the type of flow control required when the element executes.</span></span> <span data-ttu-id="538c5-111">Akış çizelgesi öğelerinin türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="538c5-111">Types of flowchart elements include:</span></span>

- <span data-ttu-id="538c5-112">`FlowStep`-Akış çizelgesinde bir yürütme adımını modeller.</span><span class="sxs-lookup"><span data-stu-id="538c5-112">`FlowStep` - Models one step of execution in the flowchart.</span></span>

- <span data-ttu-id="538c5-113">`FlowDecision`-Öğesine benzer bir Boolean koşulu temelinde dal yürütme <xref:System.Activities.Statements.If> .</span><span class="sxs-lookup"><span data-stu-id="538c5-113">`FlowDecision` - Branches execution based on a Boolean condition, similar to <xref:System.Activities.Statements.If>.</span></span>

- <span data-ttu-id="538c5-114">`FlowSwitch`– Öğesine benzer şekilde, özel bir anahtara göre dal yürütme <xref:System.Activities.Statements.Switch%601> .</span><span class="sxs-lookup"><span data-stu-id="538c5-114">`FlowSwitch` – Branches execution based on an exclusive switch, similar to <xref:System.Activities.Statements.Switch%601>.</span></span>

<span data-ttu-id="538c5-115">Her bağlantı `Action` <xref:System.Activities.ActivityAction> , alt etkinlikleri yürütmek için kullanılabilecek bir özelliğini ve `Next` geçerli öğe yürütmeyi bitirdiğinde hangi öğe veya öğelerin yürütüleceğini tanımlayan bir veya daha fazla özelliği içerir.</span><span class="sxs-lookup"><span data-stu-id="538c5-115">Each link has an `Action` property that defines a <xref:System.Activities.ActivityAction> that can be used to execute child activities, and one or more `Next` properties that define which element or elements to execute when the current element finishes execution.</span></span>

### <a name="creating-a-basic-activity-sequence-with-a-flowstep-node"></a><span data-ttu-id="538c5-116">FlowStep düğümü ile temel etkinlik dizisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="538c5-116">Creating a basic activity sequence with a FlowStep node</span></span>

<span data-ttu-id="538c5-117">İki etkinliğin sırayla yürütüleceği temel bir diziyi modellemek için, `FlowStep` öğesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="538c5-117">To model a basic sequence in which two activities execute in turn, the `FlowStep` element is used.</span></span> <span data-ttu-id="538c5-118">Aşağıdaki örnekte iki `FlowStep` öğe sırayla iki etkinlik yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="538c5-118">In the following example, two `FlowStep` elements are used to execute two activities in sequence.</span></span>

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
        <WriteLine Text="Hello, " & [result]/>
      </FlowStep>
    </FlowStep.Next>
  </FlowStep>
</Flowchart>
```

### <a name="creating-a-conditional-flowchart-with-a-flowdecision-node"></a><span data-ttu-id="538c5-119">Flowkarar düğümüyle koşullu bir akış çizelgesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="538c5-119">Creating a conditional flowchart with a FlowDecision node</span></span>

<span data-ttu-id="538c5-120">Bir akış çizelgesi iş akışında koşullu akış düğümünü modellemek için (diğer bir deyişle, geleneksel akış çizelgesinin karar simgesi olarak işlev gören bir bağlantı oluşturmak için), bir <xref:System.Activities.Statements.FlowDecision> düğüm kullanılır.</span><span class="sxs-lookup"><span data-stu-id="538c5-120">To model a conditional flow node in a flowchart workflow (that is, to create a link that functions as a traditional flowchart's decision symbol), a <xref:System.Activities.Statements.FlowDecision> node is used.</span></span> <span data-ttu-id="538c5-121"><xref:System.Activities.Statements.FlowDecision.Condition%2A>Düğümünün özelliği, koşulu tanımlayan bir ifadeye ayarlanır ve <xref:System.Activities.Statements.FlowDecision.True%2A> <xref:System.Activities.Statements.FlowDecision.False%2A> <xref:System.Activities.Statements.FlowNode> ifade veya olarak değerlendirilirse, ve özellikleri yürütülecek örneklere ayarlanır `true` `false` .</span><span class="sxs-lookup"><span data-stu-id="538c5-121">The <xref:System.Activities.Statements.FlowDecision.Condition%2A> property of the node is set to an expression that defines the condition, and the <xref:System.Activities.Statements.FlowDecision.True%2A> and <xref:System.Activities.Statements.FlowDecision.False%2A> properties are set to <xref:System.Activities.Statements.FlowNode> instances to be executed if the expression evaluates to `true` or `false`.</span></span> <span data-ttu-id="538c5-122">Aşağıdaki örnek, bir düğümü kullanan bir iş akışının nasıl tanımlanacağını gösterir <xref:System.Activities.Statements.FlowDecision> .</span><span class="sxs-lookup"><span data-stu-id="538c5-122">The following example shows how to define a workflow that uses a <xref:System.Activities.Statements.FlowDecision> node.</span></span>

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

### <a name="creating-an-exclusive-switch-with-a-flowswitch-node"></a><span data-ttu-id="538c5-123">FlowSwitch düğümü ile dışlamalı anahtar oluşturma</span><span class="sxs-lookup"><span data-stu-id="538c5-123">Creating an exclusive switch with a FlowSwitch node</span></span>

<span data-ttu-id="538c5-124">Eşleşen bir değere göre özel bir yolun seçildiği bir akış çizelgesini modellemek için, <xref:System.Activities.Statements.FlowSwitch%601> düğüm kullanılır.</span><span class="sxs-lookup"><span data-stu-id="538c5-124">To model a flowchart in which one exclusive path is selected based on a matching value, the <xref:System.Activities.Statements.FlowSwitch%601> node is used.</span></span> <span data-ttu-id="538c5-125"><xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>Özelliği, <xref:System.Activities.Activity%601> <xref:System.Object> seçimleri ile eşleşecek değeri tanımlayan bir tür parametresi olan öğesine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="538c5-125">The <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> property is set to a <xref:System.Activities.Activity%601> with a type parameter of <xref:System.Object> that defines the value to match choices against.</span></span> <span data-ttu-id="538c5-126"><xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>Özelliği <xref:System.Activities.Statements.FlowNode> , koşullu ifadeyle eşleşecek anahtar ve nesnelerin sözlüğünü ve <xref:System.Activities.Statements.FlowNode> verilen Case koşullu ifadeyle eşleşiyorsa yürütmenin nasıl akmasını tanımlayan bir nesne kümesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="538c5-126">The <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> property defines a dictionary of keys and <xref:System.Activities.Statements.FlowNode> objects to match against the conditional expression, and a set of <xref:System.Activities.Statements.FlowNode> objects that define how execution should flow if the given case matches the conditional expression.</span></span> <span data-ttu-id="538c5-127"><xref:System.Activities.Statements.FlowSwitch%601>Ayrıca, <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> koşul ifadesiyle eşleşen hiçbir durum yoksa yürütmenin nasıl akmasını tanımlayan bir özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="538c5-127">The <xref:System.Activities.Statements.FlowSwitch%601> also defines a <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> property that defines how execution should flow if no cases match the condition expression.</span></span> <span data-ttu-id="538c5-128">Aşağıdaki örnek, bir öğesi kullanan bir iş akışının nasıl tanımlanacağını göstermektedir <xref:System.Activities.Statements.FlowSwitch%601> .</span><span class="sxs-lookup"><span data-stu-id="538c5-128">The following example demonstrates how to define a workflow that uses a <xref:System.Activities.Statements.FlowSwitch%601> element.</span></span>

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
