---
title: Mutlak gecikmesi
ms.date: 03/30/2017
ms.assetid: b483139a-39bb-4560-8003-8969a8fc2cd1
ms.openlocfilehash: 3a104f6b879e9cdc899bad2201ad1ed320a38a2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518391"
---
# <a name="absolute-delay"></a><span data-ttu-id="88742-102">Mutlak gecikmesi</span><span class="sxs-lookup"><span data-stu-id="88742-102">Absolute Delay</span></span>
<span data-ttu-id="88742-103">Bu örnek için ana senaryo belirtilen kadar gecikme olduğunu <xref:System.DateTime> dayanıklı zamanlayıcılar bir iş akışı uygulamasında kullanma.</span><span class="sxs-lookup"><span data-stu-id="88742-103">The main scenario for this sample is to delay until a specified <xref:System.DateTime> using durable timers in a workflow application.</span></span> <span data-ttu-id="88742-104">Bu, yerleşik kullanmaktan farklı değildir <xref:System.Activities.Statements.Delay> gibi bu etkinlik yalnızca izni verdiği için gecikme bir verilen <xref:System.TimeSpan> (veya dakika/saniye).</span><span class="sxs-lookup"><span data-stu-id="88742-104">This is different from using the built-in <xref:System.Activities.Statements.Delay> activity as this will only allow you to delay for a given <xref:System.TimeSpan> (or number of minutes/seconds).</span></span>  
  
 <span data-ttu-id="88742-105">Bazı gerçekçi senaryolar şunlardır Bu ayrım yapmak isteyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="88742-105">Some real-life scenarios in which you may want to make this distinction include the following:</span></span>  
  
1.  <span data-ttu-id="88742-106">Bir posta hataları siz yapmadıysanız emin olmak 30 saniye gönderme geciktirmek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="88742-106">You want to delay sending a mail for 30 seconds to make sure you didn’t make any errors.</span></span>  
  
2.  <span data-ttu-id="88742-107">Gereğinden fazla olan ve tüm, posta kadar normal iş saatleri (örneğin 8: 00) geciktirmek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="88742-107">You are working overtime and want to delay all of your mails until normal business hours (such as 8 am).</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="88742-108">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="88742-108">Demonstrates</span></span>  
  
1.  <span data-ttu-id="88742-109"><xref:System.Activities.Statements.DurableTimerExtension> Mutlak gecikme uygulamak için</span><span class="sxs-lookup"><span data-stu-id="88742-109"><xref:System.Activities.Statements.DurableTimerExtension> for implementing Absolute Delay</span></span>  
  
2.  <span data-ttu-id="88742-110">Kalıcılık kullanarak kurmanız <xref:System.Activities.WorkflowApplication> dayanıklı zamanlayıcılar için</span><span class="sxs-lookup"><span data-stu-id="88742-110">Setting up persistence using <xref:System.Activities.WorkflowApplication> for Durable Timers</span></span>  
  
3.  <span data-ttu-id="88742-111">Kullanımı <xref:System.Activities.NativeActivity%601> genişletilebilirlik noktaları kullanma</span><span class="sxs-lookup"><span data-stu-id="88742-111">Use of <xref:System.Activities.NativeActivity%601> for using Extensibility points</span></span>  
  
4.  <span data-ttu-id="88742-112">Kullanımı <xref:System.Activities.CodeActivity%601> SendEmail etkinliği içinde</span><span class="sxs-lookup"><span data-stu-id="88742-112">Use of <xref:System.Activities.CodeActivity%601> in the SendEmail activity</span></span>  
  
5.  <xref:System.Activities.Statements.Delay>  
  
