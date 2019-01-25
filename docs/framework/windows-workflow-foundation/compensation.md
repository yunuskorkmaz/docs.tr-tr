---
title: Dengeleme
ms.date: 03/30/2017
ms.assetid: 722e9766-48d7-456c-9496-d7c5c8f0fa76
ms.openlocfilehash: e8a7140e677b553d07014d0ac5a77dd1c7488f53
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607611"
---
# <a name="compensation"></a>Dengeleme
Windows Workflow Foundation (WF) Maaş tarafından daha önce tamamlanan iş geri alınamaz veya yapabilirsiniz (aşağıdaki uygulama tarafından tanımlanan mantık) dengelenebilecek mekanizması olduğunu bir sonraki hata oluştuğunda. Bu bölümde, iş akışlarında Dengeleme kullanmayı açıklar.  
  
## <a name="compensation-vs-transactions"></a>Maaş vs. İşlemler  
 Bir işlem, birden fazla işlemi tek bir birim iş birleştirmenize olanak sağlar. Bir işlem kullanarak uygulamanızı (geri alma) gelen işlem işlemi sırasında herhangi bir bölümü herhangi bir hata meydana gelirse işlem içinde yürütülen tüm değişiklikleri iptal olanağı sağlar. Ancak, işlemleri kullanarak iş uzun süredir, uygun olmayabilir. Örneğin, bir seyahat planlama uygulama iş akışı olarak uygulanır. İş akışının adımları, bir uçuştaki kayıt, manager onay bekliyor ve ardından uçuş için ödeme oluşabilir. Bu işlem günlerce sürebilir ve kayıt ve aynı işlemde katılmak uçuş için ödeme işlemleri için kullanışlı değildir. Böyle bir senaryoda maaş, işleme, bir hata varsa iş akışının kayıt adımları geri almak için kullanılabilir.  
  
> [!NOTE]
>  Bu konu, iş akışlarında maaş kapsar. İş akışlarında işlemleri hakkında daha fazla bilgi için bkz. [işlemleri](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md) ve <xref:System.Activities.Statements.TransactionScope>. İşlemler hakkında daha fazla bilgi için bkz. <xref:System.Transactions?displayProperty=nameWithType> ve <xref:System.Transactions.Transaction?displayProperty=nameWithType>.  
  
