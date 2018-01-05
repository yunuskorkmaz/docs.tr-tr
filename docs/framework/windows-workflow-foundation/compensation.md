---
title: "Maaş"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 722e9766-48d7-456c-9496-d7c5c8f0fa76
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7dd56b41b7b661b58446219d426be1a19edba059
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="compensation"></a>Maaş
İçinde maaş [!INCLUDE[wf](../../../includes/wf-md.md)] , daha önce tamamlanmış iş bulunabilir geri alınamaz veya (aşağıdaki uygulama tarafından tanımlanan mantık) dengelendi mekanizma izleyen bir hata oluştuğunda. Bu bölümde, iş akışlarında maaş kullanmayı açıklar.  
  
## <a name="compensation-vs-transactions"></a>Maaş vs. İşlemler  
 Bir işlem, tek bir birim birden çok işleme iş birleştirmenize olanak sağlar. Bir işlem kullanarak uygulamanızı (geri dön) gelen tüm hataları işlem işleminin herhangi bir bölümü sırasında oluşursa işlem içinde yürütülen tüm değişiklikleri iptal etmek için olanak sağlar. Ancak, işlemleri kullanarak iş uzunsa çalıştıran uygun olmayabilir. Örneğin, seyahat planlama uygulama iş akışı olarak uygulanır. İş akışı adımları bir uçuş kayıt, Yöneticisi onay bekliyor ve uçuş için ödeme oluşabilir. Bu işlem günlerce sürebilir ve kayıt ve aynı işlemde katılmayı uçuş için ödeme işlemleri için kullanışlı değildir. Bunun gibi bir senaryoda, maaş işlenirken bir hata olduğunda iş akışının kayıt adımı geri almak için kullanılabilir.  
  
> [!NOTE]
>  Bu konu, iş akışlarında maaş kapsar. [!INCLUDE[crabout](../../../includes/crabout-md.md)]iş akışlarında, işlemleri görmek [işlemleri](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md) ve <xref:System.Activities.Statements.TransactionScope>. [!INCLUDE[crabout](../../../includes/crabout-md.md)]işlemler, bkz: <xref:System.Transactions?displayProperty=nameWithType> ve <xref:System.Transactions.Transaction?displayProperty=nameWithType>.  
  
