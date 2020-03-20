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
# <a name="compensation"></a><span data-ttu-id="95999-102">Dengeleme</span><span class="sxs-lookup"><span data-stu-id="95999-102">Compensation</span></span>
<span data-ttu-id="95999-103">Windows İş Akışı Temeli'ndeki (WF) tazminat, daha önce tamamlanmış çalışmanın sonraki bir hata oluştuğunda geri alınabileceği veya telafi edilebildiği (uygulama tarafından tanımlanan mantığı izleyerek) bir mekanizmadır.</span><span class="sxs-lookup"><span data-stu-id="95999-103">Compensation in Windows Workflow Foundation (WF) is the mechanism by which previously completed work can be undone or compensated (following the logic defined by the application) when a subsequent failure occurs.</span></span> <span data-ttu-id="95999-104">Bu bölümde, iş akışlarında tazminatın nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="95999-104">This section describes how to use compensation in workflows.</span></span>  
  
## <a name="compensation-vs-transactions"></a><span data-ttu-id="95999-105">Tazminat ve İşlemler</span><span class="sxs-lookup"><span data-stu-id="95999-105">Compensation vs. Transactions</span></span>  
 <span data-ttu-id="95999-106">Bir işlem, birden çok işlemi tek bir çalışma biriminde birleştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="95999-106">A transaction allows you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="95999-107">Bir işlemi kullanmak, işlem işleminin herhangi bir bölümünde herhangi bir hata oluşursa, uygulamanız içinden yürütülen tüm değişiklikleri iptal etme (geri alma) olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="95999-107">Using a transaction gives your application the ability to abort (roll back) all changes executed from within the transaction if any errors occur during any part of the transaction process.</span></span> <span data-ttu-id="95999-108">Ancak, çalışma uzun sürüyorsa hareketleri kullanmak uygun olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="95999-108">However, using transactions may not be appropriate if the work is long running.</span></span> <span data-ttu-id="95999-109">Örneğin, bir seyahat planlama uygulaması iş akışı olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="95999-109">For example, a travel planning application is implemented as a workflow.</span></span> <span data-ttu-id="95999-110">İş akışının adımları, bir uçuş rezervasyonu, yönetici onayı beklemek ve uçuş için ödeme yapmak olabilir.</span><span class="sxs-lookup"><span data-stu-id="95999-110">The steps of the workflow may consist of booking a flight, waiting for manager approval, and then paying for the flight.</span></span> <span data-ttu-id="95999-111">Bu işlem günler sürebilir ve aynı işleme katılmak için uçuş için rezervasyon ve ödeme adımları için pratik değildir.</span><span class="sxs-lookup"><span data-stu-id="95999-111">This process could take many days and it is not practical for the steps of booking and paying for the flight to participate in the same transaction.</span></span> <span data-ttu-id="95999-112">Böyle bir senaryoda, daha sonra işlemde bir hata olması durumunda, tazminat iş akışının rezervasyon adımını geri almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="95999-112">In a scenario such as this, compensation could be used to undo the booking step of the workflow if there is a failure later in the processing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="95999-113">Bu konu, iş akışlarındaki tazminatı kapsar.</span><span class="sxs-lookup"><span data-stu-id="95999-113">This topic covers compensation in workflows.</span></span> <span data-ttu-id="95999-114">İş akışlarındaki hareketler hakkında daha [Transactions](workflow-transactions.md) fazla <xref:System.Activities.Statements.TransactionScope>bilgi için Hareketler ve .</span><span class="sxs-lookup"><span data-stu-id="95999-114">For more information about transactions in workflows, see [Transactions](workflow-transactions.md) and <xref:System.Activities.Statements.TransactionScope>.</span></span> <span data-ttu-id="95999-115">İşlemler hakkında daha <xref:System.Transactions?displayProperty=nameWithType> fazla <xref:System.Transactions.Transaction?displayProperty=nameWithType>bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="95999-115">For more information about transactions, see <xref:System.Transactions?displayProperty=nameWithType> and <xref:System.Transactions.Transaction?displayProperty=nameWithType>.</span></span>  
  
