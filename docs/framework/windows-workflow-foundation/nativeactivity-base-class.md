---
title: NativeActivity temel sınıfı
ms.date: 03/30/2017
ms.assetid: 254a4c50-425b-426d-a32f-0f7234925bac
ms.openlocfilehash: 40eff2e597763fd492b3051df1a91622e7a60672
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48776564"
---
# <a name="nativeactivity-base-class"></a><span data-ttu-id="76fe0-102">NativeActivity temel sınıfı</span><span class="sxs-lookup"><span data-stu-id="76fe0-102">NativeActivity Base Class</span></span>

<span data-ttu-id="76fe0-103"><xref:System.Activities.NativeActivity> korumalı Oluşturucu ile soyut bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="76fe0-103"><xref:System.Activities.NativeActivity> is an abstract class with a protected constructor.</span></span> <span data-ttu-id="76fe0-104">Gibi <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> uygulayarak kesinlik temelli davranışı yazmak için kullanılan bir <xref:System.Activities.NativeActivity.Execute%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="76fe0-104">Like <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> is used for writing imperative behavior by implementing an <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span> <span data-ttu-id="76fe0-105">Farklı <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> iş akışı çalışma zamanı kullanıma sunulan tüm özelliklere erişebilir <xref:System.Activities.NativeActivityContext> geçirilen nesne <xref:System.Activities.NativeActivity.Execute%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="76fe0-105">Unlike <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> has access to all of the exposed features of the workflow runtime through the <xref:System.Activities.NativeActivityContext> object passed to the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>

## <a name="using-nativeactivitycontext"></a><span data-ttu-id="76fe0-106">NativeActivityContext kullanma</span><span class="sxs-lookup"><span data-stu-id="76fe0-106">Using NativeActivityContext</span></span>
 <span data-ttu-id="76fe0-107">İş akışı çalışma zamanı özellikleri içinden erişilebilir <xref:System.Activities.NativeActivity.Execute%2A> üyeleri kullanarak yöntemi `context` türünde parametre <xref:System.Activities.NativeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="76fe0-107">Features of the workflow runtime can be accessed from within the <xref:System.Activities.NativeActivity.Execute%2A> method by using members of the `context` parameter, of type <xref:System.Activities.NativeActivityContext>.</span></span> <span data-ttu-id="76fe0-108">Aracılığıyla kullanılabilen özellikleri <xref:System.Activities.NativeActivityContext> şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="76fe0-108">The features available through <xref:System.Activities.NativeActivityContext> include the following:</span></span>

-   <span data-ttu-id="76fe0-109">Alma ve bağımsız değişkenler ve değişkenleri ayarlama.</span><span class="sxs-lookup"><span data-stu-id="76fe0-109">Getting and setting of arguments and variables.</span></span>

-   <span data-ttu-id="76fe0-110">Bağımlı etkinliklerle zamanlama <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A></span><span class="sxs-lookup"><span data-stu-id="76fe0-110">Scheduling child activities with <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A></span></span>

-   <span data-ttu-id="76fe0-111">Etkinlik yürütme durduruluyor kullanarak <xref:System.Activities.NativeActivityContext.Abort%2A>.</span><span class="sxs-lookup"><span data-stu-id="76fe0-111">Aborting activity execution using <xref:System.Activities.NativeActivityContext.Abort%2A>.</span></span>

-   <span data-ttu-id="76fe0-112">Yürütme kullanarak alt iptal etme <xref:System.Activities.NativeActivityContext.CancelChild%2A> ve <xref:System.Activities.NativeActivityContext.CancelChildren%2A>.</span><span class="sxs-lookup"><span data-stu-id="76fe0-112">Canceling child execution using <xref:System.Activities.NativeActivityContext.CancelChild%2A> and <xref:System.Activities.NativeActivityContext.CancelChildren%2A>.</span></span>

-   <span data-ttu-id="76fe0-113">Bu tür yöntemler olarak kullanarak etkinlik yer işaretleri erişim <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>, <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A>, ve <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A>.</span><span class="sxs-lookup"><span data-stu-id="76fe0-113">Access to activity bookmarks using such methods as <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>, <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A>, and <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A>.</span></span>

-   <span data-ttu-id="76fe0-114">Özel İzleme özelliklerini kullanarak <xref:System.Activities.CodeActivityContext.Track%2A>.</span><span class="sxs-lookup"><span data-stu-id="76fe0-114">Custom tracking features using <xref:System.Activities.CodeActivityContext.Track%2A>.</span></span>

-   <span data-ttu-id="76fe0-115">Etkinlik yürütme özellikleri ve değer özellikleri kullanarak erişim <xref:System.Activities.CodeActivityContext.GetProperty%2A> ve <xref:System.Activities.NativeActivityContext.GetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="76fe0-115">Access to the activity’s execution properties and value properties using <xref:System.Activities.CodeActivityContext.GetProperty%2A> and <xref:System.Activities.NativeActivityContext.GetValue%2A>.</span></span>

