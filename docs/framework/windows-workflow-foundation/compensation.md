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
# <a name="compensation"></a><span data-ttu-id="53864-102">Dengeleme</span><span class="sxs-lookup"><span data-stu-id="53864-102">Compensation</span></span>
<span data-ttu-id="53864-103">Windows Workflow Foundation (WF) dengelemesi, daha önce tamamlanmış işin geri alınamayacağı veya dengelemeyeceği (uygulama tarafından tanımlanan mantığı izleyerek) sonraki bir hata oluştuğunda yaptığı mekanizmadır.</span><span class="sxs-lookup"><span data-stu-id="53864-103">Compensation in Windows Workflow Foundation (WF) is the mechanism by which previously completed work can be undone or compensated (following the logic defined by the application) when a subsequent failure occurs.</span></span> <span data-ttu-id="53864-104">Bu bölümde, iş akışlarında tazminat kullanımı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="53864-104">This section describes how to use compensation in workflows.</span></span>  
  
## <a name="compensation-vs-transactions"></a><span data-ttu-id="53864-105">Tazminat karşılaştırması İşlemler</span><span class="sxs-lookup"><span data-stu-id="53864-105">Compensation vs. Transactions</span></span>  
 <span data-ttu-id="53864-106">Bir işlem, birden çok işlemi tek bir iş biriminde birleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="53864-106">A transaction allows you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="53864-107">Bir işlemin kullanılması, işlem işleminin herhangi bir bölümünde herhangi bir hata oluşursa, uygulamanıza işlemin içinden yürütülen tüm değişiklikleri (geri alma) sağlar.</span><span class="sxs-lookup"><span data-stu-id="53864-107">Using a transaction gives your application the ability to abort (roll back) all changes executed from within the transaction if any errors occur during any part of the transaction process.</span></span> <span data-ttu-id="53864-108">Ancak, iş uzun süre çalışıyorsa, işlemler kullanmak uygun olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="53864-108">However, using transactions may not be appropriate if the work is long running.</span></span> <span data-ttu-id="53864-109">Örneğin, bir seyahat planlama uygulaması iş akışı olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="53864-109">For example, a travel planning application is implemented as a workflow.</span></span> <span data-ttu-id="53864-110">İş akışının adımları, bir uçuş kaydı, yönetici onayını bekleme ve sonra uçuş için ödeme yapma bilgisinden oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="53864-110">The steps of the workflow may consist of booking a flight, waiting for manager approval, and then paying for the flight.</span></span> <span data-ttu-id="53864-111">Bu işlem birçok gün sürebilir ve aynı işleme katılabilmek için yapılan kayıt ve ödeme adımları için pratik değildir.</span><span class="sxs-lookup"><span data-stu-id="53864-111">This process could take many days and it is not practical for the steps of booking and paying for the flight to participate in the same transaction.</span></span> <span data-ttu-id="53864-112">Bunun gibi bir senaryoda, işlem içinde daha sonra bir hata oluşursa iş akışının kayıt adımını geri almak için Dengeleme kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="53864-112">In a scenario such as this, compensation could be used to undo the booking step of the workflow if there is a failure later in the processing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="53864-113">Bu konu, iş akışlarında tazminat içerir.</span><span class="sxs-lookup"><span data-stu-id="53864-113">This topic covers compensation in workflows.</span></span> <span data-ttu-id="53864-114">İş akışlarında işlemler hakkında daha fazla bilgi için bkz [](workflow-transactions.md) . işlemler <xref:System.Activities.Statements.TransactionScope>ve.</span><span class="sxs-lookup"><span data-stu-id="53864-114">For more information about transactions in workflows, see [Transactions](workflow-transactions.md) and <xref:System.Activities.Statements.TransactionScope>.</span></span> <span data-ttu-id="53864-115">İşlemler hakkında daha fazla bilgi için bkz <xref:System.Transactions?displayProperty=nameWithType> . <xref:System.Transactions.Transaction?displayProperty=nameWithType>ve.</span><span class="sxs-lookup"><span data-stu-id="53864-115">For more information about transactions, see <xref:System.Transactions?displayProperty=nameWithType> and <xref:System.Transactions.Transaction?displayProperty=nameWithType>.</span></span>  
  
