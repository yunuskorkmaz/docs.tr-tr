---
title: Yer işaretleri-WF
ms.date: 03/30/2017
ms.assetid: 9b51a346-09ae-455c-a70a-e2264ddeb9e2
ms.openlocfilehash: a15a28cc39a4227765c238a6f2b86c72197f1a39
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868923"
---
# <a name="bookmarks"></a><span data-ttu-id="0fc11-102">Yer İşaretleri</span><span class="sxs-lookup"><span data-stu-id="0fc11-102">Bookmarks</span></span>
<span data-ttu-id="0fc11-103">Yer işaretleri, bir etkinliğin bir iş akışı iş parçacığına sahip olmadan giriş için büyük bir süre beklemesini sağlayan mekanizmadır.</span><span class="sxs-lookup"><span data-stu-id="0fc11-103">Bookmarks are the mechanism that enables an activity to passively wait for input without holding onto a workflow thread.</span></span> <span data-ttu-id="0fc11-104">Bir etkinlik, Stimulus için beklediğini işaret eder, bir yer işareti oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="0fc11-104">When an activity signals that it is waiting for stimulus, it can create a bookmark.</span></span> <span data-ttu-id="0fc11-105">Bu, şu anda yürütülmekte olan Yöntem (tarafından oluşturulan <xref:System.Activities.Bookmark>) tarafından döndürülen çalışma zamanına etkinlik yürütmenin tamamlanma kabul edilmesi gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0fc11-105">This indicates to the runtime that the activity’s execution should not be considered complete even when the currently executing method (which created the <xref:System.Activities.Bookmark>) returns.</span></span>  
  
## <a name="bookmark-basics"></a><span data-ttu-id="0fc11-106">Yer işareti temelleri</span><span class="sxs-lookup"><span data-stu-id="0fc11-106">Bookmark Basics</span></span>  
 <span data-ttu-id="0fc11-107">Bir <xref:System.Activities.Bookmark> iş akışı örneği içinde yürütmenin sürdürülebilecek (ve hangi girişin teslim edileceği) bir noktayı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0fc11-107">A <xref:System.Activities.Bookmark> represents a point at which execution can be resumed (and through which input can be delivered) within a workflow instance.</span></span> <span data-ttu-id="0fc11-108">Genellikle, bir <xref:System.Activities.Bookmark> ad ve dış (konak veya uzantı) kodu, yer işaretinin ilgili verilerle sürdürülmesinden sorumludur.</span><span class="sxs-lookup"><span data-stu-id="0fc11-108">Typically, a <xref:System.Activities.Bookmark> is given a name and external (host or extension) code is responsible for resuming the bookmark with relevant data.</span></span> <span data-ttu-id="0fc11-109">Bir <xref:System.Activities.Bookmark> devam edildiğinde, iş akışı çalışma zamanı, oluşturma <xref:System.Activities.BookmarkCallback> sırasında ilişkili <xref:System.Activities.Bookmark> temsilciyi zamanlar.</span><span class="sxs-lookup"><span data-stu-id="0fc11-109">When a <xref:System.Activities.Bookmark> is resumed, the workflow runtime schedules the <xref:System.Activities.BookmarkCallback> delegate that was associated with that <xref:System.Activities.Bookmark> at the time of its creation.</span></span>  
  
