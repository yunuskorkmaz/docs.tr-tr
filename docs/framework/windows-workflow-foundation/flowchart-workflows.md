---
title: Akış Çizelgesi İş Akışları
ms.date: 03/30/2017
ms.assetid: b0a3475c-d22f-49eb-8912-973c960aebf5
ms.openlocfilehash: b84b0de34f8869d9775fe0694e74c340cc16a6b3
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249070"
---
# <a name="flowchart-workflows"></a><span data-ttu-id="84344-102">Akış Çizelgesi İş Akışları</span><span class="sxs-lookup"><span data-stu-id="84344-102">Flowchart Workflows</span></span>

<span data-ttu-id="84344-103">Akış şeması, programlar tasarlamak için iyi bilinen bir paradigmadır.</span><span class="sxs-lookup"><span data-stu-id="84344-103">A flowchart is a well-known paradigm for designing programs.</span></span> <span data-ttu-id="84344-104">Akış Şeması etkinliği genellikle sıralı olmayan iş akışlarını uygulamak için kullanılır, ancak `FlowDecision` düğüm kullanılmazsa sıralı iş akışları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="84344-104">The Flowchart activity is typically used to implement non-sequential workflows, but can be used for sequential workflows if no `FlowDecision` nodes are used.</span></span>

## <a name="flowchart-workflow-structure"></a><span data-ttu-id="84344-105">Akış şeması iş akışı yapısı</span><span class="sxs-lookup"><span data-stu-id="84344-105">Flowchart workflow structure</span></span>

 <span data-ttu-id="84344-106">Akış Şeması etkinliği, yürütülecek bir etkinlik koleksiyonu içeren bir etkinliktir.</span><span class="sxs-lookup"><span data-stu-id="84344-106">A Flowchart activity is an activity that contains a collection of activities to be executed.</span></span>  <span data-ttu-id="84344-107">Akış şemaları, değişkenlerin <xref:System.Activities.Statements.FlowDecision> değerlerine dayalı olarak içerdiği etkinlikler arasında doğrudan yürütme gibi akış <xref:System.Activities.Statements.FlowSwitch%601> kontrol öğeleri de içerir.</span><span class="sxs-lookup"><span data-stu-id="84344-107">Flowcharts also contain flow control elements such as <xref:System.Activities.Statements.FlowDecision> and <xref:System.Activities.Statements.FlowSwitch%601> that direct execution between contained activities based on the values of variables.</span></span>

## <a name="types-of-flow-nodes"></a><span data-ttu-id="84344-108">Akış düğümleri türleri</span><span class="sxs-lookup"><span data-stu-id="84344-108">Types of flow nodes</span></span>

 <span data-ttu-id="84344-109">Eleman yürüdüğünde gereken akış denetimi türüne bağlı olarak farklı türde öğeler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="84344-109">Different types of elements are used depending on the type of flow control required when the element executes.</span></span> <span data-ttu-id="84344-110">Akış şeması öğelerinin türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="84344-110">Types of flowchart elements include:</span></span>

- <span data-ttu-id="84344-111">`FlowStep`- Akış şemasında bir yürütme adımı modeller.</span><span class="sxs-lookup"><span data-stu-id="84344-111">`FlowStep` - Models one step of execution in the flowchart.</span></span>

- <span data-ttu-id="84344-112">`FlowDecision`- Boolean durumuna göre dal yürütme, benzer <xref:System.Activities.Statements.If>.</span><span class="sxs-lookup"><span data-stu-id="84344-112">`FlowDecision` - Branches execution based on a Boolean condition, similar to <xref:System.Activities.Statements.If>.</span></span>

- <span data-ttu-id="84344-113">`FlowSwitch`– Özel bir anahtara dayalı <xref:System.Activities.Statements.Switch%601>şube yürütme, benzer .</span><span class="sxs-lookup"><span data-stu-id="84344-113">`FlowSwitch` – Branches execution based on an exclusive switch, similar to <xref:System.Activities.Statements.Switch%601>.</span></span>

<span data-ttu-id="84344-114">Her bağlantı, `Action` alt etkinlikleri <xref:System.Activities.ActivityAction> yürütmek için kullanılabilecek bir özelliği tanımlayan bir `Next` özelliğe ve geçerli öğe yürütmeyi bitirdiğinde hangi öğenin veya öğelerin yürütülmesini tanımlayan bir veya daha fazla özelliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="84344-114">Each link has an `Action` property that defines a <xref:System.Activities.ActivityAction> that can be used to execute child activities, and one or more `Next` properties that define which element or elements to execute when the current element finishes execution.</span></span>

### <a name="creating-a-basic-activity-sequence-with-a-flowstep-node"></a><span data-ttu-id="84344-115">FlowStep düğümüyle temel etkinlik dizisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="84344-115">Creating a basic activity sequence with a FlowStep node</span></span>

