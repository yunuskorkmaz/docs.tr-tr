---
title: Pick Etkinliği
ms.date: 03/30/2017
ms.assetid: b3e49b7f-0285-4720-8c09-11ae18f0d53e
ms.openlocfilehash: 672de5fd3df5e8dde6c54118503bf2a11353b116
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182901"
---
# <a name="pick-activity"></a>Pick Etkinliği
Etkinlik, <xref:System.Activities.Statements.Pick> ilgili işleyicileri tarafından izlenen olay tetikleyicileri kümesinin modelliğini kolaylaştırır.  Bir <xref:System.Activities.Statements.Pick> etkinlik, her <xref:System.Activities.Statements.PickBranch> <xref:System.Activities.Statements.PickBranch> bir <xref:System.Activities.Statements.PickBranch.Trigger%2A> etkinlik ve bir <xref:System.Activities.Statements.PickBranch.Action%2A> etkinlik arasında bir eşleştirme olduğu bir etkinlik koleksiyonu içerir.  Yürütme sırasında, tüm dalların tetikleyicileri paralel olarak yürütülür.  Bir tetikleyici tamamlandığında, karşılık gelen eylemi yürütülür ve diğer tüm tetikleyiciler iptal edilir.  Etkinliğin davranışı [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] .NET Framework 3.5 <xref:System.Workflow.Activities.ListenActivity> etkinliğine benzer. <xref:System.Activities.Statements.Pick>  
  
 [Seçme Etkinliği](./samples/using-the-pick-activity.md) SDK örneğinden aşağıdaki ekran görüntüsü, iki dallı bir Çekme etkinliği gösterir.  Bir dalda **Okuma girişi**adlı bir tetikleyici vardır, komut satırından girişi okuyan özel bir etkinlik. İkinci dalda <xref:System.Activities.Statements.Delay> bir etkinlik tetikleyicisi vardır. Okundu **girişi** etkinliği etkinlik bitmeden <xref:System.Activities.Statements.Delay> önce <xref:System.Activities.Statements.Delay> veri alırsa, Gecikme iptal edilir ve konsola bir karşılama yazılır.  Aksi takdirde, **Read girişi** etkinliği ayrılan süre içinde veri almazsa, iptal edilir ve konsola bir zaman ekme iletisi yazılır.  Bu, herhangi bir eyleme zaman aşındırmak için kullanılan yaygın bir desendir.  
  
 ![Pick Etkinliği](./media/pick-activity/pick-activity-two-branches.jpg)  
  
## <a name="best-practices"></a>En iyi uygulamalar  
 Çekme'yi kullanırken, çalıştıran dal, tetikleyicisi ilk tamamlanan daldır.  Kavramsal olarak, tüm tetikleyiciler paralel olarak yürütülür ve bir tetikleyici, başka bir tetikleyicinin tamamlanmasıyla iptal edilmeden önce mantığının büyük bir kısmını yürütülmüş olabilir.  Bunu göz önünde bulundurarak, Çekme etkinliğini kullanırken izninizlen genel bir kılavuz, tetikleyiciyi tek bir olayı temsil ediyor gibi ele almak ve mümkün olduğunca az mantık koymaktır.  İdeal olarak, tetikleyici bir olay almak için yeterli mantık içermelidir ve bu olayın tüm işleme dalı eyleme gitmeli.  Bu yöntem, tetikleyicilerin yürütülmesi arasındaki çakışma miktarını en aza indirir.  Örneğin, her <xref:System.Activities.Statements.Pick> tetikleyiciek mantık ardından bir <xref:System.ServiceModel.Activities.Receive> etkinlik içeren iki tetikleyici ile a düşünün.  Ek mantık boşta bir nokta tanıtırsa, <xref:System.ServiceModel.Activities.Receive> her iki faaliyetin de başarıyla tamamlanması olasılığı vardır.  Bir tetikleyici tamamen tamamlanacak, diğeri ise kısmen tamamlanacak.  Bazı senaryolarda, bir iletiyi kabul etmek ve sonra kısmen işlemeyi tamamlamak kabul edilemez.  Bu nedenle, WF dahili mesajlaşma etkinlikleri <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply>kullanırken <xref:System.ServiceModel.Activities.Receive> ve , genellikle tetikleyici <xref:System.ServiceModel.Activities.SendReply> kullanılır ken, ve diğer mantık mümkün olduğunca eylem koymak gerekir.  
  
## <a name="using-the-pick-activity-in-the-designer"></a>Tasarımcıda Çekme etkinliğini kullanma  
 Tasarımcıda Seç'i kullanmak için araç kutusunda **Pick** ve **PickBranch'ı** bulun.  **Sürükle** ve tuval üzerine Pick bırakın.  Varsayılan olarak, tasarımcıda yeni bir **Çekme** Etkinliği iki dal içerir.  Ek dallar eklemek için **PickBranch** etkinliğini sürükleyin ve varolan dalların yanına bırakın. Etkinlikler, **Tetikleyici** alanına veya herhangi bir **PickBranch'ın** **Eylem** alanına **Çekme** Etkinliği'ne bırakılabilir.  
  
## <a name="using-the-pick-activity-in-code"></a>Kodda Çekme Etkinliği'ni kullanma  
 Etkinlik, <xref:System.Activities.Statements.Pick> <xref:System.Activities.Statements.Pick.Branches%2A> koleksiyonunu etkinliklerle <xref:System.Activities.Statements.PickBranch> doldurarak kullanılır. Etkinliklerin <xref:System.Activities.Statements.PickBranch> her <xref:System.Activities.Statements.PickBranch.Trigger%2A> biri bir <xref:System.Activities.Activity>tür özelliğine sahiptir. Belirtilen etkinlik yürütmeyi tamamladığında, yürütülür. <xref:System.Activities.Statements.PickBranch.Action%2A>  
  
 Aşağıdaki kod örneği, konsoldan <xref:System.Activities.Statements.Pick> bir satır okuyan bir etkinlik için zaman arasını uygulamak için bir etkinliğin nasıl kullanılacağını gösterir.  
  
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
