---
title: Yer Imleri - WF
ms.date: 03/30/2017
ms.assetid: 9b51a346-09ae-455c-a70a-e2264ddeb9e2
ms.openlocfilehash: c5bd8130ee623599e80014777baf92986c3b6969
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183017"
---
# <a name="bookmarks"></a><span data-ttu-id="07e80-102">Yer İşaretleri</span><span class="sxs-lookup"><span data-stu-id="07e80-102">Bookmarks</span></span>
<span data-ttu-id="07e80-103">Yer imleri, bir etkinliğin iş akışı iş parçacığına tutunmadan girişi pasif olarak beklemesini sağlayan mekanizmadır.</span><span class="sxs-lookup"><span data-stu-id="07e80-103">Bookmarks are the mechanism that enables an activity to passively wait for input without holding onto a workflow thread.</span></span> <span data-ttu-id="07e80-104">Bir etkinlik uyarıcı beklediğini niçin işaret verdiğinde, bir yer imi oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="07e80-104">When an activity signals that it is waiting for stimulus, it can create a bookmark.</span></span> <span data-ttu-id="07e80-105">Bu, çalışma süresine, şu anda yürütülen yöntem (oluşturdu) <xref:System.Activities.Bookmark>döndürülmüş olsa bile etkinliğin yürütülmesinin tamamlanmış olarak kabul edilmemesi gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="07e80-105">This indicates to the runtime that the activity’s execution should not be considered complete even when the currently executing method (which created the <xref:System.Activities.Bookmark>) returns.</span></span>  
  
## <a name="bookmark-basics"></a><span data-ttu-id="07e80-106">Yer Imi Temelleri</span><span class="sxs-lookup"><span data-stu-id="07e80-106">Bookmark Basics</span></span>  
 <span data-ttu-id="07e80-107">A, <xref:System.Activities.Bookmark> iş akışı örneği içinde yürütmenin sürdürülebileceği (ve girişin teslim edilebildiği) bir noktayı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="07e80-107">A <xref:System.Activities.Bookmark> represents a point at which execution can be resumed (and through which input can be delivered) within a workflow instance.</span></span> <span data-ttu-id="07e80-108">Genellikle, a <xref:System.Activities.Bookmark> bir ad verilir ve dış (ana bilgisayar veya uzantı) kodu ilgili verilerle yer imini devam ından sorumludur.</span><span class="sxs-lookup"><span data-stu-id="07e80-108">Typically, a <xref:System.Activities.Bookmark> is given a name and external (host or extension) code is responsible for resuming the bookmark with relevant data.</span></span> <span data-ttu-id="07e80-109">A <xref:System.Activities.Bookmark> başlatıldığında, iş akışı çalışma zamanı, <xref:System.Activities.BookmarkCallback> oluşturuldurduğu <xref:System.Activities.Bookmark> anda onunla ilişkili olan temsilciyi zamanlar.</span><span class="sxs-lookup"><span data-stu-id="07e80-109">When a <xref:System.Activities.Bookmark> is resumed, the workflow runtime schedules the <xref:System.Activities.BookmarkCallback> delegate that was associated with that <xref:System.Activities.Bookmark> at the time of its creation.</span></span>  
  
