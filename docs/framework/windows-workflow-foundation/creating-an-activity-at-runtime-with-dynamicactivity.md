---
title: "DynamicActivity ile çalışma zamanında bir etkinlik oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d40fe3601cb8ad7c4f77cf50825da1deace5644e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a><span data-ttu-id="39720-102">DynamicActivity ile çalışma zamanında bir etkinlik oluşturma</span><span class="sxs-lookup"><span data-stu-id="39720-102">Creating an Activity at Runtime with DynamicActivity</span></span>
<span data-ttu-id="39720-103"><xref:System.Activities.DynamicActivity>somut, korumalı bir public oluşturucuya sahip sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="39720-103"><xref:System.Activities.DynamicActivity> is a concrete, sealed class with a public constructor.</span></span> <span data-ttu-id="39720-104"><xref:System.Activities.DynamicActivity>bir etkinlik DOM kullanarak çalışma zamanında etkinlik işlevleri bir araya getirmek için kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="39720-104"><xref:System.Activities.DynamicActivity> can be used to assemble activity functionality at runtime using an activity DOM.</span></span>  
  
## <a name="dynamicactivity-features"></a><span data-ttu-id="39720-105">DynamicActivity özellikleri</span><span class="sxs-lookup"><span data-stu-id="39720-105">DynamicActivity Features</span></span>  
 <span data-ttu-id="39720-106"><xref:System.Activities.DynamicActivity>yürütme özellikleri, bağımsız değişkenleri ve değişkenleri erişimi, ancak alt etkinlikler zamanlama veya izleme gibi çalışma zamanı Hizmetleri erişimi vardır.</span><span class="sxs-lookup"><span data-stu-id="39720-106"><xref:System.Activities.DynamicActivity> has access to execution properties, arguments and variables, but no access to run-time services such as scheduling child activities or tracking.</span></span>  
  
 <span data-ttu-id="39720-107">İş akışı kullanarak üst düzey özellikleri ayarlanabilir <xref:System.Activities.Argument> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="39720-107">Top-level properties can be set using workflow <xref:System.Activities.Argument> objects.</span></span> <span data-ttu-id="39720-108">Kesinlik temelli kodda, bu bağımsız değişkenler, yeni bir tür CLR özellikleri kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="39720-108">In imperative code, these arguments are created using CLR properties on a new type.</span></span> <span data-ttu-id="39720-109">XAML'de, bunlar kullanılarak bildirilen `x:Class` ve `x:Member` etiketler.</span><span class="sxs-lookup"><span data-stu-id="39720-109">In XAML, they are declared using `x:Class` and `x:Member` tags.</span></span>  
  
 <span data-ttu-id="39720-110">Kullanılarak oluşturulan etkinlikleri <xref:System.Activities.DynamicActivity> Tasarımcı kullanarak arabirimi <xref:System.ComponentModel.ICustomTypeDescriptor>.</span><span class="sxs-lookup"><span data-stu-id="39720-110">Activities constructed using <xref:System.Activities.DynamicActivity> interface with the designer using <xref:System.ComponentModel.ICustomTypeDescriptor>.</span></span> <span data-ttu-id="39720-111">Tasarımcıda oluşturulan etkinlikleri kullanarak dinamik olarak yüklenebilir <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, aşağıdaki yordamda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="39720-111">Activities created in the designer can be loaded dynamically using <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, as demonstrated in the following procedure.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a><span data-ttu-id="39720-112">Kesinlik temelli kod kullanarak çalışma zamanında bir etkinlik oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="39720-112">To create an activity at runtime using imperative code</span></span>  
  
