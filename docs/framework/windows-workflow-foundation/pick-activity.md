---
title: "Etkinlik seçin"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3e49b7f-0285-4720-8c09-11ae18f0d53e
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ce650c931e94c76c669ee99068d2356f4b2ec32f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="pick-activity"></a>Etkinlik seçin
<xref:System.Activities.Statements.Pick> Etkinlik olay tetikleyicileri bunların karşılık gelen işleyiciler tarafından izlenen bir dizi modelleme basitleştirir.  A <xref:System.Activities.Statements.Pick> etkinlik koleksiyonunu içerir <xref:System.Activities.Statements.PickBranch> etkinlikleri, burada her <xref:System.Activities.Statements.PickBranch> arasında eşleştirme olduğu bir <xref:System.Activities.Statements.PickBranch.Trigger%2A> etkinliği ve bir <xref:System.Activities.Statements.PickBranch.Action%2A> etkinlik.  Yürütme sırasında tüm dalları tetikleyici paralel olarak yürütülür.  Bir tetikleyici tamamlandığında, karşılık gelen eylemi yürütülür ve diğer tüm Tetikleyicileri iptal edilir.  Davranışını [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <xref:System.Activities.Statements.Pick> etkinlik benzer [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] <xref:System.Workflow.Activities.ListenActivity> etkinlik.  
  
 Aşağıdaki ekran görüntüsünde [kullanarak çekme etkinliğini](../../../docs/framework/windows-workflow-foundation/samples/using-the-pick-activity.md) SDK'sı örneği iki dalı çekme etkinlikle gösterir.  Bir dal adı verilen bir tetikleyici sahip **okuma giriş**, komut satırından giriş okur özel bir etkinlik. İkinci şube sahip bir <xref:System.Activities.Statements.Delay> etkinlik tetikleyici. Varsa **okuma giriş** etkinlik önce verileri alan <xref:System.Activities.Statements.Delay> etkinlik bittiğinde <xref:System.Activities.Statements.Delay> gecikme iptal edilecek ve bir karşılama konsoluna yazılır.  Aksi halde, eğer **okuma giriş** etkinlik ayrılan sürede veri almaz sonra iptal edilecek ve bir zaman aşımı iletisi konsoluna yazılır.  Zaman aşımı için herhangi bir eylem eklemek için kullanılan genel bir desen budur.  
  
 ![Etkinlik çekme](../../../docs/framework/windows-workflow-foundation/media/pickconceptual.JPG "PickConceptual")  
  
## <a name="best-practices"></a>Önerilen uygulamalar  
 Çekme kullanırken yürütür şube tetikleyicisini ilk tamamlandıktan dal ' dir.  Kavramsal olarak, tüm Tetikleyicileri paralel olarak yürütün ve başka bir tetikleme tamamlanmasından tarafından iptal etmeden önce bir tetikleyici, mantığını çoğunluğu yürütülen.  Bu aklınızda kullanarak çekme etkinliğini izlemeniz gereken genel kılavuz tetikleyici tek bir olay temsil eden olarak işlemek için mümkün olduğunca az mantığı olarak içine yerleştirilecek ise.  İdeal olarak, tetikleyici bir olay almak için yeterli mantığının içermelidir ve bu olayın tüm işleme şube eyleme tamamlamalıdır.  Bu yöntem Tetikleyiciler yürütülmesi arasında örtüşme miktarını azaltır.  Örneğin, göz önünde bulundurun bir <xref:System.Activities.Statements.Pick> , her tetikleyici içerdiği iki tetikleyici içeren bir <xref:System.ServiceModel.Activities.Receive> etkinlik ek mantığı tarafından izlenen.  İlave bir mantık boşta noktanız tanıtır sonra her ikisi de olasılığı varsa <xref:System.ServiceModel.Activities.Receive> başarıyla tamamlayan etkinlikler.  Bir tetikleyici olacak tam olarak başka bir işlem sırasında tam kısmen tamamlanmış.  Bazı senaryolarda, bir ileti kabul etmek ve kısmen işlenmesini Tamamlanıyor kabul edilebilir değil.  Bu nedenle, WF yerleşik Mesajlaşma etkinlikleri gibi kullanırken <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply>, sırada <xref:System.ServiceModel.Activities.Receive> tetikleyici, yaygın olarak kullanılan <xref:System.ServiceModel.Activities.SendReply> ve diğer mantığı mümkün olduğunca eylemde sokulmalıdır.  
  
## <a name="using-the-pick-activity-in-the-designer"></a>Çekme Etkinlik Tasarımcısı'nda kullanma  
 Çekme Tasarımcısı'nda kullanmak için bulma **çekme** ve **PickBranch** araç kutusunda.  Sürükleme ve bırakma **çekme** tuvale.  Varsayılan olarak, yeni bir **çekme** etkinlik Tasarımcısı'nda iki dalı içerir.  Ek dalları eklemek için sürükleyin **PickBranch** etkinliği ve varolan dalları yanındaki bırakın. Etkinlikler bırakılan üzerine **çekme** ya da etkinliğini **tetikleyici** alan veya **eylem** herhangi bir bölümünü **PickBranch**.  
  
## <a name="using-the-pick-activity-in-code"></a>Çekme Etkinlik kod içinde kullanma  
 <xref:System.Activities.Statements.Pick> Etkinlik doldurarak kullanılır, <xref:System.Activities.Statements.Pick.Branches%2A> koleksiyonuyla <xref:System.Activities.Statements.PickBranch> etkinlikler. <xref:System.Activities.Statements.PickBranch> Etkinliklerin her bir <xref:System.Activities.Statements.PickBranch.Trigger%2A> türündeki özelliği <xref:System.Activities.Activity>. Belirtilen Etkinlik yürütme tamamlandığında <xref:System.Activities.Statements.PickBranch.Action%2A> yürütür.  
  
 Aşağıdaki kod örneğinde nasıl kullanılacağını gösteren bir <xref:System.Activities.Statements.Pick> bir satır konsoldan okur bir etkinlik için zaman aşımı uygulamak için etkinlik.  
  
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
