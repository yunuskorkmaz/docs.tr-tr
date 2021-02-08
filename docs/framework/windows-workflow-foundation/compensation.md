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
# <a name="compensation"></a><span data-ttu-id="b19dc-103">Dengeleme</span><span class="sxs-lookup"><span data-stu-id="b19dc-103">Compensation</span></span>

<span data-ttu-id="b19dc-104">Windows Workflow Foundation (WF) dengelemesi, daha önce tamamlanmış işin geri alınamayacağı veya dengelemeyeceği (uygulama tarafından tanımlanan mantığı izleyerek) sonraki bir hata oluştuğunda yaptığı mekanizmadır.</span><span class="sxs-lookup"><span data-stu-id="b19dc-104">Compensation in Windows Workflow Foundation (WF) is the mechanism by which previously completed work can be undone or compensated (following the logic defined by the application) when a subsequent failure occurs.</span></span> <span data-ttu-id="b19dc-105">Bu bölümde, iş akışlarında tazminat kullanımı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b19dc-105">This section describes how to use compensation in workflows.</span></span>  
  
## <a name="compensation-vs-transactions"></a><span data-ttu-id="b19dc-106">Dengeleme ve Işlemler</span><span class="sxs-lookup"><span data-stu-id="b19dc-106">Compensation vs. Transactions</span></span>  

 <span data-ttu-id="b19dc-107">Bir işlem, birden çok işlemi tek bir iş biriminde birleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b19dc-107">A transaction allows you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="b19dc-108">Bir işlemin kullanılması, işlem işleminin herhangi bir bölümünde herhangi bir hata oluşursa, uygulamanıza işlemin içinden yürütülen tüm değişiklikleri (geri alma) sağlar.</span><span class="sxs-lookup"><span data-stu-id="b19dc-108">Using a transaction gives your application the ability to abort (roll back) all changes executed from within the transaction if any errors occur during any part of the transaction process.</span></span> <span data-ttu-id="b19dc-109">Ancak, iş uzun süre çalışıyorsa, işlemler kullanmak uygun olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="b19dc-109">However, using transactions may not be appropriate if the work is long running.</span></span> <span data-ttu-id="b19dc-110">Örneğin, bir seyahat planlama uygulaması iş akışı olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b19dc-110">For example, a travel planning application is implemented as a workflow.</span></span> <span data-ttu-id="b19dc-111">İş akışının adımları, bir uçuş kaydı, yönetici onayını bekleme ve sonra uçuş için ödeme yapma bilgisinden oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="b19dc-111">The steps of the workflow may consist of booking a flight, waiting for manager approval, and then paying for the flight.</span></span> <span data-ttu-id="b19dc-112">Bu işlem birçok gün sürebilir ve aynı işleme katılabilmek için yapılan kayıt ve ödeme adımları için pratik değildir.</span><span class="sxs-lookup"><span data-stu-id="b19dc-112">This process could take many days and it is not practical for the steps of booking and paying for the flight to participate in the same transaction.</span></span> <span data-ttu-id="b19dc-113">Bunun gibi bir senaryoda, işlem içinde daha sonra bir hata oluşursa iş akışının kayıt adımını geri almak için Dengeleme kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b19dc-113">In a scenario such as this, compensation could be used to undo the booking step of the workflow if there is a failure later in the processing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b19dc-114">Bu konu, iş akışlarında tazminat içerir.</span><span class="sxs-lookup"><span data-stu-id="b19dc-114">This topic covers compensation in workflows.</span></span> <span data-ttu-id="b19dc-115">İş akışlarında işlemler hakkında daha fazla bilgi için bkz. [işlemler](workflow-transactions.md) ve <xref:System.Activities.Statements.TransactionScope> .</span><span class="sxs-lookup"><span data-stu-id="b19dc-115">For more information about transactions in workflows, see [Transactions](workflow-transactions.md) and <xref:System.Activities.Statements.TransactionScope>.</span></span> <span data-ttu-id="b19dc-116">İşlemler hakkında daha fazla bilgi için bkz <xref:System.Transactions?displayProperty=nameWithType> <xref:System.Transactions.Transaction?displayProperty=nameWithType> . ve.</span><span class="sxs-lookup"><span data-stu-id="b19dc-116">For more information about transactions, see <xref:System.Transactions?displayProperty=nameWithType> and <xref:System.Transactions.Transaction?displayProperty=nameWithType>.</span></span>  
  