## <a name="using-compensableactivity"></a><span data-ttu-id="53864-116">CompensableActivity kullanma</span><span class="sxs-lookup"><span data-stu-id="53864-116">Using CompensableActivity</span></span>  
 <span data-ttu-id="53864-117"><xref:System.Activities.Statements.CompensableActivity>, içindeki [!INCLUDE[wf1](../../../includes/wf1-md.md)]temel Dengeleme etkinliğidir.</span><span class="sxs-lookup"><span data-stu-id="53864-117"><xref:System.Activities.Statements.CompensableActivity> is the core compensation activity in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="53864-118">Telafi gerektiren işleri gerçekleştiren tüm etkinlikler bir ' a <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity>yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="53864-118">Any activities that perform work that may need to be compensated are placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="53864-119">Bu örnekte, bir uçuş satın almanın rezervasyon adımı bir ' a <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> yerleştirilir ve <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>ayırmanın iptal edilmesi öğesine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="53864-119">In this example, the reservation step of purchasing a flight is placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> and the cancellation of the reservation is placed into the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>.</span></span> <span data-ttu-id="53864-120">İş akışında hemen <xref:System.Activities.Statements.CompensableActivity> sonraki bölümünde, yönetici onayını bekleyen iki etkinlik vardır ve sonra uçuşın satın alma adımını tamamlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="53864-120">Immediately following the <xref:System.Activities.Statements.CompensableActivity> in the workflow are two activities that wait for manager approval and then complete the purchasing step of the flight.</span></span> <span data-ttu-id="53864-121">Bir hata durumu başarıyla tamamlandıktan sonra <xref:System.Activities.Statements.CompensableActivity> iş akışının iptal edilmesine neden oluyorsa, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> işleyicisindeki etkinlikler zamanlanır ve uçuş iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="53864-121">If an error condition causes the workflow to be canceled after the <xref:System.Activities.Statements.CompensableActivity> has successfully completed, then the activities in the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> handler are scheduled and the flight is canceled.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#1)]  
  
 <span data-ttu-id="53864-122">Aşağıdaki örnek, XAML içindeki iş akışıdır.</span><span class="sxs-lookup"><span data-stu-id="53864-122">The following example is the workflow in XAML.</span></span>  
  
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
  
 <span data-ttu-id="53864-123">İş akışı çağrıldığında, konsola aşağıdaki çıktı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="53864-123">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="53864-124">**Rezervlü Eflight: Bilet ayrıldı.**</span><span class="sxs-lookup"><span data-stu-id="53864-124">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="53864-125">**Yönetici onayı: Yönetici onayı alındı.**  </span><span class="sxs-lookup"><span data-stu-id="53864-125">**ManagerApproval: Manager approval received.** </span></span>  
<span data-ttu-id="53864-126">**PurchaseFlight: Bilet satın alındı.**  </span><span class="sxs-lookup"><span data-stu-id="53864-126">**PurchaseFlight: Ticket is purchased.** </span></span>  
<span data-ttu-id="53864-127">**İş akışı şu durumla başarıyla tamamlandı: Kapandı.**</span><span class="sxs-lookup"><span data-stu-id="53864-127">**Workflow completed successfully with status: Closed.**</span></span>    
> [!NOTE]
> <span data-ttu-id="53864-128">Bu konudaki `ReserveFlight` örnek etkinlikler, tazminat gerçekleştiğinde etkinliklerin yürütüldüğü sırayı göstermeye yardımcı olmak üzere konsola adlarını ve amaçlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="53864-128">The sample activities in this topic such as `ReserveFlight` display their name and purpose to the console to help illustrate the order in which the activities are executed when compensation occurs.</span></span>  
  
