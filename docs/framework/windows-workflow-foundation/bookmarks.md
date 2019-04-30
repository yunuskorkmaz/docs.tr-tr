---
title: Bookmarks1
ms.date: 03/30/2017
ms.assetid: 9b51a346-09ae-455c-a70a-e2264ddeb9e2
ms.openlocfilehash: 8b7ca9549327087e30d6c72a8b784aa37ad09f3c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774161"
---
# <a name="bookmarks"></a><span data-ttu-id="685ce-102">Yer İşaretleri</span><span class="sxs-lookup"><span data-stu-id="685ce-102">Bookmarks</span></span>
<span data-ttu-id="685ce-103">Yer işaretleri, bir iş akışı iş parçacığı tutulmadan giriş yordamlarınıza beklenecek bir etkinlik sağlayan mekanizmasıdır.</span><span class="sxs-lookup"><span data-stu-id="685ce-103">Bookmarks are the mechanism that enables an activity to passively wait for input without holding onto a workflow thread.</span></span> <span data-ttu-id="685ce-104">Bir etkinlik için stimulus beklediğini bildirir, bir yer işareti oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="685ce-104">When an activity signals that it is waiting for stimulus, it can create a bookmark.</span></span> <span data-ttu-id="685ce-105">Bu etkinlik yürütme tam olarak değerlendirilmesi gerektiğini değil çalışma zamanının gösterir bile yürütülmekte yöntemi (oluşturulduğu <xref:System.Activities.Bookmark>) döndürür.</span><span class="sxs-lookup"><span data-stu-id="685ce-105">This indicates to the runtime that the activity’s execution should not be considered complete even when the currently executing method (which created the <xref:System.Activities.Bookmark>) returns.</span></span>  
  
## <a name="bookmark-basics"></a><span data-ttu-id="685ce-106">Yer işareti temelleri</span><span class="sxs-lookup"><span data-stu-id="685ce-106">Bookmark Basics</span></span>  
 <span data-ttu-id="685ce-107">A <xref:System.Activities.Bookmark> bir iş akışı örneği içinde bir noktaya hangi yürütme devam ettirilebilir (ve hangi girdi dağıtılabilecek aracılığıyla) temsil eder.</span><span class="sxs-lookup"><span data-stu-id="685ce-107">A <xref:System.Activities.Bookmark> represents a point at which execution can be resumed (and through which input can be delivered) within a workflow instance.</span></span> <span data-ttu-id="685ce-108">Genellikle, bir <xref:System.Activities.Bookmark> bir ad verilir ve dış kod (konak veya uzantısı), yer işareti ile ilgili verileri işlemini sürdürmek için sorumludur.</span><span class="sxs-lookup"><span data-stu-id="685ce-108">Typically, a <xref:System.Activities.Bookmark> is given a name and external (host or extension) code is responsible for resuming the bookmark with relevant data.</span></span> <span data-ttu-id="685ce-109">Olduğunda bir <xref:System.Activities.Bookmark> sürdürülür, iş akışı çalışma zamanı zamanlamaları <xref:System.Activities.BookmarkCallback> ile ilişkili temsilci <xref:System.Activities.Bookmark> oluşturulduğu zaman.</span><span class="sxs-lookup"><span data-stu-id="685ce-109">When a <xref:System.Activities.Bookmark> is resumed, the workflow runtime schedules the <xref:System.Activities.BookmarkCallback> delegate that was associated with that <xref:System.Activities.Bookmark> at the time of its creation.</span></span>  
  
