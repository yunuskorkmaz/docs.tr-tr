---
title: Pick Etkinliği
description: Workflow Foundation 'da, çekme etkinliği bir olay tetikleyicisi kümesinin ve ardından bunlara karşılık gelen işleyicileri modellemesini basitleştirir.
ms.date: 03/30/2017
ms.assetid: b3e49b7f-0285-4720-8c09-11ae18f0d53e
ms.openlocfilehash: eb59dc20919ed2d30a48f920ad154d4b0d99c41f
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421468"
---
# <a name="pick-activity"></a>Pick Etkinliği
<xref:System.Activities.Statements.Pick>Etkinlik, ardından karşılık gelen işleyiciler tarafından izlenen bir olay tetikleyicisi kümesinin modelleme işlemini basitleştirir.  Bir <xref:System.Activities.Statements.Pick> etkinlik <xref:System.Activities.Statements.PickBranch> , her birinin <xref:System.Activities.Statements.PickBranch> bir <xref:System.Activities.Statements.PickBranch.Trigger%2A> etkinlik ve etkinlik arasında bir eşleştirme olduğu etkinlik koleksiyonunu içerir <xref:System.Activities.Statements.PickBranch.Action%2A> .  Yürütme sırasında, tüm dallar için Tetikleyiciler paralel olarak yürütülür.  Bir tetikleyici tamamlandığında, ilgili eylem yürütülür ve diğer tüm tetikleyiciler iptal edilir.  [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <xref:System.Activities.Statements.Pick> Etkinliğin davranışı .NET Framework 3,5 <xref:System.Workflow.Activities.ListenActivity> etkinliğine benzerdir.  
  
 [Çekme etkinliği](./samples/using-the-pick-activity.md) SDK 'sını kullanan aşağıdaki ekran görüntüsünde, iki dala sahip bir çekme etkinliği gösterilmektedir.  Bir dalın, komut satırından girişi okuyan özel bir etkinlik olan **Read Input**adlı bir tetikleyicisi vardır. İkinci dalın bir <xref:System.Activities.Statements.Delay> etkinlik tetikleyicisi vardır. **Girişi oku** etkinliği etkinlik bitmeden önce verileri alırsa <xref:System.Activities.Statements.Delay> , <xref:System.Activities.Statements.Delay> gecikme iptal edilir ve konsola bir selamlama yazılır.  Aksi takdirde, **okundu girişi** etkinliği ayrılan sürede veri almazsa, iptal edilir ve konsola bir zaman aşımı iletisi yazılır.  Bu, herhangi bir eyleme zaman aşımı eklemek için kullanılan yaygın bir modeldir.  
  
 ![Pick Etkinliği](./media/pick-activity/pick-activity-two-branches.jpg)  
  
## <a name="best-practices"></a>En iyi uygulamalar  
 Seçme kullanılırken, yürüten dal, tetikleyicisi önce tamamlanan daldır.  Kavramsal olarak, tüm tetikleyiciler paralel olarak yürütülür ve bir tetikleyici, başka bir tetikleyicinin tamamlanmasına kadar iptal edilmeden önce mantığının çoğunluğunu yürütülemeyebilir.  Bu göz önünde bulundurularak, çekme etkinliğini kullanırken izlenecek genel bir kılavuz, tetikleyiciyi tek bir olayı temsil edecek şekilde değerlendirmek ve buna mümkün olduğunca az mantık koymak için kullanılır.  İdeal olarak, tetikleyici yalnızca bir olay almak için yeterli mantık içermelidir ve bu olayın tüm işlemleri dalın eylemine gitmelidir.  Bu yöntem, tetikleyicilerin yürütülmesi arasındaki çakışma miktarını en aza indirir.  Örneğin, <xref:System.Activities.Statements.Pick> her tetikleyicinin bir etkinlik içerdiği ve <xref:System.ServiceModel.Activities.Receive> ardından ek mantık tarafından izlenen iki tetikleyici ile düşünün.  Ek mantık bir boşta noktası tanıttığında, her iki <xref:System.ServiceModel.Activities.Receive> etkinliğin de başarıyla tamamması olasılığı vardır.  Bir tetikleyici tamamen tamamlanır, diğeri kısmen tamamlanır.  Bazı senaryolarda bir ileti kabul edilir ve sonra işlenmesi kısmen tamamlankabul edilemez.  Bu nedenle, ve gibi WF yerleşik mesajlaşma etkinliklerini kullanırken <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> , <xref:System.ServiceModel.Activities.Receive> genellikle tetikleyicide kullanılır <xref:System.ServiceModel.Activities.SendReply> ve diğer mantığın mümkün olan her durumda yerine konacak olması gerekir.  
  
## <a name="using-the-pick-activity-in-the-designer"></a>Tasarımcıda çekme etkinliğini kullanma  
 Tasarımcıda seçimi kullanmak için araç kutusunda **seçme** ve **PickBranch dalını** bulun.  **Seçimi** tuval üzerine sürükleyip bırakın.  Varsayılan olarak, tasarımcıda yeni bir **çekme** etkinliği iki dal içerecektir.  Ek dallar eklemek için **PickBranch** etkinliğini sürükleyin ve var olan dalların yanına bırakın. Etkinlikler, **çekme** etkinliğine herhangi bir **PickBranch**'In Action alanı **veya** **eylem** alanı üzerinde bırakılabilir.  
  
## <a name="using-the-pick-activity-in-code"></a>Koddaki çekme etkinliğini kullanma  
 <xref:System.Activities.Statements.Pick>Etkinlik, <xref:System.Activities.Statements.Pick.Branches%2A> koleksiyonu etkinliklerle doldurularak kullanılır <xref:System.Activities.Statements.PickBranch> . <xref:System.Activities.Statements.PickBranch>Her birinin <xref:System.Activities.Statements.PickBranch.Trigger%2A> türünde bir özelliği vardır <xref:System.Activities.Activity> . Belirtilen etkinlik yürütmeyi tamamladığında, <xref:System.Activities.Statements.PickBranch.Action%2A> yürütülür.  
  
 Aşağıdaki kod örneği, <xref:System.Activities.Statements.Pick> konsolundan bir satırı okuyan bir etkinlik için zaman aşımı uygulamak üzere etkinliğin nasıl kullanılacağını göstermektedir.  
  
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
