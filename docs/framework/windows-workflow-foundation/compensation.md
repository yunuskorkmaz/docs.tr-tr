---
description: 'Daha fazla bilgi edinin: Dengeleme'
title: Dengeleme
ms.date: 03/30/2017
ms.assetid: 722e9766-48d7-456c-9496-d7c5c8f0fa76
ms.openlocfilehash: d2c57a248939d0485075a5cbf57d91789f58d01a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792797"
---
# <a name="compensation"></a>Dengeleme

Windows Workflow Foundation (WF) dengelemesi, daha önce tamamlanmış işin geri alınamayacağı veya dengelemeyeceği (uygulama tarafından tanımlanan mantığı izleyerek) sonraki bir hata oluştuğunda yaptığı mekanizmadır. Bu bölümde, iş akışlarında tazminat kullanımı açıklanmaktadır.  
  
## <a name="compensation-vs-transactions"></a>Dengeleme ve Işlemler  

 Bir işlem, birden çok işlemi tek bir iş biriminde birleştirmenizi sağlar. Bir işlemin kullanılması, işlem işleminin herhangi bir bölümünde herhangi bir hata oluşursa, uygulamanıza işlemin içinden yürütülen tüm değişiklikleri (geri alma) sağlar. Ancak, iş uzun süre çalışıyorsa, işlemler kullanmak uygun olmayabilir. Örneğin, bir seyahat planlama uygulaması iş akışı olarak uygulanır. İş akışının adımları, bir uçuş kaydı, yönetici onayını bekleme ve sonra uçuş için ödeme yapma bilgisinden oluşabilir. Bu işlem birçok gün sürebilir ve aynı işleme katılabilmek için yapılan kayıt ve ödeme adımları için pratik değildir. Bunun gibi bir senaryoda, işlem içinde daha sonra bir hata oluşursa iş akışının kayıt adımını geri almak için Dengeleme kullanılabilir.  
  
> [!NOTE]
> Bu konu, iş akışlarında tazminat içerir. İş akışlarında işlemler hakkında daha fazla bilgi için bkz. [işlemler](workflow-transactions.md) ve <xref:System.Activities.Statements.TransactionScope> . İşlemler hakkında daha fazla bilgi için bkz <xref:System.Transactions?displayProperty=nameWithType> <xref:System.Transactions.Transaction?displayProperty=nameWithType> . ve.  
  
