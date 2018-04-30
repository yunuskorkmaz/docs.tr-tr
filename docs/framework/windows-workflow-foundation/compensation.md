---
title: Maaş
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 722e9766-48d7-456c-9496-d7c5c8f0fa76
caps.latest.revision: 26
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2ed51d14c56358e283d6c014f036a8aff73d2bfe
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="compensation"></a><span data-ttu-id="747a3-102">Maaş</span><span class="sxs-lookup"><span data-stu-id="747a3-102">Compensation</span></span>
<span data-ttu-id="747a3-103">Windows Workflow Foundation (WF) Maaş, daha önce tamamlanmış iş bulunabilir geri alınamaz veya (aşağıdaki uygulama tarafından tanımlanan mantık) dengelendi mekanizması olduğunu izleyen bir hata oluştuğunda.</span><span class="sxs-lookup"><span data-stu-id="747a3-103">Compensation in Windows Workflow Foundation (WF) is the mechanism by which previously completed work can be undone or compensated (following the logic defined by the application) when a subsequent failure occurs.</span></span> <span data-ttu-id="747a3-104">Bu bölümde, iş akışlarında maaş kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="747a3-104">This section describes how to use compensation in workflows.</span></span>  
  
## <a name="compensation-vs-transactions"></a><span data-ttu-id="747a3-105">Maaş vs. İşlemler</span><span class="sxs-lookup"><span data-stu-id="747a3-105">Compensation vs. Transactions</span></span>  
 <span data-ttu-id="747a3-106">Bir işlem, tek bir birim birden çok işleme iş birleştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="747a3-106">A transaction allows you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="747a3-107">Bir işlem kullanarak uygulamanızı (geri dön) gelen tüm hataları işlem işleminin herhangi bir bölümü sırasında oluşursa işlem içinde yürütülen tüm değişiklikleri iptal etmek için olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="747a3-107">Using a transaction gives your application the ability to abort (roll back) all changes executed from within the transaction if any errors occur during any part of the transaction process.</span></span> <span data-ttu-id="747a3-108">Ancak, işlemleri kullanarak iş uzunsa çalıştıran uygun olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="747a3-108">However, using transactions may not be appropriate if the work is long running.</span></span> <span data-ttu-id="747a3-109">Örneğin, seyahat planlama uygulama iş akışı olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="747a3-109">For example, a travel planning application is implemented as a workflow.</span></span> <span data-ttu-id="747a3-110">İş akışı adımları bir uçuş kayıt, Yöneticisi onay bekliyor ve uçuş için ödeme oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="747a3-110">The steps of the workflow may consist of booking a flight, waiting for manager approval, and then paying for the flight.</span></span> <span data-ttu-id="747a3-111">Bu işlem günlerce sürebilir ve kayıt ve aynı işlemde katılmayı uçuş için ödeme işlemleri için kullanışlı değildir.</span><span class="sxs-lookup"><span data-stu-id="747a3-111">This process could take many days and it is not practical for the steps of booking and paying for the flight to participate in the same transaction.</span></span> <span data-ttu-id="747a3-112">Bunun gibi bir senaryoda, maaş işlenirken bir hata olduğunda iş akışının kayıt adımı geri almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="747a3-112">In a scenario such as this, compensation could be used to undo the booking step of the workflow if there is a failure later in the processing.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="747a3-113">Bu konu, iş akışlarında maaş kapsar.</span><span class="sxs-lookup"><span data-stu-id="747a3-113">This topic covers compensation in workflows.</span></span> <span data-ttu-id="747a3-114">İş akışlarında işlemleri hakkında daha fazla bilgi için bkz: [işlemleri](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md) ve <xref:System.Activities.Statements.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="747a3-114">For more information about transactions in workflows, see [Transactions](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md) and <xref:System.Activities.Statements.TransactionScope>.</span></span> <span data-ttu-id="747a3-115">İşlemler hakkında daha fazla bilgi için bkz: <xref:System.Transactions?displayProperty=nameWithType> ve <xref:System.Transactions.Transaction?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="747a3-115">For more information about transactions, see <xref:System.Transactions?displayProperty=nameWithType> and <xref:System.Transactions.Transaction?displayProperty=nameWithType>.</span></span>  
  