## <a name="using-compensableactivity"></a><span data-ttu-id="95999-116">Telafi Edilebilir Aktivite kullanma</span><span class="sxs-lookup"><span data-stu-id="95999-116">Using CompensableActivity</span></span>  
 <span data-ttu-id="95999-117"><xref:System.Activities.Statements.CompensableActivity>'deki temel tazminat [!INCLUDE[wf1](../../../includes/wf1-md.md)]faaliyetidir.</span><span class="sxs-lookup"><span data-stu-id="95999-117"><xref:System.Activities.Statements.CompensableActivity> is the core compensation activity in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="95999-118">Telafi <xref:System.Activities.Statements.CompensableActivity.Body%2A> edilmesi gereken işleri gerçekleştiren faaliyetler bir <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="95999-118">Any activities that perform work that may need to be compensated are placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="95999-119">Bu örnekte, bir uçuş satın alma rezervasyon <xref:System.Activities.Statements.CompensableActivity.Body%2A> adımı <xref:System.Activities.Statements.CompensableActivity> a yerleştirilir ve rezervasyon iptali <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="95999-119">In this example, the reservation step of purchasing a flight is placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> and the cancellation of the reservation is placed into the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>.</span></span> <span data-ttu-id="95999-120">Hemen iş <xref:System.Activities.Statements.CompensableActivity> akışı nda takip yönetici onayı bekleyin ve daha sonra uçuş satın alma adımı tamamlamak iki faaliyetvardır.</span><span class="sxs-lookup"><span data-stu-id="95999-120">Immediately following the <xref:System.Activities.Statements.CompensableActivity> in the workflow are two activities that wait for manager approval and then complete the purchasing step of the flight.</span></span> <span data-ttu-id="95999-121">Bir hata koşulu, iş akışının başarıyla <xref:System.Activities.Statements.CompensableActivity> tamamlandıktan sonra iptal edilmesine <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> neden oluyorsa, işleyicideki etkinlikler zamanlanır ve uçuş iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="95999-121">If an error condition causes the workflow to be canceled after the <xref:System.Activities.Statements.CompensableActivity> has successfully completed, then the activities in the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> handler are scheduled and the flight is canceled.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#1)]  
  
 <span data-ttu-id="95999-122">Aşağıdaki örnek XAML'deki iş akışıdır.</span><span class="sxs-lookup"><span data-stu-id="95999-122">The following example is the workflow in XAML.</span></span>  
  
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
  
 <span data-ttu-id="95999-123">İş akışı çağrıldığında, aşağıdaki çıktı konsola görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="95999-123">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="95999-124">**Rezerv Uçuş: Bilet rezerve edilir.**</span><span class="sxs-lookup"><span data-stu-id="95999-124">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="95999-125">**ManagerApproval: Yönetici onayı alındı.** 
 **Satın Alma Uçuşu: Bilet satın alınır.** 
 **Durumla birlikte başarıyla tamamlanan iş akışı: Kapalı.**</span><span class="sxs-lookup"><span data-stu-id="95999-125">**ManagerApproval: Manager approval received.**
**PurchaseFlight: Ticket is purchased.**
**Workflow completed successfully with status: Closed.**</span></span>
> [!NOTE]
> <span data-ttu-id="95999-126">Bu konudaki örnek etkinlikler, telafi gerçekleştiğinde etkinliklerin yürütülme sırasını göstermeye yardımcı olmak için adlarını ve amaçlarını konsola görüntülemek gibi. `ReserveFlight`</span><span class="sxs-lookup"><span data-stu-id="95999-126">The sample activities in this topic such as `ReserveFlight` display their name and purpose to the console to help illustrate the order in which the activities are executed when compensation occurs.</span></span>  
  