## <a name="bookmark-options"></a><span data-ttu-id="685ce-110">Yer işareti seçenekleri</span><span class="sxs-lookup"><span data-stu-id="685ce-110">Bookmark Options</span></span>  
 <span data-ttu-id="685ce-111"><xref:System.Activities.BookmarkOptions> Sınıf türünü belirten <xref:System.Activities.Bookmark> oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="685ce-111">The <xref:System.Activities.BookmarkOptions> class specifies the type of <xref:System.Activities.Bookmark> being created.</span></span> <span data-ttu-id="685ce-112">Mümkün olmayan birbirini dışlayan değerler <xref:System.Activities.BookmarkOptions.None>, <xref:System.Activities.BookmarkOptions.MultipleResume>, ve <xref:System.Activities.BookmarkOptions.NonBlocking>.</span><span class="sxs-lookup"><span data-stu-id="685ce-112">The possible non mutually-exclusive values are <xref:System.Activities.BookmarkOptions.None>, <xref:System.Activities.BookmarkOptions.MultipleResume>, and <xref:System.Activities.BookmarkOptions.NonBlocking>.</span></span> <span data-ttu-id="685ce-113">Kullanım <xref:System.Activities.BookmarkOptions.None>, oluştururken varsayılan bir <xref:System.Activities.Bookmark> tam bir kez devam ettirilemedi beklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="685ce-113">Use <xref:System.Activities.BookmarkOptions.None>, the default, when creating a <xref:System.Activities.Bookmark> that is expected to be resumed exactly once.</span></span> <span data-ttu-id="685ce-114">Kullanım <xref:System.Activities.BookmarkOptions.MultipleResume> oluştururken bir <xref:System.Activities.Bookmark> birden çok kez ettirilebilir.</span><span class="sxs-lookup"><span data-stu-id="685ce-114">Use <xref:System.Activities.BookmarkOptions.MultipleResume> when creating a <xref:System.Activities.Bookmark> that can be resumed multiple times.</span></span> <span data-ttu-id="685ce-115">Kullanım <xref:System.Activities.BookmarkOptions.NonBlocking> oluştururken bir <xref:System.Activities.Bookmark> , hiçbir zaman sürdürüldü.</span><span class="sxs-lookup"><span data-stu-id="685ce-115">Use <xref:System.Activities.BookmarkOptions.NonBlocking> when creating a <xref:System.Activities.Bookmark> that might never be resumed.</span></span> <span data-ttu-id="685ce-116">Varsayılan değer kullanılarak oluşturulan yer işaretleri aksine <xref:System.Activities.BookmarkOptions>, <xref:System.Activities.BookmarkOptions.NonBlocking> yer işaretleri engel olmaz bir etkinliğin tamamlanmasını.</span><span class="sxs-lookup"><span data-stu-id="685ce-116">Unlike bookmarks created using the default <xref:System.Activities.BookmarkOptions>, <xref:System.Activities.BookmarkOptions.NonBlocking> bookmarks do not prevent an activity from completing.</span></span>  
  
