---
title: "NativeActivity taban sınıfı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 254a4c50-425b-426d-a32f-0f7234925bac
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5f5a925aa9fc14c370c50ab0877742b207461c1d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="nativeactivity-base-class"></a><span data-ttu-id="afbf4-102">NativeActivity taban sınıfı</span><span class="sxs-lookup"><span data-stu-id="afbf4-102">NativeActivity Base Class</span></span>
<span data-ttu-id="afbf4-103"><xref:System.Activities.NativeActivity>soyut bir sınıf korumalı Oluşturucu ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="afbf4-103"><xref:System.Activities.NativeActivity> is an abstract class with a protected constructor.</span></span> <span data-ttu-id="afbf4-104">Gibi <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> uygulayarak kesinlik temelli davranışı yazmak için kullanılan bir <xref:System.Activities.NativeActivity.Execute%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="afbf4-104">Like <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> is used for writing imperative behavior by implementing an <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span> <span data-ttu-id="afbf4-105">Farklı <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> tüm iş akışı çalışma zamanı sunulan özelliklerini erişimi <xref:System.Activities.NativeActivityContext> nesne geçirilen <xref:System.Activities.NativeActivity.Execute%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="afbf4-105">Unlike <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> has access to all of the exposed features of the workflow runtime through the <xref:System.Activities.NativeActivityContext> object passed to the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>  
  
## <a name="using-nativeactivitycontext"></a><span data-ttu-id="afbf4-106">NativeActivityContext kullanma</span><span class="sxs-lookup"><span data-stu-id="afbf4-106">Using NativeActivityContext</span></span>  
 <span data-ttu-id="afbf4-107">İş akışı çalışma zamanı özelliklerini erişilebilir içinden <xref:System.Activities.NativeActivity.Execute%2A> üyeleri kullanarak yöntemi `context` parametresinin türü <xref:System.Activities.NativeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="afbf4-107">Features of the workflow runtime can be accessed from within the <xref:System.Activities.NativeActivity.Execute%2A> method by using members of the `context` parameter, of type <xref:System.Activities.NativeActivityContext>.</span></span> <span data-ttu-id="afbf4-108">Aracılığıyla kullanılabilen özelliklerin <xref:System.Activities.NativeActivityContext> şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="afbf4-108">The features available through <xref:System.Activities.NativeActivityContext> include the following:</span></span>  
  
-   <span data-ttu-id="afbf4-109">Alma ve bağımsız değişkenleri ve değişkenleri ayarlama.</span><span class="sxs-lookup"><span data-stu-id="afbf4-109">Getting and setting of arguments and variables.</span></span>  
  
-   <span data-ttu-id="afbf4-110">Bağımlı etkinliklerle planlama<xref:System.Activities.NativeActivityContext.ScheduleActivity%2A></span><span class="sxs-lookup"><span data-stu-id="afbf4-110">Scheduling child activities with <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A></span></span>  
  
-   <span data-ttu-id="afbf4-111">Durduruluyor etkinlik kullanılarak yürütme <xref:System.Activities.NativeActivityContext.Abort%2A>.</span><span class="sxs-lookup"><span data-stu-id="afbf4-111">Aborting activity execution using <xref:System.Activities.NativeActivityContext.Abort%2A>.</span></span>  
  
-   <span data-ttu-id="afbf4-112">İptal etme alt kullanılarak yürütme <xref:System.Activities.NativeActivityContext.CancelChild%2A> ve <xref:System.Activities.NativeActivityContext.CancelChildren%2A>.</span><span class="sxs-lookup"><span data-stu-id="afbf4-112">Canceling child execution using <xref:System.Activities.NativeActivityContext.CancelChild%2A> and <xref:System.Activities.NativeActivityContext.CancelChildren%2A>.</span></span>  
  
-   <span data-ttu-id="afbf4-113">Etkinlik yer işaretleri gibi yöntemlerle olarak erişim <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>, <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A>, ve <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A>.</span><span class="sxs-lookup"><span data-stu-id="afbf4-113">Access to activity bookmarks using such methods as <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>, <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A>, and <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A>.</span></span>  
  
-   <span data-ttu-id="afbf4-114">Özel İzleme özelliklerini kullanarak <xref:System.Activities.CodeActivityContext.Track%2A>.</span><span class="sxs-lookup"><span data-stu-id="afbf4-114">Custom tracking features using <xref:System.Activities.CodeActivityContext.Track%2A>.</span></span>  
  
-   <span data-ttu-id="afbf4-115">Etkinliğin yürütme özellikleri ve değer özelliklerini kullanarak erişim <xref:System.Activities.CodeActivityContext.GetProperty%2A> ve <xref:System.Activities.NativeActivityContext.GetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="afbf4-115">Access to the activity’s execution properties and value properties using <xref:System.Activities.CodeActivityContext.GetProperty%2A> and <xref:System.Activities.NativeActivityContext.GetValue%2A>.</span></span>  
  