-   <span data-ttu-id="76fe0-116">Etkinlik eylemleri ve işlevleri kullanarak zamanlama <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> ve <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>.</span><span class="sxs-lookup"><span data-stu-id="76fe0-116">Scheduling activity actions and functions using <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> and <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>.</span></span>

### <a name="to-create-a-custom-activity-that-inherits-from-nativeactivity"></a><span data-ttu-id="76fe0-117">NativeActivity devralan bir özel etkinlik oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="76fe0-117">To create a custom activity that inherits from NativeActivity</span></span>

1.  <span data-ttu-id="76fe0-118">Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="76fe0-118">OpenVisual Studio 2010.</span></span>

2.  <span data-ttu-id="76fe0-119">Seçin **dosya**, **yeni**, ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="76fe0-119">Select **File**, **New**, and then **Project**.</span></span> <span data-ttu-id="76fe0-120">Seçin **Workflow 4.0** altında **Visual C#** içinde **proje türleri** penceresi ve select **v2010** düğümü.</span><span class="sxs-lookup"><span data-stu-id="76fe0-120">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="76fe0-121">Seçin **etkinlik Kitaplığı** içinde **şablonları** penceresi.</span><span class="sxs-lookup"><span data-stu-id="76fe0-121">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="76fe0-122">Yeni Proje HelloActivity adı.</span><span class="sxs-lookup"><span data-stu-id="76fe0-122">Name the new project HelloActivity.</span></span>

3.  <span data-ttu-id="76fe0-123">Gt;activity1.XAML HelloActivity projeye sağ tıklayıp **Sil**.</span><span class="sxs-lookup"><span data-stu-id="76fe0-123">Right-click Activity1.xaml in the HelloActivity project and select **Delete**.</span></span>

4.  <span data-ttu-id="76fe0-124">HelloActivity projeye sağ tıklayıp **Ekle**, ardından **sınıfı**.</span><span class="sxs-lookup"><span data-stu-id="76fe0-124">Right-click the HelloActivity project and select **Add**, and then **Class**.</span></span> <span data-ttu-id="76fe0-125">Yeni bir sınıf HelloActivity.cs adı.</span><span class="sxs-lookup"><span data-stu-id="76fe0-125">Name the new class HelloActivity.cs.</span></span>

5.  <span data-ttu-id="76fe0-126">HelloActivity.cs dosyasına aşağıdakileri ekleyin `using` yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="76fe0-126">In the HelloActivity.cs file, add the following `using` directives.</span></span>

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    ```

6.  <span data-ttu-id="76fe0-127">Devralınan yeni bir sınıf olun <xref:System.Activities.NativeActivity> için sınıf bildiriminin bir temel sınıf ekleyerek.</span><span class="sxs-lookup"><span data-stu-id="76fe0-127">Make the new class inherit from <xref:System.Activities.NativeActivity> by adding a base class to the class declaration.</span></span>

    ```csharp
    class HelloActivity : NativeActivity
    ```

7.  <span data-ttu-id="76fe0-128">Ekleyerek sınıfına işlevsellik ekleme bir <xref:System.Activities.NativeActivity.Execute%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="76fe0-128">Add functionality to the class by adding an <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>

    ```csharp
    protected override void Execute(NativeActivityContext context)
    {
        Console.WriteLine("Hello World!");
    }
    ```

8.  <span data-ttu-id="76fe0-129">Geçersiz kılma <xref:System.Activities.NativeActivity.CacheMetadata%2A> yöntemi ve özel etkinliğin değişkenleri, bağımsız değişkenler, alt ve temsilciler hakkında bilmeniz iş akışı çalışma zamanı izin vermek için uygun Ekle yöntemi çağrısı.</span><span class="sxs-lookup"><span data-stu-id="76fe0-129">Override the <xref:System.Activities.NativeActivity.CacheMetadata%2A> method and call the appropriate Add method to let the workflow runtime know about the custom activity’s variables, arguments, children, and delegates.</span></span> <span data-ttu-id="76fe0-130">Daha fazla bilgi için <xref:System.Activities.NativeActivityMetadata> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="76fe0-130">For more information see the <xref:System.Activities.NativeActivityMetadata> class.</span></span>

9. <span data-ttu-id="76fe0-131">Kullanım <xref:System.Activities.NativeActivityContext> bir yer işareti zamanlamak için nesne.</span><span class="sxs-lookup"><span data-stu-id="76fe0-131">Use the <xref:System.Activities.NativeActivityContext> object to schedule a bookmark.</span></span> <span data-ttu-id="76fe0-132">Bkz: <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A> oluşturma hakkında ayrıntılar için zamanlamak ve bir yer işareti devam edin.</span><span class="sxs-lookup"><span data-stu-id="76fe0-132">See <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A> for details on how to create, schedule, and resume a bookmark.</span></span>

    ```
    protected override void Execute(NativeActivityContext context)
        {
            // Create a Bookmark and wait for it to be resumed.
            context.CreateBookmark(BookmarkName.Get(context),
                new BookmarkCallback(OnResumeBookmark));
        }
    ```