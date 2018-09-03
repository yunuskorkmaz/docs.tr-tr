---
title: Mutlak gecikme
ms.date: 03/30/2017
ms.assetid: b483139a-39bb-4560-8003-8969a8fc2cd1
ms.openlocfilehash: 30719a4340b738a7462584c4dca00f6d5d90ac72
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486108"
---
# <a name="absolute-delay"></a><span data-ttu-id="77292-102">Mutlak gecikme</span><span class="sxs-lookup"><span data-stu-id="77292-102">Absolute Delay</span></span>
<span data-ttu-id="77292-103">Bu örnek için ana senaryo kadar belirtilen bir gecikme olduğunu <xref:System.DateTime> dayanıklı zamanlayıcılar bir iş akışı uygulamasında kullanma.</span><span class="sxs-lookup"><span data-stu-id="77292-103">The main scenario for this sample is to delay until a specified <xref:System.DateTime> using durable timers in a workflow application.</span></span> <span data-ttu-id="77292-104">Bu yerleşik kullanımından farklı <xref:System.Activities.Statements.Delay> etkinliği olarak bu işlem yalnızca sonrasında için gecikme bir verilen <xref:System.TimeSpan> (veya kaç dakika/saniye).</span><span class="sxs-lookup"><span data-stu-id="77292-104">This is different from using the built-in <xref:System.Activities.Statements.Delay> activity as this will only allow you to delay for a given <xref:System.TimeSpan> (or number of minutes/seconds).</span></span>  
  
 <span data-ttu-id="77292-105">Bazı gerçek durum senaryolarının şunlar Bu ayrım yapmak isteyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="77292-105">Some real-life scenarios in which you may want to make this distinction include the following:</span></span>  
  
1.  <span data-ttu-id="77292-106">Hataları yapmadım emin olmak 30 saniye için bir e-posta göndermeye gecikme istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="77292-106">You want to delay sending a mail for 30 seconds to make sure you didn’t make any errors.</span></span>  
  
2.  <span data-ttu-id="77292-107">Gereğinden fazla ve tüm postalarınızı kadar normal çalışma saatleri (örneğin 8: 00) geciktirmek istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="77292-107">You are working overtime and want to delay all of your mails until normal business hours (such as 8 am).</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="77292-108">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="77292-108">Demonstrates</span></span>  
  
1.  <span data-ttu-id="77292-109"><xref:System.Activities.Statements.DurableTimerExtension> Mutlak gecikme uygulamak için</span><span class="sxs-lookup"><span data-stu-id="77292-109"><xref:System.Activities.Statements.DurableTimerExtension> for implementing Absolute Delay</span></span>  
  
2.  <span data-ttu-id="77292-110">Kalıcılık kullanarak ayarı <xref:System.Activities.WorkflowApplication> dayanıklı zamanlayıcılar için</span><span class="sxs-lookup"><span data-stu-id="77292-110">Setting up persistence using <xref:System.Activities.WorkflowApplication> for Durable Timers</span></span>  
  
3.  <span data-ttu-id="77292-111">Kullanım <xref:System.Activities.NativeActivity%601> genişletilebilirlik noktaları kullanma</span><span class="sxs-lookup"><span data-stu-id="77292-111">Use of <xref:System.Activities.NativeActivity%601> for using Extensibility points</span></span>  
  
4.  <span data-ttu-id="77292-112">Kullanım <xref:System.Activities.CodeActivity%601> SendEmail etkinliği içinde</span><span class="sxs-lookup"><span data-stu-id="77292-112">Use of <xref:System.Activities.CodeActivity%601> in the SendEmail activity</span></span>  
  
5.  <xref:System.Activities.Statements.Delay>  
  