### <a name="default-workflow-compensation"></a><span data-ttu-id="95999-127">Varsayılan İş Akışı Tazminatı</span><span class="sxs-lookup"><span data-stu-id="95999-127">Default Workflow Compensation</span></span>  
 <span data-ttu-id="95999-128">Varsayılan olarak, iş akışı iptal edilirse, telafi mantığı başarıyla tamamen tamamlanmamış veya telafi edilmemiş herhangi bir telafi edilebilir etkinlik için çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="95999-128">By default, if the workflow is canceled, the compensation logic is run for any compensable activity that has successfully completely and has not already been confirmed or compensated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="95999-129">Bir <xref:System.Activities.Statements.CompensableActivity> *onaylandığında,* etkinlik için tazminat artık çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="95999-129">When a <xref:System.Activities.Statements.CompensableActivity> is *confirmed*, compensation for the activity can no longer be invoked.</span></span> <span data-ttu-id="95999-130">Onay süreci daha sonra bu bölümde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="95999-130">The confirmation process is described later in this section.</span></span>  
  
 <span data-ttu-id="95999-131">Bu örnekte, uçuş rezerve edildikten sonra ancak yönetici onay adımından önce bir özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="95999-131">In this example, an exception is thrown after the flight is reserved but before the manager approval step.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#2)]  
  
 <span data-ttu-id="95999-132">Bu örnek, XAML'deki iş akışıdır.</span><span class="sxs-lookup"><span data-stu-id="95999-132">This example is the workflow in XAML.</span></span>  
  
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
  
 <span data-ttu-id="95999-133">İş akışı çağrıldığı zaman, benzetilen hata durumu özel durumu <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>ana bilgisayar uygulaması tarafından işlenir, iş akışı iptal edilir ve telafi mantığı çağrılır.</span><span class="sxs-lookup"><span data-stu-id="95999-133">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the compensation logic is invoked.</span></span>  
  
 <span data-ttu-id="95999-134">**Rezerv Uçuş: Bilet rezerve edilir.**</span><span class="sxs-lookup"><span data-stu-id="95999-134">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="95999-135">**SimüleHata Durumu: ApplicationException atma.** 
 **İş Akışı İşlenmemiş Özel Durum:**
**System.ApplicationException: İş akışındaki benzetimli hata durumu.** 
 **İptal: Bilet iptal edilir.** 
 **Durumla birlikte başarıyla tamamlanan iş akışı: İptal edildi.**</span><span class="sxs-lookup"><span data-stu-id="95999-135">**SimulatedErrorCondition: Throwing an ApplicationException.**
