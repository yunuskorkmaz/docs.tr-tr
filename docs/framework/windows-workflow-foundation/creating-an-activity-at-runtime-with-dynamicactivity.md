---
title: Dinamik Aktivite ile Çalışma Zamanında Etkinlik Oluşturma
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: 871108fd09e9127b3f9e06174f05a47c7fd7682c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182986"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a><span data-ttu-id="db832-102">Dinamik Aktivite ile Çalışma Zamanında Etkinlik Oluşturma</span><span class="sxs-lookup"><span data-stu-id="db832-102">Creating an Activity at Runtime with DynamicActivity</span></span>
<span data-ttu-id="db832-103"><xref:System.Activities.DynamicActivity>bir kamu yapıcı ile somut, mühürlü bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="db832-103"><xref:System.Activities.DynamicActivity> is a concrete, sealed class with a public constructor.</span></span> <span data-ttu-id="db832-104"><xref:System.Activities.DynamicActivity>bir etkinlik DOM kullanarak çalışma zamanında etkinlik işlevselliğini birleştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="db832-104"><xref:System.Activities.DynamicActivity> can be used to assemble activity functionality at runtime using an activity DOM.</span></span>  
  
## <a name="dynamicactivity-features"></a><span data-ttu-id="db832-105">Dinamik Aktivite Özellikleri</span><span class="sxs-lookup"><span data-stu-id="db832-105">DynamicActivity Features</span></span>  
 <span data-ttu-id="db832-106"><xref:System.Activities.DynamicActivity>yürütme özelliklerine, bağımsız değişkenlere ve değişkenlere erişimi vardır, ancak alt etkinlikleri zamanlama veya izleme gibi çalışma zamanı hizmetlerine erişim yoktur.</span><span class="sxs-lookup"><span data-stu-id="db832-106"><xref:System.Activities.DynamicActivity> has access to execution properties, arguments and variables, but no access to run-time services such as scheduling child activities or tracking.</span></span>  
  
 <span data-ttu-id="db832-107">Üst düzey özellikler iş akışı <xref:System.Activities.Argument> nesneleri kullanılarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="db832-107">Top-level properties can be set using workflow <xref:System.Activities.Argument> objects.</span></span> <span data-ttu-id="db832-108">Zorunlu kodda, bu bağımsız değişkenler yeni bir türde CLR özellikleri kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="db832-108">In imperative code, these arguments are created using CLR properties on a new type.</span></span> <span data-ttu-id="db832-109">XAML'de, bunlar `x:Class` kullanılarak `x:Member` ve etiketlere bildirilir.</span><span class="sxs-lookup"><span data-stu-id="db832-109">In XAML, they are declared using `x:Class` and `x:Member` tags.</span></span>  
  
 <span data-ttu-id="db832-110">Kullanarak tasarımcı <xref:System.Activities.DynamicActivity> ile arayüz <xref:System.ComponentModel.ICustomTypeDescriptor>kullanılarak yapılan etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="db832-110">Activities constructed using <xref:System.Activities.DynamicActivity> interface with the designer using <xref:System.ComponentModel.ICustomTypeDescriptor>.</span></span> <span data-ttu-id="db832-111">Tasarımcıda oluşturulan <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>etkinlikler, aşağıdaki yordamda gösterildiği gibi dinamik olarak yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="db832-111">Activities created in the designer can be loaded dynamically using <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, as demonstrated in the following procedure.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a><span data-ttu-id="db832-112">Zorunlu kodu kullanarak çalışma zamanında etkinlik oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="db832-112">To create an activity at runtime using imperative code</span></span>  
  
1. <span data-ttu-id="db832-113">Açık Görsel Stüdyo 2010.</span><span class="sxs-lookup"><span data-stu-id="db832-113">OpenVisual Studio 2010.</span></span>  
  
2. <span data-ttu-id="db832-114">**Dosya**yı seçin , **Yeni**, **Proje**.</span><span class="sxs-lookup"><span data-stu-id="db832-114">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="db832-115">**Proje Türleri** penceresinde **Visual C#** altında **İş Akışı 4.0'ı** seçin ve **v2010** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="db832-115">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="db832-116">**Şablonlar** penceresinde **Sıralı İş Akışı Konsolu Uygulamasını** seçin.</span><span class="sxs-lookup"><span data-stu-id="db832-116">Select **Sequential Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="db832-117">Yeni projeye DynamicActivitySample adını verin.</span><span class="sxs-lookup"><span data-stu-id="db832-117">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="db832-118">HelloActivity projesinde İş Akışı1.xaml'a sağ tıklayın ve **Sil'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="db832-118">Right-click Workflow1.xaml in the HelloActivity project and select **Delete**.</span></span>  
  
4. <span data-ttu-id="db832-119">Açık Program.cs.</span><span class="sxs-lookup"><span data-stu-id="db832-119">Open Program.cs.</span></span> <span data-ttu-id="db832-120">Aşağıdaki yönergeyi dosyanın üst bölümüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="db832-120">Add the following directive to the top of the file.</span></span>  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
5. <span data-ttu-id="db832-121">Yöntemin `Main` içeriğini, tek <xref:System.Activities.Statements.Sequence> <xref:System.Activities.Statements.WriteLine> bir etkinlik içeren ve yeni bir dinamik etkinliğin <xref:System.Activities.DynamicActivity.Implementation%2A> özelliğine atayan bir etkinlik oluşturan aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="db832-121">Replace the contents of the `Main` method with the following code, which creates a <xref:System.Activities.Statements.Sequence> activity that contains a single <xref:System.Activities.Statements.WriteLine> activity and assigns it to the <xref:System.Activities.DynamicActivity.Implementation%2A> property of a new dynamic activity.</span></span>  
  
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
  