6.  <span data-ttu-id="88742-113">Yalnızca XAML iş akışı</span><span class="sxs-lookup"><span data-stu-id="88742-113">XAML-only workflow</span></span>  
  
 <span data-ttu-id="88742-114">Bu örnek nasıl alan içinde özel bir aktivite oluşturulduğunu gösteren bir <xref:System.DateTime> ve gecikme süresini kaydetmek için dayanıklı zamanlayıcılar kullanır.</span><span class="sxs-lookup"><span data-stu-id="88742-114">This sample demonstrates how to create a custom activity which takes in a <xref:System.DateTime> and uses durable timers to register the delay duration.</span></span> <span data-ttu-id="88742-115">Dayanıklı zamanlayıcılar kullanırken kullanmalısınız bir <xref:System.Activities.NativeActivity> bu yer işaretinin Zamanlayıcı uzantısı ile kaydetmek ihtiyaç duyacağınız bir yer işareti oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="88742-115">When using durable timers, you must use a <xref:System.Activities.NativeActivity> to create a bookmark, as you will need to register this bookmark with the timer extension.</span></span> <span data-ttu-id="88742-116">Dayanıklı Zamanlayıcı süresi dolduğunda, bu örnekteki `OnTimerExpired` yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="88742-116">In this sample, when the durable timer expires, the `OnTimerExpired` method will be called.</span></span> <span data-ttu-id="88742-117">Zamanlayıcı uzantısı'nda eklediğiniz emin olun <xref:System.Activities.NativeActivity%601.CacheMetadata%2A> bu bilgilerle çalışma zamanı sağlama emin olmak için olay.</span><span class="sxs-lookup"><span data-stu-id="88742-117">Make sure that you are adding the timer extension in the <xref:System.Activities.NativeActivity%601.CacheMetadata%2A> event to ensure you are providing the runtime with this information.</span></span> <span data-ttu-id="88742-118">Yalnızca diğer uygulama dönüştürmek için mantığı uygulamanız gerekir olup <xref:System.DateTime> için <xref:System.TimeSpan>dayanıklı zamanlayıcılar yalnızca sürer gibi bir <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="88742-118">The only other implementation detail is that you will need to implement logic to convert from <xref:System.DateTime> to <xref:System.TimeSpan>, as durable timers only take in a <xref:System.DateTime>.</span></span> <span data-ttu-id="88742-119">Küçük lapse doğruluk yaparak yoktur</span><span class="sxs-lookup"><span data-stu-id="88742-119">Do note that there is a small lapse in accuracy by doing</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88742-120">Dönüştürme tarafından doğruluğu küçük kaybı olan <xref:System.DateTime> için <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="88742-120">There is a small loss of accuracy by converting from <xref:System.DateTime> to <xref:System.TimeSpan>.</span></span>  
  
 <span data-ttu-id="88742-121">Bu örnek ayrıca kalıcılığını etkinleştirmek nasıl gösteren bir <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="88742-121">This sample also demonstrates how to turn on persistence for a <xref:System.Activities.WorkflowApplication>.</span></span> <span data-ttu-id="88742-122">Bu belirli bir örnek için biz, iş akışı veri kalıcılığı veritabanına süresi dolacak şekilde Zamanlayıcı için beklenirken boşta kalma süresi sırasında bellekten kaldırılacak dayanıklı zamanlayıcılar kullanılarak.</span><span class="sxs-lookup"><span data-stu-id="88742-122">For this particular sample, we will be using durable timers in which the workflow data will be unloaded into the persistence database during the idle time while waiting for timer to expire.</span></span> <span data-ttu-id="88742-123">Bu uygulama, diğer Kalıcılık eylemler için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="88742-123">This implementation can also be used for other persistence actions.</span></span> <span data-ttu-id="88742-124">Bu örnek, iş akışı örnekleri için veri kalıcı hale getirmek için örnek deposuna oluşturma ve SQL Server ile kalıcılığı bağlantı dizesini ayarlamak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="88742-124">This sample shows how to set up the persistence connection string with SQL Server, and how to create the instance store in order to persist the data for workflow instances.</span></span> <span data-ttu-id="88742-125">Mantığı, iş akışı örneği runnable sağlayan bir olay tetiklenir sonra iş akışını sürdürmek nasıl sağlanır.</span><span class="sxs-lookup"><span data-stu-id="88742-125">Logic is provided on how to resume the workflow once an event is raised which makes the workflow instance runnable.</span></span>  
  
 <span data-ttu-id="88742-126">Bu örnek adım gibi yerleşik gecikme başlar ve tamamlar, hangi sırayla zaman bir e-posta gönderilmesine neden olur görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="88742-126">As you step through this sample, you will see the time in which the built-in delay begins and completes, which in turn will cause an email message to be sent.</span></span> <span data-ttu-id="88742-127">Buradan, AbsoluteDelay etkinlik belirtilen kadar durdurulur <xref:System.DateTime> (veya 0 saniye varsa <xref:System.DateTime> süresi doldu) hangi sırayla gönderecek sona erme bağlı bir e-posta çıkışı.</span><span class="sxs-lookup"><span data-stu-id="88742-127">From there, the AbsoluteDelay activity will halt until a specified <xref:System.DateTime> (or 0 seconds if the <xref:System.DateTime> has expired) which in turn will send out an email upon expiration.</span></span> <span data-ttu-id="88742-128">Bu iki farklı kullanım yerleşik gösterir <xref:System.Activities.Statements.Delay> AbsoluteDelay aktivite kullanarak karşı işlevselliği.</span><span class="sxs-lookup"><span data-stu-id="88742-128">This will show the two different use cases of the built-in <xref:System.Activities.Statements.Delay> functionality versus using an AbsoluteDelay activity.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="88742-129">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="88742-129">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="88742-130">SQL Server Express (veya sonrası) makinenize yüklü olduğundan emin olun</span><span class="sxs-lookup"><span data-stu-id="88742-130">Ensure you have SQL Server Express (or higher) installed on your machine</span></span>  
  