## <a name="bookmark-options"></a><span data-ttu-id="0fc11-110">Yer işareti seçenekleri</span><span class="sxs-lookup"><span data-stu-id="0fc11-110">Bookmark Options</span></span>  
 <span data-ttu-id="0fc11-111">Sınıf, oluşturulmakta <xref:System.Activities.Bookmark> olan türünü belirtir. <xref:System.Activities.BookmarkOptions></span><span class="sxs-lookup"><span data-stu-id="0fc11-111">The <xref:System.Activities.BookmarkOptions> class specifies the type of <xref:System.Activities.Bookmark> being created.</span></span> <span data-ttu-id="0fc11-112">Birbirini dışlayan olası olmayan değerler, <xref:System.Activities.BookmarkOptions.None> <xref:System.Activities.BookmarkOptions.MultipleResume>ve <xref:System.Activities.BookmarkOptions.NonBlocking>' dir.</span><span class="sxs-lookup"><span data-stu-id="0fc11-112">The possible non mutually-exclusive values are <xref:System.Activities.BookmarkOptions.None>, <xref:System.Activities.BookmarkOptions.MultipleResume>, and <xref:System.Activities.BookmarkOptions.NonBlocking>.</span></span> <span data-ttu-id="0fc11-113">Tam <xref:System.Activities.BookmarkOptions.None>olarak bir <xref:System.Activities.Bookmark> kez sürdürülmeleri beklenen, oluşturma işlemi varsayılan olan ' ı kullanın.</span><span class="sxs-lookup"><span data-stu-id="0fc11-113">Use <xref:System.Activities.BookmarkOptions.None>, the default, when creating a <xref:System.Activities.Bookmark> that is expected to be resumed exactly once.</span></span> <span data-ttu-id="0fc11-114">Birden <xref:System.Activities.BookmarkOptions.MultipleResume> çok kez devam <xref:System.Activities.Bookmark> ettirilebilecek bir oluşturma sırasında kullanın.</span><span class="sxs-lookup"><span data-stu-id="0fc11-114">Use <xref:System.Activities.BookmarkOptions.MultipleResume> when creating a <xref:System.Activities.Bookmark> that can be resumed multiple times.</span></span> <span data-ttu-id="0fc11-115">Hiçbir <xref:System.Activities.BookmarkOptions.NonBlocking> zaman sürdürülmeyebilir <xref:System.Activities.Bookmark> bir oluşturma sırasında kullanın.</span><span class="sxs-lookup"><span data-stu-id="0fc11-115">Use <xref:System.Activities.BookmarkOptions.NonBlocking> when creating a <xref:System.Activities.Bookmark> that might never be resumed.</span></span> <span data-ttu-id="0fc11-116">Varsayılan değer <xref:System.Activities.BookmarkOptions>kullanılarak oluşturulan yer işaretlerinin aksine <xref:System.Activities.BookmarkOptions.NonBlocking> , yer işaretleri bir etkinliğin tamamlanmasını engellemez.</span><span class="sxs-lookup"><span data-stu-id="0fc11-116">Unlike bookmarks created using the default <xref:System.Activities.BookmarkOptions>, <xref:System.Activities.BookmarkOptions.NonBlocking> bookmarks do not prevent an activity from completing.</span></span>  
  
