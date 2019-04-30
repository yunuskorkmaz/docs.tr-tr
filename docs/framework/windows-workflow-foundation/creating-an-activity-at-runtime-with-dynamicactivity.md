---
title: Bir etkinlik, Dynamicactivity'nin ile çalışma zamanında oluşturma
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: ed133e972caa9a3a62ab2ac1310cb1bd666947ce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774081"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a><span data-ttu-id="66d4a-102">Bir etkinlik, Dynamicactivity'nin ile çalışma zamanında oluşturma</span><span class="sxs-lookup"><span data-stu-id="66d4a-102">Creating an Activity at Runtime with DynamicActivity</span></span>
<span data-ttu-id="66d4a-103"><xref:System.Activities.DynamicActivity> bir somut, korumalı bir public Oluşturucu ile sınıftır.</span><span class="sxs-lookup"><span data-stu-id="66d4a-103"><xref:System.Activities.DynamicActivity> is a concrete, sealed class with a public constructor.</span></span> <span data-ttu-id="66d4a-104"><xref:System.Activities.DynamicActivity> bir etkinlik yerli kullanarak çalışma zamanında etkinlik işlevselliğini bir araya getirmek için kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="66d4a-104"><xref:System.Activities.DynamicActivity> can be used to assemble activity functionality at runtime using an activity DOM.</span></span>  
  
## <a name="dynamicactivity-features"></a><span data-ttu-id="66d4a-105">DynamicActivity özellikleri</span><span class="sxs-lookup"><span data-stu-id="66d4a-105">DynamicActivity Features</span></span>  
 <span data-ttu-id="66d4a-106"><xref:System.Activities.DynamicActivity> yürütme özellikleri ve bağımsız değişkenler için erişim, ancak hiçbir alt etkinlikler zamanlamak veya izleme gibi çalışma zamanı hizmetlerine erişim vardır.</span><span class="sxs-lookup"><span data-stu-id="66d4a-106"><xref:System.Activities.DynamicActivity> has access to execution properties, arguments and variables, but no access to run-time services such as scheduling child activities or tracking.</span></span>  
  
 <span data-ttu-id="66d4a-107">İş akışı kullanarak üst düzey özellikleri ayarlanabilir <xref:System.Activities.Argument> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="66d4a-107">Top-level properties can be set using workflow <xref:System.Activities.Argument> objects.</span></span> <span data-ttu-id="66d4a-108">Kesinlik temelli kod içinde bu bağımsız değişkenler CLR özellikleri yeni bir türü kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="66d4a-108">In imperative code, these arguments are created using CLR properties on a new type.</span></span> <span data-ttu-id="66d4a-109">XAML içinde kullanılarak bildirilirler `x:Class` ve `x:Member` etiketler.</span><span class="sxs-lookup"><span data-stu-id="66d4a-109">In XAML, they are declared using `x:Class` and `x:Member` tags.</span></span>  
  
 <span data-ttu-id="66d4a-110">Kullanılarak oluşturulan etkinlikleri <xref:System.Activities.DynamicActivity> Tasarımcısı kullanarak arabirimi <xref:System.ComponentModel.ICustomTypeDescriptor>.</span><span class="sxs-lookup"><span data-stu-id="66d4a-110">Activities constructed using <xref:System.Activities.DynamicActivity> interface with the designer using <xref:System.ComponentModel.ICustomTypeDescriptor>.</span></span> <span data-ttu-id="66d4a-111">Tasarımcısı'nda oluşturulan etkinlikleri kullanarak dinamik olarak yüklenebilir <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, aşağıdaki yordamda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="66d4a-111">Activities created in the designer can be loaded dynamically using <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, as demonstrated in the following procedure.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a><span data-ttu-id="66d4a-112">Kesin kod kullanarak çalışma zamanında bir etkinlik oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="66d4a-112">To create an activity at runtime using imperative code</span></span>  
  
1. <span data-ttu-id="66d4a-113">OpenVisual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="66d4a-113">OpenVisual Studio 2010.</span></span>  
  
2. <span data-ttu-id="66d4a-114">Seçin **dosya**, **yeni**, **proje**.</span><span class="sxs-lookup"><span data-stu-id="66d4a-114">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="66d4a-115">Seçin **Workflow 4.0** altında **Visual C#** içinde **proje türleri** penceresi ve select **v2010** düğümü.</span><span class="sxs-lookup"><span data-stu-id="66d4a-115">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="66d4a-116">Seçin **sıralı iş akışı konsol uygulaması** içinde **şablonları** penceresi.</span><span class="sxs-lookup"><span data-stu-id="66d4a-116">Select **Sequential Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="66d4a-117">Yeni Proje DynamicActivitySample adı.</span><span class="sxs-lookup"><span data-stu-id="66d4a-117">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="66d4a-118">Workflow1.XAML HelloActivity projeye sağ tıklayıp **Sil**.</span><span class="sxs-lookup"><span data-stu-id="66d4a-118">Right-click Workflow1.xaml in the HelloActivity project and select **Delete**.</span></span>  
  
4. <span data-ttu-id="66d4a-119">Program.cs dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="66d4a-119">Open Program.cs.</span></span> <span data-ttu-id="66d4a-120">Aşağıdaki yönerge dosyasının en üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="66d4a-120">Add the following directive to the top of the file.</span></span>  
  
    ```  
    using System.Collections.Generic;  
    ```  
  
