---
title: DynamicActivity ile çalışma zamanında etkinlik oluşturma
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: de67fdd71f28bc0f4b16017d253682ca2615f854
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989733"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a><span data-ttu-id="62202-102">DynamicActivity ile çalışma zamanında etkinlik oluşturma</span><span class="sxs-lookup"><span data-stu-id="62202-102">Creating an Activity at Runtime with DynamicActivity</span></span>
<span data-ttu-id="62202-103"><xref:System.Activities.DynamicActivity>, ortak Oluşturucusu olan somut, mühürlenmiş bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="62202-103"><xref:System.Activities.DynamicActivity> is a concrete, sealed class with a public constructor.</span></span> <span data-ttu-id="62202-104"><xref:System.Activities.DynamicActivity>Etkinlik DOM kullanılarak çalışma zamanında etkinlik işlevselliğini birleştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="62202-104"><xref:System.Activities.DynamicActivity> can be used to assemble activity functionality at runtime using an activity DOM.</span></span>  
  
## <a name="dynamicactivity-features"></a><span data-ttu-id="62202-105">DynamicActivity özellikleri</span><span class="sxs-lookup"><span data-stu-id="62202-105">DynamicActivity Features</span></span>  
 <span data-ttu-id="62202-106"><xref:System.Activities.DynamicActivity>yürütme özelliklerine, bağımsız değişkenlere ve değişkenlere erişebilir, ancak alt etkinliklerin veya izlemenin zamanlanması gibi çalışma zamanı hizmetlerine erişemez.</span><span class="sxs-lookup"><span data-stu-id="62202-106"><xref:System.Activities.DynamicActivity> has access to execution properties, arguments and variables, but no access to run-time services such as scheduling child activities or tracking.</span></span>  
  
 <span data-ttu-id="62202-107">En üst düzey özellikler, iş akışı <xref:System.Activities.Argument> nesneleri kullanılarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="62202-107">Top-level properties can be set using workflow <xref:System.Activities.Argument> objects.</span></span> <span data-ttu-id="62202-108">Kesinlik temelli kodda, bu bağımsız değişkenler CLR özellikleri kullanılarak yeni bir tür üzerinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="62202-108">In imperative code, these arguments are created using CLR properties on a new type.</span></span> <span data-ttu-id="62202-109">XAML 'de, ve `x:Class` `x:Member` etiketleri kullanılarak bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="62202-109">In XAML, they are declared using `x:Class` and `x:Member` tags.</span></span>  
  
 <span data-ttu-id="62202-110"><xref:System.Activities.DynamicActivity> Kullanılarak<xref:System.ComponentModel.ICustomTypeDescriptor>tasarımcı ile arabirim kullanılarak oluşturulan etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="62202-110">Activities constructed using <xref:System.Activities.DynamicActivity> interface with the designer using <xref:System.ComponentModel.ICustomTypeDescriptor>.</span></span> <span data-ttu-id="62202-111">Tasarımcıda oluşturulan etkinlikler, aşağıdaki yordamda gösterildiği gibi kullanılarak <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>dinamik olarak yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="62202-111">Activities created in the designer can be loaded dynamically using <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, as demonstrated in the following procedure.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a><span data-ttu-id="62202-112">Zorunlu kod kullanarak çalışma zamanında etkinlik oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="62202-112">To create an activity at runtime using imperative code</span></span>  
  
1. <span data-ttu-id="62202-113">OpenVisual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="62202-113">OpenVisual Studio 2010.</span></span>  
  
2. <span data-ttu-id="62202-114">**Dosya**, **Yeni**, **Proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="62202-114">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="62202-115">**Proje türleri** penceresinde **Visual C#**  altında **iş akışı 4,0** ' i seçin ve **v2010** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="62202-115">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="62202-116">**Şablonlar** penceresinde **sıralı Iş akışı konsol uygulaması** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="62202-116">Select **Sequential Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="62202-117">Yeni projeyi DynamicActivitySample olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="62202-117">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="62202-118">Merhaba etkinlik projesinde Workflow1. xaml öğesine sağ tıklayın ve **Sil**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="62202-118">Right-click Workflow1.xaml in the HelloActivity project and select **Delete**.</span></span>  
  
4. <span data-ttu-id="62202-119">Program.cs 'i açın.</span><span class="sxs-lookup"><span data-stu-id="62202-119">Open Program.cs.</span></span> <span data-ttu-id="62202-120">Aşağıdaki yönergeyi dosyanın en üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="62202-120">Add the following directive to the top of the file.</span></span>  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
5. <span data-ttu-id="62202-121">`Main` Yönteminin içeriğini, tek <xref:System.Activities.Statements.Sequence> <xref:System.Activities.Statements.WriteLine> bir etkinlik içeren ve yeni bir dinamik etkinliğin <xref:System.Activities.DynamicActivity.Implementation%2A> özelliğine atayan bir etkinlik oluşturan aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="62202-121">Replace the contents of the `Main` method with the following code, which creates a <xref:System.Activities.Statements.Sequence> activity that contains a single <xref:System.Activities.Statements.WriteLine> activity and assigns it to the <xref:System.Activities.DynamicActivity.Implementation%2A> property of a new dynamic activity.</span></span>  
  
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
  