## <a name="bookmark-resumption"></a><span data-ttu-id="0fc11-117">Yer işareti sürdürme</span><span class="sxs-lookup"><span data-stu-id="0fc11-117">Bookmark Resumption</span></span>  
 <span data-ttu-id="0fc11-118">Yer işaretleri, <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> aşırı yüklerden birini kullanan bir iş akışı dışındaki kodla devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="0fc11-118">Bookmarks can be resumed by code outside of a workflow using one of the <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> overloads.</span></span> <span data-ttu-id="0fc11-119">Bu örnekte, bir `ReadLine` etkinlik oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0fc11-119">In this example, a `ReadLine` activity is created.</span></span> <span data-ttu-id="0fc11-120">Yürütüldüğünde `ReadLine` , etkinlik bir <xref:System.Activities.Bookmark>oluşturur, bir geri çağırma kaydeder <xref:System.Activities.Bookmark> ve devam etmek için bekler.</span><span class="sxs-lookup"><span data-stu-id="0fc11-120">When executed, the `ReadLine` activity creates a <xref:System.Activities.Bookmark>, registers a callback, and then waits for the <xref:System.Activities.Bookmark> to be resumed.</span></span> <span data-ttu-id="0fc11-121">Devam `ReadLine` edildiğinde etkinlik <xref:System.Activities.Bookmark> ,<xref:System.Activities.Activity%601.Result%2A> ile geçilen verileri bağımsız değişkenine atar.</span><span class="sxs-lookup"><span data-stu-id="0fc11-121">When it is resumed, the `ReadLine` activity assigns the data that was passed with the <xref:System.Activities.Bookmark> to its <xref:System.Activities.Activity%601.Result%2A> argument.</span></span>  
  
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
  
 <span data-ttu-id="0fc11-122">Bu örnekte, `ReadLine` etkinliğin Kullanıcı adını toplayıp konsol penceresinde görüntülemesi için etkinliğini kullanan bir iş akışı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0fc11-122">In this example, a workflow is created that uses the `ReadLine` activity to gather the user’s name and display it to the console window.</span></span> <span data-ttu-id="0fc11-123">Ana bilgisayar uygulaması, <xref:System.Activities.Bookmark>giriş toplama işini gerçekleştirir ve devam ederek iş akışına geçirir.</span><span class="sxs-lookup"><span data-stu-id="0fc11-123">The host application performs the actual work of gathering the input and passes it to the workflow by resuming the <xref:System.Activities.Bookmark>.</span></span>  
  
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
  
 <span data-ttu-id="0fc11-124">Etkinlik yürütüldüğünde, adlandırılmış bir <xref:System.Activities.Bookmark> adı `UserName` oluşturur ve sonra yer işaretinin sürdürülmesini bekler. `ReadLine`</span><span class="sxs-lookup"><span data-stu-id="0fc11-124">When the `ReadLine` activity is executed, it creates a <xref:System.Activities.Bookmark> named `UserName` and then waits for the bookmark to be resumed.</span></span> <span data-ttu-id="0fc11-125">Konak, istenen verileri toplar ve ardından devam ettirir <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="0fc11-125">The host collects the desired data and then resumes the <xref:System.Activities.Bookmark>.</span></span> <span data-ttu-id="0fc11-126">İş akışı devam eder, adı görüntüler ve sonra tamamlar.</span><span class="sxs-lookup"><span data-stu-id="0fc11-126">The workflow resumes, displays the name, and then completes.</span></span> <span data-ttu-id="0fc11-127">Yer işaretinin sürdürülmeye devam ettiğine ilişkin hiçbir eşitleme kodu gerekmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0fc11-127">Note that no synchronization code is required with regard to resuming the bookmark.</span></span> <span data-ttu-id="0fc11-128">Yalnızca iş akışı boşta kaldığında devam <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> edebilirveişakışıboştadeğilseişakışıboştaolanakadarbloklarıçağırır.<xref:System.Activities.Bookmark></span><span class="sxs-lookup"><span data-stu-id="0fc11-128">A <xref:System.Activities.Bookmark> can only be resumed when the workflow is idle, and if the workflow is not idle, the call to <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> blocks until the workflow becomes idle.</span></span>  
  
## <a name="bookmark-resumption-result"></a><span data-ttu-id="0fc11-129">Yer işareti sürdürme sonucu</span><span class="sxs-lookup"><span data-stu-id="0fc11-129">Bookmark Resumption Result</span></span>  
 <span data-ttu-id="0fc11-130"><xref:System.Activities.WorkflowApplication.ResumeBookmark%2A>Bookmark sürdürme <xref:System.Activities.BookmarkResumptionResult> isteğinin sonuçlarını göstermek için bir sabit listesi değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="0fc11-130"><xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> returns a <xref:System.Activities.BookmarkResumptionResult> enumeration value to indicate the results of the bookmark resumption request.</span></span> <span data-ttu-id="0fc11-131">Olası dönüş değerleri, <xref:System.Activities.BookmarkResumptionResult.Success> <xref:System.Activities.BookmarkResumptionResult.NotReady>ve <xref:System.Activities.BookmarkResumptionResult.NotFound>' dir.</span><span class="sxs-lookup"><span data-stu-id="0fc11-131">The possible return values are <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady>, and <xref:System.Activities.BookmarkResumptionResult.NotFound>.</span></span> <span data-ttu-id="0fc11-132">Konaklar ve uzantılar, devam etmek için bu değeri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="0fc11-132">Hosts and extensions can use this value to determine how to proceed.</span></span>
