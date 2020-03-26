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
# <a name="flowchart-workflows"></a>Akış Çizelgesi İş Akışları

Akış şeması, programlar tasarlamak için iyi bilinen bir paradigmadır. Akış Şeması etkinliği genellikle sıralı olmayan iş akışlarını uygulamak için kullanılır, ancak `FlowDecision` düğüm kullanılmazsa sıralı iş akışları için kullanılabilir.

## <a name="flowchart-workflow-structure"></a>Akış şeması iş akışı yapısı

 Akış Şeması etkinliği, yürütülecek bir etkinlik koleksiyonu içeren bir etkinliktir.  Akış şemaları, değişkenlerin <xref:System.Activities.Statements.FlowDecision> değerlerine dayalı olarak içerdiği etkinlikler arasında doğrudan yürütme gibi akış <xref:System.Activities.Statements.FlowSwitch%601> kontrol öğeleri de içerir.

## <a name="types-of-flow-nodes"></a>Akış düğümleri türleri

 Eleman yürüdüğünde gereken akış denetimi türüne bağlı olarak farklı türde öğeler kullanılır. Akış şeması öğelerinin türleri şunlardır:

- `FlowStep`- Akış şemasında bir yürütme adımı modeller.

- `FlowDecision`- Boolean durumuna göre dal yürütme, benzer <xref:System.Activities.Statements.If>.

- `FlowSwitch`– Özel bir anahtara dayalı <xref:System.Activities.Statements.Switch%601>şube yürütme, benzer .

Her bağlantı, `Action` alt etkinlikleri <xref:System.Activities.ActivityAction> yürütmek için kullanılabilecek bir özelliği tanımlayan bir `Next` özelliğe ve geçerli öğe yürütmeyi bitirdiğinde hangi öğenin veya öğelerin yürütülmesini tanımlayan bir veya daha fazla özelliğe sahiptir.

### <a name="creating-a-basic-activity-sequence-with-a-flowstep-node"></a>FlowStep düğümüyle temel etkinlik dizisi oluşturma

İki işlemin sırayla yürütüldettiği temel `FlowStep` bir diziyi modellemek için öğe kullanılır. Aşağıdaki örnekte, `FlowStep` iki öğe sırayla iki etkinlik yürütmek için kullanılır.

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

### <a name="creating-a-conditional-flowchart-with-a-flowdecision-node"></a>FlowDecision düğümü ile koşullu akış şeması oluşturma

Akış şeması iş akışında koşullu akış düğümlerini modellemek için (diğer bir deyişle, geleneksel akış şemasının karar simgesi olarak işlev görebilen bir bağlantı oluşturmak için), bir <xref:System.Activities.Statements.FlowDecision> düğüm kullanılır. <xref:System.Activities.Statements.FlowDecision.Condition%2A> Düğümün özelliği durumu tanımlayan bir ifadeye ayarlanır ve <xref:System.Activities.Statements.FlowDecision.True%2A> ifade <xref:System.Activities.Statements.FlowDecision.False%2A> yi değerlendirirse ve özellikler yürütülecek <xref:System.Activities.Statements.FlowNode> örneklere `false` `true` ayarlanır. Aşağıdaki örnek, <xref:System.Activities.Statements.FlowDecision> düğüm kullanan bir iş akışının nasıl tanımlandığını gösterir.

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

### <a name="creating-an-exclusive-switch-with-a-flowswitch-node"></a>FlowSwitch düğümüyle özel bir anahtar oluşturma

Eşleşen bir değere göre özel bir yolun seçildiği bir <xref:System.Activities.Statements.FlowSwitch%601> akış çizelgesini modellemek için düğüm kullanılır. Özellik, <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> seçimleri eşleşecek değeri tanımlayan <xref:System.Object> bir tür parametresi ile a <xref:System.Activities.Activity%601> olarak ayarlanır. Özellik, <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> koşullu ifadeyle <xref:System.Activities.Statements.FlowNode> eşleşecek anahtarlar ve nesneler sözlüğü ve <xref:System.Activities.Statements.FlowNode> verilen servis talebi koşullu ifadeyle eşleşiyorsa yürütmenin nasıl akması gerektiğini tanımlayan bir nesne kümesi tanımlar. Ayrıca, <xref:System.Activities.Statements.FlowSwitch%601> koşul <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> ifadesiyle eşleşen bir durum yoksa yürütmenin nasıl akması gerektiğini tanımlayan bir özellik tanımlar. Aşağıdaki örnek, bir <xref:System.Activities.Statements.FlowSwitch%601> öğe kullanan bir iş akışının nasıl tanımlandığını gösterir.

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
