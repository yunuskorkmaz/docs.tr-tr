---
title: Dengeleme
ms.date: 03/30/2017
ms.assetid: 722e9766-48d7-456c-9496-d7c5c8f0fa76
ms.openlocfilehash: 147da26fd297d41876815cffcc70450ae905ba85
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935425"
---
# <a name="compensation"></a>Dengeleme
Windows Workflow Foundation (WF) dengelemesi, daha önce tamamlanmış işin geri alınamayacağı veya dengelemeyeceği (uygulama tarafından tanımlanan mantığı izleyerek) sonraki bir hata oluştuğunda yaptığı mekanizmadır. Bu bölümde, iş akışlarında tazminat kullanımı açıklanmaktadır.  
  
## <a name="compensation-vs-transactions"></a>Tazminat karşılaştırması İşlemler  
 Bir işlem, birden çok işlemi tek bir iş biriminde birleştirmenizi sağlar. Bir işlemin kullanılması, işlem işleminin herhangi bir bölümünde herhangi bir hata oluşursa, uygulamanıza işlemin içinden yürütülen tüm değişiklikleri (geri alma) sağlar. Ancak, iş uzun süre çalışıyorsa, işlemler kullanmak uygun olmayabilir. Örneğin, bir seyahat planlama uygulaması iş akışı olarak uygulanır. İş akışının adımları, bir uçuş kaydı, yönetici onayını bekleme ve sonra uçuş için ödeme yapma bilgisinden oluşabilir. Bu işlem birçok gün sürebilir ve aynı işleme katılabilmek için yapılan kayıt ve ödeme adımları için pratik değildir. Bunun gibi bir senaryoda, işlem içinde daha sonra bir hata oluşursa iş akışının kayıt adımını geri almak için Dengeleme kullanılabilir.  
  
> [!NOTE]
> Bu konu, iş akışlarında tazminat içerir. İş akışlarında işlemler hakkında daha fazla bilgi için bkz [](workflow-transactions.md) . işlemler <xref:System.Activities.Statements.TransactionScope>ve. İşlemler hakkında daha fazla bilgi için bkz <xref:System.Transactions?displayProperty=nameWithType> . <xref:System.Transactions.Transaction?displayProperty=nameWithType>ve.  
  
## <a name="using-compensableactivity"></a>CompensableActivity kullanma  
 <xref:System.Activities.Statements.CompensableActivity>, içindeki [!INCLUDE[wf1](../../../includes/wf1-md.md)]temel Dengeleme etkinliğidir. Telafi gerektiren işleri gerçekleştiren tüm etkinlikler bir ' a <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity>yerleştirilir. Bu örnekte, bir uçuş satın almanın rezervasyon adımı bir ' a <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> yerleştirilir ve <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>ayırmanın iptal edilmesi öğesine yerleştirilir. İş akışında hemen <xref:System.Activities.Statements.CompensableActivity> sonraki bölümünde, yönetici onayını bekleyen iki etkinlik vardır ve sonra uçuşın satın alma adımını tamamlayabilirsiniz. Bir hata durumu başarıyla tamamlandıktan sonra <xref:System.Activities.Statements.CompensableActivity> iş akışının iptal edilmesine neden oluyorsa, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> işleyicisindeki etkinlikler zamanlanır ve uçuş iptal edilir.  
  
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
  
 **Rezervlü Eflight: Bilet ayrıldı.**  
**Yönetici onayı: Yönetici onayı alındı.**    
**PurchaseFlight: Bilet satın alındı.**    
**İş akışı şu durumla başarıyla tamamlandı: Kapandı.**    
> [!NOTE]
> Bu konudaki `ReserveFlight` örnek etkinlikler, tazminat gerçekleştiğinde etkinliklerin yürütüldüğü sırayı göstermeye yardımcı olmak üzere konsola adlarını ve amaçlarını görüntüler.  
  
### <a name="default-workflow-compensation"></a>Varsayılan Iş akışı dengelemesi  
 Varsayılan olarak, iş akışı iptal edilirse, Dengeleme mantığı başarıyla tamamen ve onaylanmış veya dengelenen tüm telafi etkinlikleri için çalıştırılır.  
  
> [!NOTE]
> Bir <xref:System.Activities.Statements.CompensableActivity> onaylanırsa, etkinliğin dengelemesi artık çağrılamaz. Bu bölümde daha sonra onay süreci açıklanmaktadır.  
  
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
  
 İş akışı çağrıldığında, benzetimli hata koşulu özel durumu içindeki <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>konak uygulama tarafından işlenir, iş akışı iptal edilir ve Dengeleme mantığı çağrılır.  
  
 **Rezervlü Eflight: Bilet ayrıldı.**  
