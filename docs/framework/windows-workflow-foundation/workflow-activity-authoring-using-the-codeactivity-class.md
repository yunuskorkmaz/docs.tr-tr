---
title: İş akışı etkinlik CodeActivity sınıfını kullanarak geliştirme
ms.date: 03/30/2017
ms.assetid: cfe315c1-f86d-43ec-b9ce-2f8c469b1106
ms.openlocfilehash: 6a78c4399db0c4d207921544d5faa4da022dd107
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516883"
---
# <a name="workflow-activity-authoring-using-the-codeactivity-class"></a><span data-ttu-id="5eae1-102">İş akışı etkinlik CodeActivity sınıfını kullanarak geliştirme</span><span class="sxs-lookup"><span data-stu-id="5eae1-102">Workflow Activity Authoring Using the CodeActivity Class</span></span>
<span data-ttu-id="5eae1-103">İçinden devralma tarafından oluşturulan etkinlikleri <xref:System.Activities.CodeActivity> temel kesinlik temelli davranışı geçersiz kılarak uygulayabilirsiniz <xref:System.Activities.CodeActivity.Execute%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5eae1-103">Activities created by inheriting from <xref:System.Activities.CodeActivity> can implement basic imperative behavior by overriding the <xref:System.Activities.CodeActivity.Execute%2A> method.</span></span>  
  
## <a name="using-codeactivitycontext"></a><span data-ttu-id="5eae1-104">CodeActivityContext kullanma</span><span class="sxs-lookup"><span data-stu-id="5eae1-104">Using CodeActivityContext</span></span>  
 <span data-ttu-id="5eae1-105">İş akışı çalışma zamanı özelliklerini erişilebilir içinden <xref:System.Activities.CodeActivity.Execute%2A> üyeleri kullanarak yöntemi `context` parametresinin türü <xref:System.Activities.CodeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="5eae1-105">Features of the workflow runtime can be accessed from within the <xref:System.Activities.CodeActivity.Execute%2A> method by using members of the `context` parameter, of type <xref:System.Activities.CodeActivityContext>.</span></span> <span data-ttu-id="5eae1-106">Aracılığıyla kullanılabilen özelliklerin <xref:System.Activities.CodeActivityContext> şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="5eae1-106">The features available through <xref:System.Activities.CodeActivityContext> include the following:</span></span>  
  
-   <span data-ttu-id="5eae1-107">Bağımsız değişkenler ve değerleri ayarlama ve alma.</span><span class="sxs-lookup"><span data-stu-id="5eae1-107">Getting and setting the values of variables and arguments.</span></span>  
  
-   <span data-ttu-id="5eae1-108">Özel İzleme özelliklerini kullanarak <xref:System.Activities.CodeActivityContext.Track%2A>.</span><span class="sxs-lookup"><span data-stu-id="5eae1-108">Custom tracking features using <xref:System.Activities.CodeActivityContext.Track%2A>.</span></span>  
  
-   <span data-ttu-id="5eae1-109">Etkinliğin yürütme özelliklerini kullanarak erişimi <xref:System.Activities.CodeActivityContext.GetProperty%2A>.</span><span class="sxs-lookup"><span data-stu-id="5eae1-109">Access to the activity’s execution properties using <xref:System.Activities.CodeActivityContext.GetProperty%2A>.</span></span>  
  
#### <a name="to-create-a-custom-activity-that-inherits-from-codeactivity"></a><span data-ttu-id="5eae1-110">CodeActivity devralan bir özel etkinlik oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="5eae1-110">To create a custom activity that inherits from CodeActivity</span></span>  
  
1.  <span data-ttu-id="5eae1-111">Açık[!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5eae1-111">Open[!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="5eae1-112">Seçin **dosya**, **yeni**ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="5eae1-112">Select **File**, **New**, and then **Project**.</span></span> <span data-ttu-id="5eae1-113">Seçin **Workflow 4.0** altında **Visual C#** içinde **proje türleri** penceresi ve select **v2010** düğümü.</span><span class="sxs-lookup"><span data-stu-id="5eae1-113">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="5eae1-114">Seçin **etkinlik Kitaplığı** içinde **şablonları** penceresi.</span><span class="sxs-lookup"><span data-stu-id="5eae1-114">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="5eae1-115">Yeni Proje HelloActivity olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="5eae1-115">Name the new project HelloActivity.</span></span>  
  
3.  <span data-ttu-id="5eae1-116">Activity1.XAML HelloActivity projeye sağ tıklayıp **silmek**.</span><span class="sxs-lookup"><span data-stu-id="5eae1-116">Right-click Activity1.xaml in the HelloActivity project and select **Delete**.</span></span>  
  
4.  <span data-ttu-id="5eae1-117">HelloActivity projesine sağ tıklatın ve **Ekle** ve ardından **sınıfı**.</span><span class="sxs-lookup"><span data-stu-id="5eae1-117">Right-click the HelloActivity project and select **Add** , and then **Class**.</span></span> <span data-ttu-id="5eae1-118">Yeni sınıf HelloActivity.cs olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="5eae1-118">Name the new class HelloActivity.cs.</span></span>  
  
5.  <span data-ttu-id="5eae1-119">Aşağıdaki HelloActivity.cs dosyasına ekleyin `using` yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="5eae1-119">In the HelloActivity.cs file, add the following `using` directives.</span></span>  
  
    ```csharp  
    using System.Activities;  
    using System.Activities.Statements;  
    ```  
  
6.  <span data-ttu-id="5eae1-120">Devralınan yeni sınıf olun <xref:System.Activities.CodeActivity> bir taban sınıfı için sınıf bildirimi ekleyerek.</span><span class="sxs-lookup"><span data-stu-id="5eae1-120">Make the new class inherit from <xref:System.Activities.CodeActivity> by adding a base class to the class declaration.</span></span>  
  
    ```csharp  
    class HelloActivity : CodeActivity  
    ```  
  
7.  <span data-ttu-id="5eae1-121">İşlevselliği sınıfa ekleyerek bir <xref:System.Activities.CodeActivity.Execute%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5eae1-121">Add functionality to the class by adding an <xref:System.Activities.CodeActivity.Execute%2A> method.</span></span>  
  
    ```csharp  
    protected override void Execute(CodeActivityContext context)  
    {  
        Console.WriteLine("Hello World!");  
    }  
    ```  
  
8.  <span data-ttu-id="5eae1-122">Kullanım <xref:System.Activities.CodeActivityContext> izleme kaydı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5eae1-122">Use the <xref:System.Activities.CodeActivityContext> to create a tracking record.</span></span>  
  
    ```csharp  
    protected override void Execute(CodeActivityContext context)  
    {  
        Console.WriteLine("Hello World!");  
        CustomTrackingRecord record = new CustomTrackingRecord("MyRecord");  
        record.Data.Add(new KeyValuePair<String, Object>("ExecutionTime", DateTime.Now));  
        context.Track(record);  
    }  
    ```