## <a name="bookmark-resumption"></a><span data-ttu-id="685ce-117">Yer imi sürdürme</span><span class="sxs-lookup"><span data-stu-id="685ce-117">Bookmark Resumption</span></span>  
 <span data-ttu-id="685ce-118">Yer işaretleri, kod dışında birini kullanarak bir iş akışı tarafından ettirilebilir <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> aşırı yüklemeleri.</span><span class="sxs-lookup"><span data-stu-id="685ce-118">Bookmarks can be resumed by code outside of a workflow using one of the <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> overloads.</span></span> <span data-ttu-id="685ce-119">Bu örnekte, bir `ReadLine` etkinlik oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="685ce-119">In this example, a `ReadLine` activity is created.</span></span> <span data-ttu-id="685ce-120">Yürütüldüğünde, `ReadLine` etkinliği oluşturur bir <xref:System.Activities.Bookmark>, bir geri çağırma kaydeder ve sonra bekler <xref:System.Activities.Bookmark> olarak devam eder.</span><span class="sxs-lookup"><span data-stu-id="685ce-120">When executed, the `ReadLine` activity creates a <xref:System.Activities.Bookmark>, registers a callback, and then waits for the <xref:System.Activities.Bookmark> to be resumed.</span></span> <span data-ttu-id="685ce-121">Bunu devam ettirildiğinde `ReadLine` etkinlik ile geçirilen verileri atar <xref:System.Activities.Bookmark> için kendi <xref:System.Activities.Activity%601.Result%2A> bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="685ce-121">When it is resumed, the `ReadLine` activity assigns the data that was passed with the <xref:System.Activities.Bookmark> to its <xref:System.Activities.Activity%601.Result%2A> argument.</span></span>  
  
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
  
 <span data-ttu-id="685ce-122">Bu örnekte, bir iş akışı kullanan oluşturulur `ReadLine` kullanıcı adını toplamak ve konsol penceresinde görüntülemek için etkinlik.</span><span class="sxs-lookup"><span data-stu-id="685ce-122">In this example, a workflow is created that uses the `ReadLine` activity to gather the user’s name and display it to the console window.</span></span> <span data-ttu-id="685ce-123">Konak uygulama giriş toplama asıl işi yapar ve iş akışını sürdürme tarafından geçirir <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="685ce-123">The host application performs the actual work of gathering the input and passes it to the workflow by resuming the <xref:System.Activities.Bookmark>.</span></span>  
  
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
  
 <span data-ttu-id="685ce-124">Zaman `ReadLine` etkinlik yürütüldüğünde, oluşturur bir <xref:System.Activities.Bookmark> adlı `UserName` ve devam ettirilemedi yer işareti için bekler.</span><span class="sxs-lookup"><span data-stu-id="685ce-124">When the `ReadLine` activity is executed, it creates a <xref:System.Activities.Bookmark> named `UserName` and then waits for the bookmark to be resumed.</span></span> <span data-ttu-id="685ce-125">Konak istenen verileri toplar ve ardından devam ettirir <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="685ce-125">The host collects the desired data and then resumes the <xref:System.Activities.Bookmark>.</span></span> <span data-ttu-id="685ce-126">İş akışını sürdürür, adını gösterir ve tamamlandıktan sonra.</span><span class="sxs-lookup"><span data-stu-id="685ce-126">The workflow resumes, displays the name, and then completes.</span></span> <span data-ttu-id="685ce-127">Hiçbir eşitleme kodu yer işaretinin sürdürme açısından gerekli olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="685ce-127">Note that no synchronization code is required with regard to resuming the bookmark.</span></span> <span data-ttu-id="685ce-128">A <xref:System.Activities.Bookmark> iş akışı boştayken sürdürülebilir ve iş akışı değilse, boşta, çağrı <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> iş akışı boşta olana kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="685ce-128">A <xref:System.Activities.Bookmark> can only be resumed when the workflow is idle, and if the workflow is not idle, the call to <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> blocks until the workflow becomes idle.</span></span>  
  
## <a name="bookmark-resumption-result"></a><span data-ttu-id="685ce-129">Yer imi sürdürme sonucu</span><span class="sxs-lookup"><span data-stu-id="685ce-129">Bookmark Resumption Result</span></span>  
 <span data-ttu-id="685ce-130"><xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> döndürür bir <xref:System.Activities.BookmarkResumptionResult> yer imi sürdürme isteğin sonuçlarını gösteren numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="685ce-130"><xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> returns a <xref:System.Activities.BookmarkResumptionResult> enumeration value to indicate the results of the bookmark resumption request.</span></span> <span data-ttu-id="685ce-131">Olası dönüş değerleri <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady>, ve <xref:System.Activities.BookmarkResumptionResult.NotFound>.</span><span class="sxs-lookup"><span data-stu-id="685ce-131">The possible return values are <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady>, and <xref:System.Activities.BookmarkResumptionResult.NotFound>.</span></span> <span data-ttu-id="685ce-132">Konakları ve uzantıları bu değeri nasıl ilerleyeceğiniz belirlemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="685ce-132">Hosts and extensions can use this value to determine how to proceed.</span></span>