## <a name="using-compensableactivity"></a><span data-ttu-id="747a3-116">CompensableActivity kullanma</span><span class="sxs-lookup"><span data-stu-id="747a3-116">Using CompensableActivity</span></span>  
 <span data-ttu-id="747a3-117"><xref:System.Activities.Statements.CompensableActivity> Çekirdek maaş etkinliktir [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="747a3-117"><xref:System.Activities.Statements.CompensableActivity> is the core compensation activity in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="747a3-118">Dengelenebilmesi gerekebilir çalışmayı gerçekleştirmek hiç etkinlik içine yerleştirilen <xref:System.Activities.Statements.CompensableActivity.Body%2A> , bir <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="747a3-118">Any activities that perform work that may need to be compensated are placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="747a3-119">Bu örnekte, bir uçuş satın alma ayırma adım içine yerleştirildiğinde <xref:System.Activities.Statements.CompensableActivity.Body%2A> , bir <xref:System.Activities.Statements.CompensableActivity> ve ayırma iptaline yerleştirilir <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="747a3-119">In this example, the reservation step of purchasing a flight is placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> and the cancellation of the reservation is placed into the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>.</span></span> <span data-ttu-id="747a3-120">Hemen ardından <xref:System.Activities.Statements.CompensableActivity> için yönetici onayı bekleyin ve ardından satın alma uçuş adımın iki etkinlik iş akışı içinde olan.</span><span class="sxs-lookup"><span data-stu-id="747a3-120">Immediately following the <xref:System.Activities.Statements.CompensableActivity> in the workflow are two activities that wait for manager approval and then complete the purchasing step of the flight.</span></span> <span data-ttu-id="747a3-121">Bir hata koşulu sonra iptal edilmesi iş akışı neden olursa <xref:System.Activities.Statements.CompensableActivity> başarıyla tamamlandı, ardından etkinlikler <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> işleyici zamanlanır ve uçuş iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="747a3-121">If an error condition causes the workflow to be canceled after the <xref:System.Activities.Statements.CompensableActivity> has successfully completed, then the activities in the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> handler are scheduled and the flight is canceled.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#1](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#1)]  
  
 <span data-ttu-id="747a3-122">Aşağıdaki örnek XAML'de iş akışıdır.</span><span class="sxs-lookup"><span data-stu-id="747a3-122">The following example is the workflow in XAML.</span></span>  
  
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
  
 <span data-ttu-id="747a3-123">İş akışı çağrıldığında, aşağıdaki çıktıyı konsola görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="747a3-123">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="747a3-124">**ReserveFlight: Bilet ayrılmıştır.**</span><span class="sxs-lookup"><span data-stu-id="747a3-124">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="747a3-125">**ManagerApproval: alınan yönetici onayı gerekir.** </span><span class="sxs-lookup"><span data-stu-id="747a3-125">**ManagerApproval: Manager approval received.** </span></span>  
<span data-ttu-id="747a3-126">**PurchaseFlight: Bilet satın alınır.** </span><span class="sxs-lookup"><span data-stu-id="747a3-126">**PurchaseFlight: Ticket is purchased.** </span></span>  
<span data-ttu-id="747a3-127">**İş akışı durumu ile başarıyla tamamlandı: kapalı.**</span><span class="sxs-lookup"><span data-stu-id="747a3-127">**Workflow completed successfully with status: Closed.**</span></span>    
> [!NOTE]
>  <span data-ttu-id="747a3-128">Gibi bu konudaki örnek etkinlikleri `ReserveFlight` adlarını ve amacı, etkinlikleri yürütülme maaş oluştuğunda sipariş göstermeye yardımcı olmak için konsola görüntülemek.</span><span class="sxs-lookup"><span data-stu-id="747a3-128">The sample activities in this topic such as `ReserveFlight` display their name and purpose to the console to help illustrate the order in which the activities are executed when compensation occurs.</span></span>  
  
### <a name="default-workflow-compensation"></a><span data-ttu-id="747a3-129">Varsayılan iş akışı Dengeleme</span><span class="sxs-lookup"><span data-stu-id="747a3-129">Default Workflow Compensation</span></span>  
 <span data-ttu-id="747a3-130">Varsayılan olarak, iş akışı iptal ederseniz, maaş mantığı başarıyla tamamen sahip compensable aktivite için çalıştırılır ve henüz onaylanıp veya bırakıldığı dengelendi.</span><span class="sxs-lookup"><span data-stu-id="747a3-130">By default, if the workflow is canceled, the compensation logic is run for any compensable activity that has successfully completely and has not already been confirmed or compensated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="747a3-131">Zaman bir <xref:System.Activities.Statements.CompensableActivity> olan *onaylanıp*, maaş etkinliği artık çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="747a3-131">When a <xref:System.Activities.Statements.CompensableActivity> is *confirmed*, compensation for the activity can no longer be invoked.</span></span> <span data-ttu-id="747a3-132">Onay işlemi daha sonra bu bölümde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="747a3-132">The confirmation process is described later in this section.</span></span>  
  
 <span data-ttu-id="747a3-133">Bu örnekte, uçuş ayrılmıştır sonra ancak Yöneticisi Onayı adım önce bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="747a3-133">In this example, an exception is thrown after the flight is reserved but before the manager approval step.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#2](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#2)]  
  
 <span data-ttu-id="747a3-134">Bu örnek XAML'de iş akışıdır.</span><span class="sxs-lookup"><span data-stu-id="747a3-134">This example is the workflow in XAML.</span></span>  
  
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
  
 <span data-ttu-id="747a3-135">İş akışı çağrıldığında, benzetimli hata koşulu özel konak uygulama tarafından işlenir <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, iş akışı iptal edilir ve maaş mantığı çağrılır.</span><span class="sxs-lookup"><span data-stu-id="747a3-135">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the compensation logic is invoked.</span></span>  
  
 <span data-ttu-id="747a3-136">**ReserveFlight: Bilet ayrılmıştır.**</span><span class="sxs-lookup"><span data-stu-id="747a3-136">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="747a3-137">**SimulatedErrorCondition: bir ApplicationException üretiliyor.** </span><span class="sxs-lookup"><span data-stu-id="747a3-137">**SimulatedErrorCondition: Throwing an ApplicationException.** </span></span>  
<span data-ttu-id="747a3-138">**İş akışı işlenmemiş özel durum oluştu:** </span><span class="sxs-lookup"><span data-stu-id="747a3-138">**Workflow Unhandled Exception:** </span></span>  
<span data-ttu-id="747a3-139">**System.ApplicationException: İş akışı benzetimli hata koşulu.** </span><span class="sxs-lookup"><span data-stu-id="747a3-139">**System.ApplicationException: Simulated error condition in the workflow.** </span></span>  
<span data-ttu-id="747a3-140">**CancelFlight: Bilet iptal edilir.** </span><span class="sxs-lookup"><span data-stu-id="747a3-140">**CancelFlight: Ticket is canceled.** </span></span>  
<span data-ttu-id="747a3-141">**İş akışı durumu ile başarıyla tamamlandı: iptal edildi.**</span><span class="sxs-lookup"><span data-stu-id="747a3-141">**Workflow completed successfully with status: Canceled.**</span></span>    
### <a name="cancellation-and-compensableactivity"></a><span data-ttu-id="747a3-142">İptal etme ve CompensableActivity</span><span class="sxs-lookup"><span data-stu-id="747a3-142">Cancellation and CompensableActivity</span></span>  
 <span data-ttu-id="747a3-143">Varsa etkinlikler <xref:System.Activities.Statements.CompensableActivity.Body%2A> , bir <xref:System.Activities.Statements.CompensableActivity> sahip tamamlanmadı ve etkinlik iptal edilen etkinlikler <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> yürütülür.</span><span class="sxs-lookup"><span data-stu-id="747a3-143">If the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled, the activities in the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> are executed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="747a3-144"><xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> Yalnızca oluşursa çağrılır etkinlikler <xref:System.Activities.Statements.CompensableActivity.Body%2A> , <xref:System.Activities.Statements.CompensableActivity> tamamlanmamış ve etkinliği iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="747a3-144">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is only invoked if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled.</span></span> <span data-ttu-id="747a3-145"><xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> Varsa yalnızca yürütülebilir etkinlikler <xref:System.Activities.Statements.CompensableActivity.Body%2A> , <xref:System.Activities.Statements.CompensableActivity> başarıyla tamamlandı ve maaş faaliyete daha sonra çağrılır.</span><span class="sxs-lookup"><span data-stu-id="747a3-145">The <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> is only executed if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have successfully completed and compensation is subsequently invoked on the activity.</span></span>  
  
 <span data-ttu-id="747a3-146"><xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> İş akışı yazarları herhangi uygun iptal mantığın olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="747a3-146">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> gives workflow authors the opportunity to provide any appropriate cancellation logic.</span></span> <span data-ttu-id="747a3-147">Aşağıdaki örnekte, yürütülmesi sırasında bir özel durum <xref:System.Activities.Statements.CompensableActivity.Body%2A>ve ardından <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> çağrılır.</span><span class="sxs-lookup"><span data-stu-id="747a3-147">In the following example, an exception is thrown during the execution of the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, and then the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is invoked.</span></span>  
  
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
  
 <span data-ttu-id="747a3-148">Bu örnekte iş akışı XAML içinde</span><span class="sxs-lookup"><span data-stu-id="747a3-148">This example is the workflow in XAML</span></span>  
  
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
  
 <span data-ttu-id="747a3-149">İş akışı çağrıldığında, benzetimli hata koşulu özel konak uygulama tarafından işlenir <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, iş akışı iptal ve iptal mantığını <xref:System.Activities.Statements.CompensableActivity> çağrılır.</span><span class="sxs-lookup"><span data-stu-id="747a3-149">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the cancellation logic of the <xref:System.Activities.Statements.CompensableActivity> is invoked.</span></span> <span data-ttu-id="747a3-150">Bu örnekte, farklı hedefleri maaş mantığı ve iptal mantığı vardır.</span><span class="sxs-lookup"><span data-stu-id="747a3-150">In this example, the compensation logic and the cancellation logic have different goals.</span></span> <span data-ttu-id="747a3-151">Varsa <xref:System.Activities.Statements.CompensableActivity.Body%2A> maaş her iki adımın geri almak için kredi kartı ücret uçuş ayrıldı, yani ve sonra başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="747a3-151">If the <xref:System.Activities.Statements.CompensableActivity.Body%2A> completed successfully, then this means the credit card was charged and the flight booked, so the compensation should undo both steps.</span></span> <span data-ttu-id="747a3-152">(Bu örnekte, uçuş otomatik olarak iptal etme kredi kartı ücretleri iptal eder.) Ancak, varsa <xref:System.Activities.Statements.CompensableActivity> iptal edildi, yani <xref:System.Activities.Statements.CompensableActivity.Body%2A> vermedi değil tam ve bunu mantığını <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> nasıl en iyi iptal işleneceğini belirlemek mümkün olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="747a3-152">(In this example, canceling the flight automatically cancels the credit card charges.) However, if the <xref:System.Activities.Statements.CompensableActivity> is canceled, this means the <xref:System.Activities.Statements.CompensableActivity.Body%2A> did not complete and so the logic of the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> needs to be able to determine how to best handle the cancellation.</span></span> <span data-ttu-id="747a3-153">Bu örnekte, <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> kredi kartı ücret ancak iptal `ReserveFlight` son etkinliğin edildi <xref:System.Activities.Statements.CompensableActivity.Body%2A>, uçuş iptal etmek çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="747a3-153">In this example, the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> cancels the credit card charge, but since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, it does not attempt to cancel the flight.</span></span> <span data-ttu-id="747a3-154">Bu yana `ReserveFlight` son etkinliğin edildi <xref:System.Activities.Statements.CompensableActivity.Body%2A>, başarıyla tamamlandıktan sonra <xref:System.Activities.Statements.CompensableActivity.Body%2A> tamamlamış ve hiçbir iptal mümkün olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="747a3-154">Since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, if it had successfully completed then the <xref:System.Activities.Statements.CompensableActivity.Body%2A> would have completed and no cancellation would be possible.</span></span>  
  
 <span data-ttu-id="747a3-155">**ChargeCreditCard: Ücret kredi kartı uçuş için.**</span><span class="sxs-lookup"><span data-stu-id="747a3-155">**ChargeCreditCard: Charge credit card for flight.**</span></span>  
<span data-ttu-id="747a3-156">**SimulatedErrorCondition: bir ApplicationException üretiliyor.** </span><span class="sxs-lookup"><span data-stu-id="747a3-156">**SimulatedErrorCondition: Throwing an ApplicationException.** </span></span>  
<span data-ttu-id="747a3-157">**İş akışı işlenmemiş özel durum oluştu:** </span><span class="sxs-lookup"><span data-stu-id="747a3-157">**Workflow Unhandled Exception:** </span></span>  
<span data-ttu-id="747a3-158">**System.ApplicationException: İş akışı benzetimli hata koşulu.** </span><span class="sxs-lookup"><span data-stu-id="747a3-158">**System.ApplicationException: Simulated error condition in the workflow.** </span></span>  
<span data-ttu-id="747a3-159">**CancelCreditCard: kredi kartı ücretleri iptal edin.** </span><span class="sxs-lookup"><span data-stu-id="747a3-159">**CancelCreditCard: Cancel credit card charges.** </span></span>  
<span data-ttu-id="747a3-160">**İş akışı durumu ile başarıyla tamamlandı: iptal edildi.**</span><span class="sxs-lookup"><span data-stu-id="747a3-160">**Workflow completed successfully with status: Canceled.**</span></span>  <span data-ttu-id="747a3-161">İptal etme hakkında daha fazla bilgi için bkz: [iptal](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md).</span><span class="sxs-lookup"><span data-stu-id="747a3-161">For more information about cancellation, see [Cancellation](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md).</span></span>  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a><span data-ttu-id="747a3-162">Açık maaş kullanarak etkinlik dengelemek</span><span class="sxs-lookup"><span data-stu-id="747a3-162">Explicit Compensation Using the Compensate Activity</span></span>  
 <span data-ttu-id="747a3-163">Önceki bölümde örtük maaş ele.</span><span class="sxs-lookup"><span data-stu-id="747a3-163">In the previous section, implicit compensation was covered.</span></span> <span data-ttu-id="747a3-164">Örtük maaş sonra işleme maaş zamanlama üzerinden daha açık denetim gerekli olup olmadığını ancak basit senaryolar için uygun olabilir <xref:System.Activities.Statements.Compensate> etkinlik kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="747a3-164">Implicit compensation can be appropriate for simple scenarios, but if more explicit control is required over the scheduling of compensation handling then the <xref:System.Activities.Statements.Compensate> activity can be used.</span></span> <span data-ttu-id="747a3-165">İle maaş işlemini başlatmak için <xref:System.Activities.Statements.Compensate> etkinliği <xref:System.Activities.Statements.CompensationToken> , <xref:System.Activities.Statements.CompensableActivity> hangi maaş istenen kullanılır.</span><span class="sxs-lookup"><span data-stu-id="747a3-165">To initiate the compensation process with the <xref:System.Activities.Statements.Compensate> activity, the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> for which compensation is desired is used.</span></span> <span data-ttu-id="747a3-166"><xref:System.Activities.Statements.Compensate> Etkinlik, herhangi bir tamamlandı maaş başlatmak için kullanılabilir <xref:System.Activities.Statements.CompensableActivity> , doğrulanmamış veya dengelendi.</span><span class="sxs-lookup"><span data-stu-id="747a3-166">The <xref:System.Activities.Statements.Compensate> activity can be used to initiate compensation on any completed <xref:System.Activities.Statements.CompensableActivity> that has not been confirmed or compensated.</span></span> <span data-ttu-id="747a3-167">Örneğin, bir <xref:System.Activities.Statements.Compensate> etkinlik kullanılabilirdi <xref:System.Activities.Statements.TryCatch.Catches%2A> bölümünü bir <xref:System.Activities.Statements.TryCatch> etkinlik ya da sonra her zaman <xref:System.Activities.Statements.CompensableActivity> tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="747a3-167">For example, a <xref:System.Activities.Statements.Compensate> activity could be used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity, or any time after the <xref:System.Activities.Statements.CompensableActivity> has completed.</span></span> <span data-ttu-id="747a3-168">Bu örnekte, <xref:System.Activities.Statements.Compensate> etkinlik kullanılıyor <xref:System.Activities.Statements.TryCatch.Catches%2A> bölümünü bir <xref:System.Activities.Statements.TryCatch> eylemini tersine çevirmek için etkinlik <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="747a3-168">In this example, the <xref:System.Activities.Statements.Compensate> activity is used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity to reverse the action of the <xref:System.Activities.Statements.CompensableActivity>.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#3](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#3)]  
  
 <span data-ttu-id="747a3-169">Bu örnek XAML'de iş akışıdır.</span><span class="sxs-lookup"><span data-stu-id="747a3-169">This example is the workflow in XAML.</span></span>  
  
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
  
 <span data-ttu-id="747a3-170">İş akışı çağrıldığında, aşağıdaki çıktıyı konsola görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="747a3-170">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="747a3-171">**ReserveFlight: Bilet ayrılmıştır.**</span><span class="sxs-lookup"><span data-stu-id="747a3-171">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="747a3-172">**SimulatedErrorCondition: bir ApplicationException üretiliyor.** </span><span class="sxs-lookup"><span data-stu-id="747a3-172">**SimulatedErrorCondition: Throwing an ApplicationException.** </span></span>  
<span data-ttu-id="747a3-173">**CancelFlight: Bilet iptal edilir.** </span><span class="sxs-lookup"><span data-stu-id="747a3-173">**CancelFlight: Ticket is canceled.** </span></span>  
<span data-ttu-id="747a3-174">**İş akışı durumu ile başarıyla tamamlandı: kapalı.**</span><span class="sxs-lookup"><span data-stu-id="747a3-174">**Workflow completed successfully with status: Closed.**</span></span>    
### <a name="confirming-compensation"></a><span data-ttu-id="747a3-175">Maaş onaylama</span><span class="sxs-lookup"><span data-stu-id="747a3-175">Confirming Compensation</span></span>  
 <span data-ttu-id="747a3-176">Varsayılan olarak, bunlar tamamladıktan sonra istediğiniz zaman compensable etkinlikleri dengelenebilmesi.</span><span class="sxs-lookup"><span data-stu-id="747a3-176">By default, compensable activities can be compensated any time after they have completed.</span></span> <span data-ttu-id="747a3-177">Bazı senaryolarda bu uygun olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="747a3-177">In some scenarios this may not be appropriate.</span></span> <span data-ttu-id="747a3-178">Önceki örnekte ayırması iptal etmek için bilet ayırma için maaş idi.</span><span class="sxs-lookup"><span data-stu-id="747a3-178">In the previous example the compensation to reserving the ticket was to cancel the reservation.</span></span> <span data-ttu-id="747a3-179">Uçuş tamamlandıktan sonra ancak, bu maaş adımı artık geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="747a3-179">However, after the flight has been completed this compensation step is no longer valid.</span></span> <span data-ttu-id="747a3-180">Çağıran tarafından belirtilen etkinlik compensable etkinlik onaylayan <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="747a3-180">Confirming the compensable activity invokes the activity specified by the <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>.</span></span> <span data-ttu-id="747a3-181">Bu olası kullanım yayımlanacak maaş gerçekleştirmek için gerekli olan herhangi bir kaynağa izin vermektir.</span><span class="sxs-lookup"><span data-stu-id="747a3-181">One possible use for this is to allow any resources that are necessary to perform the compensation to be released.</span></span> <span data-ttu-id="747a3-182">Compensable etkinlik dengelenebilmesi için mümkün değildir onaylandıktan sonra ve bu denenmesi durumunda bir <xref:System.InvalidOperationException> özel durumu oluşur.</span><span class="sxs-lookup"><span data-stu-id="747a3-182">After a compensable activity is confirmed it is not possible for it to be compensated, and if this is attempted an <xref:System.InvalidOperationException> exception is thrown.</span></span> <span data-ttu-id="747a3-183">Bir iş akışı başarıyla tamamlandığında, başarıyla tamamlanan tüm onaylanmamış ve dengelendi olmayan compensable etkinlikleri ters sırada tamamlanmasından onaylanır.</span><span class="sxs-lookup"><span data-stu-id="747a3-183">When a workflow completes successfully, all non-confirmed and non-compensated compensable activities that completed successfully are confirmed in reverse order of completion.</span></span> <span data-ttu-id="747a3-184">Bu örnekte, uçuş ayrılmıştır, satın alınan tamamlandı ve ve ardından compensable etkinlik onaylanıp.</span><span class="sxs-lookup"><span data-stu-id="747a3-184">In this example the flight is reserved, purchased, and completed, and then the compensable activity is confirmed.</span></span> <span data-ttu-id="747a3-185">Onaylamak için bir <xref:System.Activities.Statements.CompensableActivity>, kullanın <xref:System.Activities.Statements.Confirm> etkinliği ve belirtin <xref:System.Activities.Statements.CompensationToken> , <xref:System.Activities.Statements.CompensableActivity> onaylamak için.</span><span class="sxs-lookup"><span data-stu-id="747a3-185">To confirm a <xref:System.Activities.Statements.CompensableActivity>, use the <xref:System.Activities.Statements.Confirm> activity and specify the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> to confirm.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#4](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#4)]  
  
 <span data-ttu-id="747a3-186">Bu örnek XAML'de iş akışıdır.</span><span class="sxs-lookup"><span data-stu-id="747a3-186">This example is the workflow in XAML.</span></span>  
  
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
  
 <span data-ttu-id="747a3-187">İş akışı çağrıldığında, aşağıdaki çıktıyı konsola görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="747a3-187">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="747a3-188">**ReserveFlight: Bilet ayrılmıştır.**</span><span class="sxs-lookup"><span data-stu-id="747a3-188">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="747a3-189">**ManagerApproval: alınan yönetici onayı gerekir.** </span><span class="sxs-lookup"><span data-stu-id="747a3-189">**ManagerApproval: Manager approval received.** </span></span>  
<span data-ttu-id="747a3-190">**PurchaseFlight: Bilet satın alınır.** </span><span class="sxs-lookup"><span data-stu-id="747a3-190">**PurchaseFlight: Ticket is purchased.** </span></span>  
<span data-ttu-id="747a3-191">**TakeFlight: Uçuş tamamlandı.** </span><span class="sxs-lookup"><span data-stu-id="747a3-191">**TakeFlight: Flight is completed.** </span></span>  
<span data-ttu-id="747a3-192">**ConfirmFlight: Uçuş alınmış, hiçbir maaş mümkün.** </span><span class="sxs-lookup"><span data-stu-id="747a3-192">**ConfirmFlight: Flight has been taken, no compensation possible.** </span></span>  
<span data-ttu-id="747a3-193">**İş akışı durumu ile başarıyla tamamlandı: kapalı.**</span><span class="sxs-lookup"><span data-stu-id="747a3-193">**Workflow completed successfully with status: Closed.**</span></span>   
## <a name="nesting-compensation-activities"></a><span data-ttu-id="747a3-194">İç içe geçme maaş etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="747a3-194">Nesting Compensation Activities</span></span>  
 <span data-ttu-id="747a3-195">A <xref:System.Activities.Statements.CompensableActivity> içine yerleştirilebilir <xref:System.Activities.Statements.CompensableActivity.Body%2A> başka bir bölüm <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="747a3-195">A <xref:System.Activities.Statements.CompensableActivity> can be placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> section of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="747a3-196">A <xref:System.Activities.Statements.CompensableActivity> başka bir işleyici yerleştirilebilir <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="747a3-196">A <xref:System.Activities.Statements.CompensableActivity> may not be placed into a handler of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="747a3-197">Bir üst sorumluluğundadır <xref:System.Activities.Statements.CompensableActivity> onu, onaylanan, dengelendi ya da iptal edildiğinde, başarılı bir şekilde tamamladınız ve henüz onaylanıp veya silinmiş dengelendi tüm alt compensable etkinlikleri onaylanmalıdır emin olmak için veya üst iptal, onay ya da maaş tamamlanmadan önce dengelendi.</span><span class="sxs-lookup"><span data-stu-id="747a3-197">It is the responsibility of a parent <xref:System.Activities.Statements.CompensableActivity> to ensure that when it is canceled, confirmed, or compensated, all child compensable activities that have completed successfully and have not already been confirmed or compensated must be confirmed or compensated before the parent completes cancellation, confirmation, or compensation.</span></span> <span data-ttu-id="747a3-198">Bu açıkça modellenir değil, üst <xref:System.Activities.Statements.CompensableActivity> örtük olarak iptal üst aldıysanız, alt compensable etkinlikler dengelemek veya sinyal dengelemek.</span><span class="sxs-lookup"><span data-stu-id="747a3-198">If this is not modeled explicitly the parent <xref:System.Activities.Statements.CompensableActivity> will implicitly compensate child compensable activities if the parent received the cancel or compensate signal.</span></span> <span data-ttu-id="747a3-199">Üst Onayla sinyal aldıysanız üst örtük olarak alt compensable etkinlikler onaylayın.</span><span class="sxs-lookup"><span data-stu-id="747a3-199">If the parent received the confirm signal the parent will implicitly confirm child compensable activities.</span></span> <span data-ttu-id="747a3-200">İptal, onay ya da Maaş işleme mantığı açıkça üst işleyicisinde modellenir varsa <xref:System.Activities.Statements.CompensableActivity>, açıkça işlenen tüm alt örtük olarak onaylandı.</span><span class="sxs-lookup"><span data-stu-id="747a3-200">If the logic to handle cancellation, confirmation, or compensation is explicitly modeled in the handler of the parent <xref:System.Activities.Statements.CompensableActivity>, any child not explicitly handled will be implicitly confirmed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="747a3-201">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="747a3-201">See Also</span></span>  
 <xref:System.Activities.Statements.CompensableActivity>  
 <xref:System.Activities.Statements.Compensate>  
 <xref:System.Activities.Statements.Confirm>  
 <xref:System.Activities.Statements.CompensationToken>  
 [<span data-ttu-id="747a3-202">Compensable Etkinliği</span><span class="sxs-lookup"><span data-stu-id="747a3-202">Compensable Activity</span></span>](../../../docs/framework/windows-workflow-foundation/samples/compensable-activity-sample.md)