### <a name="default-workflow-compensation"></a><span data-ttu-id="53864-129">Varsayılan Iş akışı dengelemesi</span><span class="sxs-lookup"><span data-stu-id="53864-129">Default Workflow Compensation</span></span>  
 <span data-ttu-id="53864-130">Varsayılan olarak, iş akışı iptal edilirse, Dengeleme mantığı başarıyla tamamen ve onaylanmış veya dengelenen tüm telafi etkinlikleri için çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="53864-130">By default, if the workflow is canceled, the compensation logic is run for any compensable activity that has successfully completely and has not already been confirmed or compensated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="53864-131">Bir <xref:System.Activities.Statements.CompensableActivity> onaylanırsa, etkinliğin dengelemesi artık çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="53864-131">When a <xref:System.Activities.Statements.CompensableActivity> is *confirmed*, compensation for the activity can no longer be invoked.</span></span> <span data-ttu-id="53864-132">Bu bölümde daha sonra onay süreci açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="53864-132">The confirmation process is described later in this section.</span></span>  
  
 <span data-ttu-id="53864-133">Bu örnekte, uçuş ayrıldıktan sonra ancak yöneticinin onay adımından önce bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="53864-133">In this example, an exception is thrown after the flight is reserved but before the manager approval step.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#2)]  
  
 <span data-ttu-id="53864-134">Bu örnek, XAML 'deki iş akışıdır.</span><span class="sxs-lookup"><span data-stu-id="53864-134">This example is the workflow in XAML.</span></span>  
  
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
  
 <span data-ttu-id="53864-135">İş akışı çağrıldığında, benzetimli hata koşulu özel durumu içindeki <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>konak uygulama tarafından işlenir, iş akışı iptal edilir ve Dengeleme mantığı çağrılır.</span><span class="sxs-lookup"><span data-stu-id="53864-135">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the compensation logic is invoked.</span></span>  
  
 <span data-ttu-id="53864-136">**Rezervlü Eflight: Bilet ayrıldı.**</span><span class="sxs-lookup"><span data-stu-id="53864-136">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="53864-137">**SimulatedErrorCondition: ApplicationException oluşturuluyor.**  </span><span class="sxs-lookup"><span data-stu-id="53864-137">**SimulatedErrorCondition: Throwing an ApplicationException.** </span></span>  