<span data-ttu-id="84344-116">İki işlemin sırayla yürütüldettiği temel `FlowStep` bir diziyi modellemek için öğe kullanılır.</span><span class="sxs-lookup"><span data-stu-id="84344-116">To model a basic sequence in which two activities execute in turn, the `FlowStep` element is used.</span></span> <span data-ttu-id="84344-117">Aşağıdaki örnekte, `FlowStep` iki öğe sırayla iki etkinlik yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="84344-117">In the following example, two `FlowStep` elements are used to execute two activities in sequence.</span></span>

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

### <a name="creating-a-conditional-flowchart-with-a-flowdecision-node"></a><span data-ttu-id="84344-118">FlowDecision düğümü ile koşullu akış şeması oluşturma</span><span class="sxs-lookup"><span data-stu-id="84344-118">Creating a conditional flowchart with a FlowDecision node</span></span>

<span data-ttu-id="84344-119">Akış şeması iş akışında koşullu akış düğümlerini modellemek için (diğer bir deyişle, geleneksel akış şemasının karar simgesi olarak işlev görebilen bir bağlantı oluşturmak için), bir <xref:System.Activities.Statements.FlowDecision> düğüm kullanılır.</span><span class="sxs-lookup"><span data-stu-id="84344-119">To model a conditional flow node in a flowchart workflow (that is, to create a link that functions as a traditional flowchart's decision symbol), a <xref:System.Activities.Statements.FlowDecision> node is used.</span></span> <span data-ttu-id="84344-120"><xref:System.Activities.Statements.FlowDecision.Condition%2A> Düğümün özelliği durumu tanımlayan bir ifadeye ayarlanır ve <xref:System.Activities.Statements.FlowDecision.True%2A> ifade <xref:System.Activities.Statements.FlowDecision.False%2A> yi değerlendirirse ve özellikler yürütülecek <xref:System.Activities.Statements.FlowNode> örneklere `false` `true` ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="84344-120">The <xref:System.Activities.Statements.FlowDecision.Condition%2A> property of the node is set to an expression that defines the condition, and the <xref:System.Activities.Statements.FlowDecision.True%2A> and <xref:System.Activities.Statements.FlowDecision.False%2A> properties are set to <xref:System.Activities.Statements.FlowNode> instances to be executed if the expression evaluates to `true` or `false`.</span></span> <span data-ttu-id="84344-121">Aşağıdaki örnek, <xref:System.Activities.Statements.FlowDecision> düğüm kullanan bir iş akışının nasıl tanımlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="84344-121">The following example shows how to define a workflow that uses a <xref:System.Activities.Statements.FlowDecision> node.</span></span>

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

### <a name="creating-an-exclusive-switch-with-a-flowswitch-node"></a><span data-ttu-id="84344-122">FlowSwitch düğümüyle özel bir anahtar oluşturma</span><span class="sxs-lookup"><span data-stu-id="84344-122">Creating an exclusive switch with a FlowSwitch node</span></span>

<span data-ttu-id="84344-123">Eşleşen bir değere göre özel bir yolun seçildiği bir <xref:System.Activities.Statements.FlowSwitch%601> akış çizelgesini modellemek için düğüm kullanılır.</span><span class="sxs-lookup"><span data-stu-id="84344-123">To model a flowchart in which one exclusive path is selected based on a matching value, the <xref:System.Activities.Statements.FlowSwitch%601> node is used.</span></span> <span data-ttu-id="84344-124">Özellik, <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> seçimleri eşleşecek değeri tanımlayan <xref:System.Object> bir tür parametresi ile a <xref:System.Activities.Activity%601> olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="84344-124">The <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> property is set to a <xref:System.Activities.Activity%601> with a type parameter of <xref:System.Object> that defines the value to match choices against.</span></span> <span data-ttu-id="84344-125">Özellik, <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> koşullu ifadeyle <xref:System.Activities.Statements.FlowNode> eşleşecek anahtarlar ve nesneler sözlüğü ve <xref:System.Activities.Statements.FlowNode> verilen servis talebi koşullu ifadeyle eşleşiyorsa yürütmenin nasıl akması gerektiğini tanımlayan bir nesne kümesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="84344-125">The <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> property defines a dictionary of keys and <xref:System.Activities.Statements.FlowNode> objects to match against the conditional expression, and a set of <xref:System.Activities.Statements.FlowNode> objects that define how execution should flow if the given case matches the conditional expression.</span></span> <span data-ttu-id="84344-126">Ayrıca, <xref:System.Activities.Statements.FlowSwitch%601> koşul <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> ifadesiyle eşleşen bir durum yoksa yürütmenin nasıl akması gerektiğini tanımlayan bir özellik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="84344-126">The <xref:System.Activities.Statements.FlowSwitch%601> also defines a <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> property that defines how execution should flow if no cases match the condition expression.</span></span> <span data-ttu-id="84344-127">Aşağıdaki örnek, bir <xref:System.Activities.Statements.FlowSwitch%601> öğe kullanan bir iş akışının nasıl tanımlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="84344-127">The following example demonstrates how to define a workflow that uses a <xref:System.Activities.Statements.FlowSwitch%601> element.</span></span>

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
