---
description: 'Daha fazla bilgi edinin: yer Işaretleri'
title: Yer işaretleri-WF
ms.date: 03/30/2017
ms.assetid: 9b51a346-09ae-455c-a70a-e2264ddeb9e2
ms.openlocfilehash: b4f0e68e0868ecd4eb97673ff6c09ee8c806cf43
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787935"
---
# <a name="bookmarks"></a><span data-ttu-id="5253f-103">Yer işaretleri</span><span class="sxs-lookup"><span data-stu-id="5253f-103">Bookmarks</span></span>

<span data-ttu-id="5253f-104">Yer işaretleri, bir etkinliğin bir iş akışı iş parçacığına sahip olmadan giriş için büyük bir süre beklemesini sağlayan mekanizmadır.</span><span class="sxs-lookup"><span data-stu-id="5253f-104">Bookmarks are the mechanism that enables an activity to passively wait for input without holding onto a workflow thread.</span></span> <span data-ttu-id="5253f-105">Bir etkinlik, Stimulus için beklediğini işaret eder, bir yer işareti oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="5253f-105">When an activity signals that it is waiting for stimulus, it can create a bookmark.</span></span> <span data-ttu-id="5253f-106">Bu, şu anda yürütülmekte olan Yöntem (tarafından oluşturulan) tarafından döndürülen çalışma zamanına etkinlik yürütmenin tamamlanma kabul edilmesi gerektiğini gösterir <xref:System.Activities.Bookmark> .</span><span class="sxs-lookup"><span data-stu-id="5253f-106">This indicates to the runtime that the activity’s execution should not be considered complete even when the currently executing method (which created the <xref:System.Activities.Bookmark>) returns.</span></span>  
  
## <a name="bookmark-basics"></a><span data-ttu-id="5253f-107">Yer işareti temelleri</span><span class="sxs-lookup"><span data-stu-id="5253f-107">Bookmark Basics</span></span>  

 <span data-ttu-id="5253f-108">Bir <xref:System.Activities.Bookmark> iş akışı örneği içinde yürütmenin sürdürülebilecek (ve hangi girişin teslim edileceği) bir noktayı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5253f-108">A <xref:System.Activities.Bookmark> represents a point at which execution can be resumed (and through which input can be delivered) within a workflow instance.</span></span> <span data-ttu-id="5253f-109">Genellikle, bir <xref:System.Activities.Bookmark> ad ve dış (konak veya uzantı) kodu, yer işaretinin ilgili verilerle sürdürülmesinden sorumludur.</span><span class="sxs-lookup"><span data-stu-id="5253f-109">Typically, a <xref:System.Activities.Bookmark> is given a name and external (host or extension) code is responsible for resuming the bookmark with relevant data.</span></span> <span data-ttu-id="5253f-110">Bir <xref:System.Activities.Bookmark> devam edildiğinde, iş akışı çalışma zamanı, <xref:System.Activities.BookmarkCallback> oluşturma sırasında ilişkili temsilciyi zamanlar <xref:System.Activities.Bookmark> .</span><span class="sxs-lookup"><span data-stu-id="5253f-110">When a <xref:System.Activities.Bookmark> is resumed, the workflow runtime schedules the <xref:System.Activities.BookmarkCallback> delegate that was associated with that <xref:System.Activities.Bookmark> at the time of its creation.</span></span>  
  