## <a name="using-compensableactivity"></a>CompensableActivity kullanma  

 <xref:System.Activities.Statements.CompensableActivity> , içindeki temel Dengeleme etkinliğidir [!INCLUDE[wf1](../../../includes/wf1-md.md)] . Telafi gerektiren işleri gerçekleştiren tüm etkinlikler <xref:System.Activities.Statements.CompensableActivity.Body%2A> bir ' a yerleştirilir <xref:System.Activities.Statements.CompensableActivity> . Bu örnekte, bir uçuş satın almanın rezervasyon adımı <xref:System.Activities.Statements.CompensableActivity.Body%2A> bir ' a yerleştirilir <xref:System.Activities.Statements.CompensableActivity> ve ayırmanın iptal edilmesi öğesine yerleştirilir <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> . <xref:System.Activities.Statements.CompensableActivity>İş akışında hemen sonraki bölümünde, yönetici onayını bekleyen iki etkinlik vardır ve sonra uçuşın satın alma adımını tamamlayabilirsiniz. Bir hata durumu başarıyla tamamlandıktan sonra iş akışının iptal edilmesine neden oluyorsa <xref:System.Activities.Statements.CompensableActivity> , <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> işleyicisindeki etkinlikler zamanlanır ve uçuş iptal edilir.  
  
 [!code-csharp[CFX_CompensationExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#1)]  
  
 Aşağıdaki örnek, XAML içindeki iş akışıdır.  
  
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
  
 İş akışı çağrıldığında, konsola aşağıdaki çıktı görüntülenir.  
  
 **Rezerveflight: bilet ayrıldı.**  
**Managerapproval: yönetici onayı alındı.** 
 **PurchaseFlight: bilet satın alındı.** 
 **Iş akışı şu durumla başarıyla tamamlandı: kapatıldı.**
> [!NOTE]
> Bu konudaki örnek etkinlikler, `ReserveFlight` tazminat gerçekleştiğinde etkinliklerin yürütüldüğü sırayı göstermeye yardımcı olmak üzere konsola adlarını ve amaçlarını görüntüler.  
  
### <a name="default-workflow-compensation"></a>Varsayılan Iş akışı dengelemesi  

 Varsayılan olarak, iş akışı iptal edilirse, Dengeleme mantığı başarıyla tamamen ve onaylanmış veya dengelenen tüm telafi etkinlikleri için çalıştırılır.  
  
> [!NOTE]
> Bir <xref:System.Activities.Statements.CompensableActivity> *onaylanırsa*, etkinliğin dengelemesi artık çağrılamaz. Bu bölümde daha sonra onay süreci açıklanmaktadır.  
  
 Bu örnekte, uçuş ayrıldıktan sonra ancak yöneticinin onay adımından önce bir özel durum oluşturulur.  
  
 [!code-csharp[CFX_CompensationExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#2)]  
  
 Bu örnek, XAML 'deki iş akışıdır.  
  
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
  
 [!code-csharp[CFX_CompensationExample#100](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#100)]  
  
 İş akışı çağrıldığında, benzetimli hata koşulu özel durumu içindeki konak uygulama tarafından işlenir <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> , iş akışı iptal edilir ve Dengeleme mantığı çağrılır.  
  
 **Rezerveflight: bilet ayrıldı.**  
**SimulatedErrorCondition: ApplicationException oluşturuluyor.** 
 **Iş akışı Işlenmemiş özel durumu:** 
 **System. ApplicationException: iş akışında Benzetimli hata koşulu.** 
 **Canceluçuş: bilet iptal edildi.** 
 **Iş akışı şu durumla başarıyla tamamlandı: Iptal edildi.**

### <a name="cancellation-and-compensableactivity"></a>İptal ve CompensableActivity  

 İçindeki etkinlikler <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> tamamlanmadıysa ve etkinlik iptal edilirse, içindeki etkinlikler <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> yürütülür.  
  
> [!NOTE]
> <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>Yalnızca içindeki etkinlikler <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> tamamlanmadıysa ve etkinlik iptal edildiğinde çağrılır. <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>Yalnızca içindeki etkinlikler <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> başarıyla tamamlandığında ve tazminat etkinlik üzerinde çağrılırsa yürütülür.  
  
 , <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> İş akışı için uygun bir iptal mantığı sağlama fırsatı yazar. Aşağıdaki örnekte, öğesinin yürütülmesi sırasında bir özel durum oluşturulur <xref:System.Activities.Statements.CompensableActivity.Body%2A> ve sonra <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> çağrılır.  
  
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
  
 Bu örnek, XAML 'deki iş akışıdır  
  
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
  
 İş akışı çağrıldığında, benzetimli hata koşulu özel durumu ' de konak uygulama tarafından işlenir <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> , iş akışı iptal edilir ve öğesinin iptal mantığı <xref:System.Activities.Statements.CompensableActivity> çağrılır. Bu örnekte, Dengeleme mantığı ve iptal etme mantığının farklı hedefleri vardır. Başarılı bir <xref:System.Activities.Statements.CompensableActivity.Body%2A> şekilde tamamlanırsa, kredi kartının ücretlendirilildiği ve uçuşın her iki adımı da geri alması gerektiği anlamına gelir. (Bu örnekte, uçuşmanın iptal edilmesi, kredi kartı ücretlerini otomatik olarak iptal eder.) Ancak, <xref:System.Activities.Statements.CompensableActivity> iptal edilirse bu, tamamlanmamış olduğu anlamına gelir <xref:System.Activities.Statements.CompensableActivity.Body%2A> ve bu nedenle <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> İptalin en iyi şekilde nasıl işleneceğini belirleyebilmelidir. Bu örnekte, <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> kredi kartı ücreti iptal edilir, ancak `ReserveFlight` içinde son etkinlik olduğundan, <xref:System.Activities.Statements.CompensableActivity.Body%2A> uçuştan iptal etmeyi denemez. `ReserveFlight`İçindeki son etkinlik olduğundan, bu, <xref:System.Activities.Statements.CompensableActivity.Body%2A> başarıyla tamamlandıysa, <xref:System.Activities.Statements.CompensableActivity.Body%2A> tamamlanmış olur ve hiçbir iptali mümkün olmaz.  
  
 **ChargeCreditCard: uçuş için kredi kartı ücreti.**  
**SimulatedErrorCondition: ApplicationException oluşturuluyor.** 
 **Iş akışı Işlenmemiş özel durumu:** 
 **System. ApplicationException: iş akışında Benzetimli hata koşulu.** 
 **Cancelcreditcard: kredi kartı ücretlerini Iptal et.** 
 **Iş akışı şu durumla başarıyla tamamlandı: Iptal edildi.**  İptal hakkında daha fazla bilgi için bkz. [iptal](modeling-cancellation-behavior-in-workflows.md).  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a>Telafi etkinliğini kullanan açık Dengeleme  

 Önceki bölümde örtük Dengeleme ele alınmıştır. Örtük Dengeleme basit senaryolar için uygun olabilir, ancak tazmin işleme zamanlaması üzerinde daha fazla açık denetim gerekliyse <xref:System.Activities.Statements.Compensate> etkinlik kullanılabilir. İşlem ile dengeleme işlemini başlatmak için <xref:System.Activities.Statements.Compensate> <xref:System.Activities.Statements.CompensationToken> <xref:System.Activities.Statements.CompensableActivity> tazminat istenen öğesinin kullanıldığı yer. <xref:System.Activities.Statements.Compensate>Etkinlik, <xref:System.Activities.Statements.CompensableActivity> onaylanmayan veya dengelenen herhangi bir tamamlanmış üzerinden tazminat başlatmak için kullanılabilir. Örneğin, etkinlik <xref:System.Activities.Statements.Compensate> <xref:System.Activities.Statements.TryCatch.Catches%2A> bir <xref:System.Activities.Statements.TryCatch> etkinliğin bölümünde veya tamamlandıktan sonra herhangi bir zaman kullanılabilir <xref:System.Activities.Statements.CompensableActivity> . Bu örnekte <xref:System.Activities.Statements.Compensate> etkinlik <xref:System.Activities.Statements.TryCatch.Catches%2A> <xref:System.Activities.Statements.TryCatch> , eylemi tersine çevirmek için etkinliğin bölümünde kullanılır <xref:System.Activities.Statements.CompensableActivity> .  
  
 [!code-csharp[CFX_CompensationExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#3)]  
  
 Bu örnek, XAML 'deki iş akışıdır.  
  
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
  
 İş akışı çağrıldığında, konsola aşağıdaki çıktı görüntülenir.  
  
 **Rezerveflight: bilet ayrıldı.**  
**SimulatedErrorCondition: ApplicationException oluşturuluyor.** 
 **Canceluçuş: bilet iptal edildi.** 
 **Iş akışı şu durumla başarıyla tamamlandı: kapatıldı.**

### <a name="confirming-compensation"></a>Tazminat onaylama  

 Varsayılan olarak, compensable etkinlikleri tamamlandıktan sonra herhangi bir zaman dengelenebilir. Bazı senaryolarda bu uygun olmayabilir. Önceki örnekte, anahtarı ayırma dengelemesi ayırmayı iptal etmiydi. Ancak, uçuş tamamlandıktan sonra bu dengeleme adımı artık geçerli değildir. Dengelenebilir etkinliğin tarafından belirtilen etkinliği çağırdığı doğrulanıyor <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> . Bunun olası bir kullanımı, tazminatı gerçekleştirmek için gerekli olan tüm kaynaklara izin vermedir. Dengelenebilir bir etkinliğin onaylandıktan sonra, telafi olması mümkün değildir ve bu denendiğinde <xref:System.InvalidOperationException> özel bir durum oluşturulur. Bir iş akışı başarıyla tamamlandığında, başarıyla tamamlanan, onaylanmamış ve dengelenmemiş tüm telafi etkinlikleri, tamamlanma sırasında onaylanır. Bu örnekte uçuş ayrılmıştır, satın alınır ve tamamlanır ve sonra dengelenebilir etkinlik onaylanır. Bir doğrulamak için <xref:System.Activities.Statements.CompensableActivity> , etkinliğini kullanın <xref:System.Activities.Statements.Confirm> ve öğesini <xref:System.Activities.Statements.CompensationToken> doğrulamak için öğesini belirtin <xref:System.Activities.Statements.CompensableActivity> .  
  
 [!code-csharp[CFX_CompensationExample#4](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#4)]  
  
 Bu örnek, XAML 'deki iş akışıdır.  
  
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
  
İş akışı çağrıldığında, konsola aşağıdaki çıktı görüntülenir.  
  
**Rezerveflight: bilet ayrıldı.**  
**Managerapproval: yönetici onayı alındı.** 
 **PurchaseFlight: bilet satın alındı.** 
 **Takeuçuş: uçuş tamamlandı.** 
 **ConfirmFlight: uçuş alındı, hiçbir telafi yapılamaz.** 
 **Iş akışı şu durumla başarıyla tamamlandı: kapatıldı.**

## <a name="nesting-compensation-activities"></a>Telafi etkinliklerinin iç içe geçirilmesi  

Bir <xref:System.Activities.Statements.CompensableActivity> <xref:System.Activities.Statements.CompensableActivity.Body%2A> diğerinin bölümüne eklenebilir <xref:System.Activities.Statements.CompensableActivity> . Bir <xref:System.Activities.Statements.CompensableActivity> başka bir işleyiciye yerleştirilmeyebilir <xref:System.Activities.Statements.CompensableActivity> . Bir üst, <xref:System.Activities.Statements.CompensableActivity> iptal edildiğinde, teyit edildiğinde veya telafi edildiğinde, başarıyla tamamlanan ve henüz onaylanmamış veya dengelenen tüm alt öğe telafi etkinliklerinin, üst öğe iptali, onaylama veya tazminat tamamlanmadan önce onaylanması veya telafi edilmesi gerekir. Bu, açıkça modellenmezse, <xref:System.Activities.Statements.CompensableActivity> üst öğe iptal veya telafi sinyalini alıyorsa üst öğe, alt öğe dengelenebilir etkinlikleri dolaylı olarak dengelenir. Üst öğe onaylama sinyali aldıysa, üst öğe, alt dengelenebilir etkinlikleri dolaylı olarak kabul eder. İptali, onayı veya tazminatı işlemek için mantık, üst öğenin işleyicisinde açıkça modellendiyse <xref:System.Activities.Statements.CompensableActivity> , açıkça işlenmeyen tüm alt öğe örtük olarak onaylanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Statements.CompensableActivity>
- <xref:System.Activities.Statements.Compensate>
- <xref:System.Activities.Statements.Confirm>
- <xref:System.Activities.Statements.CompensationToken>
