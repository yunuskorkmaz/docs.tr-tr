---
title: Dengeleme
ms.date: 03/30/2017
ms.assetid: 722e9766-48d7-456c-9496-d7c5c8f0fa76
ms.openlocfilehash: 75c5ed2f5e5c3a93834632ce499a2c8195fbc6bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183000"
---
# <a name="compensation"></a>Dengeleme
Windows İş Akışı Temeli'ndeki (WF) tazminat, daha önce tamamlanmış çalışmanın sonraki bir hata oluştuğunda geri alınabileceği veya telafi edilebildiği (uygulama tarafından tanımlanan mantığı izleyerek) bir mekanizmadır. Bu bölümde, iş akışlarında tazminatın nasıl kullanılacağı açıklanmaktadır.  
  
## <a name="compensation-vs-transactions"></a>Tazminat ve İşlemler  
 Bir işlem, birden çok işlemi tek bir çalışma biriminde birleştirmenize olanak tanır. Bir işlemi kullanmak, işlem işleminin herhangi bir bölümünde herhangi bir hata oluşursa, uygulamanız içinden yürütülen tüm değişiklikleri iptal etme (geri alma) olanağı sağlar. Ancak, çalışma uzun sürüyorsa hareketleri kullanmak uygun olmayabilir. Örneğin, bir seyahat planlama uygulaması iş akışı olarak uygulanır. İş akışının adımları, bir uçuş rezervasyonu, yönetici onayı beklemek ve uçuş için ödeme yapmak olabilir. Bu işlem günler sürebilir ve aynı işleme katılmak için uçuş için rezervasyon ve ödeme adımları için pratik değildir. Böyle bir senaryoda, daha sonra işlemde bir hata olması durumunda, tazminat iş akışının rezervasyon adımını geri almak için kullanılabilir.  
  
> [!NOTE]
> Bu konu, iş akışlarındaki tazminatı kapsar. İş akışlarındaki hareketler hakkında daha [Transactions](workflow-transactions.md) fazla <xref:System.Activities.Statements.TransactionScope>bilgi için Hareketler ve . İşlemler hakkında daha <xref:System.Transactions?displayProperty=nameWithType> fazla <xref:System.Transactions.Transaction?displayProperty=nameWithType>bilgi için bkz.  
  