1.  <span data-ttu-id="39720-113">Açık[!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="39720-113">Open[!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="39720-114">Seçin **dosya**, **yeni**, **proje**.</span><span class="sxs-lookup"><span data-stu-id="39720-114">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="39720-115">Seçin **Workflow 4.0** altında **Visual C#** içinde **proje türleri** penceresi ve select **v2010** düğümü.</span><span class="sxs-lookup"><span data-stu-id="39720-115">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="39720-116">Seçin **sıralı iş akışı konsol uygulaması** içinde **şablonları** penceresi.</span><span class="sxs-lookup"><span data-stu-id="39720-116">Select **Sequential Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="39720-117">Yeni Proje DynamicActivitySample olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="39720-117">Name the new project DynamicActivitySample.</span></span>  
  
3.  <span data-ttu-id="39720-118">Workflow1.XAML HelloActivity projeye sağ tıklayıp **silmek**.</span><span class="sxs-lookup"><span data-stu-id="39720-118">Right-click Workflow1.xaml in the HelloActivity project and select **Delete**.</span></span>  
  
4.  <span data-ttu-id="39720-119">Program.cs açın.</span><span class="sxs-lookup"><span data-stu-id="39720-119">Open Program.cs.</span></span> <span data-ttu-id="39720-120">Aşağıdaki yönergesi dosyasının üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="39720-120">Add the following directive to the top of the file.</span></span>  
  
    ```  
    using System.Collections.Generic;  
    ```  
  
5.  <span data-ttu-id="39720-121">Değiştir `Main` oluşturur aşağıdaki kod ile yöntemi bir <xref:System.Activities.Statements.Sequence> içeren tek bir etkinlik <xref:System.Activities.Statements.WriteLine> etkinliği ve atar <xref:System.Activities.DynamicActivity.Implementation%2A> yeni bir dinamik etkinlik özelliği.</span><span class="sxs-lookup"><span data-stu-id="39720-121">Replace the contents of the `Main` method with the following code, which creates a <xref:System.Activities.Statements.Sequence> activity that contains a single <xref:System.Activities.Statements.WriteLine> activity and assigns it to the <xref:System.Activities.DynamicActivity.Implementation%2A> property of a new dynamic activity.</span></span>  
  
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
  
6.  <span data-ttu-id="39720-122">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="39720-122">Execute the application.</span></span> <span data-ttu-id="39720-123">"Hello World!" metnini içeren bir konsol penceresi</span><span class="sxs-lookup"><span data-stu-id="39720-123">A console window with the text "Hello World!"</span></span> <span data-ttu-id="39720-124">görüntüler.</span><span class="sxs-lookup"><span data-stu-id="39720-124">displays.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a><span data-ttu-id="39720-125">XAML kullanarak çalışma zamanında bir etkinlik oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="39720-125">To create an activity at runtime using XAML</span></span>  
  
1.  <span data-ttu-id="39720-126">Açık [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="39720-126">Open [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="39720-127">Seçin **dosya**, **yeni**, **proje**.</span><span class="sxs-lookup"><span data-stu-id="39720-127">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="39720-128">Seçin **Workflow 4.0** altında **Visual C#** içinde **proje türleri** penceresi ve select **v2010** düğümü.</span><span class="sxs-lookup"><span data-stu-id="39720-128">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="39720-129">Seçin **iş akışı konsol uygulaması** içinde **şablonları** penceresi.</span><span class="sxs-lookup"><span data-stu-id="39720-129">Select  **Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="39720-130">Yeni Proje DynamicActivitySample olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="39720-130">Name the new project DynamicActivitySample.</span></span>  
  
3.  <span data-ttu-id="39720-131">Workflow1.XAML HelloActivity projeyi açın.</span><span class="sxs-lookup"><span data-stu-id="39720-131">Open Workflow1.xaml in the HelloActivity project.</span></span> <span data-ttu-id="39720-132">Tıklatın **bağımsız değişkenleri** Tasarımcısı'nın altındaki seçeneği.</span><span class="sxs-lookup"><span data-stu-id="39720-132">Click the **Arguments** option at the bottom of the designer.</span></span> <span data-ttu-id="39720-133">Yeni bir `In` bağımsız değişkeni olarak adlandırılan `TextToWrite` türü `String`.</span><span class="sxs-lookup"><span data-stu-id="39720-133">Create a new `In` argument called `TextToWrite` of type `String`.</span></span>  
  
4.  <span data-ttu-id="39720-134">Sürükleme bir **WriteLine** etkinliğinden **Temelleri** Tasarımcı yüzeyine araç bölümü.</span><span class="sxs-lookup"><span data-stu-id="39720-134">Drag a **WriteLine** activity from the **Primitives** section of the toolbox onto the designer surface.</span></span> <span data-ttu-id="39720-135">Değer atamak `TextToWrite` için **metin** etkinliğin özelliği.</span><span class="sxs-lookup"><span data-stu-id="39720-135">Assign the value `TextToWrite` to the **Text** property of the activity.</span></span>  
  
5.  <span data-ttu-id="39720-136">Program.cs açın.</span><span class="sxs-lookup"><span data-stu-id="39720-136">Open Program.cs.</span></span> <span data-ttu-id="39720-137">Aşağıdaki yönergesi dosyasının üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="39720-137">Add the following directive to the top of the file.</span></span>  
  
    ```  
    using System.Activities.XamlIntegration;  
    ```  
  
6.  <span data-ttu-id="39720-138">Değiştir `Main` aşağıdaki kod ile yöntemi.</span><span class="sxs-lookup"><span data-stu-id="39720-138">Replace the contents of the `Main` method with the following code.</span></span>  
  
    ```  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7.  <span data-ttu-id="39720-139">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="39720-139">Execute the application.</span></span> <span data-ttu-id="39720-140">"Hello World!" metnini içeren bir konsol penceresi</span><span class="sxs-lookup"><span data-stu-id="39720-140">A console window with the text "Hello World!"</span></span> <span data-ttu-id="39720-141">görünür.</span><span class="sxs-lookup"><span data-stu-id="39720-141">appears.</span></span>  
  
8.  <span data-ttu-id="39720-142">Workflow1.xaml dosyasında sağ **Çözüm Gezgini** seçip **görünümü kodu**.</span><span class="sxs-lookup"><span data-stu-id="39720-142">Right-click the Workflow1.xaml file in the **Solution Explorer** and select **View Code**.</span></span> <span data-ttu-id="39720-143">Etkinliği sınıf ile oluşturulan Not `x:Class` ve özelliği ile oluşturulan `x:Property`.</span><span class="sxs-lookup"><span data-stu-id="39720-143">Note that the activity class is created with `x:Class` and the property is created with `x:Property`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39720-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="39720-144">See Also</span></span>  
 [<span data-ttu-id="39720-145">İş akışları, etkinlikler ve ifadeler kesinlik temelli kod kullanarak geliştirme</span><span class="sxs-lookup"><span data-stu-id="39720-145">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md)  
 [<span data-ttu-id="39720-146">DynamicActivity oluşturma</span><span class="sxs-lookup"><span data-stu-id="39720-146">DynamicActivity Creation</span></span>](../../../docs/framework/windows-workflow-foundation/samples/dynamicactivity-creation.md)