## <a name="bookmark-options"></a><span data-ttu-id="5253f-111">Yer işareti seçenekleri</span><span class="sxs-lookup"><span data-stu-id="5253f-111">Bookmark Options</span></span>  

 <span data-ttu-id="5253f-112"><xref:System.Activities.BookmarkOptions>Sınıf, oluşturulmakta olan türünü belirtir <xref:System.Activities.Bookmark> .</span><span class="sxs-lookup"><span data-stu-id="5253f-112">The <xref:System.Activities.BookmarkOptions> class specifies the type of <xref:System.Activities.Bookmark> being created.</span></span> <span data-ttu-id="5253f-113">Birbirini dışlayan olası olmayan değerler <xref:System.Activities.BookmarkOptions.None> , ve ' dir <xref:System.Activities.BookmarkOptions.MultipleResume> <xref:System.Activities.BookmarkOptions.NonBlocking> .</span><span class="sxs-lookup"><span data-stu-id="5253f-113">The possible non mutually-exclusive values are <xref:System.Activities.BookmarkOptions.None>, <xref:System.Activities.BookmarkOptions.MultipleResume>, and <xref:System.Activities.BookmarkOptions.NonBlocking>.</span></span> <span data-ttu-id="5253f-114"><xref:System.Activities.BookmarkOptions.None> <xref:System.Activities.Bookmark> Tam olarak bir kez sürdürülmeleri beklenen, oluşturma işlemi varsayılan olan ' ı kullanın.</span><span class="sxs-lookup"><span data-stu-id="5253f-114">Use <xref:System.Activities.BookmarkOptions.None>, the default, when creating a <xref:System.Activities.Bookmark> that is expected to be resumed exactly once.</span></span> <span data-ttu-id="5253f-115"><xref:System.Activities.BookmarkOptions.MultipleResume> <xref:System.Activities.Bookmark> Birden çok kez devam ettirilebilecek bir oluşturma sırasında kullanın.</span><span class="sxs-lookup"><span data-stu-id="5253f-115">Use <xref:System.Activities.BookmarkOptions.MultipleResume> when creating a <xref:System.Activities.Bookmark> that can be resumed multiple times.</span></span> <span data-ttu-id="5253f-116"><xref:System.Activities.BookmarkOptions.NonBlocking> <xref:System.Activities.Bookmark> Hiçbir zaman sürdürülmeyebilir bir oluşturma sırasında kullanın.</span><span class="sxs-lookup"><span data-stu-id="5253f-116">Use <xref:System.Activities.BookmarkOptions.NonBlocking> when creating a <xref:System.Activities.Bookmark> that might never be resumed.</span></span> <span data-ttu-id="5253f-117">Varsayılan değer kullanılarak oluşturulan yer işaretlerinin aksine <xref:System.Activities.BookmarkOptions> , <xref:System.Activities.BookmarkOptions.NonBlocking> yer işaretleri bir etkinliğin tamamlanmasını engellemez.</span><span class="sxs-lookup"><span data-stu-id="5253f-117">Unlike bookmarks created using the default <xref:System.Activities.BookmarkOptions>, <xref:System.Activities.BookmarkOptions.NonBlocking> bookmarks do not prevent an activity from completing.</span></span>  
  
## <a name="bookmark-resumption"></a><span data-ttu-id="5253f-118">Yer işareti sürdürme</span><span class="sxs-lookup"><span data-stu-id="5253f-118">Bookmark Resumption</span></span>  

 <span data-ttu-id="5253f-119">Yer işaretleri, aşırı yüklerden birini kullanan bir iş akışı dışındaki kodla devam edebilir <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> .</span><span class="sxs-lookup"><span data-stu-id="5253f-119">Bookmarks can be resumed by code outside of a workflow using one of the <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> overloads.</span></span> <span data-ttu-id="5253f-120">Bu örnekte, bir `ReadLine` etkinlik oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5253f-120">In this example, a `ReadLine` activity is created.</span></span> <span data-ttu-id="5253f-121">Yürütüldüğünde, `ReadLine` etkinlik bir oluşturur, bir <xref:System.Activities.Bookmark> geri çağırma kaydeder ve <xref:System.Activities.Bookmark> devam etmek için bekler.</span><span class="sxs-lookup"><span data-stu-id="5253f-121">When executed, the `ReadLine` activity creates a <xref:System.Activities.Bookmark>, registers a callback, and then waits for the <xref:System.Activities.Bookmark> to be resumed.</span></span> <span data-ttu-id="5253f-122">Devam edildiğinde `ReadLine` etkinlik, ile geçilen verileri <xref:System.Activities.Bookmark> <xref:System.Activities.Activity%601.Result%2A> bağımsız değişkenine atar.</span><span class="sxs-lookup"><span data-stu-id="5253f-122">When it is resumed, the `ReadLine` activity assigns the data that was passed with the <xref:System.Activities.Bookmark> to its <xref:System.Activities.Activity%601.Result%2A> argument.</span></span>  
  
```csharp  
public sealed class ReadLine : NativeActivity<string>  
{  
    [RequiredArgument]  
    public  InArgument<string> BookmarkName { get; set; }  
  
    protected override void Execute(NativeActivityContext context)  
    {  
        // Create a Bookmark and wait for it to be resumed.  
        context.CreateBookmark(BookmarkName.Get(context),
            new BookmarkCallback(OnResumeBookmark));  
    }  
  
    // NativeActivity derived activities that do asynchronous operations by calling
    // one of the CreateBookmark overloads defined on System.Activities.NativeActivityContext
    // must override the CanInduceIdle property and return true.  
    protected override bool CanInduceIdle  
    {  
        get { return true; }  
    }  
  
    public void OnResumeBookmark(NativeActivityContext context, Bookmark bookmark, object obj)  
    {  
        // When the Bookmark is resumed, assign its value to  
        // the Result argument.  
        Result.Set(context, (string)obj);  
    }  
}  
```  
  
 <span data-ttu-id="5253f-123">Bu örnekte, `ReadLine` etkinliğin Kullanıcı adını toplayıp konsol penceresinde görüntülemesi için etkinliğini kullanan bir iş akışı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5253f-123">In this example, a workflow is created that uses the `ReadLine` activity to gather the user’s name and display it to the console window.</span></span> <span data-ttu-id="5253f-124">Ana bilgisayar uygulaması, giriş toplama işini gerçekleştirir ve devam ederek iş akışına geçirir <xref:System.Activities.Bookmark> .</span><span class="sxs-lookup"><span data-stu-id="5253f-124">The host application performs the actual work of gathering the input and passes it to the workflow by resuming the <xref:System.Activities.Bookmark>.</span></span>  
  