## <a name="using-compensableactivity"></a>Telafi Edilebilir Aktivite kullanma  
 <xref:System.Activities.Statements.CompensableActivity>'deki temel tazminat [!INCLUDE[wf1](../../../includes/wf1-md.md)]faaliyetidir. Telafi <xref:System.Activities.Statements.CompensableActivity.Body%2A> edilmesi gereken işleri gerçekleştiren faaliyetler bir <xref:System.Activities.Statements.CompensableActivity>. Bu örnekte, bir uçuş satın alma rezervasyon <xref:System.Activities.Statements.CompensableActivity.Body%2A> adımı <xref:System.Activities.Statements.CompensableActivity> a yerleştirilir ve rezervasyon iptali <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>yerleştirilir. Hemen iş <xref:System.Activities.Statements.CompensableActivity> akışı nda takip yönetici onayı bekleyin ve daha sonra uçuş satın alma adımı tamamlamak iki faaliyetvardır. Bir hata koşulu, iş akışının başarıyla <xref:System.Activities.Statements.CompensableActivity> tamamlandıktan sonra iptal edilmesine <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> neden oluyorsa, işleyicideki etkinlikler zamanlanır ve uçuş iptal edilir.  
  
 [!code-csharp[CFX_CompensationExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#1)]  
  
 Aşağıdaki örnek XAML'deki iş akışıdır.  
  
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
  
 İş akışı çağrıldığında, aşağıdaki çıktı konsola görüntülenir.  
  
 **Rezerv Uçuş: Bilet rezerve edilir.**  
**ManagerApproval: Yönetici onayı alındı.** 
 **Satın Alma Uçuşu: Bilet satın alınır.** 
 **Durumla birlikte başarıyla tamamlanan iş akışı: Kapalı.**
> [!NOTE]
> Bu konudaki örnek etkinlikler, telafi gerçekleştiğinde etkinliklerin yürütülme sırasını göstermeye yardımcı olmak için adlarını ve amaçlarını konsola görüntülemek gibi. `ReserveFlight`  
  
### <a name="default-workflow-compensation"></a>Varsayılan İş Akışı Tazminatı  
 Varsayılan olarak, iş akışı iptal edilirse, telafi mantığı başarıyla tamamen tamamlanmamış veya telafi edilmemiş herhangi bir telafi edilebilir etkinlik için çalıştırılır.  
  
> [!NOTE]
> Bir <xref:System.Activities.Statements.CompensableActivity> *onaylandığında,* etkinlik için tazminat artık çağrılabilir. Onay süreci daha sonra bu bölümde açıklanmıştır.  
  
 Bu örnekte, uçuş rezerve edildikten sonra ancak yönetici onay adımından önce bir özel durum atılır.  
  
 [!code-csharp[CFX_CompensationExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#2)]  
  
 Bu örnek, XAML'deki iş akışıdır.  
  
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
  
 İş akışı çağrıldığı zaman, benzetilen hata durumu özel durumu <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>ana bilgisayar uygulaması tarafından işlenir, iş akışı iptal edilir ve telafi mantığı çağrılır.  
  
 **Rezerv Uçuş: Bilet rezerve edilir.**  
**SimüleHata Durumu: ApplicationException atma.** 
 **İş Akışı İşlenmemiş Özel Durum:**
**System.ApplicationException: İş akışındaki benzetimli hata durumu.** 
 **İptal: Bilet iptal edilir.** 
 **Durumla birlikte başarıyla tamamlanan iş akışı: İptal edildi.**
### <a name="cancellation-and-compensableactivity"></a>İptal ve Telafi Etkinliği  
 A'daki <xref:System.Activities.Statements.CompensableActivity.Body%2A> faaliyetler <xref:System.Activities.Statements.CompensableActivity> tamamlanmamış sayılsa ve etkinlik iptal <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> edilirse, etkinlikteki faaliyetler yürütülür.  
  
> [!NOTE]
> Yalnızca, <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> etkinlikler <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> tamamlanmamışsa ve etkinlik iptal edilirse çağrılır. Yalnızca, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> etkinlikler başarıyla <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> tamamlanırsa ve daha sonra etkinlik üzerinde tazminat çağrılmışsa yürütülür.  
  
 İş <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> akışı yazarlarına uygun iptal mantığını sağlama fırsatı verir. Aşağıdaki örnekte, bir özel durum yürütme <xref:System.Activities.Statements.CompensableActivity.Body%2A>sırasında atılır <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> ve sonra çağrılır.  
  
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
  
 Bu örnek, XAML'deki iş akışıdır  
  
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
  
 İş akışı çağrıldığı zaman, benzetilen hata durumu özel durumu <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>ana bilgisayar uygulaması tarafından işlenir, iş <xref:System.Activities.Statements.CompensableActivity> akışı iptal edilir ve iptal mantığı çağrılır. Bu örnekte, telafi mantığı ve iptal mantığı farklı hedefleri vardır. Başarıyla <xref:System.Activities.Statements.CompensableActivity.Body%2A> tamamlanırsa, bu kredi kartının tahsil edildiği ve uçuş rezervasyonu nun yapılandığı anlamına gelir, bu yüzden tazminat her iki adımı da geri alınmıştır. (Bu örnekte, uçuşu iptal etmek kredi kartı ücretlerini otomatik olarak iptal eder.) Ancak, iptal <xref:System.Activities.Statements.CompensableActivity> edilirse, bu <xref:System.Activities.Statements.CompensableActivity.Body%2A> tamamlanmadı ve bu nedenle <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> iptal en iyi nasıl işleyeceğini belirlemek için gereken mantığı anlamına gelir. Bu örnekte, <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> kredi kartı ücretini iptal `ReserveFlight` eder, ancak son <xref:System.Activities.Statements.CompensableActivity.Body%2A>etkinlik olduğu için, uçuşu iptal etmeye çalışmaz. Bu `ReserveFlight` yana son faaliyet <xref:System.Activities.Statements.CompensableActivity.Body%2A>oldu , başarılı bir <xref:System.Activities.Statements.CompensableActivity.Body%2A> şekilde tamamlanmış olsaydı o zaman tamamlanmış olurdu ve hiçbir iptal mümkün olurdu.  
  
 **ChargeCreditCard: Uçuş için kredi kartından ücret alın.**  
**SimüleHata Durumu: ApplicationException atma.** 
 **İş Akışı İşlenmemiş Özel Durum:**
**System.ApplicationException: İş akışındaki benzetimli hata durumu.** 
 **CancelCreditCard: Kredi kartı ücretlerini iptal edin.** 
 **Durumla birlikte başarıyla tamamlanan iş akışı: İptal edildi.**  İptal hakkında daha fazla bilgi için [İptal'e](modeling-cancellation-behavior-in-workflows.md)bakın.  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a>Telafi Etkinliğini Kullanarak Açık Tazminat  
 Bir önceki bölümde örtülü tazminat ele alınmıştır. Örtük telafi basit senaryolar için uygun olabilir, ancak tazminat işleme zamanlaması üzerinde <xref:System.Activities.Statements.Compensate> daha açık denetim gerekiyorsa, etkinlik kullanılabilir. <xref:System.Activities.Statements.Compensate> Etkinlik le birlikte tazmin işlemini <xref:System.Activities.Statements.CompensationToken> başlatmak <xref:System.Activities.Statements.CompensableActivity> için, hangi tazminatın istendiği kullanılır. Etkinlik, <xref:System.Activities.Statements.Compensate> onaylanmamış veya tazmin edilmemiş <xref:System.Activities.Statements.CompensableActivity> herhangi bir tamamlanmış üzerinde tazminat başlatmak için kullanılabilir. Örneğin, bir <xref:System.Activities.Statements.Compensate> etkinlik bir etkinlik <xref:System.Activities.Statements.TryCatch.Catches%2A> bölümünde <xref:System.Activities.Statements.TryCatch> veya tamamlandıktan herhangi <xref:System.Activities.Statements.CompensableActivity> bir zamanda kullanılabilir. Bu örnekte, <xref:System.Activities.Statements.Compensate> etkinlik bir <xref:System.Activities.Statements.TryCatch.Catches%2A> <xref:System.Activities.Statements.TryCatch> etkinliğin bölümünde eylemi tersine çevirmek <xref:System.Activities.Statements.CompensableActivity>için kullanılır.  
  
 [!code-csharp[CFX_CompensationExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#3)]  
  
 Bu örnek, XAML'deki iş akışıdır.  
  
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
  
 İş akışı çağrıldığında, aşağıdaki çıktı konsola görüntülenir.  
  
 **Rezerv Uçuş: Bilet rezerve edilir.**  
**SimüleHata Durumu: ApplicationException atma.** 
 **İptal: Bilet iptal edilir.** 
 **Durumla birlikte başarıyla tamamlanan iş akışı: Kapalı.**
### <a name="confirming-compensation"></a>Tazminatı Onaylama  
 Varsayılan olarak, telafi edilebilir faaliyetler tamamlandıktan sonra herhangi bir zamanda telafi edilebilir. Bazı senaryolarda bu uygun olmayabilir. Önceki örnekte bilet rezervasyonu için tazminat rezervasyon iptal etmek oldu. Ancak, uçuş tamamlandıktan sonra bu tazminat adımı artık geçerli değildir. Telafi edilebilir etkinliğin onaylanması, <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>'. Bunun olası bir kullanımı, tazminatı gerçekleştirmek için gerekli olan kaynakların serbest bırakılmasına izin vermektir. Telafi edilebilir bir etkinlik onaylandıktan sonra telafi edilmesi mümkün değildir ve bu denenirse bir <xref:System.InvalidOperationException> istisna atılır. Bir iş akışı başarıyla tamamlandığında, başarıyla tamamlanan tüm onaylanmamış ve telafi edilemeyen telafi edilebilir tüm faaliyetler ters tamamlama sırasına göre onaylanır. Bu örnekte uçuş rezerve edilir, satın alınır ve tamamlanır ve telafi edilebilir etkinlik onaylanır. Bir <xref:System.Activities.Statements.CompensableActivity>onaylamak için, <xref:System.Activities.Statements.Confirm> etkinliği kullanın <xref:System.Activities.Statements.CompensationToken> ve <xref:System.Activities.Statements.CompensableActivity> onaylamak için belirtin.  
  
 [!code-csharp[CFX_CompensationExample#4](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#4)]  
  
 Bu örnek, XAML'deki iş akışıdır.  
  
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
  
İş akışı çağrıldığında, aşağıdaki çıktı konsola görüntülenir.  
  
**Rezerv Uçuş: Bilet rezerve edilir.**  
**ManagerApproval: Yönetici onayı alındı.** 
 **Satın Alma Uçuşu: Bilet satın alınır.** 
 **TakeFlight: Uçuş tamamlandı.** 
 **ConfirmFlight: Uçuş alınmıştır, hiçbir tazminat mümkün.** 
 **Durumla birlikte başarıyla tamamlanan iş akışı: Kapalı.**

## <a name="nesting-compensation-activities"></a>İç Içe Tazminat Faaliyetleri  

A <xref:System.Activities.Statements.CompensableActivity> başka bir <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity>bölüme yerleştirilebilir. A, <xref:System.Activities.Statements.CompensableActivity> başka <xref:System.Activities.Statements.CompensableActivity>bir işleyiciye yerleştirilemeyebilir. <xref:System.Activities.Statements.CompensableActivity> İptal edildiğinde, onaylandığunda veya tazmin edildiğinde, başarıyla tamamlanmış ve onaylanmamış veya telafi edilmemiş tüm çocuk telafi edici faaliyetlerin, ebeveyn iptal, onay veya tazminatı tamamlamadan önce onaylanması veya tazmin edilmesi gerekir. Bu açıkça modellenmemişse, <xref:System.Activities.Statements.CompensableActivity> ebeveyn iptal veya telafi sinyalini alırsa, ebeveyn alt takibe tabi olarak telafi eder. Ebeveyn onay sinyalini aldıysa, ebeveyn çocuğun telafi edilebilir etkinlikleri nizatla onaylayacaktır. İptal, onay veya tazminatı işleme mantığı açıkça ebeveynin <xref:System.Activities.Statements.CompensableActivity>işleyicisinde modellenirse, açıkça ele alınmayan herhangi bir çocuk örtülü olarak onaylanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Statements.CompensableActivity>
- <xref:System.Activities.Statements.Compensate>
- <xref:System.Activities.Statements.Confirm>
- <xref:System.Activities.Statements.CompensationToken>
