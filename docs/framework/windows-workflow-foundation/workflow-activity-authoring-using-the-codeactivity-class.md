---
title: CodeActivity sınıfını kullanarak iş akışı etkinlik yazma
ms.date: 03/30/2017
ms.assetid: cfe315c1-f86d-43ec-b9ce-2f8c469b1106
ms.openlocfilehash: 714e0971a006db20d002b0f3a486533b1357fba7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293825"
---
# <a name="workflow-activity-authoring-using-the-codeactivity-class"></a><span data-ttu-id="5de64-102">CodeActivity sınıfını kullanarak iş akışı etkinlik yazma</span><span class="sxs-lookup"><span data-stu-id="5de64-102">Workflow Activity Authoring Using the CodeActivity Class</span></span>

<span data-ttu-id="5de64-103">Devralma tarafından oluşturulan etkinlikler <xref:System.Activities.CodeActivity> , yöntemi geçersiz kılarak temel kesinlik davranışını uygulayabilir <xref:System.Activities.CodeActivity.Execute%2A> .</span><span class="sxs-lookup"><span data-stu-id="5de64-103">Activities created by inheriting from <xref:System.Activities.CodeActivity> can implement basic imperative behavior by overriding the <xref:System.Activities.CodeActivity.Execute%2A> method.</span></span>

## <a name="using-codeactivitycontext"></a><span data-ttu-id="5de64-104">CodeActivityContext kullanma</span><span class="sxs-lookup"><span data-stu-id="5de64-104">Using CodeActivityContext</span></span>

 <span data-ttu-id="5de64-105">İş akışı çalışma zamanının özelliklerine <xref:System.Activities.CodeActivity.Execute%2A> , türünün ' nin üyelerini kullanarak yönteminin içinden erişilebilir `context` <xref:System.Activities.CodeActivityContext> .</span><span class="sxs-lookup"><span data-stu-id="5de64-105">Features of the workflow runtime can be accessed from within the <xref:System.Activities.CodeActivity.Execute%2A> method by using members of the `context` parameter, of type <xref:System.Activities.CodeActivityContext>.</span></span> <span data-ttu-id="5de64-106">Aracılığıyla kullanılabilen özellikler şunları <xref:System.Activities.CodeActivityContext> içerir:</span><span class="sxs-lookup"><span data-stu-id="5de64-106">The features available through <xref:System.Activities.CodeActivityContext> include the following:</span></span>

- <span data-ttu-id="5de64-107">Değişkenlerin ve bağımsız değişkenlerin değerlerini alma ve ayarlama.</span><span class="sxs-lookup"><span data-stu-id="5de64-107">Getting and setting the values of variables and arguments.</span></span>

- <span data-ttu-id="5de64-108">Kullanarak özel izleme özellikleri <xref:System.Activities.CodeActivityContext.Track%2A> .</span><span class="sxs-lookup"><span data-stu-id="5de64-108">Custom tracking features using <xref:System.Activities.CodeActivityContext.Track%2A>.</span></span>

- <span data-ttu-id="5de64-109">Kullanılarak etkinliğin yürütme özelliklerine erişin <xref:System.Activities.CodeActivityContext.GetProperty%2A> .</span><span class="sxs-lookup"><span data-stu-id="5de64-109">Access to the activity’s execution properties using <xref:System.Activities.CodeActivityContext.GetProperty%2A>.</span></span>

#### <a name="to-create-a-custom-activity-that-inherits-from-codeactivity"></a><span data-ttu-id="5de64-110">CodeActivity 'den devralan özel etkinlik oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="5de64-110">To create a custom activity that inherits from CodeActivity</span></span>

1. <span data-ttu-id="5de64-111">Visual Studio 2010 ' i açın.</span><span class="sxs-lookup"><span data-stu-id="5de64-111">Open Visual Studio 2010.</span></span>

2. <span data-ttu-id="5de64-112">**Dosya**, **Yeni** ve ardından **Proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="5de64-112">Select **File**, **New**, and then **Project**.</span></span> <span data-ttu-id="5de64-113">**Proje türleri** penceresinde **Visual C#** altında **iş akışı 4,0** ' i seçin ve **v2010** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="5de64-113">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="5de64-114">**Şablonlar** penceresinde **etkinlik kitaplığı** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="5de64-114">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="5de64-115">Yeni proje Merhaba etkinliğini adlandırın.</span><span class="sxs-lookup"><span data-stu-id="5de64-115">Name the new project HelloActivity.</span></span>

3. <span data-ttu-id="5de64-116">Merhaba etkinlik projesinde Activity1. xaml öğesine sağ tıklayın ve **Sil**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="5de64-116">Right-click Activity1.xaml in the HelloActivity project and select **Delete**.</span></span>

4. <span data-ttu-id="5de64-117">Merhaba etkinlik projesine sağ tıklayın ve **Ekle** ' yi ve ardından **sınıf**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="5de64-117">Right-click the HelloActivity project and select **Add** , and then **Class**.</span></span> <span data-ttu-id="5de64-118">Yeni sınıfı HelloActivity.cs olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="5de64-118">Name the new class HelloActivity.cs.</span></span>

5. <span data-ttu-id="5de64-119">HelloActivity.cs dosyasında aşağıdaki `using` yönergeleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5de64-119">In the HelloActivity.cs file, add the following `using` directives.</span></span>

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    ```

6. <span data-ttu-id="5de64-120"><xref:System.Activities.CodeActivity>Sınıf bildirimine bir temel sınıf ekleyerek yeni sınıfın öğesinden devralmasını sağlayın.</span><span class="sxs-lookup"><span data-stu-id="5de64-120">Make the new class inherit from <xref:System.Activities.CodeActivity> by adding a base class to the class declaration.</span></span>

    ```csharp
    class HelloActivity : CodeActivity
    ```

7. <span data-ttu-id="5de64-121">Bir yöntem ekleyerek sınıfa işlevsellik ekleyin <xref:System.Activities.CodeActivity.Execute%2A> .</span><span class="sxs-lookup"><span data-stu-id="5de64-121">Add functionality to the class by adding an <xref:System.Activities.CodeActivity.Execute%2A> method.</span></span>

    ```csharp
    protected override void Execute(CodeActivityContext context)
    {
        Console.WriteLine("Hello World!");
    }
    ```

8. <span data-ttu-id="5de64-122"><xref:System.Activities.CodeActivityContext>İzleme kaydı oluşturmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="5de64-122">Use the <xref:System.Activities.CodeActivityContext> to create a tracking record.</span></span>

    ```csharp
    protected override void Execute(CodeActivityContext context)
    {
        Console.WriteLine("Hello World!");
        CustomTrackingRecord record = new CustomTrackingRecord("MyRecord");
        record.Data.Add(new KeyValuePair<String, Object>("ExecutionTime", DateTime.Now));
        context.Track(record);
    }
    ```