## <a name="bookmark-options"></a><span data-ttu-id="07e80-110">Yer Imi Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="07e80-110">Bookmark Options</span></span>  
 <span data-ttu-id="07e80-111">Sınıf <xref:System.Activities.BookmarkOptions> oluşturulan türü <xref:System.Activities.Bookmark> belirtir.</span><span class="sxs-lookup"><span data-stu-id="07e80-111">The <xref:System.Activities.BookmarkOptions> class specifies the type of <xref:System.Activities.Bookmark> being created.</span></span> <span data-ttu-id="07e80-112">Olası olmayan birbirini dışlamayan <xref:System.Activities.BookmarkOptions.None>değerler <xref:System.Activities.BookmarkOptions.MultipleResume>, <xref:System.Activities.BookmarkOptions.NonBlocking>ve .</span><span class="sxs-lookup"><span data-stu-id="07e80-112">The possible non mutually-exclusive values are <xref:System.Activities.BookmarkOptions.None>, <xref:System.Activities.BookmarkOptions.MultipleResume>, and <xref:System.Activities.BookmarkOptions.NonBlocking>.</span></span> <span data-ttu-id="07e80-113">Tam <xref:System.Activities.BookmarkOptions.None>olarak bir kez <xref:System.Activities.Bookmark> devam etmesi beklenen bir oluşturma yaparken varsayılan kullanın.</span><span class="sxs-lookup"><span data-stu-id="07e80-113">Use <xref:System.Activities.BookmarkOptions.None>, the default, when creating a <xref:System.Activities.Bookmark> that is expected to be resumed exactly once.</span></span> <span data-ttu-id="07e80-114">Birden <xref:System.Activities.BookmarkOptions.MultipleResume> çok <xref:System.Activities.Bookmark> kez yeniden başlatılabilen bir oluşturma yaparken kullanın.</span><span class="sxs-lookup"><span data-stu-id="07e80-114">Use <xref:System.Activities.BookmarkOptions.MultipleResume> when creating a <xref:System.Activities.Bookmark> that can be resumed multiple times.</span></span> <span data-ttu-id="07e80-115">Hiçbir <xref:System.Activities.BookmarkOptions.NonBlocking> zaman <xref:System.Activities.Bookmark> başlatılmayan bir şey oluştururken kullanın.</span><span class="sxs-lookup"><span data-stu-id="07e80-115">Use <xref:System.Activities.BookmarkOptions.NonBlocking> when creating a <xref:System.Activities.Bookmark> that might never be resumed.</span></span> <span data-ttu-id="07e80-116">Varsayılan <xref:System.Activities.BookmarkOptions>kullanılarak oluşturulan yer <xref:System.Activities.BookmarkOptions.NonBlocking> imlerinden farklı olarak, yer imleri bir etkinliğin tamamlanmasını engellemez.</span><span class="sxs-lookup"><span data-stu-id="07e80-116">Unlike bookmarks created using the default <xref:System.Activities.BookmarkOptions>, <xref:System.Activities.BookmarkOptions.NonBlocking> bookmarks do not prevent an activity from completing.</span></span>  
  
