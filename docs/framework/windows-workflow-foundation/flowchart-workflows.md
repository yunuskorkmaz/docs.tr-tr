---
title: Akış Çizelgesi iş akışları
ms.date: 03/30/2017
ms.assetid: b0a3475c-d22f-49eb-8912-973c960aebf5
ms.openlocfilehash: dd013e47da881c16d1fa469dfc3e3c4f2a86b6e2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="flowchart-workflows"></a>Akış Çizelgesi iş akışları
Bir akış çizelgesi, programları tasarlamak için iyi bilinen bir örnektir. Akış etkinliği genellikle sıralı olmayan iş akışları uygulamak için kullanılır, ancak sıralı iş akışları için hiç kullanılabilir `FlowDecision` düğümleri kullanılır.  
  
## <a name="flowchart-workflow-structure"></a>Akış iş akışı yapısı  
 Bir akış etkinliği yürütülecek etkinlikleri koleksiyonunu içeren bir etkinliktir.  Akış çizelgeleri de içeren akış denetimi öğeleri gibi <xref:System.Activities.Statements.FlowDecision> ve <xref:System.Activities.Statements.FlowSwitch%601> yürütme değişkenleri değerlerine göre içerilen etkinlikler arasında doğrudan.  
  
## <a name="types-of-flow-nodes"></a>Akış düğüm türleri  
 Farklı türde öğeler öğe yürüttüğünde gerekli akış denetimi türüne bağlı olarak kullanılır. Akış Çizelgesi öğelerinin türleri şunlardır:  
  
-   `FlowStep` -Tek bir adımda akış yürütme modeller.  
  
-   `FlowDecision` -Dalları yürütme temel alarak, benzer Boolean bir koşul <xref:System.Activities.Statements.If>.  
  
-   `FlowSwitch` – Dalları yürütme temel alarak, benzer özel bir anahtar <xref:System.Activities.Statements.Switch%601>.  
  
 Her bir bağlantısı olan bir `Action` tanımlayan özelliğini bir <xref:System.Activities.ActivityAction> alt etkinlikler ve bir veya daha fazla yürütmek için kullanılabilir `Next` hangi öğesi veya öğeleri geçerli öğe yürütme tamamlandığında yürütmek için tanımlayan özellikleri.  
  
### <a name="creating-a-basic-activity-sequence-with-a-flowstep-node"></a>Temel etkinlik dizisi olan bir FlowStep düğümü oluşturma  
 İçinde iki etkinlikleri yürütmek sırayla temel sıralı modellemek için `FlowStep` öğe kullanılır. Aşağıdaki örnekte, iki `FlowStep` öğeleri iki etkinlikleri sırayla yürütmek için kullanılır.  
  
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
  
### <a name="creating-a-conditional-flowchart-with-a-flowdecision-node"></a>Koşullu bir akış çizelgesi FlowDecision düğümle oluşturma  
 Bir akış iş akışı koşullu akışı düğümünde modellemek için (diğer bir deyişle, geleneksel akış grafiği 's karar simgesi olarak işlevleri bir bağlantı oluşturmak için), bir <xref:System.Activities.Statements.FlowDecision> düğümü kullanılır. <xref:System.Activities.Statements.FlowDecision.Condition%2A> Özelliği düğümün durumu tanımlayan bir ifade ayarlanır ve <xref:System.Activities.Statements.FlowDecision.True%2A> ve <xref:System.Activities.Statements.FlowDecision.False%2A> özelliklerinin <xref:System.Activities.Statements.FlowNode> ifade değerlendirilirse yürütülecek örnekleri `true` veya `false`. Aşağıdaki örnek kullanan bir iş akışı tanımlamak nasıl gösterir bir <xref:System.Activities.Statements.FlowDecision> düğümü.  
  
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
  
### <a name="creating-an-exclusive-switch-with-a-flowswitch-node"></a>Bir özel anahtarı olan bir FlowSwitch düğümü oluşturma  
 İçinde bir özel yol seçili dayalı eşleşen bir değeri bir akış çizelgesi modellemek için <xref:System.Activities.Statements.FlowSwitch%601> düğümü kullanılır. <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> Özelliği ayarlanmış bir <xref:System.Activities.Activity%601> bir tür parametresi ile <xref:System.Object> karşı seçimler eşleşecek değer tanımlar. <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> Özellik anahtarları sözlüğü tanımlar ve <xref:System.Activities.Statements.FlowNode> koşullu ifade ve bir dizi karşı eşleşecek şekilde nesneleri <xref:System.Activities.Statements.FlowNode> verilen durumu koşullu ifade eşleşirse yürütme nasıl gerçekleştiğini tanımlayan nesneleri. <xref:System.Activities.Statements.FlowSwitch%601> De tanımlayan bir <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> hiçbir örnek koşul ifadesi eşleşiyorsa yürütme nasıl gerçekleştiğini tanımlar özelliği. Aşağıdaki örnek kullanan bir iş akışı tanımlamak gösterilmiştir bir <xref:System.Activities.Statements.FlowSwitch%601> öğesi.  
  
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
