---
description: 'Daha fazla bilgi edinin: NativeActivity temel sınıfı'
title: NativeActivity Temel Sınıfı
ms.date: 03/30/2017
ms.assetid: 254a4c50-425b-426d-a32f-0f7234925bac
ms.openlocfilehash: 184001ad9ee83c238265764cda3bc007e4a1fc71
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720143"
---
# <a name="nativeactivity-base-class"></a><span data-ttu-id="19acb-103">NativeActivity Temel Sınıfı</span><span class="sxs-lookup"><span data-stu-id="19acb-103">NativeActivity Base Class</span></span>

<span data-ttu-id="19acb-104"><xref:System.Activities.NativeActivity> , korumalı Oluşturucusu olan soyut bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="19acb-104"><xref:System.Activities.NativeActivity> is an abstract class with a protected constructor.</span></span> <span data-ttu-id="19acb-105">Benzer şekilde <xref:System.Activities.CodeActivity> , <xref:System.Activities.NativeActivity> bir yöntemi uygulayarak kesinlik davranışı yazmak için kullanılır <xref:System.Activities.NativeActivity.Execute%2A> .</span><span class="sxs-lookup"><span data-stu-id="19acb-105">Like <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> is used for writing imperative behavior by implementing an <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span> <span data-ttu-id="19acb-106">Aksine <xref:System.Activities.CodeActivity> , <xref:System.Activities.NativeActivity> yöntemine geçirilen nesne aracılığıyla iş akışı çalışma zamanının tüm sunulan özelliklerine erişimi vardır <xref:System.Activities.NativeActivityContext> <xref:System.Activities.NativeActivity.Execute%2A> .</span><span class="sxs-lookup"><span data-stu-id="19acb-106">Unlike <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> has access to all of the exposed features of the workflow runtime through the <xref:System.Activities.NativeActivityContext> object passed to the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>

## <a name="using-nativeactivitycontext"></a><span data-ttu-id="19acb-107">NativeActivityContext kullanma</span><span class="sxs-lookup"><span data-stu-id="19acb-107">Using NativeActivityContext</span></span>

 <span data-ttu-id="19acb-108">İş akışı çalışma zamanının özelliklerine <xref:System.Activities.NativeActivity.Execute%2A> , türünün ' nin üyelerini kullanarak yönteminin içinden erişilebilir `context` <xref:System.Activities.NativeActivityContext> .</span><span class="sxs-lookup"><span data-stu-id="19acb-108">Features of the workflow runtime can be accessed from within the <xref:System.Activities.NativeActivity.Execute%2A> method by using members of the `context` parameter, of type <xref:System.Activities.NativeActivityContext>.</span></span> <span data-ttu-id="19acb-109">Aracılığıyla kullanılabilen özellikler şunları <xref:System.Activities.NativeActivityContext> içerir:</span><span class="sxs-lookup"><span data-stu-id="19acb-109">The features available through <xref:System.Activities.NativeActivityContext> include the following:</span></span>

- <span data-ttu-id="19acb-110">Bağımsız değişkenlerin ve değişkenlerin alınması ve ayarlanması.</span><span class="sxs-lookup"><span data-stu-id="19acb-110">Getting and setting of arguments and variables.</span></span>

- <span data-ttu-id="19acb-111">İle alt etkinlikleri zamanlama <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A></span><span class="sxs-lookup"><span data-stu-id="19acb-111">Scheduling child activities with <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A></span></span>

- <span data-ttu-id="19acb-112">Kullanılarak Etkinlik yürütme durduruluyor <xref:System.Activities.NativeActivityContext.Abort%2A> .</span><span class="sxs-lookup"><span data-stu-id="19acb-112">Aborting activity execution using <xref:System.Activities.NativeActivityContext.Abort%2A>.</span></span>

- <span data-ttu-id="19acb-113">Ve kullanarak alt yürütme iptal ediliyor <xref:System.Activities.NativeActivityContext.CancelChild%2A> <xref:System.Activities.NativeActivityContext.CancelChildren%2A> .</span><span class="sxs-lookup"><span data-stu-id="19acb-113">Canceling child execution using <xref:System.Activities.NativeActivityContext.CancelChild%2A> and <xref:System.Activities.NativeActivityContext.CancelChildren%2A>.</span></span>

- <span data-ttu-id="19acb-114">, Ve gibi yöntemler kullanılarak etkinlik yer işaretlerine <xref:System.Activities.NativeActivityContext.CreateBookmark%2A> erişin <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A> <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A> .</span><span class="sxs-lookup"><span data-stu-id="19acb-114">Access to activity bookmarks using such methods as <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>, <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A>, and <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A>.</span></span>

- <span data-ttu-id="19acb-115">Kullanarak özel izleme özellikleri <xref:System.Activities.CodeActivityContext.Track%2A> .</span><span class="sxs-lookup"><span data-stu-id="19acb-115">Custom tracking features using <xref:System.Activities.CodeActivityContext.Track%2A>.</span></span>