**SimulatedErrorCondition: ApplicationException oluşturuluyor.**    
**İş akışı Işlenmemiş özel durumu:**    
**System. ApplicationException: İş akışında Benzetimli hata koşulu.**    
**Canceluçuş: Bilet iptal edildi.**    
**İş akışı şu durumla başarıyla tamamlandı: Edilmesi.**    
### <a name="cancellation-and-compensableactivity"></a>İptal ve CompensableActivity  
 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> İçindeki <xref:System.Activities.Statements.CompensableActivity.Body%2A> Etkinliklertamamlanmadıysaveetkinlikiptaledilirse,<xref:System.Activities.Statements.CompensableActivity> içindeki etkinlikler yürütülür.  
  
> [!NOTE]
> <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> Yalnızca içindeki<xref:System.Activities.Statements.CompensableActivity> etkinlikler tamamlanmadıysa ve etkinlik iptal edildiğinde çağrılır. <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> Yalnızca içindeki<xref:System.Activities.Statements.CompensableActivity> etkinlikler başarıyla tamamlandığında ve tazminat etkinlik üzerinde çağrılırsa yürütülür. <xref:System.Activities.Statements.CompensableActivity.Body%2A>  
  
 , <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> İş akışı için uygun bir iptal mantığı sağlama fırsatı yazar. Aşağıdaki örnekte, öğesinin <xref:System.Activities.Statements.CompensableActivity.Body%2A>yürütülmesi sırasında bir özel durum oluşturulur ve <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> sonra çağrılır.  
  
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
  
 İş akışı çağrıldığında, benzetimli hata koşulu özel durumu ' de <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>konak uygulama tarafından işlenir, iş akışı iptal edilir ve <xref:System.Activities.Statements.CompensableActivity> öğesinin iptal mantığı çağrılır. Bu örnekte, Dengeleme mantığı ve iptal etme mantığının farklı hedefleri vardır. Başarılı bir şekilde tamamlanırsa, kredi kartının ücretlendirilildiği ve uçuşın her iki adımı da geri alması gerektiği anlamına gelir. <xref:System.Activities.Statements.CompensableActivity.Body%2A> (Bu örnekte, uçuşmanın iptal edilmesi, kredi kartı ücretlerini otomatik olarak iptal eder.) Ancak, iptal edilirse bu, tamamlanmamış <xref:System.Activities.Statements.CompensableActivity.Body%2A> olduğu anlamına gelir ve bu <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> nedenle İptalin en iyi şekilde nasıl işleneceğini belirleyebilmelidir. <xref:System.Activities.Statements.CompensableActivity> Bu örnekte <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> , kredi kartı ücreti iptal edilir, ancak içinde <xref:System.Activities.Statements.CompensableActivity.Body%2A>son etkinlik `ReserveFlight` olduğundan, uçuştan iptal etmeyi denemez. İçindeki son etkinlik olduğundan, bu, başarıyla tamamlandıysa, <xref:System.Activities.Statements.CompensableActivity.Body%2A> tamamlanmış olur ve hiçbir iptali mümkün olmaz. <xref:System.Activities.Statements.CompensableActivity.Body%2A> `ReserveFlight`  
  
 **ChargeCreditCard: Uçuş için kredi kartı ücreti.**  
**SimulatedErrorCondition: ApplicationException oluşturuluyor.**    
**İş akışı Işlenmemiş özel durumu:**    
**System. ApplicationException: İş akışında Benzetimli hata koşulu.**    
**CancelCreditCard: Kredi kartı ücretlerini iptal edin.**    
**İş akışı şu durumla başarıyla tamamlandı: Edilmesi.**  İptal hakkında daha fazla bilgi için bkz. [iptal](modeling-cancellation-behavior-in-workflows.md).  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a>Telafi etkinliğini kullanan açık Dengeleme  
 Önceki bölümde örtük Dengeleme ele alınmıştır. Örtük Dengeleme basit senaryolar için uygun olabilir, ancak tazmin işleme <xref:System.Activities.Statements.Compensate> zamanlaması üzerinde daha fazla açık denetim gerekliyse etkinlik kullanılabilir. İşlem ile <xref:System.Activities.Statements.Compensate> <xref:System.Activities.Statements.CompensableActivity> Dengeleme işlemini başlatmak için tazminat istenen öğesininkullanıldığıyer.<xref:System.Activities.Statements.CompensationToken> Etkinlik <xref:System.Activities.Statements.Compensate> , onaylanmayan veya dengelenen herhangi bir tamamlanmış <xref:System.Activities.Statements.CompensableActivity> üzerinden tazminat başlatmak için kullanılabilir. Örneğin, <xref:System.Activities.Statements.Compensate> etkinlik bir <xref:System.Activities.Statements.TryCatch.Catches%2A> <xref:System.Activities.Statements.TryCatch> etkinliğin bölümünde veya tamamlandıktan sonra <xref:System.Activities.Statements.CompensableActivity> herhangi bir zaman kullanılabilir. Bu örnekte <xref:System.Activities.Statements.Compensate> etkinlik, <xref:System.Activities.Statements.TryCatch> <xref:System.Activities.Statements.TryCatch.Catches%2A> eylemi<xref:System.Activities.Statements.CompensableActivity>tersine çevirmek için etkinliğin bölümünde kullanılır.  
  
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
  
 **Rezervlü Eflight: Bilet ayrıldı.**  