<span data-ttu-id="53864-138">**İş akışı Işlenmemiş özel durumu:**  </span><span class="sxs-lookup"><span data-stu-id="53864-138">**Workflow Unhandled Exception:** </span></span>  
<span data-ttu-id="53864-139">**System. ApplicationException: İş akışında Benzetimli hata koşulu.**  </span><span class="sxs-lookup"><span data-stu-id="53864-139">**System.ApplicationException: Simulated error condition in the workflow.** </span></span>  
<span data-ttu-id="53864-140">**Canceluçuş: Bilet iptal edildi.**  </span><span class="sxs-lookup"><span data-stu-id="53864-140">**CancelFlight: Ticket is canceled.** </span></span>  
<span data-ttu-id="53864-141">**İş akışı şu durumla başarıyla tamamlandı: Edilmesi.**</span><span class="sxs-lookup"><span data-stu-id="53864-141">**Workflow completed successfully with status: Canceled.**</span></span>    
### <a name="cancellation-and-compensableactivity"></a><span data-ttu-id="53864-142">İptal ve CompensableActivity</span><span class="sxs-lookup"><span data-stu-id="53864-142">Cancellation and CompensableActivity</span></span>  
 <span data-ttu-id="53864-143"><xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> İçindeki <xref:System.Activities.Statements.CompensableActivity.Body%2A> Etkinliklertamamlanmadıysaveetkinlikiptaledilirse,<xref:System.Activities.Statements.CompensableActivity> içindeki etkinlikler yürütülür.</span><span class="sxs-lookup"><span data-stu-id="53864-143">If the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled, the activities in the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> are executed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="53864-144"><xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> Yalnızca içindeki<xref:System.Activities.Statements.CompensableActivity> etkinlikler tamamlanmadıysa ve etkinlik iptal edildiğinde çağrılır. <xref:System.Activities.Statements.CompensableActivity.Body%2A></span><span class="sxs-lookup"><span data-stu-id="53864-144">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is only invoked if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled.</span></span> <span data-ttu-id="53864-145"><xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> Yalnızca içindeki<xref:System.Activities.Statements.CompensableActivity> etkinlikler başarıyla tamamlandığında ve tazminat etkinlik üzerinde çağrılırsa yürütülür. <xref:System.Activities.Statements.CompensableActivity.Body%2A></span><span class="sxs-lookup"><span data-stu-id="53864-145">The <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> is only executed if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have successfully completed and compensation is subsequently invoked on the activity.</span></span>  
  
 <span data-ttu-id="53864-146">, <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> İş akışı için uygun bir iptal mantığı sağlama fırsatı yazar.</span><span class="sxs-lookup"><span data-stu-id="53864-146">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> gives workflow authors the opportunity to provide any appropriate cancellation logic.</span></span> <span data-ttu-id="53864-147">Aşağıdaki örnekte, öğesinin <xref:System.Activities.Statements.CompensableActivity.Body%2A>yürütülmesi sırasında bir özel durum oluşturulur ve <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> sonra çağrılır.</span><span class="sxs-lookup"><span data-stu-id="53864-147">In the following example, an exception is thrown during the execution of the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, and then the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is invoked.</span></span>  
  
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
  
 <span data-ttu-id="53864-148">Bu örnek, XAML 'deki iş akışıdır</span><span class="sxs-lookup"><span data-stu-id="53864-148">This example is the workflow in XAML</span></span>  
  
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
  
 <span data-ttu-id="53864-149">İş akışı çağrıldığında, benzetimli hata koşulu özel durumu ' de <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>konak uygulama tarafından işlenir, iş akışı iptal edilir ve <xref:System.Activities.Statements.CompensableActivity> öğesinin iptal mantığı çağrılır.</span><span class="sxs-lookup"><span data-stu-id="53864-149">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the cancellation logic of the <xref:System.Activities.Statements.CompensableActivity> is invoked.</span></span> <span data-ttu-id="53864-150">Bu örnekte, Dengeleme mantığı ve iptal etme mantığının farklı hedefleri vardır.</span><span class="sxs-lookup"><span data-stu-id="53864-150">In this example, the compensation logic and the cancellation logic have different goals.</span></span> <span data-ttu-id="53864-151">Başarılı bir şekilde tamamlanırsa, kredi kartının ücretlendirilildiği ve uçuşın her iki adımı da geri alması gerektiği anlamına gelir. <xref:System.Activities.Statements.CompensableActivity.Body%2A></span><span class="sxs-lookup"><span data-stu-id="53864-151">If the <xref:System.Activities.Statements.CompensableActivity.Body%2A> completed successfully, then this means the credit card was charged and the flight booked, so the compensation should undo both steps.</span></span> <span data-ttu-id="53864-152">(Bu örnekte, uçuşmanın iptal edilmesi, kredi kartı ücretlerini otomatik olarak iptal eder.) Ancak, iptal edilirse bu, tamamlanmamış <xref:System.Activities.Statements.CompensableActivity.Body%2A> olduğu anlamına gelir ve bu <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> nedenle İptalin en iyi şekilde nasıl işleneceğini belirleyebilmelidir. <xref:System.Activities.Statements.CompensableActivity></span><span class="sxs-lookup"><span data-stu-id="53864-152">(In this example, canceling the flight automatically cancels the credit card charges.) However, if the <xref:System.Activities.Statements.CompensableActivity> is canceled, this means the <xref:System.Activities.Statements.CompensableActivity.Body%2A> did not complete and so the logic of the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> needs to be able to determine how to best handle the cancellation.</span></span> <span data-ttu-id="53864-153">Bu örnekte <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> , kredi kartı ücreti iptal edilir, ancak içinde <xref:System.Activities.Statements.CompensableActivity.Body%2A>son etkinlik `ReserveFlight` olduğundan, uçuştan iptal etmeyi denemez.</span><span class="sxs-lookup"><span data-stu-id="53864-153">In this example, the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> cancels the credit card charge, but since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, it does not attempt to cancel the flight.</span></span> <span data-ttu-id="53864-154">İçindeki son etkinlik olduğundan, bu, başarıyla tamamlandıysa, <xref:System.Activities.Statements.CompensableActivity.Body%2A> tamamlanmış olur ve hiçbir iptali mümkün olmaz. <xref:System.Activities.Statements.CompensableActivity.Body%2A> `ReserveFlight`</span><span class="sxs-lookup"><span data-stu-id="53864-154">Since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, if it had successfully completed then the <xref:System.Activities.Statements.CompensableActivity.Body%2A> would have completed and no cancellation would be possible.</span></span>  
  
 <span data-ttu-id="53864-155">**ChargeCreditCard: Uçuş için kredi kartı ücreti.**</span><span class="sxs-lookup"><span data-stu-id="53864-155">**ChargeCreditCard: Charge credit card for flight.**</span></span>  
