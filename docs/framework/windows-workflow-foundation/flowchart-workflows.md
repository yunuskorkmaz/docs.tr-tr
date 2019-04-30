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
# <a name="flowchart-workflows"></a>Akış Çizelgesi İş Akışları

Bir akış programları tasarlamak için iyi bilinen bir örnektir. Akış Çizelgesi etkinlik genellikle sıralı olmayan bir iş akışları uygulamak için kullanılır, ancak hiçbir sıralı iş akışları için kullanılabilir `FlowDecision` düğümleri kullanılır.

## <a name="flowchart-workflow-structure"></a>Akış Çizelgesi iş akışı yapısı

 Akış Çizelgesi etkinliğine etkinlikleri yürütülecek bir koleksiyonunu içeren bir etkinliktir.  Akış çizelgeleri de içeren akış denetimi öğeleri gibi <xref:System.Activities.Statements.FlowDecision> ve <xref:System.Activities.Statements.FlowSwitch%601> yürütme değişkenlerin değerlerini temel alan bağımsız etkinlikler arasında doğrudan.

## <a name="types-of-flow-nodes"></a>Akış düğüm türleri

 Farklı türde öğeler akış denetimi öğe yürütüldüğünde gerekli türüne bağlı olarak kullanılır. Akış öğeleri türleri şunlardır:

- `FlowStep` -Bir adım akış yürütmesinin modeller.

- `FlowDecision` -Bir Boolean koşulu, benzer şekilde temel dalları yürütme <xref:System.Activities.Statements.If>.

- `FlowSwitch` – Dalları yürütme, benzer özel bir anahtarı temelinde <xref:System.Activities.Statements.Switch%601>.

Her bir bağlantısı olan bir `Action` tanımlayan özellik bir <xref:System.Activities.ActivityAction> alt etkinlikleri ve bir veya daha fazla yürütmek için kullanılabilir `Next` hangi öğe veya öğe geçerli öğe yürütülmesi tamamlandığında yürütülecek tanımlayan özellikleri.

### <a name="creating-a-basic-activity-sequence-with-a-flowstep-node"></a>Temel etkinlik dizisini FlowStep düğümle oluşturma

İçinde iki etkinlikleri yürütmek sırayla, temel bir sıralı model `FlowStep` öğe kullanılır. Aşağıdaki örnekte, iki `FlowStep` öğeleri iki etkinlikleri sırayla yürütmek için kullanılır.

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

### <a name="creating-a-conditional-flowchart-with-a-flowdecision-node"></a>FlowDecision düğümle koşullu bir akış oluşturma

Bir akış çizelgesi iş akışı koşullu akış düğümünde modellemek için (diğer bir deyişle, geleneksel bir akış kişinin kararı simgesi olarak işlevleri bir bağlantı oluşturmak için), <xref:System.Activities.Statements.FlowDecision> düğümü kullanılır. <xref:System.Activities.Statements.FlowDecision.Condition%2A> Düğümün özelliği koşulu tanımlayan bir ifade kümesi ve <xref:System.Activities.Statements.FlowDecision.True%2A> ve <xref:System.Activities.Statements.FlowDecision.False%2A> özelliklerinin <xref:System.Activities.Statements.FlowNode> ifade değerlendirilirse yürütülecek örnekleri `true` veya `false`. Aşağıdaki örnek, kullanan bir iş akışı tanımlamak gösterilmiştir bir <xref:System.Activities.Statements.FlowDecision> düğümü.

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

### <a name="creating-an-exclusive-switch-with-a-flowswitch-node"></a>FlowSwitch düğümle bir özel anahtarı oluşturma

Bir akış içinde bir özel yol seçili temel üzerinde eşleşen bir değeri, model <xref:System.Activities.Statements.FlowSwitch%601> düğümü kullanılır. <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> Özelliği bir <xref:System.Activities.Activity%601> bir tür parametresi ile <xref:System.Object> karşı seçenek değerini tanımlar. <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> Özelliği anahtarları sözlüğü tanımlar ve <xref:System.Activities.Statements.FlowNode> koşullu ifadesi ve bir dizi karşı eşleştirilecek nesneleri <xref:System.Activities.Statements.FlowNode> verilen durumu koşullu ifade eşleşiyorsa yürütme nasıl akışını tanımlayan nesne. <xref:System.Activities.Statements.FlowSwitch%601> Ayrıca tanımlayan bir <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> hiçbir servis talebi koşul ifadesi eşleşiyorsa yürütme nasıl akışını tanımlayan özellik. Aşağıdaki örnek, kullanan bir iş akışı tanımlamak gösterilmiştir bir <xref:System.Activities.Statements.FlowSwitch%601> öğesi.

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
