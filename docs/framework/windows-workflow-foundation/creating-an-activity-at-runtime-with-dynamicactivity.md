---
title: DynamicActivity ile çalışma zamanında etkinlik oluşturma
description: DynamicActivity, ortak Oluşturucusu olan somut, mühürlenmiş bir sınıftır. Etkinlik DOM kullanarak çalışma zamanında etkinlik işlevselliğini birleştirmek için sınıfını kullanın.
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: 17ee14be7df4801018c7afd2e91f1fb07c34e8e1
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421546"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a><span data-ttu-id="1bcf2-104">DynamicActivity ile çalışma zamanında etkinlik oluşturma</span><span class="sxs-lookup"><span data-stu-id="1bcf2-104">Creating an Activity at Runtime with DynamicActivity</span></span>
<span data-ttu-id="1bcf2-105"><xref:System.Activities.DynamicActivity>, ortak Oluşturucusu olan somut, mühürlenmiş bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="1bcf2-105"><xref:System.Activities.DynamicActivity> is a concrete, sealed class with a public constructor.</span></span> <span data-ttu-id="1bcf2-106"><xref:System.Activities.DynamicActivity>Etkinlik DOM kullanılarak çalışma zamanında etkinlik işlevselliğini birleştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1bcf2-106"><xref:System.Activities.DynamicActivity> can be used to assemble activity functionality at runtime using an activity DOM.</span></span>  
  
## <a name="dynamicactivity-features"></a><span data-ttu-id="1bcf2-107">DynamicActivity özellikleri</span><span class="sxs-lookup"><span data-stu-id="1bcf2-107">DynamicActivity Features</span></span>  
 <span data-ttu-id="1bcf2-108"><xref:System.Activities.DynamicActivity>yürütme özelliklerine, bağımsız değişkenlere ve değişkenlere erişebilir, ancak alt etkinliklerin veya izlemenin zamanlanması gibi çalışma zamanı hizmetlerine erişemez.</span><span class="sxs-lookup"><span data-stu-id="1bcf2-108"><xref:System.Activities.DynamicActivity> has access to execution properties, arguments and variables, but no access to run-time services such as scheduling child activities or tracking.</span></span>  
  
 <span data-ttu-id="1bcf2-109">En üst düzey özellikler, iş akışı nesneleri kullanılarak ayarlanabilir <xref:System.Activities.Argument> .</span><span class="sxs-lookup"><span data-stu-id="1bcf2-109">Top-level properties can be set using workflow <xref:System.Activities.Argument> objects.</span></span> <span data-ttu-id="1bcf2-110">Kesinlik temelli kodda, bu bağımsız değişkenler CLR özellikleri kullanılarak yeni bir tür üzerinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1bcf2-110">In imperative code, these arguments are created using CLR properties on a new type.</span></span> <span data-ttu-id="1bcf2-111">XAML 'de, ve etiketleri kullanılarak bildirilmiştir `x:Class` `x:Member` .</span><span class="sxs-lookup"><span data-stu-id="1bcf2-111">In XAML, they are declared using `x:Class` and `x:Member` tags.</span></span>  
  
 <span data-ttu-id="1bcf2-112"><xref:System.Activities.DynamicActivity>Kullanılarak tasarımcı ile arabirim kullanılarak oluşturulan etkinlikler <xref:System.ComponentModel.ICustomTypeDescriptor> .</span><span class="sxs-lookup"><span data-stu-id="1bcf2-112">Activities constructed using <xref:System.Activities.DynamicActivity> interface with the designer using <xref:System.ComponentModel.ICustomTypeDescriptor>.</span></span> <span data-ttu-id="1bcf2-113">Tasarımcıda oluşturulan etkinlikler <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> , aşağıdaki yordamda gösterildiği gibi kullanılarak dinamik olarak yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="1bcf2-113">Activities created in the designer can be loaded dynamically using <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, as demonstrated in the following procedure.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a><span data-ttu-id="1bcf2-114">Zorunlu kod kullanarak çalışma zamanında etkinlik oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1bcf2-114">To create an activity at runtime using imperative code</span></span>  
  
1. <span data-ttu-id="1bcf2-115">OpenVisual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="1bcf2-115">OpenVisual Studio 2010.</span></span>  
  
2. <span data-ttu-id="1bcf2-116">**Dosya**, **Yeni**, **Proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="1bcf2-116">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="1bcf2-117">**Proje türleri** penceresinde **Visual C#** altında **iş akışı 4,0** ' i seçin ve **v2010** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="1bcf2-117">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="1bcf2-118">**Şablonlar** penceresinde **sıralı Iş akışı konsol uygulaması** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="1bcf2-118">Select **Sequential Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="1bcf2-119">Yeni projeyi DynamicActivitySample olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="1bcf2-119">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="1bcf2-120">Merhaba etkinlik projesinde Workflow1. xaml öğesine sağ tıklayın ve **Sil**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="1bcf2-120">Right-click Workflow1.xaml in the HelloActivity project and select **Delete**.</span></span>  
  
4. <span data-ttu-id="1bcf2-121">Program.cs 'i açın.</span><span class="sxs-lookup"><span data-stu-id="1bcf2-121">Open Program.cs.</span></span> <span data-ttu-id="1bcf2-122">Aşağıdaki yönergeyi dosyanın en üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1bcf2-122">Add the following directive to the top of the file.</span></span>  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
5. <span data-ttu-id="1bcf2-123">Yönteminin içeriğini, `Main` <xref:System.Activities.Statements.Sequence> tek bir <xref:System.Activities.Statements.WriteLine> etkinlik içeren ve <xref:System.Activities.DynamicActivity.Implementation%2A> Yeni bir dinamik etkinliğin özelliğine atayan bir etkinlik oluşturan aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1bcf2-123">Replace the contents of the `Main` method with the following code, which creates a <xref:System.Activities.Statements.Sequence> activity that contains a single <xref:System.Activities.Statements.WriteLine> activity and assigns it to the <xref:System.Activities.DynamicActivity.Implementation%2A> property of a new dynamic activity.</span></span>  
  
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
  