<span data-ttu-id="53864-156">**SimulatedErrorCondition: ApplicationException oluşturuluyor.**  </span><span class="sxs-lookup"><span data-stu-id="53864-156">**SimulatedErrorCondition: Throwing an ApplicationException.** </span></span>  
<span data-ttu-id="53864-157">**İş akışı Işlenmemiş özel durumu:**  </span><span class="sxs-lookup"><span data-stu-id="53864-157">**Workflow Unhandled Exception:** </span></span>  
<span data-ttu-id="53864-158">**System. ApplicationException: İş akışında Benzetimli hata koşulu.**  </span><span class="sxs-lookup"><span data-stu-id="53864-158">**System.ApplicationException: Simulated error condition in the workflow.** </span></span>  
<span data-ttu-id="53864-159">**CancelCreditCard: Kredi kartı ücretlerini iptal edin.**  </span><span class="sxs-lookup"><span data-stu-id="53864-159">**CancelCreditCard: Cancel credit card charges.** </span></span>  
<span data-ttu-id="53864-160">**İş akışı şu durumla başarıyla tamamlandı: Edilmesi.**</span><span class="sxs-lookup"><span data-stu-id="53864-160">**Workflow completed successfully with status: Canceled.**</span></span>  <span data-ttu-id="53864-161">İptal hakkında daha fazla bilgi için bkz. [iptal](modeling-cancellation-behavior-in-workflows.md).</span><span class="sxs-lookup"><span data-stu-id="53864-161">For more information about cancellation, see [Cancellation](modeling-cancellation-behavior-in-workflows.md).</span></span>  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a><span data-ttu-id="53864-162">Telafi etkinliğini kullanan açık Dengeleme</span><span class="sxs-lookup"><span data-stu-id="53864-162">Explicit Compensation Using the Compensate Activity</span></span>  
 <span data-ttu-id="53864-163">Önceki bölümde örtük Dengeleme ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="53864-163">In the previous section, implicit compensation was covered.</span></span> <span data-ttu-id="53864-164">Örtük Dengeleme basit senaryolar için uygun olabilir, ancak tazmin işleme <xref:System.Activities.Statements.Compensate> zamanlaması üzerinde daha fazla açık denetim gerekliyse etkinlik kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="53864-164">Implicit compensation can be appropriate for simple scenarios, but if more explicit control is required over the scheduling of compensation handling then the <xref:System.Activities.Statements.Compensate> activity can be used.</span></span> <span data-ttu-id="53864-165">İşlem ile <xref:System.Activities.Statements.Compensate> <xref:System.Activities.Statements.CompensableActivity> Dengeleme işlemini başlatmak için tazminat istenen öğesininkullanıldığıyer.<xref:System.Activities.Statements.CompensationToken></span><span class="sxs-lookup"><span data-stu-id="53864-165">To initiate the compensation process with the <xref:System.Activities.Statements.Compensate> activity, the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> for which compensation is desired is used.</span></span> <span data-ttu-id="53864-166">Etkinlik <xref:System.Activities.Statements.Compensate> , onaylanmayan veya dengelenen herhangi bir tamamlanmış <xref:System.Activities.Statements.CompensableActivity> üzerinden tazminat başlatmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="53864-166">The <xref:System.Activities.Statements.Compensate> activity can be used to initiate compensation on any completed <xref:System.Activities.Statements.CompensableActivity> that has not been confirmed or compensated.</span></span> <span data-ttu-id="53864-167">Örneğin, <xref:System.Activities.Statements.Compensate> etkinlik bir <xref:System.Activities.Statements.TryCatch.Catches%2A> <xref:System.Activities.Statements.TryCatch> etkinliğin bölümünde veya tamamlandıktan sonra <xref:System.Activities.Statements.CompensableActivity> herhangi bir zaman kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="53864-167">For example, a <xref:System.Activities.Statements.Compensate> activity could be used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity, or any time after the <xref:System.Activities.Statements.CompensableActivity> has completed.</span></span> <span data-ttu-id="53864-168">Bu örnekte <xref:System.Activities.Statements.Compensate> etkinlik, <xref:System.Activities.Statements.TryCatch> <xref:System.Activities.Statements.TryCatch.Catches%2A> eylemi<xref:System.Activities.Statements.CompensableActivity>tersine çevirmek için etkinliğin bölümünde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="53864-168">In this example, the <xref:System.Activities.Statements.Compensate> activity is used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity to reverse the action of the <xref:System.Activities.Statements.CompensableActivity>.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#3)]  
  
 <span data-ttu-id="53864-169">Bu örnek, XAML 'deki iş akışıdır.</span><span class="sxs-lookup"><span data-stu-id="53864-169">This example is the workflow in XAML.</span></span>  
  
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
  
 <span data-ttu-id="53864-170">İş akışı çağrıldığında, konsola aşağıdaki çıktı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="53864-170">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="53864-171">**Rezervlü Eflight: Bilet ayrıldı.**</span><span class="sxs-lookup"><span data-stu-id="53864-171">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="53864-172">**SimulatedErrorCondition: ApplicationException oluşturuluyor.**  </span><span class="sxs-lookup"><span data-stu-id="53864-172">**SimulatedErrorCondition: Throwing an ApplicationException.** </span></span>  