-   <span data-ttu-id="afbf4-116">Etkinlik eylemleri ve işlevleri kullanarak zamanlama <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> ve <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>.</span><span class="sxs-lookup"><span data-stu-id="afbf4-116">Scheduling activity actions and functions using <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> and <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>.</span></span>  
  
#### <a name="to-create-a-custom-activity-that-inherits-from-nativeactivity"></a><span data-ttu-id="afbf4-117">NativeActivity devralan bir özel etkinlik oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="afbf4-117">To create a custom activity that inherits from NativeActivity</span></span>  
  
1.  <span data-ttu-id="afbf4-118">Açık[!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="afbf4-118">Open[!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="afbf4-119">Seçin **dosya**, **yeni**ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="afbf4-119">Select **File**, **New**, and then **Project**.</span></span> <span data-ttu-id="afbf4-120">Seçin **Workflow 4.0** altında **Visual C#** içinde **proje türleri** penceresi ve select **v2010** düğümü.</span><span class="sxs-lookup"><span data-stu-id="afbf4-120">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="afbf4-121">Seçin **etkinlik Kitaplığı** içinde **şablonları** penceresi.</span><span class="sxs-lookup"><span data-stu-id="afbf4-121">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="afbf4-122">Yeni Proje HelloActivity olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="afbf4-122">Name the new project HelloActivity.</span></span>  
  
3.  <span data-ttu-id="afbf4-123">Activity1.XAML HelloActivity projeye sağ tıklayıp **silmek**.</span><span class="sxs-lookup"><span data-stu-id="afbf4-123">Right-click Activity1.xaml in the HelloActivity project and select **Delete**.</span></span>  
  
4.  <span data-ttu-id="afbf4-124">HelloActivity projesine sağ tıklatın ve **Ekle**ve ardından **sınıfı**.</span><span class="sxs-lookup"><span data-stu-id="afbf4-124">Right-click the HelloActivity project and select **Add**, and then **Class**.</span></span> <span data-ttu-id="afbf4-125">Yeni sınıf HelloActivity.cs olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="afbf4-125">Name the new class HelloActivity.cs.</span></span>  
  
5.  <span data-ttu-id="afbf4-126">Aşağıdaki HelloActivity.cs dosyasına ekleyin `using` yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="afbf4-126">In the HelloActivity.cs file, add the following `using` directives.</span></span>  
  
    ```csharp  
    using System.Activities;  
    using System.Activities.Statements;  
    ```  
  
6.  <span data-ttu-id="afbf4-127">Devralınan yeni sınıf olun <xref:System.Activities.NativeActivity> bir taban sınıfı için sınıf bildirimi ekleyerek.</span><span class="sxs-lookup"><span data-stu-id="afbf4-127">Make the new class inherit from <xref:System.Activities.NativeActivity> by adding a base class to the class declaration.</span></span>  
  
    ```csharp  
    class HelloActivity : NativeActivity  
    ```  
  
7.  <span data-ttu-id="afbf4-128">İşlevselliği sınıfa ekleyerek bir <xref:System.Activities.NativeActivity.Execute%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="afbf4-128">Add functionality to the class by adding an <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>  
  
    ```csharp  
    protected override void Execute(NativeActivityContext context)  
    {  
        Console.WriteLine("Hello World!");  
    }  
    ```  
  
8.  <span data-ttu-id="afbf4-129">Geçersiz kılma <xref:System.Activities.NativeActivity.CacheMetadata%2A> yöntemi ve özel etkinliğin değişkenleri, bağımsız değişkenler, alt ve temsilciler hakkında bilmeniz iş akışı çalışma zamanı izin vermek için uygun Ekle yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="afbf4-129">Override the <xref:System.Activities.NativeActivity.CacheMetadata%2A> method and call the appropriate Add method to let the workflow runtime know about the custom activity’s variables, arguments, children, and delegates.</span></span> <span data-ttu-id="afbf4-130">Daha fazla bilgi için bkz: <xref:System.Activities.NativeActivityMetadata> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="afbf4-130">For more information see the <xref:System.Activities.NativeActivityMetadata> class.</span></span>  
  
9. <span data-ttu-id="afbf4-131">Kullanım <xref:System.Activities.NativeActivityContext> yer işareti zamanlamak için nesne.</span><span class="sxs-lookup"><span data-stu-id="afbf4-131">Use the <xref:System.Activities.NativeActivityContext> object to schedule a bookmark.</span></span> <span data-ttu-id="afbf4-132">Bkz: <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A> nasıl oluşturulacağı hakkında bilgi için zamanlamak ve bir yer işareti devam edin.</span><span class="sxs-lookup"><span data-stu-id="afbf4-132">See <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A> for details on how to create, schedule, and resume a bookmark.</span></span>  
  
    ```  
    protected override void Execute(NativeActivityContext context)  
        {  
            // Create a Bookmark and wait for it to be resumed.  
            context.CreateBookmark(BookmarkName.Get(context),   
                new BookmarkCallback(OnResumeBookmark));  
        }  
    ```