**Workflow Unhandled Exception:**
**System.ApplicationException: Simulated error condition in the workflow.**
**CancelFlight: Ticket is canceled.**
**Workflow completed successfully with status: Canceled.**</span></span>
### <a name="cancellation-and-compensableactivity"></a><span data-ttu-id="95999-136">İptal ve Telafi Etkinliği</span><span class="sxs-lookup"><span data-stu-id="95999-136">Cancellation and CompensableActivity</span></span>  
 <span data-ttu-id="95999-137">A'daki <xref:System.Activities.Statements.CompensableActivity.Body%2A> faaliyetler <xref:System.Activities.Statements.CompensableActivity> tamamlanmamış sayılsa ve etkinlik iptal <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> edilirse, etkinlikteki faaliyetler yürütülür.</span><span class="sxs-lookup"><span data-stu-id="95999-137">If the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled, the activities in the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> are executed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="95999-138">Yalnızca, <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> etkinlikler <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> tamamlanmamışsa ve etkinlik iptal edilirse çağrılır.</span><span class="sxs-lookup"><span data-stu-id="95999-138">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is only invoked if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled.</span></span> <span data-ttu-id="95999-139">Yalnızca, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> etkinlikler başarıyla <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> tamamlanırsa ve daha sonra etkinlik üzerinde tazminat çağrılmışsa yürütülür.</span><span class="sxs-lookup"><span data-stu-id="95999-139">The <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> is only executed if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have successfully completed and compensation is subsequently invoked on the activity.</span></span>  
  
 <span data-ttu-id="95999-140">İş <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> akışı yazarlarına uygun iptal mantığını sağlama fırsatı verir.</span><span class="sxs-lookup"><span data-stu-id="95999-140">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> gives workflow authors the opportunity to provide any appropriate cancellation logic.</span></span> <span data-ttu-id="95999-141">Aşağıdaki örnekte, bir özel durum yürütme <xref:System.Activities.Statements.CompensableActivity.Body%2A>sırasında atılır <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> ve sonra çağrılır.</span><span class="sxs-lookup"><span data-stu-id="95999-141">In the following example, an exception is thrown during the execution of the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, and then the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is invoked.</span></span>  
  
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
  
 <span data-ttu-id="95999-142">Bu örnek, XAML'deki iş akışıdır</span><span class="sxs-lookup"><span data-stu-id="95999-142">This example is the workflow in XAML</span></span>  
  
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
  
 <span data-ttu-id="95999-143">İş akışı çağrıldığı zaman, benzetilen hata durumu özel durumu <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>ana bilgisayar uygulaması tarafından işlenir, iş <xref:System.Activities.Statements.CompensableActivity> akışı iptal edilir ve iptal mantığı çağrılır.</span><span class="sxs-lookup"><span data-stu-id="95999-143">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the cancellation logic of the <xref:System.Activities.Statements.CompensableActivity> is invoked.</span></span> <span data-ttu-id="95999-144">Bu örnekte, telafi mantığı ve iptal mantığı farklı hedefleri vardır.</span><span class="sxs-lookup"><span data-stu-id="95999-144">In this example, the compensation logic and the cancellation logic have different goals.</span></span> <span data-ttu-id="95999-145">Başarıyla <xref:System.Activities.Statements.CompensableActivity.Body%2A> tamamlanırsa, bu kredi kartının tahsil edildiği ve uçuş rezervasyonu nun yapılandığı anlamına gelir, bu yüzden tazminat her iki adımı da geri alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="95999-145">If the <xref:System.Activities.Statements.CompensableActivity.Body%2A> completed successfully, then this means the credit card was charged and the flight booked, so the compensation should undo both steps.</span></span> <span data-ttu-id="95999-146">(Bu örnekte, uçuşu iptal etmek kredi kartı ücretlerini otomatik olarak iptal eder.) Ancak, iptal <xref:System.Activities.Statements.CompensableActivity> edilirse, bu <xref:System.Activities.Statements.CompensableActivity.Body%2A> tamamlanmadı ve bu nedenle <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> iptal en iyi nasıl işleyeceğini belirlemek için gereken mantığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="95999-146">(In this example, canceling the flight automatically cancels the credit card charges.) However, if the <xref:System.Activities.Statements.CompensableActivity> is canceled, this means the <xref:System.Activities.Statements.CompensableActivity.Body%2A> did not complete and so the logic of the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> needs to be able to determine how to best handle the cancellation.</span></span> <span data-ttu-id="95999-147">Bu örnekte, <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> kredi kartı ücretini iptal `ReserveFlight` eder, ancak son <xref:System.Activities.Statements.CompensableActivity.Body%2A>etkinlik olduğu için, uçuşu iptal etmeye çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="95999-147">In this example, the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> cancels the credit card charge, but since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, it does not attempt to cancel the flight.</span></span> <span data-ttu-id="95999-148">Bu `ReserveFlight` yana son faaliyet <xref:System.Activities.Statements.CompensableActivity.Body%2A>oldu , başarılı bir <xref:System.Activities.Statements.CompensableActivity.Body%2A> şekilde tamamlanmış olsaydı o zaman tamamlanmış olurdu ve hiçbir iptal mümkün olurdu.</span><span class="sxs-lookup"><span data-stu-id="95999-148">Since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, if it had successfully completed then the <xref:System.Activities.Statements.CompensableActivity.Body%2A> would have completed and no cancellation would be possible.</span></span>  
  
 <span data-ttu-id="95999-149">**ChargeCreditCard: Uçuş için kredi kartından ücret alın.**</span><span class="sxs-lookup"><span data-stu-id="95999-149">**ChargeCreditCard: Charge credit card for flight.**</span></span>  
<span data-ttu-id="95999-150">**SimüleHata Durumu: ApplicationException atma.** 
 **İş Akışı İşlenmemiş Özel Durum:**
**System.ApplicationException: İş akışındaki benzetimli hata durumu.** 
 **CancelCreditCard: Kredi kartı ücretlerini iptal edin.** 
 **Durumla birlikte başarıyla tamamlanan iş akışı: İptal edildi.**</span><span class="sxs-lookup"><span data-stu-id="95999-150">**SimulatedErrorCondition: Throwing an ApplicationException.**