5. <span data-ttu-id="66d4a-121">Öğesinin içeriğini değiştirin `Main` yöntemini aşağıdaki kodla oluşturan bir <xref:System.Activities.Statements.Sequence> içeren tek bir etkinlik <xref:System.Activities.Statements.WriteLine> etkinlik ve atar <xref:System.Activities.DynamicActivity.Implementation%2A> yeni dinamik bir etkinliğin özelliği.</span><span class="sxs-lookup"><span data-stu-id="66d4a-121">Replace the contents of the `Main` method with the following code, which creates a <xref:System.Activities.Statements.Sequence> activity that contains a single <xref:System.Activities.Statements.WriteLine> activity and assigns it to the <xref:System.Activities.DynamicActivity.Implementation%2A> property of a new dynamic activity.</span></span>  
  
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
  
6. <span data-ttu-id="66d4a-122">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="66d4a-122">Execute the application.</span></span> <span data-ttu-id="66d4a-123">"Hello World!" metni ile bir konsol penceresi</span><span class="sxs-lookup"><span data-stu-id="66d4a-123">A console window with the text "Hello World!"</span></span> <span data-ttu-id="66d4a-124">görüntüler.</span><span class="sxs-lookup"><span data-stu-id="66d4a-124">displays.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a><span data-ttu-id="66d4a-125">XAML kullanarak çalışma zamanında bir etkinlik oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="66d4a-125">To create an activity at runtime using XAML</span></span>  
  
1. <span data-ttu-id="66d4a-126">Visual Studio 2010'u açın.</span><span class="sxs-lookup"><span data-stu-id="66d4a-126">Open Visual Studio 2010.</span></span>  
  
2. <span data-ttu-id="66d4a-127">Seçin **dosya**, **yeni**, **proje**.</span><span class="sxs-lookup"><span data-stu-id="66d4a-127">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="66d4a-128">Seçin **Workflow 4.0** altında **Visual C#** içinde **proje türleri** penceresi ve select **v2010** düğümü.</span><span class="sxs-lookup"><span data-stu-id="66d4a-128">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="66d4a-129">Seçin **iş akışı konsol uygulaması** içinde **şablonları** penceresi.</span><span class="sxs-lookup"><span data-stu-id="66d4a-129">Select  **Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="66d4a-130">Yeni Proje DynamicActivitySample adı.</span><span class="sxs-lookup"><span data-stu-id="66d4a-130">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="66d4a-131">Workflow1.XAML HelloActivity projeyi açın.</span><span class="sxs-lookup"><span data-stu-id="66d4a-131">Open Workflow1.xaml in the HelloActivity project.</span></span> <span data-ttu-id="66d4a-132">Tıklayın **bağımsız değişkenleri** Tasarımcısı'nın altındaki seçeneği.</span><span class="sxs-lookup"><span data-stu-id="66d4a-132">Click the **Arguments** option at the bottom of the designer.</span></span> <span data-ttu-id="66d4a-133">Yeni bir `In` bağımsız değişken olarak adlandırılan `TextToWrite` türü `String`.</span><span class="sxs-lookup"><span data-stu-id="66d4a-133">Create a new `In` argument called `TextToWrite` of type `String`.</span></span>  
  
4. <span data-ttu-id="66d4a-134">Sürükleme bir **WriteLine** etkinliğinden **Temelleri** Tasarımcı yüzeyine araç bölümü.</span><span class="sxs-lookup"><span data-stu-id="66d4a-134">Drag a **WriteLine** activity from the **Primitives** section of the toolbox onto the designer surface.</span></span> <span data-ttu-id="66d4a-135">Değer atamak `TextToWrite` için **metin** etkinliğin özelliği.</span><span class="sxs-lookup"><span data-stu-id="66d4a-135">Assign the value `TextToWrite` to the **Text** property of the activity.</span></span>  
  
5. <span data-ttu-id="66d4a-136">Program.cs dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="66d4a-136">Open Program.cs.</span></span> <span data-ttu-id="66d4a-137">Aşağıdaki yönerge dosyasının en üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="66d4a-137">Add the following directive to the top of the file.</span></span>  
  
    ```  
    using System.Activities.XamlIntegration;  
    ```  
  
6. <span data-ttu-id="66d4a-138">Öğesinin içeriğini değiştirin `Main` yöntemini aşağıdaki kod ile.</span><span class="sxs-lookup"><span data-stu-id="66d4a-138">Replace the contents of the `Main` method with the following code.</span></span>  
  
    ```  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7. <span data-ttu-id="66d4a-139">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="66d4a-139">Execute the application.</span></span> <span data-ttu-id="66d4a-140">"Hello World!" metni ile bir konsol penceresi</span><span class="sxs-lookup"><span data-stu-id="66d4a-140">A console window with the text "Hello World!"</span></span> <span data-ttu-id="66d4a-141">görünür.</span><span class="sxs-lookup"><span data-stu-id="66d4a-141">appears.</span></span>  
  
8. <span data-ttu-id="66d4a-142">Workflow1.xaml dosyaya sağ **Çözüm Gezgini** seçip **kodu görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="66d4a-142">Right-click the Workflow1.xaml file in the **Solution Explorer** and select **View Code**.</span></span> <span data-ttu-id="66d4a-143">Etkinliği sınıf oluşturulur Not `x:Class` ve özelliği ile oluşturulan `x:Property`.</span><span class="sxs-lookup"><span data-stu-id="66d4a-143">Note that the activity class is created with `x:Class` and the property is created with `x:Property`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66d4a-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66d4a-144">See also</span></span>

- [<span data-ttu-id="66d4a-145">Kesin Kod Kullanarak İş Akışları, Etkinlikler ve İfadeler Yazma</span><span class="sxs-lookup"><span data-stu-id="66d4a-145">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](authoring-workflows-activities-and-expressions-using-imperative-code.md)
