---
title: NativeActivity Temel Sınıfı
ms.date: 03/30/2017
ms.assetid: 254a4c50-425b-426d-a32f-0f7234925bac
ms.openlocfilehash: f718d247e7110b46cdd13038c7c93c1e45612c75
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296595"
---
# <a name="nativeactivity-base-class"></a><span data-ttu-id="0d6de-102">NativeActivity Temel Sınıfı</span><span class="sxs-lookup"><span data-stu-id="0d6de-102">NativeActivity Base Class</span></span>

<xref:System.Activities.NativeActivity> <span data-ttu-id="0d6de-103">korumalı Oluşturucu ile soyut bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="0d6de-103">is an abstract class with a protected constructor.</span></span> <span data-ttu-id="0d6de-104">Gibi <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> uygulayarak kesinlik temelli davranışı yazmak için kullanılan bir <xref:System.Activities.NativeActivity.Execute%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0d6de-104">Like <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> is used for writing imperative behavior by implementing an <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span> <span data-ttu-id="0d6de-105">Farklı <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> iş akışı çalışma zamanı kullanıma sunulan tüm özelliklere erişebilir <xref:System.Activities.NativeActivityContext> geçirilen nesne <xref:System.Activities.NativeActivity.Execute%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0d6de-105">Unlike <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> has access to all of the exposed features of the workflow runtime through the <xref:System.Activities.NativeActivityContext> object passed to the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>

## <a name="using-nativeactivitycontext"></a><span data-ttu-id="0d6de-106">NativeActivityContext kullanma</span><span class="sxs-lookup"><span data-stu-id="0d6de-106">Using NativeActivityContext</span></span>
 <span data-ttu-id="0d6de-107">İş akışı çalışma zamanı özellikleri içinden erişilebilir <xref:System.Activities.NativeActivity.Execute%2A> üyeleri kullanarak yöntemi `context` türünde parametre <xref:System.Activities.NativeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="0d6de-107">Features of the workflow runtime can be accessed from within the <xref:System.Activities.NativeActivity.Execute%2A> method by using members of the `context` parameter, of type <xref:System.Activities.NativeActivityContext>.</span></span> <span data-ttu-id="0d6de-108">Aracılığıyla kullanılabilen özellikleri <xref:System.Activities.NativeActivityContext> şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="0d6de-108">The features available through <xref:System.Activities.NativeActivityContext> include the following:</span></span>

-   <span data-ttu-id="0d6de-109">Alma ve bağımsız değişkenler ve değişkenleri ayarlama.</span><span class="sxs-lookup"><span data-stu-id="0d6de-109">Getting and setting of arguments and variables.</span></span>

-   <span data-ttu-id="0d6de-110">Bağımlı etkinliklerle zamanlama</span><span class="sxs-lookup"><span data-stu-id="0d6de-110">Scheduling child activities with</span></span> <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>

-   <span data-ttu-id="0d6de-111">Etkinlik yürütme durduruluyor kullanarak <xref:System.Activities.NativeActivityContext.Abort%2A>.</span><span class="sxs-lookup"><span data-stu-id="0d6de-111">Aborting activity execution using <xref:System.Activities.NativeActivityContext.Abort%2A>.</span></span>

-   <span data-ttu-id="0d6de-112">Yürütme kullanarak alt iptal etme <xref:System.Activities.NativeActivityContext.CancelChild%2A> ve <xref:System.Activities.NativeActivityContext.CancelChildren%2A>.</span><span class="sxs-lookup"><span data-stu-id="0d6de-112">Canceling child execution using <xref:System.Activities.NativeActivityContext.CancelChild%2A> and <xref:System.Activities.NativeActivityContext.CancelChildren%2A>.</span></span>

-   <span data-ttu-id="0d6de-113">Bu tür yöntemler olarak kullanarak etkinlik yer işaretleri erişim <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>, <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A>, ve <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A>.</span><span class="sxs-lookup"><span data-stu-id="0d6de-113">Access to activity bookmarks using such methods as <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>, <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A>, and <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A>.</span></span>

-   <span data-ttu-id="0d6de-114">Özel İzleme özelliklerini kullanarak <xref:System.Activities.CodeActivityContext.Track%2A>.</span><span class="sxs-lookup"><span data-stu-id="0d6de-114">Custom tracking features using <xref:System.Activities.CodeActivityContext.Track%2A>.</span></span>

-   <span data-ttu-id="0d6de-115">Etkinlik yürütme özellikleri ve değer özellikleri kullanarak erişim <xref:System.Activities.CodeActivityContext.GetProperty%2A> ve <xref:System.Activities.NativeActivityContext.GetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="0d6de-115">Access to the activity’s execution properties and value properties using <xref:System.Activities.CodeActivityContext.GetProperty%2A> and <xref:System.Activities.NativeActivityContext.GetValue%2A>.</span></span>