**Workflow Unhandled Exception:**
**System.ApplicationException: Simulated error condition in the workflow.**
**CancelCreditCard: Cancel credit card charges.**
**Workflow completed successfully with status: Canceled.**</span></span>  <span data-ttu-id="95999-151">İptal hakkında daha fazla bilgi için [İptal'e](modeling-cancellation-behavior-in-workflows.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="95999-151">For more information about cancellation, see [Cancellation](modeling-cancellation-behavior-in-workflows.md).</span></span>  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a><span data-ttu-id="95999-152">Telafi Etkinliğini Kullanarak Açık Tazminat</span><span class="sxs-lookup"><span data-stu-id="95999-152">Explicit Compensation Using the Compensate Activity</span></span>  
 <span data-ttu-id="95999-153">Bir önceki bölümde örtülü tazminat ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="95999-153">In the previous section, implicit compensation was covered.</span></span> <span data-ttu-id="95999-154">Örtük telafi basit senaryolar için uygun olabilir, ancak tazminat işleme zamanlaması üzerinde <xref:System.Activities.Statements.Compensate> daha açık denetim gerekiyorsa, etkinlik kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="95999-154">Implicit compensation can be appropriate for simple scenarios, but if more explicit control is required over the scheduling of compensation handling then the <xref:System.Activities.Statements.Compensate> activity can be used.</span></span> <span data-ttu-id="95999-155"><xref:System.Activities.Statements.Compensate> Etkinlik le birlikte tazmin işlemini <xref:System.Activities.Statements.CompensationToken> başlatmak <xref:System.Activities.Statements.CompensableActivity> için, hangi tazminatın istendiği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="95999-155">To initiate the compensation process with the <xref:System.Activities.Statements.Compensate> activity, the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> for which compensation is desired is used.</span></span> <span data-ttu-id="95999-156">Etkinlik, <xref:System.Activities.Statements.Compensate> onaylanmamış veya tazmin edilmemiş <xref:System.Activities.Statements.CompensableActivity> herhangi bir tamamlanmış üzerinde tazminat başlatmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="95999-156">The <xref:System.Activities.Statements.Compensate> activity can be used to initiate compensation on any completed <xref:System.Activities.Statements.CompensableActivity> that has not been confirmed or compensated.</span></span> <span data-ttu-id="95999-157">Örneğin, bir <xref:System.Activities.Statements.Compensate> etkinlik bir etkinlik <xref:System.Activities.Statements.TryCatch.Catches%2A> bölümünde <xref:System.Activities.Statements.TryCatch> veya tamamlandıktan herhangi <xref:System.Activities.Statements.CompensableActivity> bir zamanda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="95999-157">For example, a <xref:System.Activities.Statements.Compensate> activity could be used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity, or any time after the <xref:System.Activities.Statements.CompensableActivity> has completed.</span></span> <span data-ttu-id="95999-158">Bu örnekte, <xref:System.Activities.Statements.Compensate> etkinlik bir <xref:System.Activities.Statements.TryCatch.Catches%2A> <xref:System.Activities.Statements.TryCatch> etkinliğin bölümünde eylemi tersine çevirmek <xref:System.Activities.Statements.CompensableActivity>için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="95999-158">In this example, the <xref:System.Activities.Statements.Compensate> activity is used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity to reverse the action of the <xref:System.Activities.Statements.CompensableActivity>.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#3)]  
  
 <span data-ttu-id="95999-159">Bu örnek, XAML'deki iş akışıdır.</span><span class="sxs-lookup"><span data-stu-id="95999-159">This example is the workflow in XAML.</span></span>  
  
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
  
 <span data-ttu-id="95999-160">İş akışı çağrıldığında, aşağıdaki çıktı konsola görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="95999-160">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="95999-161">**Rezerv Uçuş: Bilet rezerve edilir.**</span><span class="sxs-lookup"><span data-stu-id="95999-161">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="95999-162">**SimüleHata Durumu: ApplicationException atma.** 
 **İptal: Bilet iptal edilir.** 
 **Durumla birlikte başarıyla tamamlanan iş akışı: Kapalı.**</span><span class="sxs-lookup"><span data-stu-id="95999-162">**SimulatedErrorCondition: Throwing an ApplicationException.**
**CancelFlight: Ticket is canceled.**
**Workflow completed successfully with status: Closed.**</span></span>
### <a name="confirming-compensation"></a><span data-ttu-id="95999-163">Tazminatı Onaylama</span><span class="sxs-lookup"><span data-stu-id="95999-163">Confirming Compensation</span></span>  
 <span data-ttu-id="95999-164">Varsayılan olarak, telafi edilebilir faaliyetler tamamlandıktan sonra herhangi bir zamanda telafi edilebilir.</span><span class="sxs-lookup"><span data-stu-id="95999-164">By default, compensable activities can be compensated any time after they have completed.</span></span> <span data-ttu-id="95999-165">Bazı senaryolarda bu uygun olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="95999-165">In some scenarios this may not be appropriate.</span></span> <span data-ttu-id="95999-166">Önceki örnekte bilet rezervasyonu için tazminat rezervasyon iptal etmek oldu.</span><span class="sxs-lookup"><span data-stu-id="95999-166">In the previous example the compensation to reserving the ticket was to cancel the reservation.</span></span> <span data-ttu-id="95999-167">Ancak, uçuş tamamlandıktan sonra bu tazminat adımı artık geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="95999-167">However, after the flight has been completed this compensation step is no longer valid.</span></span> <span data-ttu-id="95999-168">Telafi edilebilir etkinliğin onaylanması, <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>'.</span><span class="sxs-lookup"><span data-stu-id="95999-168">Confirming the compensable activity invokes the activity specified by the <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>.</span></span> <span data-ttu-id="95999-169">Bunun olası bir kullanımı, tazminatı gerçekleştirmek için gerekli olan kaynakların serbest bırakılmasına izin vermektir.</span><span class="sxs-lookup"><span data-stu-id="95999-169">One possible use for this is to allow any resources that are necessary to perform the compensation to be released.</span></span> <span data-ttu-id="95999-170">Telafi edilebilir bir etkinlik onaylandıktan sonra telafi edilmesi mümkün değildir ve bu denenirse bir <xref:System.InvalidOperationException> istisna atılır.</span><span class="sxs-lookup"><span data-stu-id="95999-170">After a compensable activity is confirmed it is not possible for it to be compensated, and if this is attempted an <xref:System.InvalidOperationException> exception is thrown.</span></span> <span data-ttu-id="95999-171">Bir iş akışı başarıyla tamamlandığında, başarıyla tamamlanan tüm onaylanmamış ve telafi edilemeyen telafi edilebilir tüm faaliyetler ters tamamlama sırasına göre onaylanır.</span><span class="sxs-lookup"><span data-stu-id="95999-171">When a workflow completes successfully, all non-confirmed and non-compensated compensable activities that completed successfully are confirmed in reverse order of completion.</span></span> <span data-ttu-id="95999-172">Bu örnekte uçuş rezerve edilir, satın alınır ve tamamlanır ve telafi edilebilir etkinlik onaylanır.</span><span class="sxs-lookup"><span data-stu-id="95999-172">In this example the flight is reserved, purchased, and completed, and then the compensable activity is confirmed.</span></span> <span data-ttu-id="95999-173">Bir <xref:System.Activities.Statements.CompensableActivity>onaylamak için, <xref:System.Activities.Statements.Confirm> etkinliği kullanın <xref:System.Activities.Statements.CompensationToken> ve <xref:System.Activities.Statements.CompensableActivity> onaylamak için belirtin.</span><span class="sxs-lookup"><span data-stu-id="95999-173">To confirm a <xref:System.Activities.Statements.CompensableActivity>, use the <xref:System.Activities.Statements.Confirm> activity and specify the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> to confirm.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#4](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#4)]  
  
 <span data-ttu-id="95999-174">Bu örnek, XAML'deki iş akışıdır.</span><span class="sxs-lookup"><span data-stu-id="95999-174">This example is the workflow in XAML.</span></span>  
  
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
  
<span data-ttu-id="95999-175">İş akışı çağrıldığında, aşağıdaki çıktı konsola görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="95999-175">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
<span data-ttu-id="95999-176">**Rezerv Uçuş: Bilet rezerve edilir.**</span><span class="sxs-lookup"><span data-stu-id="95999-176">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="95999-177">**ManagerApproval: Yönetici onayı alındı.** 
 **Satın Alma Uçuşu: Bilet satın alınır.** 
 **TakeFlight: Uçuş tamamlandı.** 
 **ConfirmFlight: Uçuş alınmıştır, hiçbir tazminat mümkün.** 
 **Durumla birlikte başarıyla tamamlanan iş akışı: Kapalı.**</span><span class="sxs-lookup"><span data-stu-id="95999-177">**ManagerApproval: Manager approval received.**
**PurchaseFlight: Ticket is purchased.**
**TakeFlight: Flight is completed.**
**ConfirmFlight: Flight has been taken, no compensation possible.**
**Workflow completed successfully with status: Closed.**</span></span>

## <a name="nesting-compensation-activities"></a><span data-ttu-id="95999-178">İç Içe Tazminat Faaliyetleri</span><span class="sxs-lookup"><span data-stu-id="95999-178">Nesting Compensation Activities</span></span>  

<span data-ttu-id="95999-179">A <xref:System.Activities.Statements.CompensableActivity> başka bir <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity>bölüme yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="95999-179">A <xref:System.Activities.Statements.CompensableActivity> can be placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> section of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="95999-180">A, <xref:System.Activities.Statements.CompensableActivity> başka <xref:System.Activities.Statements.CompensableActivity>bir işleyiciye yerleştirilemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="95999-180">A <xref:System.Activities.Statements.CompensableActivity> may not be placed into a handler of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="95999-181"><xref:System.Activities.Statements.CompensableActivity> İptal edildiğinde, onaylandığunda veya tazmin edildiğinde, başarıyla tamamlanmış ve onaylanmamış veya telafi edilmemiş tüm çocuk telafi edici faaliyetlerin, ebeveyn iptal, onay veya tazminatı tamamlamadan önce onaylanması veya tazmin edilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="95999-181">It is the responsibility of a parent <xref:System.Activities.Statements.CompensableActivity> to ensure that when it is canceled, confirmed, or compensated, all child compensable activities that have completed successfully and have not already been confirmed or compensated must be confirmed or compensated before the parent completes cancellation, confirmation, or compensation.</span></span> <span data-ttu-id="95999-182">Bu açıkça modellenmemişse, <xref:System.Activities.Statements.CompensableActivity> ebeveyn iptal veya telafi sinyalini alırsa, ebeveyn alt takibe tabi olarak telafi eder.</span><span class="sxs-lookup"><span data-stu-id="95999-182">If this is not modeled explicitly the parent <xref:System.Activities.Statements.CompensableActivity> will implicitly compensate child compensable activities if the parent received the cancel or compensate signal.</span></span> <span data-ttu-id="95999-183">Ebeveyn onay sinyalini aldıysa, ebeveyn çocuğun telafi edilebilir etkinlikleri nizatla onaylayacaktır.</span><span class="sxs-lookup"><span data-stu-id="95999-183">If the parent received the confirm signal the parent will implicitly confirm child compensable activities.</span></span> <span data-ttu-id="95999-184">İptal, onay veya tazminatı işleme mantığı açıkça ebeveynin <xref:System.Activities.Statements.CompensableActivity>işleyicisinde modellenirse, açıkça ele alınmayan herhangi bir çocuk örtülü olarak onaylanır.</span><span class="sxs-lookup"><span data-stu-id="95999-184">If the logic to handle cancellation, confirmation, or compensation is explicitly modeled in the handler of the parent <xref:System.Activities.Statements.CompensableActivity>, any child not explicitly handled will be implicitly confirmed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95999-185">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95999-185">See also</span></span>

- <xref:System.Activities.Statements.CompensableActivity>
- <xref:System.Activities.Statements.Compensate>
- <xref:System.Activities.Statements.Confirm>
- <xref:System.Activities.Statements.CompensationToken>