## <a name="using-compensableactivity"></a>CompensableActivity kullanma  
 <xref:System.Activities.Statements.CompensableActivity> Çekirdek maaş etkinliktir [!INCLUDE[wf1](../../../includes/wf1-md.md)]. Dengelenebilecek gereken çalışmayı gerçekleştirmek herhangi bir etkinlik içine yerleştirilir <xref:System.Activities.Statements.CompensableActivity.Body%2A> , bir <xref:System.Activities.Statements.CompensableActivity>. Bu örnekte, bir uçuştaki satın ayırma adım içine yerleştirilir <xref:System.Activities.Statements.CompensableActivity.Body%2A> , bir <xref:System.Activities.Statements.CompensableActivity> ve rezervasyon iptal getirilir <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>. Hemen <xref:System.Activities.Statements.CompensableActivity> akışında olan iki etkinliği için yönetici onayı bekleyin ve ardından uçuş satın alma adımı tamamlayın. Bir hata durumu iş akışını sonra iptal edilmesine neden olursa <xref:System.Activities.Statements.CompensableActivity> başarıyla tamamlandı, ardından etkinliklerinin <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> işleyici zamanlanır ve uçuş iptal edilir.  
  
 [!code-csharp[CFX_CompensationExample#1](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#1)]  
  
 Aşağıdaki örnekte iş akışı XAML içinde bulunur.  
  
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
**ManagerApproval: Yönetici onayı aldı.**   
**PurchaseFlight: Bilet satın alınır.**   
**İş akışı durumu ile başarıyla tamamlandı: Kapatıldı.**    
> [!NOTE]
>  Gibi bu konudaki örnek etkinlikleri `ReserveFlight` adlarını ve amaçlı etkinlikleri yürütüldüğü maaş oluştuğunda sırasını göstermeye yardımcı olmak üzere konsola görüntüler.  
  
### <a name="default-workflow-compensation"></a>Varsayılan iş akışı Dengeleme  
 Varsayılan olarak, iş akışını iptal edilirse, ve telafi mantığının başarıyla tamamen sahip için compensable etkinliğinde çalıştırın ve değil zaten Onaylandı veya dengelendi.  
  
> [!NOTE]
>  Olduğunda bir <xref:System.Activities.Statements.CompensableActivity> olan *onaylanan*, etkinliğin maaş artık çağrılabilir. Onaylama işlemi daha sonra bu bölümde açıklanmıştır.  
  
 Bu örnekte, uçuş ayrılmış sonra ancak yönetici onayı adımdan önce bir özel durum oluşturulur.  
  
 [!code-csharp[CFX_CompensationExample#2](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#2)]  
  
 Bu örnek iş akışı XAML içinde içindir.  
  
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
  
 İş akışı çağrıldığında benzetilmiş hata koşulu özel durum konak uygulama tarafından işlenir <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, iş akışını iptal edilir ve telafi mantığının çağrılır.  
  
 **ReserveFlight: Bilet ayrılmıştır.**  
**SimulatedErrorCondition: Bir ApplicationException gönderme.**   
**İş akışı, işlenmemiş özel durum oluştu:**   
**System.ApplicationException: İş akışında hata koşulu benzetimi.**   
**CancelFlight: Bilet iptal edildi.**   
**İş akışı durumu ile başarıyla tamamlandı: İptal edildi.**    
### <a name="cancellation-and-compensableactivity"></a>İptal ve CompensableActivity  
 Etkinlikler, <xref:System.Activities.Statements.CompensableActivity.Body%2A> , bir <xref:System.Activities.Statements.CompensableActivity> sahip tamamlanmadı ve etkinlik iptal edilen etkinlikler, <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> yürütülür.  
  
> [!NOTE]
>  <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> Yalnızca oluşursa çağrılır etkinliklerinin <xref:System.Activities.Statements.CompensableActivity.Body%2A> , <xref:System.Activities.Statements.CompensableActivity> tamamlanmamış ve etkinlik iptal edilir. <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> , Yalnızca yürütülen etkinlikler, <xref:System.Activities.Statements.CompensableActivity.Body%2A> , <xref:System.Activities.Statements.CompensableActivity> başarıyla tamamlandı ve maaş, faaliyete daha sonra çağrılır.  
  
 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> İş akışı yazarları herhangi bir uygun iptal etme mantığı sağlamaya fırsatı sunar. Aşağıdaki örnekte, yürütülmesi sırasında bir özel durum <xref:System.Activities.Statements.CompensableActivity.Body%2A>, ardından <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> çağrılır.  
  
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
  
 Bu örnekte, XAML iş akışı  
  
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
  
 İş akışı çağrıldığında benzetilmiş hata koşulu özel durum konak uygulama tarafından işlenir <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, iş akışını iptal edilen ve iptal mantığına <xref:System.Activities.Statements.CompensableActivity> çağrılır. Bu örnekte, farklı hedeflere ve telafi mantığının ve iptal etme mantığı vardır. Varsa <xref:System.Activities.Statements.CompensableActivity.Body%2A> maaş hem adımları geri almak için kredi kartınıza ilk başta ücret ve uçuş ayrıldı, bu demektir başarıyla tamamlandı. (Bu örnekte, uçuş otomatik olarak iptal kredi kartı ücretleri iptal eder.) Ancak, varsa <xref:System.Activities.Statements.CompensableActivity> iptal edildi, yani <xref:System.Activities.Statements.CompensableActivity.Body%2A> yaptığınız değil eksiksiz ve bunu mantığını <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> iptal en iyi şekilde nasıl ele alınacağını belirlemek mümkün olması gerekir. Bu örnekte, <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> kredi kartı giderleri, ancak iptal `ReserveFlight` son etkinliğin olan <xref:System.Activities.Statements.CompensableActivity.Body%2A>, uçuş iptal etmek çalışmaz. Bu yana `ReserveFlight` son etkinliğin olan <xref:System.Activities.Statements.CompensableActivity.Body%2A>, başarıyla tamamlandıysa sonra <xref:System.Activities.Statements.CompensableActivity.Body%2A> tamamlamış olmanız ve iptal mümkün olacaktır.  
  
 **ChargeCreditCard: Uçuş kredi kartından çekim.**  
**SimulatedErrorCondition: Bir ApplicationException gönderme.**   
**İş akışı, işlenmemiş özel durum oluştu:**   
**System.ApplicationException: İş akışında hata koşulu benzetimi.**   
**CancelCreditCard: Kredi kartı ücretleri iptal edin.**   
**İş akışı durumu ile başarıyla tamamlandı: İptal edildi.**  İptal işlemleri hakkında daha fazla bilgi için bkz. [iptal](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md).  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a>Açık maaş kullanarak etkinlik dengelemek  
 Önceki bölümde örtük maaş çalışmasındaki. Örtük maaş sonra işleme maaş zamanlama üzerinde daha kesin denetim gerekli olup olmadığını fakat basit senaryolar için uygun olabilir <xref:System.Activities.Statements.Compensate> etkinlik kullanılabilir. İle telafi işlemini başlatmak için <xref:System.Activities.Statements.Compensate> etkinliği <xref:System.Activities.Statements.CompensationToken> , <xref:System.Activities.Statements.CompensableActivity> hangi maaş istenen kullanılır. <xref:System.Activities.Statements.Compensate> Etkinliği, tüm tamamlanan maaş başlatmak için kullanılabilir <xref:System.Activities.Statements.CompensableActivity> , doğrulanmamış veya dengelendi. Örneğin, bir <xref:System.Activities.Statements.Compensate> etkinlik kullanılabilirdi <xref:System.Activities.Statements.TryCatch.Catches%2A> bölümünü bir <xref:System.Activities.Statements.TryCatch> etkinliği ya da sonra istediğiniz zaman <xref:System.Activities.Statements.CompensableActivity> tamamlandı. Bu örnekte, <xref:System.Activities.Statements.Compensate> etkinlik kullanılan <xref:System.Activities.Statements.TryCatch.Catches%2A> bölümünü bir <xref:System.Activities.Statements.TryCatch> eylemi tersine çevirmek için etkinlik <xref:System.Activities.Statements.CompensableActivity>.  
  
 [!code-csharp[CFX_CompensationExample#3](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#3)]  
  
 Bu örnek iş akışı XAML içinde içindir.  
  
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
**SimulatedErrorCondition: Bir ApplicationException gönderme.**   
**CancelFlight: Bilet iptal edildi.**   
**İş akışı durumu ile başarıyla tamamlandı: Kapatıldı.**    
### <a name="confirming-compensation"></a>Maaş onaylanıyor  
 Varsayılan olarak, bunlar tamamladıktan sonra istediğiniz zaman compensable etkinlikleri dengelenebilecek. Bazı senaryolarda bu uygun olmayabilir. Önceki örnekte bileti rezervasyonu için maaş ayırmayı iptal etmek için oluştu. Uçuş tamamlandıktan sonra ancak bu maaş adımı artık geçerli değil. Compensable etkinliğinde onaylayan tarafından belirtilen etkinliği çağırır <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>. Bunun için bir olası kullanım, yayımlanacak Dengeleme gerçekleştirmek gerekli olan herhangi bir kaynağa izin vermektir. Compensable etkinliğinde dengelenebilecek için mümkün değildir onaylandıktan sonra ve bu yapılmaya çalışılırsa bir <xref:System.InvalidOperationException> özel durumu oluşturulur. Bir iş akışı başarıyla tamamlandığında başarıyla tamamlanan tüm onaylanmamış ve dengelenebilecek compensable etkinlikler tamamlandığında, ters sırada onaylanır. Bu örnekte, uçuş ayrılmış, satın alınan tamamlandı ve ve ardından compensable etkinliğinde onaylanır. Onaylamak için bir <xref:System.Activities.Statements.CompensableActivity>, kullanın <xref:System.Activities.Statements.Confirm> etkinlik belirtin <xref:System.Activities.Statements.CompensationToken> , <xref:System.Activities.Statements.CompensableActivity> onaylamak için.  
  
 [!code-csharp[CFX_CompensationExample#4](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#4)]  
  
 Bu örnek iş akışı XAML içinde içindir.  
  
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
**ManagerApproval: Yönetici onayı aldı.**   
**PurchaseFlight: Bilet satın alınır.**   
**TakeFlight: Uçuş tamamlanır.**   
**ConfirmFlight: Uçuş alınmış, hiçbir tazminat mümkün.**   
**İş akışı durumu ile başarıyla tamamlandı: Kapatıldı.**   

## <a name="nesting-compensation-activities"></a>İç içe geçme maaş etkinlikleri  

A <xref:System.Activities.Statements.CompensableActivity> içine yerleştirilebilir <xref:System.Activities.Statements.CompensableActivity.Body%2A> başka bir bölümünü <xref:System.Activities.Statements.CompensableActivity>. A <xref:System.Activities.Statements.CompensableActivity> , başka bir işleyici yerleştirilebilir <xref:System.Activities.Statements.CompensableActivity>. Bir üst sorumluluğundadır <xref:System.Activities.Statements.CompensableActivity> başarıyla tamamladınız ve değil zaten Onaylandı veya dengelenebilecek tüm alt compensable etkinlikler, iptal, onaylanan dengelenebilecek veya olduğunda, onaylanmasını sağlamak veya İptal, onayı veya maaş üst tamamlanmadan önce dengelendi. Bu açıkça modellenmiştir değil, üst <xref:System.Activities.Statements.CompensableActivity> örtük olarak iptal üst aldığında, alt compensable etkinlikleri dengelemek ve sinyal dengelemek. Üst Onayla sinyal aldıysanız üst alt compensable etkinlikleri örtük olarak onaylayın. İptal, onayı veya Maaş işleme mantığı açıkça üst işleyicisinde modellenmiştir varsa <xref:System.Activities.Statements.CompensableActivity>, açıkça işlenen tüm alt örtük olarak onaylandı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Statements.CompensableActivity>
- <xref:System.Activities.Statements.Compensate>
- <xref:System.Activities.Statements.Confirm>
- <xref:System.Activities.Statements.CompensationToken>