## <a name="using-compensableactivity"></a>CompensableActivity kullanma  
 <xref:System.Activities.Statements.CompensableActivity>Çekirdek maaş etkinliktir [!INCLUDE[wf1](../../../includes/wf1-md.md)]. Dengelenebilmesi gerekebilir çalışmayı gerçekleştirmek hiç etkinlik içine yerleştirilen <xref:System.Activities.Statements.CompensableActivity.Body%2A> , bir <xref:System.Activities.Statements.CompensableActivity>. Bu örnekte, bir uçuş satın alma ayırma adım içine yerleştirildiğinde <xref:System.Activities.Statements.CompensableActivity.Body%2A> , bir <xref:System.Activities.Statements.CompensableActivity> ve ayırma iptaline yerleştirilir <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>. Hemen ardından <xref:System.Activities.Statements.CompensableActivity> için yönetici onayı bekleyin ve ardından satın alma uçuş adımın iki etkinlik iş akışı içinde olan. Bir hata koşulu sonra iptal edilmesi iş akışı neden olursa <xref:System.Activities.Statements.CompensableActivity> başarıyla tamamlandı, ardından etkinlikler <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> işleyici zamanlanır ve uçuş iptal edilir.  
  
 [!code-csharp[CFX_CompensationExample#1](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#1)]  
  
 Aşağıdaki örnek XAML'de iş akışıdır.  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 İş akışı çağrıldığında, aşağıdaki çıktıyı konsola görüntülenir.  
  
 **ReserveFlight: Bilet ayrılmıştır.**  
**ManagerApproval: alınan yönetici onayı gerekir.**   
**PurchaseFlight: Bilet satın alınır.**   
**İş akışı durumu ile başarıyla tamamlandı: kapalı.**    
> [!NOTE]
>  Gibi bu konudaki örnek etkinlikleri `ReserveFlight` adlarını ve amacı, etkinlikleri yürütülme maaş oluştuğunda sipariş göstermeye yardımcı olmak için konsola görüntülemek.  
  
### <a name="default-workflow-compensation"></a>Varsayılan iş akışı Dengeleme  
 Varsayılan olarak, iş akışı iptal ederseniz, maaş mantığı başarıyla tamamen sahip compensable aktivite için çalıştırılır ve henüz onaylanıp veya bırakıldığı dengelendi.  
  
> [!NOTE]
>  Zaman bir <xref:System.Activities.Statements.CompensableActivity> olan *onaylanıp*, maaş etkinliği artık çağrılabilir. Onay işlemi daha sonra bu bölümde açıklanmıştır.  
  
 Bu örnekte, uçuş ayrılmıştır sonra ancak Yöneticisi Onayı adım önce bir özel durum oluşur.  
  
 [!code-csharp[CFX_CompensationExample#2](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#2)]  
  
 Bu örnek XAML'de iş akışıdır.  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:SimulatedErrorCondition />  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 [!code-csharp[CFX_CompensationExample#100](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#100)]  
  
 İş akışı çağrıldığında, benzetimli hata koşulu özel konak uygulama tarafından işlenir <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, iş akışı iptal edilir ve maaş mantığı çağrılır.  
  
 **ReserveFlight: Bilet ayrılmıştır.**  
**SimulatedErrorCondition: bir ApplicationException üretiliyor.**   
**İş akışı işlenmemiş özel durum oluştu:**   
**System.ApplicationException: İş akışı benzetimli hata koşulu.**   
**CancelFlight: Bilet iptal edilir.**   
**İş akışı durumu ile başarıyla tamamlandı: iptal edildi.**    
### <a name="cancellation-and-compensableactivity"></a>İptal etme ve CompensableActivity  
 Varsa etkinlikler <xref:System.Activities.Statements.CompensableActivity.Body%2A> , bir <xref:System.Activities.Statements.CompensableActivity> sahip tamamlanmadı ve etkinlik iptal edilen etkinlikler <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> yürütülür.  
  
> [!NOTE]
>  <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> Yalnızca oluşursa çağrılır etkinlikler <xref:System.Activities.Statements.CompensableActivity.Body%2A> , <xref:System.Activities.Statements.CompensableActivity> tamamlanmamış ve etkinliği iptal edilir. <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> Varsa yalnızca yürütülebilir etkinlikler <xref:System.Activities.Statements.CompensableActivity.Body%2A> , <xref:System.Activities.Statements.CompensableActivity> başarıyla tamamlandı ve maaş faaliyete daha sonra çağrılır.  
  
 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> İş akışı yazarları herhangi uygun iptal mantığın olanağı sağlar. Aşağıdaki örnekte, yürütülmesi sırasında bir özel durum <xref:System.Activities.Statements.CompensableActivity.Body%2A>ve ardından <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> çağrılır.  
  
```csharp  
Activity wf = new Sequence()  
{  
    Activities =  
    {  
        new CompensableActivity  
        {  
            Body = new Sequence  
            {  
                Activities =   
                {  
                    new ChargeCreditCard(),  
                    new SimulatedErrorCondition(),  
                    new ReserveFlight()  
                }  
            },  
            CompensationHandler = new CancelFlight(),  
            CancellationHandler = new CancelCreditCard()  
        },  
        new ManagerApproval(),  
        new PurchaseFlight()  
    }  
};  
```  
  
 Bu örnekte iş akışı XAML içinde  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <Sequence>  
      <c:ChargeCreditCard />  
      <c:SimulatedErrorCondition />  
      <c:ReserveFlight />  
    </Sequence>  
    <CompensableActivity.CancellationHandler>  
      <c:CancelCreditCard />  
    </CompensableActivity.CancellationHandler>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 İş akışı çağrıldığında, benzetimli hata koşulu özel konak uygulama tarafından işlenir <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, iş akışı iptal ve iptal mantığını <xref:System.Activities.Statements.CompensableActivity> çağrılır. Bu örnekte, farklı hedefleri maaş mantığı ve iptal mantığı vardır. Varsa <xref:System.Activities.Statements.CompensableActivity.Body%2A> maaş her iki adımın geri almak için kredi kartı ücret uçuş ayrıldı, yani ve sonra başarıyla tamamlandı. (Bu örnekte, uçuş otomatik olarak iptal etme kredi kartı ücretleri iptal eder.) Ancak, varsa <xref:System.Activities.Statements.CompensableActivity> iptal edildi, yani <xref:System.Activities.Statements.CompensableActivity.Body%2A> vermedi değil tam ve bunu mantığını <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> nasıl en iyi iptal işleneceğini belirlemek mümkün olması gerekir. Bu örnekte, <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> kredi kartı ücret ancak iptal `ReserveFlight` son etkinliğin edildi <xref:System.Activities.Statements.CompensableActivity.Body%2A>, uçuş iptal etmek çalışmaz. Bu yana `ReserveFlight` son etkinliğin edildi <xref:System.Activities.Statements.CompensableActivity.Body%2A>, başarıyla tamamlandıktan sonra <xref:System.Activities.Statements.CompensableActivity.Body%2A> tamamlamış ve hiçbir iptal mümkün olmayacaktır.  
  
 **ChargeCreditCard: Ücret kredi kartı uçuş için.**  
**SimulatedErrorCondition: bir ApplicationException üretiliyor.**   
**İş akışı işlenmemiş özel durum oluştu:**   
**System.ApplicationException: İş akışı benzetimli hata koşulu.**   
**CancelCreditCard: kredi kartı ücretleri iptal edin.**   
**İş akışı durumu ile başarıyla tamamlandı: iptal edildi.**  [!INCLUDE[crabout](../../../includes/crabout-md.md)]iptal etme, bkz: [iptal](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md).  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a>Açık maaş kullanarak etkinlik dengelemek  
 Önceki bölümde örtük maaş ele. Örtük maaş sonra işleme maaş zamanlama üzerinden daha açık denetim gerekli olup olmadığını ancak basit senaryolar için uygun olabilir <xref:System.Activities.Statements.Compensate> etkinlik kullanılabilir. İle maaş işlemini başlatmak için <xref:System.Activities.Statements.Compensate> etkinliği <xref:System.Activities.Statements.CompensationToken> , <xref:System.Activities.Statements.CompensableActivity> hangi maaş istenen kullanılır. <xref:System.Activities.Statements.Compensate> Etkinlik, herhangi bir tamamlandı maaş başlatmak için kullanılabilir <xref:System.Activities.Statements.CompensableActivity> , doğrulanmamış veya dengelendi. Örneğin, bir <xref:System.Activities.Statements.Compensate> etkinlik kullanılabilirdi <xref:System.Activities.Statements.TryCatch.Catches%2A> bölümünü bir <xref:System.Activities.Statements.TryCatch> etkinlik ya da sonra her zaman <xref:System.Activities.Statements.CompensableActivity> tamamlandı. Bu örnekte, <xref:System.Activities.Statements.Compensate> etkinlik kullanılıyor <xref:System.Activities.Statements.TryCatch.Catches%2A> bölümünü bir <xref:System.Activities.Statements.TryCatch> eylemini tersine çevirmek için etkinlik <xref:System.Activities.Statements.CompensableActivity>.  
  
 [!code-csharp[CFX_CompensationExample#3](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#3)]  
  
 Bu örnek XAML'de iş akışıdır.  
  
```xaml  
<TryCatch  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:s="clr-namespace:System;assembly=mscorlib"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <TryCatch.Variables>  
    <Variable  
       x:TypeArguments="CompensationToken"  
       x:Name="__ReferenceID0"  
       Name="token1" />  
  </TryCatch.Variables>  
  <TryCatch.Try>  
    <Sequence>  
      <CompensableActivity>  
        <CompensableActivity.Result>  
          <OutArgument  
             x:TypeArguments="CompensationToken">  
            <VariableReference  
               x:TypeArguments="CompensationToken"  
               Variable="{x:Reference __ReferenceID0}">  
              <VariableReference.Result>  
                <OutArgument  
                   x:TypeArguments="Location(CompensationToken)" />  
              </VariableReference.Result>  
            </VariableReference>  
          </OutArgument>  
        </CompensableActivity.Result>  
        <CompensableActivity.CompensationHandler>  
          <c:CancelFlight />  
        </CompensableActivity.CompensationHandler>  
        <CompensableActivity.ConfirmationHandler>  
          <c:ConfirmFlight />  
        </CompensableActivity.ConfirmationHandler>  
        <c:ReserveFlight />  
      </CompensableActivity>  
      <c:SimulatedErrorCondition />  
      <c:ManagerApproval />  
      <c:PurchaseFlight />  
    </Sequence>  
  </TryCatch.Try>  
  <TryCatch.Catches>  
    <Catch  
       x:TypeArguments="s:ApplicationException">  
      <ActivityAction  
         x:TypeArguments="s:ApplicationException">  
        <Compensate>  
          <Compensate.Target>  
            <InArgument  
               x:TypeArguments="CompensationToken">  
              <VariableValue  
                 x:TypeArguments="CompensationToken"  
                 Variable="{x:Reference __ReferenceID0}">  
                <VariableValue.Result>  
                  <OutArgument  
                     x:TypeArguments="CompensationToken" />  
                </VariableValue.Result>  
              </VariableValue>  
            </InArgument>  
          </Compensate.Target>  
        </Compensate>  
      </ActivityAction>  
    </Catch>  
  </TryCatch.Catches>  
</TryCatch>  
```  
  
 İş akışı çağrıldığında, aşağıdaki çıktıyı konsola görüntülenir.  
  
 **ReserveFlight: Bilet ayrılmıştır.**  
**SimulatedErrorCondition: bir ApplicationException üretiliyor.**   
**CancelFlight: Bilet iptal edilir.**   
**İş akışı durumu ile başarıyla tamamlandı: kapalı.**    
### <a name="confirming-compensation"></a>Maaş onaylama  
 Varsayılan olarak, bunlar tamamladıktan sonra istediğiniz zaman compensable etkinlikleri dengelenebilmesi. Bazı senaryolarda bu uygun olmayabilir. Önceki örnekte ayırması iptal etmek için bilet ayırma için maaş idi. Uçuş tamamlandıktan sonra ancak, bu maaş adımı artık geçerli değil. Çağıran tarafından belirtilen etkinlik compensable etkinlik onaylayan <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>. Bu olası kullanım yayımlanacak maaş gerçekleştirmek için gerekli olan herhangi bir kaynağa izin vermektir. Compensable etkinlik dengelenebilmesi için mümkün değildir onaylandıktan sonra ve bu denenmesi durumunda bir <xref:System.InvalidOperationException> özel durumu oluşur. Bir iş akışı başarıyla tamamlandığında, başarıyla tamamlanan tüm onaylanmamış ve dengelendi olmayan compensable etkinlikleri ters sırada tamamlanmasından onaylanır. Bu örnekte, uçuş ayrılmıştır, satın alınan tamamlandı ve ve ardından compensable etkinlik onaylanıp. Onaylamak için bir <xref:System.Activities.Statements.CompensableActivity>, kullanın <xref:System.Activities.Statements.Confirm> etkinliği ve belirtin <xref:System.Activities.Statements.CompensationToken> , <xref:System.Activities.Statements.CompensableActivity> onaylamak için.  
  
 [!code-csharp[CFX_CompensationExample#4](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#4)]  
  
 Bu örnek XAML'de iş akışıdır.  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <x:Reference>__ReferenceID0</x:Reference>  
  </Sequence.Variables>  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken">  
        <VariableReference  
           x:TypeArguments="CompensationToken">  
          <VariableReference.Result>  
            <OutArgument  
               x:TypeArguments="Location(CompensationToken)" />  
          </VariableReference.Result>  
          <VariableReference.Variable>  
            <Variable  
               x:TypeArguments="CompensationToken"  
               x:Name="__ReferenceID0"  
               Name="token1" />  
          </VariableReference.Variable>  
        </VariableReference>  
      </OutArgument>  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <CompensableActivity.ConfirmationHandler>  
      <c:ConfirmFlight />  
    </CompensableActivity.ConfirmationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
  <c:TakeFlight />  
  <Confirm>  
    <Confirm.Target>  
      <InArgument  
         x:TypeArguments="CompensationToken">  
        <VariableValue  
           x:TypeArguments="CompensationToken"  
           Variable="{x:Reference __ReferenceID0}">  
          <VariableValue.Result>  
            <OutArgument  
               x:TypeArguments="CompensationToken" />  
          </VariableValue.Result>  
        </VariableValue>  
      </InArgument>  
    </Confirm.Target>  
  </Confirm>  
</Sequence>  
```  
  
 İş akışı çağrıldığında, aşağıdaki çıktıyı konsola görüntülenir.  
  
 **ReserveFlight: Bilet ayrılmıştır.**  
**ManagerApproval: alınan yönetici onayı gerekir.**   
**PurchaseFlight: Bilet satın alınır.**   
**TakeFlight: Uçuş tamamlandı.**   
**ConfirmFlight: Uçuş alınmış, hiçbir maaş mümkün.**   
**İş akışı durumu ile başarıyla tamamlandı: kapalı.**   
## <a name="nesting-compensation-activities"></a>İç içe geçme maaş etkinlikleri  
 A <xref:System.Activities.Statements.CompensableActivity> içine yerleştirilebilir <xref:System.Activities.Statements.CompensableActivity.Body%2A> başka bir bölüm <xref:System.Activities.Statements.CompensableActivity>. A <xref:System.Activities.Statements.CompensableActivity> başka bir işleyici yerleştirilebilir <xref:System.Activities.Statements.CompensableActivity>. Bir üst sorumluluğundadır <xref:System.Activities.Statements.CompensableActivity> onu, onaylanan, dengelendi ya da iptal edildiğinde, başarılı bir şekilde tamamladınız ve henüz onaylanıp veya silinmiş dengelendi tüm alt compensable etkinlikleri onaylanmalıdır emin olmak için veya üst iptal, onay ya da maaş tamamlanmadan önce dengelendi. Bu açıkça modellenir değil, üst <xref:System.Activities.Statements.CompensableActivity> örtük olarak iptal üst aldıysanız, alt compensable etkinlikler dengelemek veya sinyal dengelemek. Üst Onayla sinyal aldıysanız üst örtük olarak alt compensable etkinlikler onaylayın. İptal, onay ya da Maaş işleme mantığı açıkça üst işleyicisinde modellenir varsa <xref:System.Activities.Statements.CompensableActivity>, açıkça işlenen tüm alt örtük olarak onaylandı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Activities.Statements.CompensableActivity>  
 <xref:System.Activities.Statements.Compensate>  
 <xref:System.Activities.Statements.Confirm>  
 <xref:System.Activities.Statements.CompensationToken>  
 [Compensable Etkinliği](../../../docs/framework/windows-workflow-foundation/samples/compensable-activity-sample.md)