## <a name="using-compensableactivity"></a><span data-ttu-id="b19dc-117">CompensableActivity kullanma</span><span class="sxs-lookup"><span data-stu-id="b19dc-117">Using CompensableActivity</span></span>  

 <span data-ttu-id="b19dc-118"><xref:System.Activities.Statements.CompensableActivity> , içindeki temel Dengeleme etkinliğidir [!INCLUDE[wf1](../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b19dc-118"><xref:System.Activities.Statements.CompensableActivity> is the core compensation activity in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="b19dc-119">Telafi gerektiren işleri gerçekleştiren tüm etkinlikler <xref:System.Activities.Statements.CompensableActivity.Body%2A> bir ' a yerleştirilir <xref:System.Activities.Statements.CompensableActivity> .</span><span class="sxs-lookup"><span data-stu-id="b19dc-119">Any activities that perform work that may need to be compensated are placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="b19dc-120">Bu örnekte, bir uçuş satın almanın rezervasyon adımı <xref:System.Activities.Statements.CompensableActivity.Body%2A> bir ' a yerleştirilir <xref:System.Activities.Statements.CompensableActivity> ve ayırmanın iptal edilmesi öğesine yerleştirilir <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> .</span><span class="sxs-lookup"><span data-stu-id="b19dc-120">In this example, the reservation step of purchasing a flight is placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> and the cancellation of the reservation is placed into the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>.</span></span> <span data-ttu-id="b19dc-121"><xref:System.Activities.Statements.CompensableActivity>İş akışında hemen sonraki bölümünde, yönetici onayını bekleyen iki etkinlik vardır ve sonra uçuşın satın alma adımını tamamlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b19dc-121">Immediately following the <xref:System.Activities.Statements.CompensableActivity> in the workflow are two activities that wait for manager approval and then complete the purchasing step of the flight.</span></span> <span data-ttu-id="b19dc-122">Bir hata durumu başarıyla tamamlandıktan sonra iş akışının iptal edilmesine neden oluyorsa <xref:System.Activities.Statements.CompensableActivity> , <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> işleyicisindeki etkinlikler zamanlanır ve uçuş iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="b19dc-122">If an error condition causes the workflow to be canceled after the <xref:System.Activities.Statements.CompensableActivity> has successfully completed, then the activities in the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> handler are scheduled and the flight is canceled.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#1)]  
  
 <span data-ttu-id="b19dc-123">Aşağıdaki örnek, XAML içindeki iş akışıdır.</span><span class="sxs-lookup"><span data-stu-id="b19dc-123">The following example is the workflow in XAML.</span></span>  
  
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
  
 <span data-ttu-id="b19dc-124">İş akışı çağrıldığında, konsola aşağıdaki çıktı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b19dc-124">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="b19dc-125">**Rezerveflight: bilet ayrıldı.**</span><span class="sxs-lookup"><span data-stu-id="b19dc-125">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="b19dc-126">**Managerapproval: yönetici onayı alındı.** 
 **PurchaseFlight: bilet satın alındı.** 
 **Iş akışı şu durumla başarıyla tamamlandı: kapatıldı.**</span><span class="sxs-lookup"><span data-stu-id="b19dc-126">**ManagerApproval: Manager approval received.**
**PurchaseFlight: Ticket is purchased.**
**Workflow completed successfully with status: Closed.**</span></span>
> [!NOTE]
> <span data-ttu-id="b19dc-127">Bu konudaki örnek etkinlikler, `ReserveFlight` tazminat gerçekleştiğinde etkinliklerin yürütüldüğü sırayı göstermeye yardımcı olmak üzere konsola adlarını ve amaçlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b19dc-127">The sample activities in this topic such as `ReserveFlight` display their name and purpose to the console to help illustrate the order in which the activities are executed when compensation occurs.</span></span>  
  
### <a name="default-workflow-compensation"></a><span data-ttu-id="b19dc-128">Varsayılan Iş akışı dengelemesi</span><span class="sxs-lookup"><span data-stu-id="b19dc-128">Default Workflow Compensation</span></span>  

 <span data-ttu-id="b19dc-129">Varsayılan olarak, iş akışı iptal edilirse, Dengeleme mantığı başarıyla tamamen ve onaylanmış veya dengelenen tüm telafi etkinlikleri için çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="b19dc-129">By default, if the workflow is canceled, the compensation logic is run for any compensable activity that has successfully completely and has not already been confirmed or compensated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b19dc-130">Bir <xref:System.Activities.Statements.CompensableActivity> *onaylanırsa*, etkinliğin dengelemesi artık çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="b19dc-130">When a <xref:System.Activities.Statements.CompensableActivity> is *confirmed*, compensation for the activity can no longer be invoked.</span></span> <span data-ttu-id="b19dc-131">Bu bölümde daha sonra onay süreci açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b19dc-131">The confirmation process is described later in this section.</span></span>  
  
 <span data-ttu-id="b19dc-132">Bu örnekte, uçuş ayrıldıktan sonra ancak yöneticinin onay adımından önce bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b19dc-132">In this example, an exception is thrown after the flight is reserved but before the manager approval step.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#2)]  
  
 <span data-ttu-id="b19dc-133">Bu örnek, XAML 'deki iş akışıdır.</span><span class="sxs-lookup"><span data-stu-id="b19dc-133">This example is the workflow in XAML.</span></span>  
  
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
  
 <span data-ttu-id="b19dc-134">İş akışı çağrıldığında, benzetimli hata koşulu özel durumu içindeki konak uygulama tarafından işlenir <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> , iş akışı iptal edilir ve Dengeleme mantığı çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b19dc-134">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the compensation logic is invoked.</span></span>  
  
 <span data-ttu-id="b19dc-135">**Rezerveflight: bilet ayrıldı.**</span><span class="sxs-lookup"><span data-stu-id="b19dc-135">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="b19dc-136">**SimulatedErrorCondition: ApplicationException oluşturuluyor.** 
 **Iş akışı Işlenmemiş özel durumu:** 
 **System. ApplicationException: iş akışında Benzetimli hata koşulu.** 
 **Canceluçuş: bilet iptal edildi.** 
 **Iş akışı şu durumla başarıyla tamamlandı: Iptal edildi.**</span><span class="sxs-lookup"><span data-stu-id="b19dc-136">**SimulatedErrorCondition: Throwing an ApplicationException.**
**Workflow Unhandled Exception:**
**System.ApplicationException: Simulated error condition in the workflow.**
**CancelFlight: Ticket is canceled.**
**Workflow completed successfully with status: Canceled.**</span></span>

### <a name="cancellation-and-compensableactivity"></a><span data-ttu-id="b19dc-137">İptal ve CompensableActivity</span><span class="sxs-lookup"><span data-stu-id="b19dc-137">Cancellation and CompensableActivity</span></span>  

 <span data-ttu-id="b19dc-138">İçindeki etkinlikler <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> tamamlanmadıysa ve etkinlik iptal edilirse, içindeki etkinlikler <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> yürütülür.</span><span class="sxs-lookup"><span data-stu-id="b19dc-138">If the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled, the activities in the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> are executed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b19dc-139"><xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>Yalnızca içindeki etkinlikler <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> tamamlanmadıysa ve etkinlik iptal edildiğinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b19dc-139">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is only invoked if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled.</span></span> <span data-ttu-id="b19dc-140"><xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>Yalnızca içindeki etkinlikler <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> başarıyla tamamlandığında ve tazminat etkinlik üzerinde çağrılırsa yürütülür.</span><span class="sxs-lookup"><span data-stu-id="b19dc-140">The <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> is only executed if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have successfully completed and compensation is subsequently invoked on the activity.</span></span>  
  
 <span data-ttu-id="b19dc-141">, <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> İş akışı için uygun bir iptal mantığı sağlama fırsatı yazar.</span><span class="sxs-lookup"><span data-stu-id="b19dc-141">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> gives workflow authors the opportunity to provide any appropriate cancellation logic.</span></span> <span data-ttu-id="b19dc-142">Aşağıdaki örnekte, öğesinin yürütülmesi sırasında bir özel durum oluşturulur <xref:System.Activities.Statements.CompensableActivity.Body%2A> ve sonra <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b19dc-142">In the following example, an exception is thrown during the execution of the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, and then the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is invoked.</span></span>  
  
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
  
 <span data-ttu-id="b19dc-143">Bu örnek, XAML 'deki iş akışıdır</span><span class="sxs-lookup"><span data-stu-id="b19dc-143">This example is the workflow in XAML</span></span>  
  
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
  
 <span data-ttu-id="b19dc-144">İş akışı çağrıldığında, benzetimli hata koşulu özel durumu ' de konak uygulama tarafından işlenir <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> , iş akışı iptal edilir ve öğesinin iptal mantığı <xref:System.Activities.Statements.CompensableActivity> çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b19dc-144">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the cancellation logic of the <xref:System.Activities.Statements.CompensableActivity> is invoked.</span></span> <span data-ttu-id="b19dc-145">Bu örnekte, Dengeleme mantığı ve iptal etme mantığının farklı hedefleri vardır.</span><span class="sxs-lookup"><span data-stu-id="b19dc-145">In this example, the compensation logic and the cancellation logic have different goals.</span></span> <span data-ttu-id="b19dc-146">Başarılı bir <xref:System.Activities.Statements.CompensableActivity.Body%2A> şekilde tamamlanırsa, kredi kartının ücretlendirilildiği ve uçuşın her iki adımı da geri alması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b19dc-146">If the <xref:System.Activities.Statements.CompensableActivity.Body%2A> completed successfully, then this means the credit card was charged and the flight booked, so the compensation should undo both steps.</span></span> <span data-ttu-id="b19dc-147">(Bu örnekte, uçuşmanın iptal edilmesi, kredi kartı ücretlerini otomatik olarak iptal eder.) Ancak, <xref:System.Activities.Statements.CompensableActivity> iptal edilirse bu, tamamlanmamış olduğu anlamına gelir <xref:System.Activities.Statements.CompensableActivity.Body%2A> ve bu nedenle <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> İptalin en iyi şekilde nasıl işleneceğini belirleyebilmelidir.</span><span class="sxs-lookup"><span data-stu-id="b19dc-147">(In this example, canceling the flight automatically cancels the credit card charges.) However, if the <xref:System.Activities.Statements.CompensableActivity> is canceled, this means the <xref:System.Activities.Statements.CompensableActivity.Body%2A> did not complete and so the logic of the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> needs to be able to determine how to best handle the cancellation.</span></span> <span data-ttu-id="b19dc-148">Bu örnekte, <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> kredi kartı ücreti iptal edilir, ancak `ReserveFlight` içinde son etkinlik olduğundan, <xref:System.Activities.Statements.CompensableActivity.Body%2A> uçuştan iptal etmeyi denemez.</span><span class="sxs-lookup"><span data-stu-id="b19dc-148">In this example, the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> cancels the credit card charge, but since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, it does not attempt to cancel the flight.</span></span> <span data-ttu-id="b19dc-149">`ReserveFlight`İçindeki son etkinlik olduğundan, bu, <xref:System.Activities.Statements.CompensableActivity.Body%2A> başarıyla tamamlandıysa, <xref:System.Activities.Statements.CompensableActivity.Body%2A> tamamlanmış olur ve hiçbir iptali mümkün olmaz.</span><span class="sxs-lookup"><span data-stu-id="b19dc-149">Since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, if it had successfully completed then the <xref:System.Activities.Statements.CompensableActivity.Body%2A> would have completed and no cancellation would be possible.</span></span>  
  
 <span data-ttu-id="b19dc-150">**ChargeCreditCard: uçuş için kredi kartı ücreti.**</span><span class="sxs-lookup"><span data-stu-id="b19dc-150">**ChargeCreditCard: Charge credit card for flight.**</span></span>  
<span data-ttu-id="b19dc-151">**SimulatedErrorCondition: ApplicationException oluşturuluyor.** 
 **Iş akışı Işlenmemiş özel durumu:** 
 **System. ApplicationException: iş akışında Benzetimli hata koşulu.** 
 **Cancelcreditcard: kredi kartı ücretlerini Iptal et.** 
 **Iş akışı şu durumla başarıyla tamamlandı: Iptal edildi.**</span><span class="sxs-lookup"><span data-stu-id="b19dc-151">**SimulatedErrorCondition: Throwing an ApplicationException.**
**Workflow Unhandled Exception:**
**System.ApplicationException: Simulated error condition in the workflow.**
**CancelCreditCard: Cancel credit card charges.**
**Workflow completed successfully with status: Canceled.**</span></span>  <span data-ttu-id="b19dc-152">İptal hakkında daha fazla bilgi için bkz. [iptal](modeling-cancellation-behavior-in-workflows.md).</span><span class="sxs-lookup"><span data-stu-id="b19dc-152">For more information about cancellation, see [Cancellation](modeling-cancellation-behavior-in-workflows.md).</span></span>  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a><span data-ttu-id="b19dc-153">Telafi etkinliğini kullanan açık Dengeleme</span><span class="sxs-lookup"><span data-stu-id="b19dc-153">Explicit Compensation Using the Compensate Activity</span></span>  

 <span data-ttu-id="b19dc-154">Önceki bölümde örtük Dengeleme ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="b19dc-154">In the previous section, implicit compensation was covered.</span></span> <span data-ttu-id="b19dc-155">Örtük Dengeleme basit senaryolar için uygun olabilir, ancak tazmin işleme zamanlaması üzerinde daha fazla açık denetim gerekliyse <xref:System.Activities.Statements.Compensate> etkinlik kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b19dc-155">Implicit compensation can be appropriate for simple scenarios, but if more explicit control is required over the scheduling of compensation handling then the <xref:System.Activities.Statements.Compensate> activity can be used.</span></span> <span data-ttu-id="b19dc-156">İşlem ile dengeleme işlemini başlatmak için <xref:System.Activities.Statements.Compensate> <xref:System.Activities.Statements.CompensationToken> <xref:System.Activities.Statements.CompensableActivity> tazminat istenen öğesinin kullanıldığı yer.</span><span class="sxs-lookup"><span data-stu-id="b19dc-156">To initiate the compensation process with the <xref:System.Activities.Statements.Compensate> activity, the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> for which compensation is desired is used.</span></span> <span data-ttu-id="b19dc-157"><xref:System.Activities.Statements.Compensate>Etkinlik, <xref:System.Activities.Statements.CompensableActivity> onaylanmayan veya dengelenen herhangi bir tamamlanmış üzerinden tazminat başlatmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b19dc-157">The <xref:System.Activities.Statements.Compensate> activity can be used to initiate compensation on any completed <xref:System.Activities.Statements.CompensableActivity> that has not been confirmed or compensated.</span></span> <span data-ttu-id="b19dc-158">Örneğin, etkinlik <xref:System.Activities.Statements.Compensate> <xref:System.Activities.Statements.TryCatch.Catches%2A> bir <xref:System.Activities.Statements.TryCatch> etkinliğin bölümünde veya tamamlandıktan sonra herhangi bir zaman kullanılabilir <xref:System.Activities.Statements.CompensableActivity> .</span><span class="sxs-lookup"><span data-stu-id="b19dc-158">For example, a <xref:System.Activities.Statements.Compensate> activity could be used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity, or any time after the <xref:System.Activities.Statements.CompensableActivity> has completed.</span></span> <span data-ttu-id="b19dc-159">Bu örnekte <xref:System.Activities.Statements.Compensate> etkinlik <xref:System.Activities.Statements.TryCatch.Catches%2A> <xref:System.Activities.Statements.TryCatch> , eylemi tersine çevirmek için etkinliğin bölümünde kullanılır <xref:System.Activities.Statements.CompensableActivity> .</span><span class="sxs-lookup"><span data-stu-id="b19dc-159">In this example, the <xref:System.Activities.Statements.Compensate> activity is used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity to reverse the action of the <xref:System.Activities.Statements.CompensableActivity>.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#3)]  
  
 <span data-ttu-id="b19dc-160">Bu örnek, XAML 'deki iş akışıdır.</span><span class="sxs-lookup"><span data-stu-id="b19dc-160">This example is the workflow in XAML.</span></span>  
  
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
  
 <span data-ttu-id="b19dc-161">İş akışı çağrıldığında, konsola aşağıdaki çıktı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b19dc-161">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="b19dc-162">**Rezerveflight: bilet ayrıldı.**</span><span class="sxs-lookup"><span data-stu-id="b19dc-162">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="b19dc-163">**SimulatedErrorCondition: ApplicationException oluşturuluyor.** 
 **Canceluçuş: bilet iptal edildi.** 
 **Iş akışı şu durumla başarıyla tamamlandı: kapatıldı.**</span><span class="sxs-lookup"><span data-stu-id="b19dc-163">**SimulatedErrorCondition: Throwing an ApplicationException.**
**CancelFlight: Ticket is canceled.**
**Workflow completed successfully with status: Closed.**</span></span>

### <a name="confirming-compensation"></a><span data-ttu-id="b19dc-164">Tazminat onaylama</span><span class="sxs-lookup"><span data-stu-id="b19dc-164">Confirming Compensation</span></span>  

 <span data-ttu-id="b19dc-165">Varsayılan olarak, compensable etkinlikleri tamamlandıktan sonra herhangi bir zaman dengelenebilir.</span><span class="sxs-lookup"><span data-stu-id="b19dc-165">By default, compensable activities can be compensated any time after they have completed.</span></span> <span data-ttu-id="b19dc-166">Bazı senaryolarda bu uygun olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="b19dc-166">In some scenarios this may not be appropriate.</span></span> <span data-ttu-id="b19dc-167">Önceki örnekte, anahtarı ayırma dengelemesi ayırmayı iptal etmiydi.</span><span class="sxs-lookup"><span data-stu-id="b19dc-167">In the previous example the compensation to reserving the ticket was to cancel the reservation.</span></span> <span data-ttu-id="b19dc-168">Ancak, uçuş tamamlandıktan sonra bu dengeleme adımı artık geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="b19dc-168">However, after the flight has been completed this compensation step is no longer valid.</span></span> <span data-ttu-id="b19dc-169">Dengelenebilir etkinliğin tarafından belirtilen etkinliği çağırdığı doğrulanıyor <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> .</span><span class="sxs-lookup"><span data-stu-id="b19dc-169">Confirming the compensable activity invokes the activity specified by the <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>.</span></span> <span data-ttu-id="b19dc-170">Bunun olası bir kullanımı, tazminatı gerçekleştirmek için gerekli olan tüm kaynaklara izin vermedir.</span><span class="sxs-lookup"><span data-stu-id="b19dc-170">One possible use for this is to allow any resources that are necessary to perform the compensation to be released.</span></span> <span data-ttu-id="b19dc-171">Dengelenebilir bir etkinliğin onaylandıktan sonra, telafi olması mümkün değildir ve bu denendiğinde <xref:System.InvalidOperationException> özel bir durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b19dc-171">After a compensable activity is confirmed it is not possible for it to be compensated, and if this is attempted an <xref:System.InvalidOperationException> exception is thrown.</span></span> <span data-ttu-id="b19dc-172">Bir iş akışı başarıyla tamamlandığında, başarıyla tamamlanan, onaylanmamış ve dengelenmemiş tüm telafi etkinlikleri, tamamlanma sırasında onaylanır.</span><span class="sxs-lookup"><span data-stu-id="b19dc-172">When a workflow completes successfully, all non-confirmed and non-compensated compensable activities that completed successfully are confirmed in reverse order of completion.</span></span> <span data-ttu-id="b19dc-173">Bu örnekte uçuş ayrılmıştır, satın alınır ve tamamlanır ve sonra dengelenebilir etkinlik onaylanır.</span><span class="sxs-lookup"><span data-stu-id="b19dc-173">In this example the flight is reserved, purchased, and completed, and then the compensable activity is confirmed.</span></span> <span data-ttu-id="b19dc-174">Bir doğrulamak için <xref:System.Activities.Statements.CompensableActivity> , etkinliğini kullanın <xref:System.Activities.Statements.Confirm> ve öğesini <xref:System.Activities.Statements.CompensationToken> doğrulamak için öğesini belirtin <xref:System.Activities.Statements.CompensableActivity> .</span><span class="sxs-lookup"><span data-stu-id="b19dc-174">To confirm a <xref:System.Activities.Statements.CompensableActivity>, use the <xref:System.Activities.Statements.Confirm> activity and specify the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> to confirm.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#4](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#4)]  
  
 <span data-ttu-id="b19dc-175">Bu örnek, XAML 'deki iş akışıdır.</span><span class="sxs-lookup"><span data-stu-id="b19dc-175">This example is the workflow in XAML.</span></span>  
  
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
  
<span data-ttu-id="b19dc-176">İş akışı çağrıldığında, konsola aşağıdaki çıktı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b19dc-176">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
<span data-ttu-id="b19dc-177">**Rezerveflight: bilet ayrıldı.**</span><span class="sxs-lookup"><span data-stu-id="b19dc-177">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="b19dc-178">**Managerapproval: yönetici onayı alındı.** 
 **PurchaseFlight: bilet satın alındı.** 
 **Takeuçuş: uçuş tamamlandı.** 
 **ConfirmFlight: uçuş alındı, hiçbir telafi yapılamaz.** 
 **Iş akışı şu durumla başarıyla tamamlandı: kapatıldı.**</span><span class="sxs-lookup"><span data-stu-id="b19dc-178">**ManagerApproval: Manager approval received.**
**PurchaseFlight: Ticket is purchased.**
**TakeFlight: Flight is completed.**
**ConfirmFlight: Flight has been taken, no compensation possible.**
**Workflow completed successfully with status: Closed.**</span></span>

## <a name="nesting-compensation-activities"></a><span data-ttu-id="b19dc-179">Telafi etkinliklerinin iç içe geçirilmesi</span><span class="sxs-lookup"><span data-stu-id="b19dc-179">Nesting Compensation Activities</span></span>  

<span data-ttu-id="b19dc-180">Bir <xref:System.Activities.Statements.CompensableActivity> <xref:System.Activities.Statements.CompensableActivity.Body%2A> diğerinin bölümüne eklenebilir <xref:System.Activities.Statements.CompensableActivity> .</span><span class="sxs-lookup"><span data-stu-id="b19dc-180">A <xref:System.Activities.Statements.CompensableActivity> can be placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> section of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="b19dc-181">Bir <xref:System.Activities.Statements.CompensableActivity> başka bir işleyiciye yerleştirilmeyebilir <xref:System.Activities.Statements.CompensableActivity> .</span><span class="sxs-lookup"><span data-stu-id="b19dc-181">A <xref:System.Activities.Statements.CompensableActivity> may not be placed into a handler of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="b19dc-182">Bir üst, <xref:System.Activities.Statements.CompensableActivity> iptal edildiğinde, teyit edildiğinde veya telafi edildiğinde, başarıyla tamamlanan ve henüz onaylanmamış veya dengelenen tüm alt öğe telafi etkinliklerinin, üst öğe iptali, onaylama veya tazminat tamamlanmadan önce onaylanması veya telafi edilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="b19dc-182">It is the responsibility of a parent <xref:System.Activities.Statements.CompensableActivity> to ensure that when it is canceled, confirmed, or compensated, all child compensable activities that have completed successfully and have not already been confirmed or compensated must be confirmed or compensated before the parent completes cancellation, confirmation, or compensation.</span></span> <span data-ttu-id="b19dc-183">Bu, açıkça modellenmezse, <xref:System.Activities.Statements.CompensableActivity> üst öğe iptal veya telafi sinyalini alıyorsa üst öğe, alt öğe dengelenebilir etkinlikleri dolaylı olarak dengelenir.</span><span class="sxs-lookup"><span data-stu-id="b19dc-183">If this is not modeled explicitly the parent <xref:System.Activities.Statements.CompensableActivity> will implicitly compensate child compensable activities if the parent received the cancel or compensate signal.</span></span> <span data-ttu-id="b19dc-184">Üst öğe onaylama sinyali aldıysa, üst öğe, alt dengelenebilir etkinlikleri dolaylı olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="b19dc-184">If the parent received the confirm signal the parent will implicitly confirm child compensable activities.</span></span> <span data-ttu-id="b19dc-185">İptali, onayı veya tazminatı işlemek için mantık, üst öğenin işleyicisinde açıkça modellendiyse <xref:System.Activities.Statements.CompensableActivity> , açıkça işlenmeyen tüm alt öğe örtük olarak onaylanır.</span><span class="sxs-lookup"><span data-stu-id="b19dc-185">If the logic to handle cancellation, confirmation, or compensation is explicitly modeled in the handler of the parent <xref:System.Activities.Statements.CompensableActivity>, any child not explicitly handled will be implicitly confirmed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b19dc-186">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b19dc-186">See also</span></span>

- <xref:System.Activities.Statements.CompensableActivity>
- <xref:System.Activities.Statements.Compensate>
- <xref:System.Activities.Statements.Confirm>
- <xref:System.Activities.Statements.CompensationToken>
