---
title: Bookmarks1
ms.date: 03/30/2017
ms.assetid: 9b51a346-09ae-455c-a70a-e2264ddeb9e2
ms.openlocfilehash: 8b7ca9549327087e30d6c72a8b784aa37ad09f3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515574"
---
# <a name="bookmarks"></a><span data-ttu-id="372e4-102">Yer işaretleri</span><span class="sxs-lookup"><span data-stu-id="372e4-102">Bookmarks</span></span>
<span data-ttu-id="372e4-103">Yer işaretleri pasif olarak giriş için bir iş akışı iş parçacığı tutmadan beklemek için bir etkinlik sağlayan sistemdir.</span><span class="sxs-lookup"><span data-stu-id="372e4-103">Bookmarks are the mechanism that enables an activity to passively wait for input without holding onto a workflow thread.</span></span> <span data-ttu-id="372e4-104">Bir etkinlik için stimulus beklediğini bildirir, bir yer işareti oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="372e4-104">When an activity signals that it is waiting for stimulus, it can create a bookmark.</span></span> <span data-ttu-id="372e4-105">Bu etkinliğin yürütme tam düşünülmemelidir, çalışma zamanı gösterir bile şu anda yürütülen yöntemi (oluşturulduğu <xref:System.Activities.Bookmark>) döndürür.</span><span class="sxs-lookup"><span data-stu-id="372e4-105">This indicates to the runtime that the activity’s execution should not be considered complete even when the currently executing method (which created the <xref:System.Activities.Bookmark>) returns.</span></span>  
  
## <a name="bookmark-basics"></a><span data-ttu-id="372e4-106">Yer işareti temelleri</span><span class="sxs-lookup"><span data-stu-id="372e4-106">Bookmark Basics</span></span>  
 <span data-ttu-id="372e4-107">A <xref:System.Activities.Bookmark> noktası hangi yürütme devam ettirilebilir (ve hangi girdi teslim edilebilir aracılığıyla) içinde bir iş akışı örneği temsil eder.</span><span class="sxs-lookup"><span data-stu-id="372e4-107">A <xref:System.Activities.Bookmark> represents a point at which execution can be resumed (and through which input can be delivered) within a workflow instance.</span></span> <span data-ttu-id="372e4-108">Genellikle, bir <xref:System.Activities.Bookmark> bir ad verilir ve dış (ana bilgisayar veya uzantısı) kod yer ilgili verilerle birlikte yeniden başlatma için sorumlu.</span><span class="sxs-lookup"><span data-stu-id="372e4-108">Typically, a <xref:System.Activities.Bookmark> is given a name and external (host or extension) code is responsible for resuming the bookmark with relevant data.</span></span> <span data-ttu-id="372e4-109">Zaman bir <xref:System.Activities.Bookmark> devam ettirildiğinde, iş akışı çalışma zamanı zamanlamaları <xref:System.Activities.BookmarkCallback> ile ilişkili temsilci <xref:System.Activities.Bookmark> ile oluşturulma zamanında.</span><span class="sxs-lookup"><span data-stu-id="372e4-109">When a <xref:System.Activities.Bookmark> is resumed, the workflow runtime schedules the <xref:System.Activities.BookmarkCallback> delegate that was associated with that <xref:System.Activities.Bookmark> at the time of its creation.</span></span>  
  
## <a name="bookmark-options"></a><span data-ttu-id="372e4-110">Yer işareti seçenekleri</span><span class="sxs-lookup"><span data-stu-id="372e4-110">Bookmark Options</span></span>  
 <span data-ttu-id="372e4-111"><xref:System.Activities.BookmarkOptions> Sınıfı türünü belirten <xref:System.Activities.Bookmark> oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="372e4-111">The <xref:System.Activities.BookmarkOptions> class specifies the type of <xref:System.Activities.Bookmark> being created.</span></span> <span data-ttu-id="372e4-112">Olası olmayan birbirini dışlayan değerleri <xref:System.Activities.BookmarkOptions.None>, <xref:System.Activities.BookmarkOptions.MultipleResume>, ve <xref:System.Activities.BookmarkOptions.NonBlocking>.</span><span class="sxs-lookup"><span data-stu-id="372e4-112">The possible non mutually-exclusive values are <xref:System.Activities.BookmarkOptions.None>, <xref:System.Activities.BookmarkOptions.MultipleResume>, and <xref:System.Activities.BookmarkOptions.NonBlocking>.</span></span> <span data-ttu-id="372e4-113">Kullanım <xref:System.Activities.BookmarkOptions.None>, oluştururken varsayılan olarak bir <xref:System.Activities.Bookmark> tam olarak bir kez sürdürülmesini bekleniyordu.</span><span class="sxs-lookup"><span data-stu-id="372e4-113">Use <xref:System.Activities.BookmarkOptions.None>, the default, when creating a <xref:System.Activities.Bookmark> that is expected to be resumed exactly once.</span></span> <span data-ttu-id="372e4-114">Kullanım <xref:System.Activities.BookmarkOptions.MultipleResume> oluştururken bir <xref:System.Activities.Bookmark> , sürdürüldü birden çok kez.</span><span class="sxs-lookup"><span data-stu-id="372e4-114">Use <xref:System.Activities.BookmarkOptions.MultipleResume> when creating a <xref:System.Activities.Bookmark> that can be resumed multiple times.</span></span> <span data-ttu-id="372e4-115">Kullanım <xref:System.Activities.BookmarkOptions.NonBlocking> oluştururken bir <xref:System.Activities.Bookmark> , hiçbir zaman sürdürüldü.</span><span class="sxs-lookup"><span data-stu-id="372e4-115">Use <xref:System.Activities.BookmarkOptions.NonBlocking> when creating a <xref:System.Activities.Bookmark> that might never be resumed.</span></span> <span data-ttu-id="372e4-116">Yer işaretleri varsayılan kullanılarak oluşturulan aksine <xref:System.Activities.BookmarkOptions>, <xref:System.Activities.BookmarkOptions.NonBlocking> yer işaretleri engel olmaz aktivite tamamlamanızı.</span><span class="sxs-lookup"><span data-stu-id="372e4-116">Unlike bookmarks created using the default <xref:System.Activities.BookmarkOptions>, <xref:System.Activities.BookmarkOptions.NonBlocking> bookmarks do not prevent an activity from completing.</span></span>  
  