## <a name="bookmark-resumption"></a><span data-ttu-id="07e80-117">Yer Ii Devamı</span><span class="sxs-lookup"><span data-stu-id="07e80-117">Bookmark Resumption</span></span>  
 <span data-ttu-id="07e80-118">Yer <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> imleri, aşırı yüklerden birini kullanarak iş akışı dışında kodla yeniden başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="07e80-118">Bookmarks can be resumed by code outside of a workflow using one of the <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> overloads.</span></span> <span data-ttu-id="07e80-119">Bu örnekte, `ReadLine` bir etkinlik oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="07e80-119">In this example, a `ReadLine` activity is created.</span></span> <span data-ttu-id="07e80-120">Yürütüldüğünde, `ReadLine` etkinlik bir <xref:System.Activities.Bookmark>, geri arama kaydeder ve sonra <xref:System.Activities.Bookmark> devam etmesini bekler.</span><span class="sxs-lookup"><span data-stu-id="07e80-120">When executed, the `ReadLine` activity creates a <xref:System.Activities.Bookmark>, registers a callback, and then waits for the <xref:System.Activities.Bookmark> to be resumed.</span></span> <span data-ttu-id="07e80-121">Devam ettiğinde, `ReadLine` etkinlik <xref:System.Activities.Bookmark> <xref:System.Activities.Activity%601.Result%2A> bağımsız değişkeniyle geçirilen verileri atar.</span><span class="sxs-lookup"><span data-stu-id="07e80-121">When it is resumed, the `ReadLine` activity assigns the data that was passed with the <xref:System.Activities.Bookmark> to its <xref:System.Activities.Activity%601.Result%2A> argument.</span></span>  
  
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
  
 <span data-ttu-id="07e80-122">Bu örnekte, kullanıcının `ReadLine` adını toplamak ve konsol penceresine görüntülemek için etkinliği kullanan bir iş akışı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="07e80-122">In this example, a workflow is created that uses the `ReadLine` activity to gather the user’s name and display it to the console window.</span></span> <span data-ttu-id="07e80-123">Ana bilgisayar uygulaması, girdiyi toplama fiili işini gerçekleştirir ve <xref:System.Activities.Bookmark>devam ederek iş akışına aktarın.</span><span class="sxs-lookup"><span data-stu-id="07e80-123">The host application performs the actual work of gathering the input and passes it to the workflow by resuming the <xref:System.Activities.Bookmark>.</span></span>  
  
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
  
 <span data-ttu-id="07e80-124">`ReadLine` Etkinlik yürütüldüğünde, bir <xref:System.Activities.Bookmark> ad `UserName` ve ardından yer işaretinin devam etmesini bekler.</span><span class="sxs-lookup"><span data-stu-id="07e80-124">When the `ReadLine` activity is executed, it creates a <xref:System.Activities.Bookmark> named `UserName` and then waits for the bookmark to be resumed.</span></span> <span data-ttu-id="07e80-125">Ana bilgisayar istenen verileri toplar ve <xref:System.Activities.Bookmark>sonra .</span><span class="sxs-lookup"><span data-stu-id="07e80-125">The host collects the desired data and then resumes the <xref:System.Activities.Bookmark>.</span></span> <span data-ttu-id="07e80-126">İş akışı devam eder, adı görüntüler ve tamamlar.</span><span class="sxs-lookup"><span data-stu-id="07e80-126">The workflow resumes, displays the name, and then completes.</span></span> <span data-ttu-id="07e80-127">Yer imi devam ı ile ilgili olarak eşitleme kodu gerekmemektedir.</span><span class="sxs-lookup"><span data-stu-id="07e80-127">Note that no synchronization code is required with regard to resuming the bookmark.</span></span> <span data-ttu-id="07e80-128">A <xref:System.Activities.Bookmark> yalnızca iş akışı boştayken ve iş akışı boşta değilse, iş <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> akışı boşalana kadar çağrıyı engeller.</span><span class="sxs-lookup"><span data-stu-id="07e80-128">A <xref:System.Activities.Bookmark> can only be resumed when the workflow is idle, and if the workflow is not idle, the call to <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> blocks until the workflow becomes idle.</span></span>  
  
## <a name="bookmark-resumption-result"></a><span data-ttu-id="07e80-129">Yer Ii Devamı Sonucu</span><span class="sxs-lookup"><span data-stu-id="07e80-129">Bookmark Resumption Result</span></span>  
 <span data-ttu-id="07e80-130"><xref:System.Activities.WorkflowApplication.ResumeBookmark%2A>yer <xref:System.Activities.BookmarkResumptionResult> imi yeniden başlama isteğinin sonuçlarını belirtmek için numaralandırma değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="07e80-130"><xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> returns a <xref:System.Activities.BookmarkResumptionResult> enumeration value to indicate the results of the bookmark resumption request.</span></span> <span data-ttu-id="07e80-131">Olası iade değerleri <xref:System.Activities.BookmarkResumptionResult.Success> <xref:System.Activities.BookmarkResumptionResult.NotReady>, <xref:System.Activities.BookmarkResumptionResult.NotFound>ve .</span><span class="sxs-lookup"><span data-stu-id="07e80-131">The possible return values are <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady>, and <xref:System.Activities.BookmarkResumptionResult.NotFound>.</span></span> <span data-ttu-id="07e80-132">Ana bilgisayarlar ve uzantılar, nasıl devam edileceğine karar vermek için bu değeri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="07e80-132">Hosts and extensions can use this value to determine how to proceed.</span></span>
