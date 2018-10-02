---
title: Bir etkinlik, Dynamicactivity'nin ile çalışma zamanında oluşturma
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: 880dbc6263b64c877d3211347541766d91534c85
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48027370"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a><span data-ttu-id="7b27f-102">Bir etkinlik, Dynamicactivity'nin ile çalışma zamanında oluşturma</span><span class="sxs-lookup"><span data-stu-id="7b27f-102">Creating an Activity at Runtime with DynamicActivity</span></span>
<span data-ttu-id="7b27f-103"><xref:System.Activities.DynamicActivity> bir somut, korumalı bir public Oluşturucu ile sınıftır.</span><span class="sxs-lookup"><span data-stu-id="7b27f-103"><xref:System.Activities.DynamicActivity> is a concrete, sealed class with a public constructor.</span></span> <span data-ttu-id="7b27f-104"><xref:System.Activities.DynamicActivity> bir etkinlik yerli kullanarak çalışma zamanında etkinlik işlevselliğini bir araya getirmek için kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="7b27f-104"><xref:System.Activities.DynamicActivity> can be used to assemble activity functionality at runtime using an activity DOM.</span></span>  
  
## <a name="dynamicactivity-features"></a><span data-ttu-id="7b27f-105">DynamicActivity özellikleri</span><span class="sxs-lookup"><span data-stu-id="7b27f-105">DynamicActivity Features</span></span>  
 <span data-ttu-id="7b27f-106"><xref:System.Activities.DynamicActivity> yürütme özellikleri ve bağımsız değişkenler için erişim, ancak hiçbir alt etkinlikler zamanlamak veya izleme gibi çalışma zamanı hizmetlerine erişim vardır.</span><span class="sxs-lookup"><span data-stu-id="7b27f-106"><xref:System.Activities.DynamicActivity> has access to execution properties, arguments and variables, but no access to run-time services such as scheduling child activities or tracking.</span></span>  
  
 <span data-ttu-id="7b27f-107">İş akışı kullanarak üst düzey özellikleri ayarlanabilir <xref:System.Activities.Argument> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="7b27f-107">Top-level properties can be set using workflow <xref:System.Activities.Argument> objects.</span></span> <span data-ttu-id="7b27f-108">Kesinlik temelli kod içinde bu bağımsız değişkenler CLR özellikleri yeni bir türü kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7b27f-108">In imperative code, these arguments are created using CLR properties on a new type.</span></span> <span data-ttu-id="7b27f-109">XAML içinde kullanılarak bildirilirler `x:Class` ve `x:Member` etiketler.</span><span class="sxs-lookup"><span data-stu-id="7b27f-109">In XAML, they are declared using `x:Class` and `x:Member` tags.</span></span>  
  
 <span data-ttu-id="7b27f-110">Kullanılarak oluşturulan etkinlikleri <xref:System.Activities.DynamicActivity> Tasarımcısı kullanarak arabirimi <xref:System.ComponentModel.ICustomTypeDescriptor>.</span><span class="sxs-lookup"><span data-stu-id="7b27f-110">Activities constructed using <xref:System.Activities.DynamicActivity> interface with the designer using <xref:System.ComponentModel.ICustomTypeDescriptor>.</span></span> <span data-ttu-id="7b27f-111">Tasarımcısı'nda oluşturulan etkinlikleri kullanarak dinamik olarak yüklenebilir <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, aşağıdaki yordamda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="7b27f-111">Activities created in the designer can be loaded dynamically using <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, as demonstrated in the following procedure.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a><span data-ttu-id="7b27f-112">Kesin kod kullanarak çalışma zamanında bir etkinlik oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="7b27f-112">To create an activity at runtime using imperative code</span></span>  
  