## <a name="bookmark-resumption"></a><span data-ttu-id="372e4-117">Yer işareti sürdürme</span><span class="sxs-lookup"><span data-stu-id="372e4-117">Bookmark Resumption</span></span>  
 <span data-ttu-id="372e4-118">Yer işaretleri sürdürüldü birini kullanarak bir iş akışı dışında bir kod tarafından <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> aşırı.</span><span class="sxs-lookup"><span data-stu-id="372e4-118">Bookmarks can be resumed by code outside of a workflow using one of the <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> overloads.</span></span> <span data-ttu-id="372e4-119">Bu örnekte, bir `ReadLine` etkinlik oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="372e4-119">In this example, a `ReadLine` activity is created.</span></span> <span data-ttu-id="372e4-120">Çalıştırıldığında, `ReadLine` aktivite oluşturan bir <xref:System.Activities.Bookmark>, bir geri çağırma kaydeder ve sonra bekler <xref:System.Activities.Bookmark> olarak devam eder.</span><span class="sxs-lookup"><span data-stu-id="372e4-120">When executed, the `ReadLine` activity creates a <xref:System.Activities.Bookmark>, registers a callback, and then waits for the <xref:System.Activities.Bookmark> to be resumed.</span></span> <span data-ttu-id="372e4-121">Ettirildiğinde, `ReadLine` etkinlik atar ile geçirilen verileri <xref:System.Activities.Bookmark> için kendi <xref:System.Activities.Activity%601.Result%2A> bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="372e4-121">When it is resumed, the `ReadLine` activity assigns the data that was passed with the <xref:System.Activities.Bookmark> to its <xref:System.Activities.Activity%601.Result%2A> argument.</span></span>  
  
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
  
 <span data-ttu-id="372e4-122">Bu örnekte, bir iş akışı kullanan oluşturulur `ReadLine` kullanıcı adını toplamak ve konsol penceresine görüntülemek için etkinliği.</span><span class="sxs-lookup"><span data-stu-id="372e4-122">In this example, a workflow is created that uses the `ReadLine` activity to gather the user’s name and display it to the console window.</span></span> <span data-ttu-id="372e4-123">Konak uygulama giriş toplama asıl işi yapar ve devam ettirme tarafından iş akışına geçirir <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="372e4-123">The host application performs the actual work of gathering the input and passes it to the workflow by resuming the <xref:System.Activities.Bookmark>.</span></span>  
  
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
  
 <span data-ttu-id="372e4-124">Zaman `ReadLine` etkinlik yürütülürse, oluşturduğu bir <xref:System.Activities.Bookmark> adlı `UserName` ve yer işareti devam ettirilebilir bekler.</span><span class="sxs-lookup"><span data-stu-id="372e4-124">When the `ReadLine` activity is executed, it creates a <xref:System.Activities.Bookmark> named `UserName` and then waits for the bookmark to be resumed.</span></span> <span data-ttu-id="372e4-125">Ana bilgisayar istenen verileri toplar ve ardından sürdürür <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="372e4-125">The host collects the desired data and then resumes the <xref:System.Activities.Bookmark>.</span></span> <span data-ttu-id="372e4-126">İş akışını sürdürür, adını görüntüler ve sonra tamamlar.</span><span class="sxs-lookup"><span data-stu-id="372e4-126">The workflow resumes, displays the name, and then completes.</span></span> <span data-ttu-id="372e4-127">Hiçbir eşitleme kodu yer işareti sürdürme açısından gerekli olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="372e4-127">Note that no synchronization code is required with regard to resuming the bookmark.</span></span> <span data-ttu-id="372e4-128">A <xref:System.Activities.Bookmark> iş akışı boştayken ettirilebilir ve iş akışı değilse, boşta, çağrısı <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> iş akışı boşta olana kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="372e4-128">A <xref:System.Activities.Bookmark> can only be resumed when the workflow is idle, and if the workflow is not idle, the call to <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> blocks until the workflow becomes idle.</span></span>  
  
## <a name="bookmark-resumption-result"></a><span data-ttu-id="372e4-129">Yer işareti sürdürme sonucu</span><span class="sxs-lookup"><span data-stu-id="372e4-129">Bookmark Resumption Result</span></span>  
 <span data-ttu-id="372e4-130"><xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> döndüren bir <xref:System.Activities.BookmarkResumptionResult> yer işareti sürdürme isteği sonuçlarını göstermek için numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="372e4-130"><xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> returns a <xref:System.Activities.BookmarkResumptionResult> enumeration value to indicate the results of the bookmark resumption request.</span></span> <span data-ttu-id="372e4-131">Olası dönüş değerleri <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady>, ve <xref:System.Activities.BookmarkResumptionResult.NotFound>.</span><span class="sxs-lookup"><span data-stu-id="372e4-131">The possible return values are <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady>, and <xref:System.Activities.BookmarkResumptionResult.NotFound>.</span></span> <span data-ttu-id="372e4-132">Konaklar ve uzantıları bu değerin nasıl ilerleyeceğiniz belirlemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="372e4-132">Hosts and extensions can use this value to determine how to proceed.</span></span>
