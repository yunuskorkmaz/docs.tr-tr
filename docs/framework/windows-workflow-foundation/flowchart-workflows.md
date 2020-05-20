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
# <a name="flowchart-workflows"></a>Akış Çizelgesi İş Akışları

Akış çizelgesi, programları tasarlamak için iyi bilinen bir paradigdır. Akış çizelgesi etkinliği genellikle sıralı olmayan iş akışlarını uygulamak için kullanılır, ancak hiçbir düğüm kullanılmazsa sıralı iş akışları için kullanılabilir `FlowDecision` .

## <a name="flowchart-workflow-structure"></a>Akış çizelgesi iş akışı yapısı

 Akış çizelgesi etkinliği, yürütülecek etkinlik koleksiyonunu içeren bir etkinliktir.  Akış çizelgeleri Ayrıca gibi akış denetim öğelerini <xref:System.Activities.Statements.FlowDecision> ve <xref:System.Activities.Statements.FlowSwitch%601> bağımsız etkinlikler arasında değişken değerlerine göre doğrudan yürütmeyi içerir.

## <a name="types-of-flow-nodes"></a>Akış düğümleri türleri

 Farklı öğe türleri, öğe yürütüldüğünde gereken akış denetimi türüne bağlı olarak kullanılır. Akış çizelgesi öğelerinin türleri şunlardır:

- `FlowStep`-Akış çizelgesinde bir yürütme adımını modeller.

- `FlowDecision`-Öğesine benzer bir Boolean koşulu temelinde dal yürütme <xref:System.Activities.Statements.If> .

- `FlowSwitch`– Öğesine benzer şekilde, özel bir anahtara göre dal yürütme <xref:System.Activities.Statements.Switch%601> .

Her bağlantı `Action` <xref:System.Activities.ActivityAction> , alt etkinlikleri yürütmek için kullanılabilecek bir özelliğini ve `Next` geçerli öğe yürütmeyi bitirdiğinde hangi öğe veya öğelerin yürütüleceğini tanımlayan bir veya daha fazla özelliği içerir.

### <a name="creating-a-basic-activity-sequence-with-a-flowstep-node"></a>FlowStep düğümü ile temel etkinlik dizisi oluşturma

İki etkinliğin sırayla yürütüleceği temel bir diziyi modellemek için, `FlowStep` öğesi kullanılır. Aşağıdaki örnekte iki `FlowStep` öğe sırayla iki etkinlik yürütmek için kullanılır.

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

### <a name="creating-a-conditional-flowchart-with-a-flowdecision-node"></a>Flowkarar düğümüyle koşullu bir akış çizelgesi oluşturma

Bir akış çizelgesi iş akışında koşullu akış düğümünü modellemek için (diğer bir deyişle, geleneksel akış çizelgesinin karar simgesi olarak işlev gören bir bağlantı oluşturmak için), bir <xref:System.Activities.Statements.FlowDecision> düğüm kullanılır. <xref:System.Activities.Statements.FlowDecision.Condition%2A>Düğümünün özelliği, koşulu tanımlayan bir ifadeye ayarlanır ve <xref:System.Activities.Statements.FlowDecision.True%2A> <xref:System.Activities.Statements.FlowDecision.False%2A> <xref:System.Activities.Statements.FlowNode> ifade veya olarak değerlendirilirse, ve özellikleri yürütülecek örneklere ayarlanır `true` `false` . Aşağıdaki örnek, bir düğümü kullanan bir iş akışının nasıl tanımlanacağını gösterir <xref:System.Activities.Statements.FlowDecision> .

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

### <a name="creating-an-exclusive-switch-with-a-flowswitch-node"></a>FlowSwitch düğümü ile dışlamalı anahtar oluşturma

Eşleşen bir değere göre özel bir yolun seçildiği bir akış çizelgesini modellemek için, <xref:System.Activities.Statements.FlowSwitch%601> düğüm kullanılır. <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>Özelliği, <xref:System.Activities.Activity%601> <xref:System.Object> seçimleri ile eşleşecek değeri tanımlayan bir tür parametresi olan öğesine ayarlanır. <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>Özelliği <xref:System.Activities.Statements.FlowNode> , koşullu ifadeyle eşleşecek anahtar ve nesnelerin sözlüğünü ve <xref:System.Activities.Statements.FlowNode> verilen Case koşullu ifadeyle eşleşiyorsa yürütmenin nasıl akmasını tanımlayan bir nesne kümesi tanımlar. <xref:System.Activities.Statements.FlowSwitch%601>Ayrıca, <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> koşul ifadesiyle eşleşen hiçbir durum yoksa yürütmenin nasıl akmasını tanımlayan bir özelliği tanımlar. Aşağıdaki örnek, bir öğesi kullanan bir iş akışının nasıl tanımlanacağını göstermektedir <xref:System.Activities.Statements.FlowSwitch%601> .

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