-   <span data-ttu-id="0d6de-116">Etkinlik eylemleri ve işlevleri kullanarak zamanlama <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> ve <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>.</span><span class="sxs-lookup"><span data-stu-id="0d6de-116">Scheduling activity actions and functions using <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> and <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>.</span></span>

### <a name="to-create-a-custom-activity-that-inherits-from-nativeactivity"></a><span data-ttu-id="0d6de-117">NativeActivity devralan bir özel etkinlik oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="0d6de-117">To create a custom activity that inherits from NativeActivity</span></span>

1. <span data-ttu-id="0d6de-118">OpenVisual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="0d6de-118">OpenVisual Studio 2010.</span></span>

2. <span data-ttu-id="0d6de-119">Seçin **dosya**, **yeni**, ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="0d6de-119">Select **File**, **New**, and then **Project**.</span></span> <span data-ttu-id="0d6de-120">Seçin **Workflow 4.0** altında **Visual C#** içinde **proje türleri** penceresi ve select **v2010** düğümü.</span><span class="sxs-lookup"><span data-stu-id="0d6de-120">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="0d6de-121">Seçin **etkinlik Kitaplığı** içinde **şablonları** penceresi.</span><span class="sxs-lookup"><span data-stu-id="0d6de-121">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="0d6de-122">Yeni Proje HelloActivity adı.</span><span class="sxs-lookup"><span data-stu-id="0d6de-122">Name the new project HelloActivity.</span></span>

3. <span data-ttu-id="0d6de-123">Gt;activity1.XAML HelloActivity projeye sağ tıklayıp **Sil**.</span><span class="sxs-lookup"><span data-stu-id="0d6de-123">Right-click Activity1.xaml in the HelloActivity project and select **Delete**.</span></span>

4. <span data-ttu-id="0d6de-124">HelloActivity projeye sağ tıklayıp **Ekle**, ardından **sınıfı**.</span><span class="sxs-lookup"><span data-stu-id="0d6de-124">Right-click the HelloActivity project and select **Add**, and then **Class**.</span></span> <span data-ttu-id="0d6de-125">Yeni bir sınıf HelloActivity.cs adı.</span><span class="sxs-lookup"><span data-stu-id="0d6de-125">Name the new class HelloActivity.cs.</span></span>

5. <span data-ttu-id="0d6de-126">HelloActivity.cs dosyasına aşağıdakileri ekleyin `using` yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="0d6de-126">In the HelloActivity.cs file, add the following `using` directives.</span></span>

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    ```

6. <span data-ttu-id="0d6de-127">Devralınan yeni bir sınıf olun <xref:System.Activities.NativeActivity> için sınıf bildiriminin bir temel sınıf ekleyerek.</span><span class="sxs-lookup"><span data-stu-id="0d6de-127">Make the new class inherit from <xref:System.Activities.NativeActivity> by adding a base class to the class declaration.</span></span>

    ```csharp
    class HelloActivity : NativeActivity
    ```

7. <span data-ttu-id="0d6de-128">Ekleyerek sınıfına işlevsellik ekleme bir <xref:System.Activities.NativeActivity.Execute%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0d6de-128">Add functionality to the class by adding an <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>

    ```csharp
    protected override void Execute(NativeActivityContext context)
    {
        Console.WriteLine("Hello World!");
    }
    ```

8. <span data-ttu-id="0d6de-129">Geçersiz kılma <xref:System.Activities.NativeActivity.CacheMetadata%2A> yöntemi ve özel etkinliğin değişkenleri, bağımsız değişkenler, alt ve temsilciler hakkında bilmeniz iş akışı çalışma zamanı izin vermek için uygun Ekle yöntemi çağrısı.</span><span class="sxs-lookup"><span data-stu-id="0d6de-129">Override the <xref:System.Activities.NativeActivity.CacheMetadata%2A> method and call the appropriate Add method to let the workflow runtime know about the custom activity’s variables, arguments, children, and delegates.</span></span> <span data-ttu-id="0d6de-130">Daha fazla bilgi için <xref:System.Activities.NativeActivityMetadata> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0d6de-130">For more information see the <xref:System.Activities.NativeActivityMetadata> class.</span></span>

9. <span data-ttu-id="0d6de-131">Kullanım <xref:System.Activities.NativeActivityContext> bir yer işareti zamanlamak için nesne.</span><span class="sxs-lookup"><span data-stu-id="0d6de-131">Use the <xref:System.Activities.NativeActivityContext> object to schedule a bookmark.</span></span> <span data-ttu-id="0d6de-132">Bkz: <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A> oluşturma hakkında ayrıntılar için zamanlamak ve bir yer işareti devam edin.</span><span class="sxs-lookup"><span data-stu-id="0d6de-132">See <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A> for details on how to create, schedule, and resume a bookmark.</span></span>

    ```
    protected override void Execute(NativeActivityContext context)
        {
            // Create a Bookmark and wait for it to be resumed.
            context.CreateBookmark(BookmarkName.Get(context),
                new BookmarkCallback(OnResumeBookmark));
        }
    ```