<span data-ttu-id="53864-173">**Canceluçuş: Bilet iptal edildi.**  </span><span class="sxs-lookup"><span data-stu-id="53864-173">**CancelFlight: Ticket is canceled.** </span></span>  
<span data-ttu-id="53864-174">**İş akışı şu durumla başarıyla tamamlandı: Kapandı.**</span><span class="sxs-lookup"><span data-stu-id="53864-174">**Workflow completed successfully with status: Closed.**</span></span>    
### <a name="confirming-compensation"></a><span data-ttu-id="53864-175">Tazminat onaylama</span><span class="sxs-lookup"><span data-stu-id="53864-175">Confirming Compensation</span></span>  
 <span data-ttu-id="53864-176">Varsayılan olarak, compensable etkinlikleri tamamlandıktan sonra herhangi bir zaman dengelenebilir.</span><span class="sxs-lookup"><span data-stu-id="53864-176">By default, compensable activities can be compensated any time after they have completed.</span></span> <span data-ttu-id="53864-177">Bazı senaryolarda bu uygun olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="53864-177">In some scenarios this may not be appropriate.</span></span> <span data-ttu-id="53864-178">Önceki örnekte, anahtarı ayırma dengelemesi ayırmayı iptal etmiydi.</span><span class="sxs-lookup"><span data-stu-id="53864-178">In the previous example the compensation to reserving the ticket was to cancel the reservation.</span></span> <span data-ttu-id="53864-179">Ancak, uçuş tamamlandıktan sonra bu dengeleme adımı artık geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="53864-179">However, after the flight has been completed this compensation step is no longer valid.</span></span> <span data-ttu-id="53864-180">Dengelenebilir etkinliğin tarafından <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>belirtilen etkinliği çağırdığı doğrulanıyor.</span><span class="sxs-lookup"><span data-stu-id="53864-180">Confirming the compensable activity invokes the activity specified by the <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>.</span></span> <span data-ttu-id="53864-181">Bunun olası bir kullanımı, tazminatı gerçekleştirmek için gerekli olan tüm kaynaklara izin vermedir.</span><span class="sxs-lookup"><span data-stu-id="53864-181">One possible use for this is to allow any resources that are necessary to perform the compensation to be released.</span></span> <span data-ttu-id="53864-182">Dengelenebilir bir etkinliğin onaylandıktan sonra, telafi olması mümkün değildir ve bu denendiğinde özel bir <xref:System.InvalidOperationException> durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="53864-182">After a compensable activity is confirmed it is not possible for it to be compensated, and if this is attempted an <xref:System.InvalidOperationException> exception is thrown.</span></span> <span data-ttu-id="53864-183">Bir iş akışı başarıyla tamamlandığında, başarıyla tamamlanan, onaylanmamış ve dengelenmemiş tüm telafi etkinlikleri, tamamlanma sırasında onaylanır.</span><span class="sxs-lookup"><span data-stu-id="53864-183">When a workflow completes successfully, all non-confirmed and non-compensated compensable activities that completed successfully are confirmed in reverse order of completion.</span></span> <span data-ttu-id="53864-184">Bu örnekte uçuş ayrılmıştır, satın alınır ve tamamlanır ve sonra dengelenebilir etkinlik onaylanır.</span><span class="sxs-lookup"><span data-stu-id="53864-184">In this example the flight is reserved, purchased, and completed, and then the compensable activity is confirmed.</span></span> <span data-ttu-id="53864-185">Bir <xref:System.Activities.Statements.CompensableActivity>doğrulamak için, <xref:System.Activities.Statements.Confirm> etkinliğini <xref:System.Activities.Statements.CompensationToken> kullanın<xref:System.Activities.Statements.CompensableActivity> ve öğesini doğrulamak için öğesini belirtin.</span><span class="sxs-lookup"><span data-stu-id="53864-185">To confirm a <xref:System.Activities.Statements.CompensableActivity>, use the <xref:System.Activities.Statements.Confirm> activity and specify the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> to confirm.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#4](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#4)]  
  
 <span data-ttu-id="53864-186">Bu örnek, XAML 'deki iş akışıdır.</span><span class="sxs-lookup"><span data-stu-id="53864-186">This example is the workflow in XAML.</span></span>  
  
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
  
