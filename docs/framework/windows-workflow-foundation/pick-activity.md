---
title: Pick Etkinliği
ms.date: 03/30/2017
ms.assetid: b3e49b7f-0285-4720-8c09-11ae18f0d53e
ms.openlocfilehash: b9ee6c06377760d27bc54d39c1d1f3ecf67ea0d8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61909434"
---
# <a name="pick-activity"></a>Pick Etkinliği
<xref:System.Activities.Statements.Pick> Modelleme olay tetikleyicilerini karşılık gelen işleyicilerini tarafından izlenen bir dizi etkinlik basitleştirir.  A <xref:System.Activities.Statements.Pick> etkinliği içeren bir koleksiyonu <xref:System.Activities.Statements.PickBranch> etkinlikleri, burada her <xref:System.Activities.Statements.PickBranch> arasında eşleştirme olduğu bir <xref:System.Activities.Statements.PickBranch.Trigger%2A> etkinliği ve bir <xref:System.Activities.Statements.PickBranch.Action%2A> etkinlik.  Yürütme sırasında tüm dallar için Tetikleyiciler paralel olarak yürütülür.  Bir tetikleyici tamamlandığında, karşılık gelen eylemi yürütülür ve diğer tüm tetikleyiciler iptal edilir.  Davranışını [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <xref:System.Activities.Statements.Pick> etkinlik benzer [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] <xref:System.Workflow.Activities.ListenActivity> etkinlik.  
  
 Aşağıdaki ekran görüntüsünden [çekme etkinliğini kullanarak](./samples/using-the-pick-activity.md) SDK'sı örneği bir Pick etkinliği iki dal ile gösterir.  Bir dal olarak adlandırılan bir tetikleyici sahip **okuma giriş**, komut satırından giriş okuyan özel bir etkinlik. İkinci dalında olan bir <xref:System.Activities.Statements.Delay> etkinlik tetikleyici. Varsa **okuma giriş** etkinlik önce veri aldığında <xref:System.Activities.Statements.Delay> etkinlik bittiğinde <xref:System.Activities.Statements.Delay> gecikme iptal edildi ve bir karşılama konsoluna yazılır.  Aksi takdirde **okuma giriş** etkinlik ayrılan sürede veri almaz sonra iptal edilecek ve bir zaman aşımı iletisi konsoluna yazılır.  Bu, bir zaman aşımı için herhangi bir eylem eklemek için kullanılan ortak bir desendir.  
  
 ![Pick Etkinliği](./media/pick-activity/pick-activity-two-branches.jpg)  
  
## <a name="best-practices"></a>Önerilen uygulamalar  
 Seçim kullanırken, yürütülen dal tetikleyicisini ilk tamamlandıktan daldır.  Kavramsal olarak, tüm tetikleyiciler paralel olarak yürütmek ve başka bir tetikleyici tamamlanmasından tarafından iptal edilmeden önce bir tetikleyici mantığını çoğunu yürütülen.  Tetikleyici temsil eden tek bir olay olarak kabul ve mümkün olduğunca az mantıksal olarak içine yerleştirmek için bunu aklınızda Pick etkinliği kullanma değiştirirken izlemeniz gereken genel kılavuz sağlamaktır.  İdeal olarak, tetikleyici olaya almak için yeterli mantıksal içermelidir ve bu olayın tüm işleme dalın eylemlere tamamlamalıdır.  Bu yöntem Tetikleyiciler yürütülmesi arasında çakışma miktarını en aza indirir.  Örneğin, göz önünde bulundurun bir <xref:System.Activities.Statements.Pick> burada her tetikleyicisi içeren iki tetikleyicilerle bir <xref:System.ServiceModel.Activities.Receive> etkinliği izleyen tarafından ilave bir mantık.  İlave bir mantık boşta noktanız tanıtır sonra her ikisi de olasılığı yoktur <xref:System.ServiceModel.Activities.Receive> tamamlanmasıyla etkinlikler.  Bir tetikleyici olacak tam olarak tam, başka bir işlem sırasında kısmen tamamlandı.  Bazı senaryolarda, bir ileti kabul etmek ve kısmen işlenmesini Tamamlanıyor kabul edilebilir değil.  Bu nedenle, WF yerleşik Mesajlaşma etkinlikleri gibi kullanırken <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply>, ancak <xref:System.ServiceModel.Activities.Receive> tetikleyici, yaygın olarak kullanılan <xref:System.ServiceModel.Activities.SendReply> ve başka bir mantık eylemi mümkün olduğunca koymanız gerekir.  
  
## <a name="using-the-pick-activity-in-the-designer"></a>Tasarımcıda Pick etkinliği kullanma  
 Çekme Tasarımcısı'nda kullanmak için bulma **çekme** ve **PickBranch** araç.  Sürükle ve bırak **çekme** tuvale.  Varsayılan olarak, yeni bir **çekme** etkinlik Tasarımcısı'nda iki dal içerir.  Ek dalları eklemek için sürükleyin **PickBranch** etkinlik ve var olan dalların yanındaki bırakın. Etkinlikler bırakılan üzerine **çekme** ya da etkinliğini **tetikleyici** alan veya **eylem** herhangi bir bölümünü **PickBranch**.  
  
## <a name="using-the-pick-activity-in-code"></a>Kodda çekme etkinliği kullanma  
 <xref:System.Activities.Statements.Pick> Etkinliği doldurarak kullanılır, <xref:System.Activities.Statements.Pick.Branches%2A> koleksiyonuyla <xref:System.Activities.Statements.PickBranch> etkinlikler. <xref:System.Activities.Statements.PickBranch> Etkinliklerin her bir <xref:System.Activities.Statements.PickBranch.Trigger%2A> türünün özelliği <xref:System.Activities.Activity>. Belirtilen Etkinlik yürütme tamamlandığında <xref:System.Activities.Statements.PickBranch.Action%2A> yürütür.  
  
 Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir. bir <xref:System.Activities.Statements.Pick> konsoldan bir satır okur bir etkinlik için bir zaman aşımı uygulamak için etkinlik.  
  
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