- <span data-ttu-id="19acb-116">Ve kullanarak etkinliğin yürütme özelliklerine ve değer özelliklerine erişin <xref:System.Activities.CodeActivityContext.GetProperty%2A> <xref:System.Activities.NativeActivityContext.GetValue%2A> .</span><span class="sxs-lookup"><span data-stu-id="19acb-116">Access to the activity’s execution properties and value properties using <xref:System.Activities.CodeActivityContext.GetProperty%2A> and <xref:System.Activities.NativeActivityContext.GetValue%2A>.</span></span>

- <span data-ttu-id="19acb-117">Ve kullanarak etkinlik eylemlerini ve işlevleri <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> zamanlama <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A> .</span><span class="sxs-lookup"><span data-stu-id="19acb-117">Scheduling activity actions and functions using <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> and <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>.</span></span>

### <a name="to-create-a-custom-activity-that-inherits-from-nativeactivity"></a><span data-ttu-id="19acb-118">NativeActivity 'den devralan özel etkinlik oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="19acb-118">To create a custom activity that inherits from NativeActivity</span></span>

1. <span data-ttu-id="19acb-119">OpenVisual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="19acb-119">OpenVisual Studio 2010.</span></span>

2. <span data-ttu-id="19acb-120">**Dosya**, **Yeni** ve ardından **Proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="19acb-120">Select **File**, **New**, and then **Project**.</span></span> <span data-ttu-id="19acb-121">**Proje türleri** penceresinde **Visual C#** altında **iş akışı 4,0** ' i seçin ve **v2010** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="19acb-121">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="19acb-122">**Şablonlar** penceresinde **etkinlik kitaplığı** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="19acb-122">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="19acb-123">Yeni proje Merhaba etkinliğini adlandırın.</span><span class="sxs-lookup"><span data-stu-id="19acb-123">Name the new project HelloActivity.</span></span>

3. <span data-ttu-id="19acb-124">Merhaba etkinlik projesinde Activity1. xaml öğesine sağ tıklayın ve **Sil**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="19acb-124">Right-click Activity1.xaml in the HelloActivity project and select **Delete**.</span></span>

4. <span data-ttu-id="19acb-125">Merhaba etkinlik projesine sağ tıklayın ve **Ekle**' yi ve ardından **sınıf**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="19acb-125">Right-click the HelloActivity project and select **Add**, and then **Class**.</span></span> <span data-ttu-id="19acb-126">Yeni sınıfı HelloActivity.cs olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="19acb-126">Name the new class HelloActivity.cs.</span></span>

5. <span data-ttu-id="19acb-127">HelloActivity.cs dosyasında aşağıdaki `using` yönergeleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="19acb-127">In the HelloActivity.cs file, add the following `using` directives.</span></span>

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    ```

6. <span data-ttu-id="19acb-128"><xref:System.Activities.NativeActivity>Sınıf bildirimine bir temel sınıf ekleyerek yeni sınıfın öğesinden devralmasını sağlayın.</span><span class="sxs-lookup"><span data-stu-id="19acb-128">Make the new class inherit from <xref:System.Activities.NativeActivity> by adding a base class to the class declaration.</span></span>

    ```csharp
    class HelloActivity : NativeActivity
    ```

7. <span data-ttu-id="19acb-129">Bir yöntem ekleyerek sınıfa işlevsellik ekleyin <xref:System.Activities.NativeActivity.Execute%2A> .</span><span class="sxs-lookup"><span data-stu-id="19acb-129">Add functionality to the class by adding an <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>

    ```csharp
    protected override void Execute(NativeActivityContext context)
    {
        Console.WriteLine("Hello World!");
    }
    ```

8. <span data-ttu-id="19acb-130">Yöntemi geçersiz kılın <xref:System.Activities.NativeActivity.CacheMetadata%2A> ve iş akışı çalışma zamanının özel etkinliğin değişkenleri, bağımsız değişkenleri, alt öğeleri ve Temsilciler hakkında bilgi almasına izin vermek için uygun ekleme yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="19acb-130">Override the <xref:System.Activities.NativeActivity.CacheMetadata%2A> method and call the appropriate Add method to let the workflow runtime know about the custom activity’s variables, arguments, children, and delegates.</span></span> <span data-ttu-id="19acb-131">Daha fazla bilgi için <xref:System.Activities.NativeActivityMetadata> sınıfına bakın.</span><span class="sxs-lookup"><span data-stu-id="19acb-131">For more information see the <xref:System.Activities.NativeActivityMetadata> class.</span></span>

9. <span data-ttu-id="19acb-132"><xref:System.Activities.NativeActivityContext>Bir yer işareti zamanlamak için nesnesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="19acb-132">Use the <xref:System.Activities.NativeActivityContext> object to schedule a bookmark.</span></span> <span data-ttu-id="19acb-133"><xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A>Bir yer işaretinin oluşturulması, zamanlanzamanlaması ve sürdürülmesine ilişkin ayrıntılar için bkz..</span><span class="sxs-lookup"><span data-stu-id="19acb-133">See <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A> for details on how to create, schedule, and resume a bookmark.</span></span>

    ```csharp
    protected override void Execute(NativeActivityContext context)
        {
            // Create a Bookmark and wait for it to be resumed.
            context.CreateBookmark(BookmarkName.Get(context),
                new BookmarkCallback(OnResumeBookmark));
        }
    ```
