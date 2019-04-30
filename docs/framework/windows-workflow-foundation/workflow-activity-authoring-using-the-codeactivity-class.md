---
title: CodeActivity sınıfını kullanarak iş akışı etkinliği yazma
ms.date: 03/30/2017
ms.assetid: cfe315c1-f86d-43ec-b9ce-2f8c469b1106
ms.openlocfilehash: 549acec8b8101312d48bd20e63a4a988b798ff38
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669452"
---
# <a name="workflow-activity-authoring-using-the-codeactivity-class"></a><span data-ttu-id="88e7c-102">CodeActivity sınıfını kullanarak iş akışı etkinliği yazma</span><span class="sxs-lookup"><span data-stu-id="88e7c-102">Workflow Activity Authoring Using the CodeActivity Class</span></span>
<span data-ttu-id="88e7c-103">Devralarak oluşturulan etkinlikleri <xref:System.Activities.CodeActivity> temel kesinlik temelli davranışını geçersiz kılarak uygulayabilirsiniz <xref:System.Activities.CodeActivity.Execute%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="88e7c-103">Activities created by inheriting from <xref:System.Activities.CodeActivity> can implement basic imperative behavior by overriding the <xref:System.Activities.CodeActivity.Execute%2A> method.</span></span>

## <a name="using-codeactivitycontext"></a><span data-ttu-id="88e7c-104">CodeActivityContext kullanma</span><span class="sxs-lookup"><span data-stu-id="88e7c-104">Using CodeActivityContext</span></span>
 <span data-ttu-id="88e7c-105">İş akışı çalışma zamanı özellikleri içinden erişilebilir <xref:System.Activities.CodeActivity.Execute%2A> üyeleri kullanarak yöntemi `context` türünde parametre <xref:System.Activities.CodeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="88e7c-105">Features of the workflow runtime can be accessed from within the <xref:System.Activities.CodeActivity.Execute%2A> method by using members of the `context` parameter, of type <xref:System.Activities.CodeActivityContext>.</span></span> <span data-ttu-id="88e7c-106">Aracılığıyla kullanılabilen özellikleri <xref:System.Activities.CodeActivityContext> şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="88e7c-106">The features available through <xref:System.Activities.CodeActivityContext> include the following:</span></span>

- <span data-ttu-id="88e7c-107">Alma ve değişkenleri ve bağımsız değişken değerlerini ayarlama.</span><span class="sxs-lookup"><span data-stu-id="88e7c-107">Getting and setting the values of variables and arguments.</span></span>

- <span data-ttu-id="88e7c-108">Özel İzleme özelliklerini kullanarak <xref:System.Activities.CodeActivityContext.Track%2A>.</span><span class="sxs-lookup"><span data-stu-id="88e7c-108">Custom tracking features using <xref:System.Activities.CodeActivityContext.Track%2A>.</span></span>

- <span data-ttu-id="88e7c-109">Kullanarak Etkinlik yürütme özelliklerine erişimi <xref:System.Activities.CodeActivityContext.GetProperty%2A>.</span><span class="sxs-lookup"><span data-stu-id="88e7c-109">Access to the activity’s execution properties using <xref:System.Activities.CodeActivityContext.GetProperty%2A>.</span></span>

#### <a name="to-create-a-custom-activity-that-inherits-from-codeactivity"></a><span data-ttu-id="88e7c-110">CodeActivity devralan bir özel etkinlik oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="88e7c-110">To create a custom activity that inherits from CodeActivity</span></span>

1. <span data-ttu-id="88e7c-111">Visual Studio 2010'u açın.</span><span class="sxs-lookup"><span data-stu-id="88e7c-111">Open Visual Studio 2010.</span></span>

2. <span data-ttu-id="88e7c-112">Seçin **dosya**, **yeni**, ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="88e7c-112">Select **File**, **New**, and then **Project**.</span></span> <span data-ttu-id="88e7c-113">Seçin **Workflow 4.0** altında **Visual C#** içinde **proje türleri** penceresi ve select **v2010** düğümü.</span><span class="sxs-lookup"><span data-stu-id="88e7c-113">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="88e7c-114">Seçin **etkinlik Kitaplığı** içinde **şablonları** penceresi.</span><span class="sxs-lookup"><span data-stu-id="88e7c-114">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="88e7c-115">Yeni Proje HelloActivity adı.</span><span class="sxs-lookup"><span data-stu-id="88e7c-115">Name the new project HelloActivity.</span></span>

3. <span data-ttu-id="88e7c-116">Gt;activity1.XAML HelloActivity projeye sağ tıklayıp **Sil**.</span><span class="sxs-lookup"><span data-stu-id="88e7c-116">Right-click Activity1.xaml in the HelloActivity project and select **Delete**.</span></span>

4. <span data-ttu-id="88e7c-117">HelloActivity projeye sağ tıklayıp **Ekle** , ardından **sınıfı**.</span><span class="sxs-lookup"><span data-stu-id="88e7c-117">Right-click the HelloActivity project and select **Add** , and then **Class**.</span></span> <span data-ttu-id="88e7c-118">Yeni bir sınıf HelloActivity.cs adı.</span><span class="sxs-lookup"><span data-stu-id="88e7c-118">Name the new class HelloActivity.cs.</span></span>

5. <span data-ttu-id="88e7c-119">HelloActivity.cs dosyasına aşağıdakileri ekleyin `using` yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="88e7c-119">In the HelloActivity.cs file, add the following `using` directives.</span></span>

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    ```

6. <span data-ttu-id="88e7c-120">Devralınan yeni bir sınıf olun <xref:System.Activities.CodeActivity> için sınıf bildiriminin bir temel sınıf ekleyerek.</span><span class="sxs-lookup"><span data-stu-id="88e7c-120">Make the new class inherit from <xref:System.Activities.CodeActivity> by adding a base class to the class declaration.</span></span>

    ```csharp
    class HelloActivity : CodeActivity
    ```

7. <span data-ttu-id="88e7c-121">Ekleyerek sınıfına işlevsellik ekleme bir <xref:System.Activities.CodeActivity.Execute%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="88e7c-121">Add functionality to the class by adding an <xref:System.Activities.CodeActivity.Execute%2A> method.</span></span>

    ```csharp
    protected override void Execute(CodeActivityContext context)
    {
        Console.WriteLine("Hello World!");
    }
    ```

8. <span data-ttu-id="88e7c-122">Kullanım <xref:System.Activities.CodeActivityContext> bir izleme kaydını oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="88e7c-122">Use the <xref:System.Activities.CodeActivityContext> to create a tracking record.</span></span>

    ```csharp
    protected override void Execute(CodeActivityContext context)
    {
        Console.WriteLine("Hello World!");
        CustomTrackingRecord record = new CustomTrackingRecord("MyRecord");
        record.Data.Add(new KeyValuePair<String, Object>("ExecutionTime", DateTime.Now));
        context.Track(record);
    }
    ```