```csharp  
Variable<string> name = new Variable<string>  
{  
    Name = "name"  
};  
  
Activity wf = new Sequence  
{  
    Variables =  
    {  
        name  
    },  
    Activities =  
    {  
        new WriteLine()  
        {  
            Text = "What is your name?"  
        },  
        new ReadLine()  
        {  
            BookmarkName = "UserName",  
            Result = name  
        },  
        new WriteLine()  
        {  
            Text = new InArgument<string>((env) => "Hello, " + name.Get(env))  
        }  
    }  
};  
  
AutoResetEvent syncEvent = new AutoResetEvent(false);  
  
// Create the WorkflowApplication using the desired  
// workflow definition.  
WorkflowApplication wfApp = new WorkflowApplication(wf);  
  
// Handle the desired lifecycle events.  
wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
{  
    // Signal the host that the workflow is complete.  
    syncEvent.Set();  
};  
  
// Start the workflow.  
wfApp.Run();  
  
// Collect the user's name and resume the bookmark.  
// Bookmark resumption only occurs when the workflow  
// is idle. If a call to ResumeBookmark is made and the workflow  
// is not idle, ResumeBookmark blocks until the workflow becomes  
// idle before resuming the bookmark.  
wfApp.ResumeBookmark("UserName", Console.ReadLine());  
  
// Wait for Completed to arrive and signal that  
// the workflow is complete.  
syncEvent.WaitOne();  
```  
  
 <span data-ttu-id="5253f-125">`ReadLine`Etkinlik yürütüldüğünde, <xref:System.Activities.Bookmark> adlandırılmış bir adı oluşturur `UserName` ve sonra yer işaretinin sürdürülmesini bekler.</span><span class="sxs-lookup"><span data-stu-id="5253f-125">When the `ReadLine` activity is executed, it creates a <xref:System.Activities.Bookmark> named `UserName` and then waits for the bookmark to be resumed.</span></span> <span data-ttu-id="5253f-126">Konak, istenen verileri toplar ve ardından devam ettirir <xref:System.Activities.Bookmark> .</span><span class="sxs-lookup"><span data-stu-id="5253f-126">The host collects the desired data and then resumes the <xref:System.Activities.Bookmark>.</span></span> <span data-ttu-id="5253f-127">İş akışı devam eder, adı görüntüler ve sonra tamamlar.</span><span class="sxs-lookup"><span data-stu-id="5253f-127">The workflow resumes, displays the name, and then completes.</span></span> <span data-ttu-id="5253f-128">Yer işaretinin sürdürülmeye devam ettiğine ilişkin hiçbir eşitleme kodu gerekmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5253f-128">Note that no synchronization code is required with regard to resuming the bookmark.</span></span> <span data-ttu-id="5253f-129"><xref:System.Activities.Bookmark>Yalnızca iş akışı boşta kaldığında devam edebilir ve iş akışı boşta değilse <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> iş akışı boşta olana kadar blokları çağırır.</span><span class="sxs-lookup"><span data-stu-id="5253f-129">A <xref:System.Activities.Bookmark> can only be resumed when the workflow is idle, and if the workflow is not idle, the call to <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> blocks until the workflow becomes idle.</span></span>  
  
## <a name="bookmark-resumption-result"></a><span data-ttu-id="5253f-130">Yer işareti sürdürme sonucu</span><span class="sxs-lookup"><span data-stu-id="5253f-130">Bookmark Resumption Result</span></span>  

 <span data-ttu-id="5253f-131"><xref:System.Activities.WorkflowApplication.ResumeBookmark%2A><xref:System.Activities.BookmarkResumptionResult>Bookmark sürdürme isteğinin sonuçlarını göstermek için bir sabit listesi değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="5253f-131"><xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> returns a <xref:System.Activities.BookmarkResumptionResult> enumeration value to indicate the results of the bookmark resumption request.</span></span> <span data-ttu-id="5253f-132">Olası dönüş değerleri <xref:System.Activities.BookmarkResumptionResult.Success> , ve ' dir <xref:System.Activities.BookmarkResumptionResult.NotReady> <xref:System.Activities.BookmarkResumptionResult.NotFound> .</span><span class="sxs-lookup"><span data-stu-id="5253f-132">The possible return values are <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady>, and <xref:System.Activities.BookmarkResumptionResult.NotFound>.</span></span> <span data-ttu-id="5253f-133">Konaklar ve uzantılar, devam etmek için bu değeri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="5253f-133">Hosts and extensions can use this value to determine how to proceed.</span></span>