6. <span data-ttu-id="db832-122">Uygulamayı yürütün.</span><span class="sxs-lookup"><span data-stu-id="db832-122">Execute the application.</span></span> <span data-ttu-id="db832-123">"Merhaba Dünya!" metninin yer verdiği bir konsol penceresi</span><span class="sxs-lookup"><span data-stu-id="db832-123">A console window with the text "Hello World!"</span></span> <span data-ttu-id="db832-124">Görüntü -ler.</span><span class="sxs-lookup"><span data-stu-id="db832-124">displays.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a><span data-ttu-id="db832-125">XAML kullanarak çalışma zamanında etkinlik oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="db832-125">To create an activity at runtime using XAML</span></span>  
  
1. <span data-ttu-id="db832-126">Açık Görsel Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="db832-126">Open Visual Studio 2010.</span></span>  
  
2. <span data-ttu-id="db832-127">**Dosya**yı seçin , **Yeni**, **Proje**.</span><span class="sxs-lookup"><span data-stu-id="db832-127">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="db832-128">**Proje Türleri** penceresinde **Visual C#** altında **İş Akışı 4.0'ı** seçin ve **v2010** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="db832-128">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="db832-129">**Şablonlar** penceresinde **İş Akışı Konsolu Uygulamasını** seçin.</span><span class="sxs-lookup"><span data-stu-id="db832-129">Select  **Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="db832-130">Yeni projeye DynamicActivitySample adını verin.</span><span class="sxs-lookup"><span data-stu-id="db832-130">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="db832-131">HelloActivity projesinde İş Akışı1.xaml'ı açın.</span><span class="sxs-lookup"><span data-stu-id="db832-131">Open Workflow1.xaml in the HelloActivity project.</span></span> <span data-ttu-id="db832-132">Tasarımcının altındaki **Bağımsız Değişkenler** seçeneğini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="db832-132">Click the **Arguments** option at the bottom of the designer.</span></span> <span data-ttu-id="db832-133">Türü `String`adlı `In` `TextToWrite` yeni bir bağımsız değişken oluşturun.</span><span class="sxs-lookup"><span data-stu-id="db832-133">Create a new `In` argument called `TextToWrite` of type `String`.</span></span>  
  
4. <span data-ttu-id="db832-134">Bir **WriteLine** etkinliğini araç kutusunun **Primitives** bölümünden tasarımcı yüzeyine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="db832-134">Drag a **WriteLine** activity from the **Primitives** section of the toolbox onto the designer surface.</span></span> <span data-ttu-id="db832-135">Etkinliğin Metin `TextToWrite` özelliğine **Text** değeri atayın.</span><span class="sxs-lookup"><span data-stu-id="db832-135">Assign the value `TextToWrite` to the **Text** property of the activity.</span></span>  
  
5. <span data-ttu-id="db832-136">Açık Program.cs.</span><span class="sxs-lookup"><span data-stu-id="db832-136">Open Program.cs.</span></span> <span data-ttu-id="db832-137">Aşağıdaki yönergeyi dosyanın üst bölümüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="db832-137">Add the following directive to the top of the file.</span></span>  
  
    ```csharp  
    using System.Activities.XamlIntegration;  
    ```  
  
6. <span data-ttu-id="db832-138">`Main` yönteminin içeriğini aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="db832-138">Replace the contents of the `Main` method with the following code.</span></span>  
  
    ```csharp  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7. <span data-ttu-id="db832-139">Uygulamayı yürütün.</span><span class="sxs-lookup"><span data-stu-id="db832-139">Execute the application.</span></span> <span data-ttu-id="db832-140">"Merhaba Dünya!" metninin yer verdiği bir konsol penceresi</span><span class="sxs-lookup"><span data-stu-id="db832-140">A console window with the text "Hello World!"</span></span> <span data-ttu-id="db832-141">Görünür.</span><span class="sxs-lookup"><span data-stu-id="db832-141">appears.</span></span>  
  
8. <span data-ttu-id="db832-142">**Çözüm** Gezgini'ndeki Workflow1.xaml dosyasına sağ tıklayın ve **Kodu Görüntüle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="db832-142">Right-click the Workflow1.xaml file in the **Solution Explorer** and select **View Code**.</span></span> <span data-ttu-id="db832-143">Etkinlik sınıfı ile `x:Class` oluşturulduğunu ve özelliğin `x:Property`.</span><span class="sxs-lookup"><span data-stu-id="db832-143">Note that the activity class is created with `x:Class` and the property is created with `x:Property`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db832-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db832-144">See also</span></span>

- [<span data-ttu-id="db832-145">Kesin Kod Kullanarak İş Akışları, Etkinlikler ve İfadeler Yazma</span><span class="sxs-lookup"><span data-stu-id="db832-145">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](authoring-workflows-activities-and-expressions-using-imperative-code.md)