<span data-ttu-id="53864-187">İş akışı çağrıldığında, konsola aşağıdaki çıktı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="53864-187">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
<span data-ttu-id="53864-188">**Rezervlü Eflight: Bilet ayrıldı.**</span><span class="sxs-lookup"><span data-stu-id="53864-188">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="53864-189">**Yönetici onayı: Yönetici onayı alındı.**  </span><span class="sxs-lookup"><span data-stu-id="53864-189">**ManagerApproval: Manager approval received.** </span></span>  
<span data-ttu-id="53864-190">**PurchaseFlight: Bilet satın alındı.**  </span><span class="sxs-lookup"><span data-stu-id="53864-190">**PurchaseFlight: Ticket is purchased.** </span></span>  
<span data-ttu-id="53864-191">**Takeuçuş: Uçuş tamamlandı.**  </span><span class="sxs-lookup"><span data-stu-id="53864-191">**TakeFlight: Flight is completed.** </span></span>  
<span data-ttu-id="53864-192">**ConfirmFlight: Uçuş alındı, hiçbir telafi yapılamaz.**  </span><span class="sxs-lookup"><span data-stu-id="53864-192">**ConfirmFlight: Flight has been taken, no compensation possible.** </span></span>  
<span data-ttu-id="53864-193">**İş akışı şu durumla başarıyla tamamlandı: Kapandı.**</span><span class="sxs-lookup"><span data-stu-id="53864-193">**Workflow completed successfully with status: Closed.**</span></span>   