6. <span data-ttu-id="1bcf2-124">Uygulamayı yürütün.</span><span class="sxs-lookup"><span data-stu-id="1bcf2-124">Execute the application.</span></span> <span data-ttu-id="1bcf2-125">"Merhaba Dünya!" metnini içeren bir konsol penceresi</span><span class="sxs-lookup"><span data-stu-id="1bcf2-125">A console window with the text "Hello World!"</span></span> <span data-ttu-id="1bcf2-126">görüntülenmektedir.</span><span class="sxs-lookup"><span data-stu-id="1bcf2-126">displays.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a><span data-ttu-id="1bcf2-127">XAML kullanarak çalışma zamanında etkinlik oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1bcf2-127">To create an activity at runtime using XAML</span></span>  
  
1. <span data-ttu-id="1bcf2-128">Visual Studio 2010 ' i açın.</span><span class="sxs-lookup"><span data-stu-id="1bcf2-128">Open Visual Studio 2010.</span></span>  
  
2. <span data-ttu-id="1bcf2-129">**Dosya**, **Yeni**, **Proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="1bcf2-129">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="1bcf2-130">**Proje türleri** penceresinde **Visual C#** altında **iş akışı 4,0** ' i seçin ve **v2010** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="1bcf2-130">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="1bcf2-131">**Şablonlar** penceresinde **Iş akışı konsol uygulaması** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="1bcf2-131">Select  **Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="1bcf2-132">Yeni projeyi DynamicActivitySample olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="1bcf2-132">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="1bcf2-133">Merhaba etkinlik projesinde Workflow1. xaml ' i açın.</span><span class="sxs-lookup"><span data-stu-id="1bcf2-133">Open Workflow1.xaml in the HelloActivity project.</span></span> <span data-ttu-id="1bcf2-134">Tasarımcının alt kısmındaki **bağımsız değişkenler** seçeneğine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1bcf2-134">Click the **Arguments** option at the bottom of the designer.</span></span> <span data-ttu-id="1bcf2-135">`In`Türünde adlı yeni bir bağımsız değişken oluşturun `TextToWrite` `String` .</span><span class="sxs-lookup"><span data-stu-id="1bcf2-135">Create a new `In` argument called `TextToWrite` of type `String`.</span></span>  
  
4. <span data-ttu-id="1bcf2-136">Araç kutusunun **temel öğeler** bölümünden bir **WriteLine** etkinliğini tasarımcı yüzeyine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="1bcf2-136">Drag a **WriteLine** activity from the **Primitives** section of the toolbox onto the designer surface.</span></span> <span data-ttu-id="1bcf2-137">`TextToWrite`Etkinliğin **Text** özelliğine değeri atayın.</span><span class="sxs-lookup"><span data-stu-id="1bcf2-137">Assign the value `TextToWrite` to the **Text** property of the activity.</span></span>  
  
5. <span data-ttu-id="1bcf2-138">Program.cs 'i açın.</span><span class="sxs-lookup"><span data-stu-id="1bcf2-138">Open Program.cs.</span></span> <span data-ttu-id="1bcf2-139">Aşağıdaki yönergeyi dosyanın en üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1bcf2-139">Add the following directive to the top of the file.</span></span>  
  
    ```csharp  
    using System.Activities.XamlIntegration;  
    ```  
  
6. <span data-ttu-id="1bcf2-140">`Main` yönteminin içeriğini aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1bcf2-140">Replace the contents of the `Main` method with the following code.</span></span>  
  
    ```csharp  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7. <span data-ttu-id="1bcf2-141">Uygulamayı yürütün.</span><span class="sxs-lookup"><span data-stu-id="1bcf2-141">Execute the application.</span></span> <span data-ttu-id="1bcf2-142">"Merhaba Dünya!" metnini içeren bir konsol penceresi</span><span class="sxs-lookup"><span data-stu-id="1bcf2-142">A console window with the text "Hello World!"</span></span> <span data-ttu-id="1bcf2-143">görüneceği.</span><span class="sxs-lookup"><span data-stu-id="1bcf2-143">appears.</span></span>  
  
8. <span data-ttu-id="1bcf2-144">**Çözüm Gezgini** Workflow1. xaml dosyasına sağ tıklayın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="1bcf2-144">Right-click the Workflow1.xaml file in the **Solution Explorer** and select **View Code**.</span></span> <span data-ttu-id="1bcf2-145">Etkinlik sınıfının ile oluşturulduğunu `x:Class` ve özelliğinin ile oluşturulduğunu unutmayın `x:Property` .</span><span class="sxs-lookup"><span data-stu-id="1bcf2-145">Note that the activity class is created with `x:Class` and the property is created with `x:Property`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bcf2-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1bcf2-146">See also</span></span>

- [<span data-ttu-id="1bcf2-147">Kesin Kod Kullanarak İş Akışları, Etkinlikler ve İfadeler Yazma</span><span class="sxs-lookup"><span data-stu-id="1bcf2-147">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](authoring-workflows-activities-and-expressions-using-imperative-code.md)