6.  <span data-ttu-id="77292-113">Yalnızca XAML iş akışı</span><span class="sxs-lookup"><span data-stu-id="77292-113">XAML-only workflow</span></span>  
  
 <span data-ttu-id="77292-114">Bu örnek alan olarak özel etkinlik oluşturma işlemini gösterir. bir <xref:System.DateTime> ve dayanıklı zamanlayıcılar gecikme süresi kaydetmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="77292-114">This sample demonstrates how to create a custom activity which takes in a <xref:System.DateTime> and uses durable timers to register the delay duration.</span></span> <span data-ttu-id="77292-115">Dayanıklı zamanlayıcılar kullanırken kullanmalısınız bir <xref:System.Activities.NativeActivity> bu yer işaretinin Zamanlayıcı uzantısı ile kaydetmek ihtiyacınız olacak şekilde bir yer işareti oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="77292-115">When using durable timers, you must use a <xref:System.Activities.NativeActivity> to create a bookmark, as you will need to register this bookmark with the timer extension.</span></span> <span data-ttu-id="77292-116">Dayanıklı süreölçerdeki Süre dolduğunda, bu örnekteki `OnTimerExpired` yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="77292-116">In this sample, when the durable timer expires, the `OnTimerExpired` method will be called.</span></span> <span data-ttu-id="77292-117">Zamanlayıcı uzantı eklemekte olduğunuz emin <xref:System.Activities.NativeActivity%601.CacheMetadata%2A> bu bilgilerle çalışma zamanı sağlama emin olmak için olay.</span><span class="sxs-lookup"><span data-stu-id="77292-117">Make sure that you are adding the timer extension in the <xref:System.Activities.NativeActivity%601.CacheMetadata%2A> event to ensure you are providing the runtime with this information.</span></span> <span data-ttu-id="77292-118">Dönüştürmek için mantığını gerekecektir yalnızca diğer uygulama ayrıntısı olduğunu <xref:System.DateTime> için <xref:System.TimeSpan>dayanıklı zamanlayıcılar yalnızca almak gibi bir <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="77292-118">The only other implementation detail is that you will need to implement logic to convert from <xref:System.DateTime> to <xref:System.TimeSpan>, as durable timers only take in a <xref:System.DateTime>.</span></span> <span data-ttu-id="77292-119">Küçük lapse doğruluk yaparak unutmayın</span><span class="sxs-lookup"><span data-stu-id="77292-119">Do note that there is a small lapse in accuracy by doing</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77292-120">Dönüştürme göre küçük bir doğruluk kaybı olan <xref:System.DateTime> için <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="77292-120">There is a small loss of accuracy by converting from <xref:System.DateTime> to <xref:System.TimeSpan>.</span></span>  
  
 <span data-ttu-id="77292-121">Bu örnek ayrıca kalıcılığını etkinleştirme gösterir bir <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="77292-121">This sample also demonstrates how to turn on persistence for a <xref:System.Activities.WorkflowApplication>.</span></span> <span data-ttu-id="77292-122">Bu belirli bir örnek için sizi, iş akışı verileri Kalıcılık veritabanına boşta kalma süresi dolmak üzere Zamanlayıcı için beklenirken sırasında bellekten kaldırılacak dayanıklı zamanlayıcılar kullanacaklardır.</span><span class="sxs-lookup"><span data-stu-id="77292-122">For this particular sample, we will be using durable timers in which the workflow data will be unloaded into the persistence database during the idle time while waiting for timer to expire.</span></span> <span data-ttu-id="77292-123">Bu uygulama, diğer Kalıcılık eylemler için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="77292-123">This implementation can also be used for other persistence actions.</span></span> <span data-ttu-id="77292-124">Bu örnek, SQL Server Kalıcılık bağlantı dizesiyle kurma ve iş akışı örnekleri için verileri kalıcı hale getirmek için örnek deposu oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="77292-124">This sample shows how to set up the persistence connection string with SQL Server, and how to create the instance store in order to persist the data for workflow instances.</span></span> <span data-ttu-id="77292-125">Mantıksal iş akışı örneği çalıştırılabilir sağlayan bir olay tetiklenir sonra iş akışını sürdürmek nasıl sağlanır.</span><span class="sxs-lookup"><span data-stu-id="77292-125">Logic is provided on how to resume the workflow once an event is raised which makes the workflow instance runnable.</span></span>  
  
 <span data-ttu-id="77292-126">Bu örnek adım olarak, yerleşik gecikme başlar ve tamamlar, hangi sırayla zaman gönderilecek e-posta iletisine neden olur görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="77292-126">As you step through this sample, you will see the time in which the built-in delay begins and completes, which in turn will cause an email message to be sent.</span></span> <span data-ttu-id="77292-127">Burada, AbsoluteDelay etkinlik belirtilen kadar durdurulur <xref:System.DateTime> (veya 0 saniye, <xref:System.DateTime> süresi doldu) hangi sırayla göndermek sona erme üzerine bir e-posta.</span><span class="sxs-lookup"><span data-stu-id="77292-127">From there, the AbsoluteDelay activity will halt until a specified <xref:System.DateTime> (or 0 seconds if the <xref:System.DateTime> has expired) which in turn will send out an email upon expiration.</span></span> <span data-ttu-id="77292-128">Bu iki farklı kullanım örnekleri yerleşik gösterir <xref:System.Activities.Statements.Delay> AbsoluteDelay etkinlik kullanma ve işlevleri.</span><span class="sxs-lookup"><span data-stu-id="77292-128">This will show the two different use cases of the built-in <xref:System.Activities.Statements.Delay> functionality versus using an AbsoluteDelay activity.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="77292-129">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="77292-129">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="77292-130">SQL Server Express (veya üzeri), makinenizde yüklü olduğundan emin olun</span><span class="sxs-lookup"><span data-stu-id="77292-130">Ensure you have SQL Server Express (or higher) installed on your machine</span></span>  
  