2.  <span data-ttu-id="88742-131">(WF/Basic/Services/AbsoluteDelay/CS) Setup.cmd Çalıştır bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi AbsoluteDelaySampleDB veritabanı oluşturma, Kalıcılık şema oluşturun ve kalıcılığı mantığı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="88742-131">Run setup.cmd (from WF/Basic/Services/AbsoluteDelay/CS) in a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt to create the AbsoluteDelaySampleDB database, create the persistence schema and create the persistence logic.</span></span>  
  
3.  <span data-ttu-id="88742-132">Çözümde açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="88742-132">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
4.  <span data-ttu-id="88742-133">Gecikme etkinliğinde süreyi belirtin.</span><span class="sxs-lookup"><span data-stu-id="88742-133">Specify the Duration in the Delay activity.</span></span>  
  
5.  <span data-ttu-id="88742-134">ExpirationTime AbsoluteDelay etkinliğinde belirtin.</span><span class="sxs-lookup"><span data-stu-id="88742-134">Specify the ExpirationTime in the AbsoluteDelay activity.</span></span>  
  
6.  <span data-ttu-id="88742-135">SendMail etkinliğinde SendMailTo, SendMailFrom, SendMailSubject, SendMailBody ve SmtpHost alanları güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="88742-135">Update the SendMailTo, SendMailFrom, SendMailSubject, SendMailBody, and SmtpHost fields in the SendMail activity.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="88742-136">Geçerli bir SMTP konak girmezseniz, uygulama bir SMTP özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="88742-136">If you do not enter a valid SMTP host, the application will throw a SMTP exception.</span></span>  
  
7.  <span data-ttu-id="88742-137">Seçerek çözümü derleme **yapı**, **yapı çözümü**.</span><span class="sxs-lookup"><span data-stu-id="88742-137">Build the solution by selecting **Build**, **Build Solution**.</span></span>  
  
8.  <span data-ttu-id="88742-138">Tuşlarına basarak çözümü çalıştırın **F5**.</span><span class="sxs-lookup"><span data-stu-id="88742-138">Run the solution by pressing **F5**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="88742-139">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="88742-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="88742-140">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="88742-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="88742-141">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="88742-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="88742-142">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="88742-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\AbsoluteDelay`