6. <span data-ttu-id="62202-122">Uygulamayı yürütün.</span><span class="sxs-lookup"><span data-stu-id="62202-122">Execute the application.</span></span> <span data-ttu-id="62202-123">"Merhaba Dünya!" metnini içeren bir konsol penceresi</span><span class="sxs-lookup"><span data-stu-id="62202-123">A console window with the text "Hello World!"</span></span> <span data-ttu-id="62202-124">görüntülenmektedir.</span><span class="sxs-lookup"><span data-stu-id="62202-124">displays.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a><span data-ttu-id="62202-125">XAML kullanarak çalışma zamanında etkinlik oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="62202-125">To create an activity at runtime using XAML</span></span>  
  
1. <span data-ttu-id="62202-126">Visual Studio 2010 ' i açın.</span><span class="sxs-lookup"><span data-stu-id="62202-126">Open Visual Studio 2010.</span></span>  
  
2. <span data-ttu-id="62202-127">**Dosya**, **Yeni**, **Proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="62202-127">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="62202-128">**Proje türleri** penceresinde **Visual C#**  altında **iş akışı 4,0** ' i seçin ve **v2010** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="62202-128">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="62202-129">**Şablonlar** penceresinde **Iş akışı konsol uygulaması** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="62202-129">Select  **Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="62202-130">Yeni projeyi DynamicActivitySample olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="62202-130">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="62202-131">Merhaba etkinlik projesinde Workflow1. xaml ' i açın.</span><span class="sxs-lookup"><span data-stu-id="62202-131">Open Workflow1.xaml in the HelloActivity project.</span></span> <span data-ttu-id="62202-132">Tasarımcının alt kısmındaki **bağımsız değişkenler** seçeneğine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="62202-132">Click the **Arguments** option at the bottom of the designer.</span></span> <span data-ttu-id="62202-133">Türünde `In` `TextToWrite` adlı Yenibirbağımsızdeğişkenoluşturun.`String`</span><span class="sxs-lookup"><span data-stu-id="62202-133">Create a new `In` argument called `TextToWrite` of type `String`.</span></span>  
  
4. <span data-ttu-id="62202-134">Araç kutusunun **temel öğeler** bölümünden bir **WriteLine** etkinliğini tasarımcı yüzeyine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="62202-134">Drag a **WriteLine** activity from the **Primitives** section of the toolbox onto the designer surface.</span></span> <span data-ttu-id="62202-135">Etkinliğin Text özelliğine `TextToWrite` değeri atayın .</span><span class="sxs-lookup"><span data-stu-id="62202-135">Assign the value `TextToWrite` to the **Text** property of the activity.</span></span>  
  
5. <span data-ttu-id="62202-136">Program.cs 'i açın.</span><span class="sxs-lookup"><span data-stu-id="62202-136">Open Program.cs.</span></span> <span data-ttu-id="62202-137">Aşağıdaki yönergeyi dosyanın en üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="62202-137">Add the following directive to the top of the file.</span></span>  
  
    ```csharp  
    using System.Activities.XamlIntegration;  
    ```  
  
6. <span data-ttu-id="62202-138">`Main` Yönteminin içeriğini aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="62202-138">Replace the contents of the `Main` method with the following code.</span></span>  
  
    ```csharp  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7. <span data-ttu-id="62202-139">Uygulamayı yürütün.</span><span class="sxs-lookup"><span data-stu-id="62202-139">Execute the application.</span></span> <span data-ttu-id="62202-140">"Merhaba Dünya!" metnini içeren bir konsol penceresi</span><span class="sxs-lookup"><span data-stu-id="62202-140">A console window with the text "Hello World!"</span></span> <span data-ttu-id="62202-141">görüneceği.</span><span class="sxs-lookup"><span data-stu-id="62202-141">appears.</span></span>  
  
8. <span data-ttu-id="62202-142">**Çözüm Gezgini** Workflow1. xaml dosyasına sağ tıklayın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="62202-142">Right-click the Workflow1.xaml file in the **Solution Explorer** and select **View Code**.</span></span> <span data-ttu-id="62202-143">Etkinlik sınıfının ile `x:Class` oluşturulduğunu ve özelliğinin ile `x:Property`oluşturulduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="62202-143">Note that the activity class is created with `x:Class` and the property is created with `x:Property`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62202-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62202-144">See also</span></span>

- [<span data-ttu-id="62202-145">Kesin Kod Kullanarak İş Akışları, Etkinlikler ve İfadeler Yazma</span><span class="sxs-lookup"><span data-stu-id="62202-145">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](authoring-workflows-activities-and-expressions-using-imperative-code.md)
