---
title: Pick Etkinliği
ms.date: 03/30/2017
ms.assetid: b3e49b7f-0285-4720-8c09-11ae18f0d53e
ms.openlocfilehash: 51caf020042212b570ae915ead00a4225df2c588
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283176"
---
# <a name="pick-activity"></a>Pick Etkinliği
<xref:System.Activities.Statements.Pick> etkinliği, karşılık gelen işleyicileri izleyen bir olay tetikleyicisi kümesinin modelleme işlemini basitleştirir.  <xref:System.Activities.Statements.Pick> etkinliği, her <xref:System.Activities.Statements.PickBranch> <xref:System.Activities.Statements.PickBranch.Trigger%2A> etkinliği ve <xref:System.Activities.Statements.PickBranch.Action%2A> etkinliği arasında bir eşleştirme olduğu <xref:System.Activities.Statements.PickBranch> etkinliklerin bir koleksiyonunu içerir.  Yürütme sırasında, tüm dallar için Tetikleyiciler paralel olarak yürütülür.  Bir tetikleyici tamamlandığında, ilgili eylem yürütülür ve diğer tüm tetikleyiciler iptal edilir.  [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<xref:System.Activities.Statements.Pick> etkinliğinin davranışı .NET Framework 3,5 <xref:System.Workflow.Activities.ListenActivity> etkinliğine benzerdir.  
  
 [Çekme etkinliği](./samples/using-the-pick-activity.md) SDK 'sını kullanan aşağıdaki ekran görüntüsünde, iki dala sahip bir çekme etkinliği gösterilmektedir.  Bir dalın, komut satırından girişi okuyan özel bir etkinlik olan **Read Input**adlı bir tetikleyicisi vardır. İkinci dalın <xref:System.Activities.Statements.Delay> etkinlik tetikleyicisi vardır. **Girişi oku** etkinliği <xref:System.Activities.Statements.Delay> etkinlik bitmeden önce verileri alırsa, <xref:System.Activities.Statements.Delay> gecikme iptal edilir ve konsola bir selamlama yazılır.  Aksi takdirde, **okundu girişi** etkinliği ayrılan sürede veri almazsa, iptal edilir ve konsola bir zaman aşımı iletisi yazılır.  Bu, herhangi bir eyleme zaman aşımı eklemek için kullanılan yaygın bir modeldir.  
  
 ![Pick Etkinliği](./media/pick-activity/pick-activity-two-branches.jpg)  
  
## <a name="best-practices"></a>En iyi uygulamalar  
 Seçme kullanılırken, yürüten dal, tetikleyicisi önce tamamlanan daldır.  Kavramsal olarak, tüm tetikleyiciler paralel olarak yürütülür ve bir tetikleyici, başka bir tetikleyicinin tamamlanmasına kadar iptal edilmeden önce mantığının çoğunluğunu yürütülemeyebilir.  Bu göz önünde bulundurularak, çekme etkinliğini kullanırken izlenecek genel bir kılavuz, tetikleyiciyi tek bir olayı temsil edecek şekilde değerlendirmek ve buna mümkün olduğunca az mantık koymak için kullanılır.  İdeal olarak, tetikleyici yalnızca bir olay almak için yeterli mantık içermelidir ve bu olayın tüm işlemleri dalın eylemine gitmelidir.  Bu yöntem, tetikleyicilerin yürütülmesi arasındaki çakışma miktarını en aza indirir.  Örneğin, her tetikleyicinin bir <xref:System.ServiceModel.Activities.Receive> etkinlik ve ardından ek mantık içerdiği iki tetikleyiciyle <xref:System.Activities.Statements.Pick> düşünün.  Ek mantık boş bir nokta tanımışsa, her iki <xref:System.ServiceModel.Activities.Receive> etkinliğin de başarıyla tamamması olasılığı vardır.  Bir tetikleyici tamamen tamamlanır, diğeri kısmen tamamlanır.  Bazı senaryolarda bir ileti kabul edilir ve sonra işlenmesi kısmen tamamlankabul edilemez.  Bu nedenle, <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply>gibi WF yerleşik mesajlaşma etkinliklerini kullanırken <xref:System.ServiceModel.Activities.Receive> yaygın olarak tetikleyicide kullanılırken, <xref:System.ServiceModel.Activities.SendReply> ve diğer mantığın mümkün olan her durumda yerine konacak olması gerekir.  
  
## <a name="using-the-pick-activity-in-the-designer"></a>Tasarımcıda çekme etkinliğini kullanma  
 Tasarımcıda seçimi kullanmak için araç kutusunda **seçme** ve **PickBranch dalını** bulun.  **Seçimi** tuval üzerine sürükleyip bırakın.  Varsayılan olarak, tasarımcıda yeni bir **çekme** etkinliği iki dal içerecektir.  Ek dallar eklemek için **PickBranch** etkinliğini sürükleyin ve var olan dalların yanına bırakın. Etkinlikler, **çekme** etkinliğine herhangi bir **PickBranch**'In Action alanı **veya** **eylem** alanı üzerinde bırakılabilir.  
  
## <a name="using-the-pick-activity-in-code"></a>Koddaki çekme etkinliğini kullanma  
 <xref:System.Activities.Statements.Pick> etkinliği, <xref:System.Activities.Statements.Pick.Branches%2A> koleksiyonu <xref:System.Activities.Statements.PickBranch> etkinlikleriyle doldurularak kullanılır. <xref:System.Activities.Statements.PickBranch> etkinliklerinin her biri <xref:System.Activities.Activity>türünde bir <xref:System.Activities.Statements.PickBranch.Trigger%2A> özelliğine sahiptir. Belirtilen etkinlik yürütmeyi tamamladığında <xref:System.Activities.Statements.PickBranch.Action%2A> yürütülür.  
  
 Aşağıdaki kod örneğinde, konsolundan bir satırı okuyan bir etkinlik için zaman aşımı uygulamak üzere <xref:System.Activities.Statements.Pick> etkinliğinin nasıl kullanılacağı gösterilmektedir.  
  
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