**SimulatedErrorCondition: ApplicationException oluşturuluyor.**    
**Canceluçuş: Bilet iptal edildi.**    
**İş akışı şu durumla başarıyla tamamlandı: Kapandı.**    
### <a name="confirming-compensation"></a>Tazminat onaylama  
 Varsayılan olarak, compensable etkinlikleri tamamlandıktan sonra herhangi bir zaman dengelenebilir. Bazı senaryolarda bu uygun olmayabilir. Önceki örnekte, anahtarı ayırma dengelemesi ayırmayı iptal etmiydi. Ancak, uçuş tamamlandıktan sonra bu dengeleme adımı artık geçerli değildir. Dengelenebilir etkinliğin tarafından <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>belirtilen etkinliği çağırdığı doğrulanıyor. Bunun olası bir kullanımı, tazminatı gerçekleştirmek için gerekli olan tüm kaynaklara izin vermedir. Dengelenebilir bir etkinliğin onaylandıktan sonra, telafi olması mümkün değildir ve bu denendiğinde özel bir <xref:System.InvalidOperationException> durum oluşturulur. Bir iş akışı başarıyla tamamlandığında, başarıyla tamamlanan, onaylanmamış ve dengelenmemiş tüm telafi etkinlikleri, tamamlanma sırasında onaylanır. Bu örnekte uçuş ayrılmıştır, satın alınır ve tamamlanır ve sonra dengelenebilir etkinlik onaylanır. Bir <xref:System.Activities.Statements.CompensableActivity>doğrulamak için, <xref:System.Activities.Statements.Confirm> etkinliğini <xref:System.Activities.Statements.CompensationToken> kullanın<xref:System.Activities.Statements.CompensableActivity> ve öğesini doğrulamak için öğesini belirtin.  
  
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
  
**Rezervlü Eflight: Bilet ayrıldı.**  
**Yönetici onayı: Yönetici onayı alındı.**    
**PurchaseFlight: Bilet satın alındı.**    
**Takeuçuş: Uçuş tamamlandı.**    
**ConfirmFlight: Uçuş alındı, hiçbir telafi yapılamaz.**    
**İş akışı şu durumla başarıyla tamamlandı: Kapandı.**   

## <a name="nesting-compensation-activities"></a>Telafi etkinliklerinin iç içe geçirilmesi  

Bir <xref:System.Activities.Statements.CompensableActivity>diğerinin bölümüneeklenebilir.<xref:System.Activities.Statements.CompensableActivity> <xref:System.Activities.Statements.CompensableActivity.Body%2A> Bir <xref:System.Activities.Statements.CompensableActivity> başka<xref:System.Activities.Statements.CompensableActivity>bir işleyiciye yerleştirilmeyebilir. Bu, bir üst <xref:System.Activities.Statements.CompensableActivity> öğenin sorumluluğundadır, teyit edildiğinde veya telafi edildiğinde, başarıyla tamamlanan ve henüz onaylanmamıştır veya telafi edilmesi gereken tüm alt öğe dengelenebilir etkinlikleri onaylamalıdır veya üst öğe iptali, onayı veya tazminatı tamamlanmadan önce dengelenen. Bu, açıkça modellenmezse, üst <xref:System.Activities.Statements.CompensableActivity> öğe iptal veya telafi sinyalini alıyorsa üst öğe, alt öğe dengelenebilir etkinlikleri dolaylı olarak dengelenir. Üst öğe onaylama sinyali aldıysa, üst öğe, alt dengelenebilir etkinlikleri dolaylı olarak kabul eder. İptali, onayı veya tazminatı işlemek için mantık, üst <xref:System.Activities.Statements.CompensableActivity>öğenin işleyicisinde açıkça modellendiyse, açıkça işlenmeyen tüm alt öğe örtük olarak onaylanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Statements.CompensableActivity>
- <xref:System.Activities.Statements.Compensate>
- <xref:System.Activities.Statements.Confirm>
- <xref:System.Activities.Statements.CompensationToken>