2.  <span data-ttu-id="77292-131">Setup.cmd (WF/Basic/Services/AbsoluteDelay/CS) içinde çalışan bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] AbsoluteDelaySampleDB veritabanı oluşturma, kalıcı şema oluşturmak ve Kalıcılık mantığı oluşturmak için bir komut istemi.</span><span class="sxs-lookup"><span data-stu-id="77292-131">Run setup.cmd (from WF/Basic/Services/AbsoluteDelay/CS) in a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt to create the AbsoluteDelaySampleDB database, create the persistence schema and create the persistence logic.</span></span>  
  
3.  <span data-ttu-id="77292-132">Bir çözüm açın [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="77292-132">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
4.  <span data-ttu-id="77292-133">Delay etkinlik süreyi belirtin.</span><span class="sxs-lookup"><span data-stu-id="77292-133">Specify the Duration in the Delay activity.</span></span>  
  
5.  <span data-ttu-id="77292-134">ExpirationTime AbsoluteDelay etkinliğinde belirtin.</span><span class="sxs-lookup"><span data-stu-id="77292-134">Specify the ExpirationTime in the AbsoluteDelay activity.</span></span>  
  
6.  <span data-ttu-id="77292-135">SendMail etkinliğinde SendMailTo, SendMailFrom SendMailSubject SendMailBody ve SmtpHost alanlarını güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="77292-135">Update the SendMailTo, SendMailFrom, SendMailSubject, SendMailBody, and SmtpHost fields in the SendMail activity.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="77292-136">Geçerli bir SMTP konağı girmezseniz, uygulama bir SMTP özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="77292-136">If you do not enter a valid SMTP host, the application will throw a SMTP exception.</span></span>  
  
7.  <span data-ttu-id="77292-137">Çözüm seçerek yapı **derleme**, **Çözümü Derle**.</span><span class="sxs-lookup"><span data-stu-id="77292-137">Build the solution by selecting **Build**, **Build Solution**.</span></span>  
  
8.  <span data-ttu-id="77292-138">Tuşlarına basarak çözümü çalıştırın **F5**.</span><span class="sxs-lookup"><span data-stu-id="77292-138">Run the solution by pressing **F5**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="77292-139">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="77292-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="77292-140">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="77292-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="77292-141">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="77292-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="77292-142">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="77292-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\AbsoluteDelay`