## <a name="nesting-compensation-activities"></a><span data-ttu-id="53864-194">Telafi etkinliklerinin iç içe geçirilmesi</span><span class="sxs-lookup"><span data-stu-id="53864-194">Nesting Compensation Activities</span></span>  

<span data-ttu-id="53864-195">Bir <xref:System.Activities.Statements.CompensableActivity>diğerinin bölümüneeklenebilir.<xref:System.Activities.Statements.CompensableActivity> <xref:System.Activities.Statements.CompensableActivity.Body%2A></span><span class="sxs-lookup"><span data-stu-id="53864-195">A <xref:System.Activities.Statements.CompensableActivity> can be placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> section of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="53864-196">Bir <xref:System.Activities.Statements.CompensableActivity> başka<xref:System.Activities.Statements.CompensableActivity>bir işleyiciye yerleştirilmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="53864-196">A <xref:System.Activities.Statements.CompensableActivity> may not be placed into a handler of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="53864-197">Bu, bir üst <xref:System.Activities.Statements.CompensableActivity> öğenin sorumluluğundadır, teyit edildiğinde veya telafi edildiğinde, başarıyla tamamlanan ve henüz onaylanmamıştır veya telafi edilmesi gereken tüm alt öğe dengelenebilir etkinlikleri onaylamalıdır veya üst öğe iptali, onayı veya tazminatı tamamlanmadan önce dengelenen.</span><span class="sxs-lookup"><span data-stu-id="53864-197">It is the responsibility of a parent <xref:System.Activities.Statements.CompensableActivity> to ensure that when it is canceled, confirmed, or compensated, all child compensable activities that have completed successfully and have not already been confirmed or compensated must be confirmed or compensated before the parent completes cancellation, confirmation, or compensation.</span></span> <span data-ttu-id="53864-198">Bu, açıkça modellenmezse, üst <xref:System.Activities.Statements.CompensableActivity> öğe iptal veya telafi sinyalini alıyorsa üst öğe, alt öğe dengelenebilir etkinlikleri dolaylı olarak dengelenir.</span><span class="sxs-lookup"><span data-stu-id="53864-198">If this is not modeled explicitly the parent <xref:System.Activities.Statements.CompensableActivity> will implicitly compensate child compensable activities if the parent received the cancel or compensate signal.</span></span> <span data-ttu-id="53864-199">Üst öğe onaylama sinyali aldıysa, üst öğe, alt dengelenebilir etkinlikleri dolaylı olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="53864-199">If the parent received the confirm signal the parent will implicitly confirm child compensable activities.</span></span> <span data-ttu-id="53864-200">İptali, onayı veya tazminatı işlemek için mantık, üst <xref:System.Activities.Statements.CompensableActivity>öğenin işleyicisinde açıkça modellendiyse, açıkça işlenmeyen tüm alt öğe örtük olarak onaylanır.</span><span class="sxs-lookup"><span data-stu-id="53864-200">If the logic to handle cancellation, confirmation, or compensation is explicitly modeled in the handler of the parent <xref:System.Activities.Statements.CompensableActivity>, any child not explicitly handled will be implicitly confirmed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53864-201">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53864-201">See also</span></span>

- <xref:System.Activities.Statements.CompensableActivity>
- <xref:System.Activities.Statements.Compensate>
- <xref:System.Activities.Statements.Confirm>
- <xref:System.Activities.Statements.CompensationToken>