1.  <span data-ttu-id="7b27f-113">Açık[!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7b27f-113">Open[!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="7b27f-114">Seçin **dosya**, **yeni**, **proje**.</span><span class="sxs-lookup"><span data-stu-id="7b27f-114">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="7b27f-115">Seçin **Workflow 4.0** altında **Visual C#** içinde **proje türleri** penceresi ve select **v2010** düğümü.</span><span class="sxs-lookup"><span data-stu-id="7b27f-115">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="7b27f-116">Seçin **sıralı iş akışı konsol uygulaması** içinde **şablonları** penceresi.</span><span class="sxs-lookup"><span data-stu-id="7b27f-116">Select **Sequential Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="7b27f-117">Yeni Proje DynamicActivitySample adı.</span><span class="sxs-lookup"><span data-stu-id="7b27f-117">Name the new project DynamicActivitySample.</span></span>  
  
3.  <span data-ttu-id="7b27f-118">Workflow1.XAML HelloActivity projeye sağ tıklayıp **Sil**.</span><span class="sxs-lookup"><span data-stu-id="7b27f-118">Right-click Workflow1.xaml in the HelloActivity project and select **Delete**.</span></span>  
  
4.  <span data-ttu-id="7b27f-119">Program.cs dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="7b27f-119">Open Program.cs.</span></span> <span data-ttu-id="7b27f-120">Aşağıdaki yönerge dosyasının en üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7b27f-120">Add the following directive to the top of the file.</span></span>  
  
    ```  
    using System.Collections.Generic;  
    ```  
  
5.  <span data-ttu-id="7b27f-121">Öğesinin içeriğini değiştirin `Main` yöntemini aşağıdaki kodla oluşturan bir <xref:System.Activities.Statements.Sequence> içeren tek bir etkinlik <xref:System.Activities.Statements.WriteLine> etkinlik ve atar <xref:System.Activities.DynamicActivity.Implementation%2A> yeni dinamik bir etkinliğin özelliği.</span><span class="sxs-lookup"><span data-stu-id="7b27f-121">Replace the contents of the `Main` method with the following code, which creates a <xref:System.Activities.Statements.Sequence> activity that contains a single <xref:System.Activities.Statements.WriteLine> activity and assigns it to the <xref:System.Activities.DynamicActivity.Implementation%2A> property of a new dynamic activity.</span></span>  
  
    ```csharp  
    //Define the input argument for the activity  
    var textOut = new InArgument<string>();  
    //Create the activity, property, and implementation  
                Activity dynamicWorkflow = new DynamicActivity()  
                {  
                    Properties =   
                    {  
                        new DynamicActivityProperty  
                        {  
                            Name = "Text",  
                            Type = typeof(InArgument<String>),  
                            Value = textOut  
                        }  
                    },  
                    Implementation = () => new Sequence()  
                    {  
                        Activities =   
                        {  
                            new WriteLine()  
                            {  
                                Text = new InArgument<string>(env => textOut.Get(env))  
                            }  
                        }  
                    }  
                };  
    //Execute the activity with a parameter dictionary  
                WorkflowInvoker.Invoke(dynamicWorkflow, new Dictionary<string, object> { { "Text", "Hello World!" } });  
                Console.ReadLine();  
    ```  
  
6.  <span data-ttu-id="7b27f-122">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7b27f-122">Execute the application.</span></span> <span data-ttu-id="7b27f-123">"Hello World!" metni ile bir konsol penceresi</span><span class="sxs-lookup"><span data-stu-id="7b27f-123">A console window with the text "Hello World!"</span></span> <span data-ttu-id="7b27f-124">görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7b27f-124">displays.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a><span data-ttu-id="7b27f-125">XAML kullanarak çalışma zamanında bir etkinlik oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="7b27f-125">To create an activity at runtime using XAML</span></span>  
  
1.  <span data-ttu-id="7b27f-126">Açık [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7b27f-126">Open [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="7b27f-127">Seçin **dosya**, **yeni**, **proje**.</span><span class="sxs-lookup"><span data-stu-id="7b27f-127">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="7b27f-128">Seçin **Workflow 4.0** altında **Visual C#** içinde **proje türleri** penceresi ve select **v2010** düğümü.</span><span class="sxs-lookup"><span data-stu-id="7b27f-128">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="7b27f-129">Seçin **iş akışı konsol uygulaması** içinde **şablonları** penceresi.</span><span class="sxs-lookup"><span data-stu-id="7b27f-129">Select  **Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="7b27f-130">Yeni Proje DynamicActivitySample adı.</span><span class="sxs-lookup"><span data-stu-id="7b27f-130">Name the new project DynamicActivitySample.</span></span>  
  
3.  <span data-ttu-id="7b27f-131">Workflow1.XAML HelloActivity projeyi açın.</span><span class="sxs-lookup"><span data-stu-id="7b27f-131">Open Workflow1.xaml in the HelloActivity project.</span></span> <span data-ttu-id="7b27f-132">Tıklayın **bağımsız değişkenleri** Tasarımcısı'nın altındaki seçeneği.</span><span class="sxs-lookup"><span data-stu-id="7b27f-132">Click the **Arguments** option at the bottom of the designer.</span></span> <span data-ttu-id="7b27f-133">Yeni bir `In` bağımsız değişken olarak adlandırılan `TextToWrite` türü `String`.</span><span class="sxs-lookup"><span data-stu-id="7b27f-133">Create a new `In` argument called `TextToWrite` of type `String`.</span></span>  
  
4.  <span data-ttu-id="7b27f-134">Sürükleme bir **WriteLine** etkinliğinden **Temelleri** Tasarımcı yüzeyine araç bölümü.</span><span class="sxs-lookup"><span data-stu-id="7b27f-134">Drag a **WriteLine** activity from the **Primitives** section of the toolbox onto the designer surface.</span></span> <span data-ttu-id="7b27f-135">Değer atamak `TextToWrite` için **metin** etkinliğin özelliği.</span><span class="sxs-lookup"><span data-stu-id="7b27f-135">Assign the value `TextToWrite` to the **Text** property of the activity.</span></span>  
  
5.  <span data-ttu-id="7b27f-136">Program.cs dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="7b27f-136">Open Program.cs.</span></span> <span data-ttu-id="7b27f-137">Aşağıdaki yönerge dosyasının en üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7b27f-137">Add the following directive to the top of the file.</span></span>  
  
    ```  
    using System.Activities.XamlIntegration;  
    ```  
  
6.  <span data-ttu-id="7b27f-138">Öğesinin içeriğini değiştirin `Main` yöntemini aşağıdaki kod ile.</span><span class="sxs-lookup"><span data-stu-id="7b27f-138">Replace the contents of the `Main` method with the following code.</span></span>  
  
    ```  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7.  <span data-ttu-id="7b27f-139">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7b27f-139">Execute the application.</span></span> <span data-ttu-id="7b27f-140">"Hello World!" metni ile bir konsol penceresi</span><span class="sxs-lookup"><span data-stu-id="7b27f-140">A console window with the text "Hello World!"</span></span> <span data-ttu-id="7b27f-141">görünür.</span><span class="sxs-lookup"><span data-stu-id="7b27f-141">appears.</span></span>  
  
8.  <span data-ttu-id="7b27f-142">Workflow1.xaml dosyaya sağ **Çözüm Gezgini** seçip **kodu görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="7b27f-142">Right-click the Workflow1.xaml file in the **Solution Explorer** and select **View Code**.</span></span> <span data-ttu-id="7b27f-143">Etkinliği sınıf oluşturulur Not `x:Class` ve özelliği ile oluşturulan `x:Property`.</span><span class="sxs-lookup"><span data-stu-id="7b27f-143">Note that the activity class is created with `x:Class` and the property is created with `x:Property`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b27f-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7b27f-144">See Also</span></span>

- [<span data-ttu-id="7b27f-145">Kesin Kod Kullanarak İş Akışları, Etkinlikler ve İfadeler Yazma</span><span class="sxs-lookup"><span data-stu-id="7b27f-145">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md)