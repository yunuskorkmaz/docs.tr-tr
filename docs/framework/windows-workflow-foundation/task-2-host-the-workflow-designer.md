---
description: 'Hakkında daha fazla bilgi edinin: 1. görev: İş Akışı Tasarımcısı barındırma'
title: 'Görev 2: İş Akışı Tasarımcısını Barındırma'
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: 5a00c9db831575dfe7f6f2b6e041f18877c60118
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755206"
---
# <a name="task-2-host-the-workflow-designer"></a><span data-ttu-id="d72c8-103">Görev 2: İş Akışı Tasarımcısını Barındırma</span><span class="sxs-lookup"><span data-stu-id="d72c8-103">Task 2: Host the Workflow Designer</span></span>

<span data-ttu-id="d72c8-104">Bu konu, bir Windows Presentation Foundation (WPF) uygulamasında Windows İş Akışı Tasarımcısı örneğini barındırma yordamını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="d72c8-104">This topic describes the procedure for hosting an instance of the Windows Workflow Designer in a Windows Presentation Foundation (WPF) application.</span></span>

<span data-ttu-id="d72c8-105">Yordam, tasarımcı içeren **kılavuz** denetimini yapılandırır, program aracılığıyla <xref:System.Activities.Presentation.WorkflowDesigner> varsayılan bir etkinlik içeren bir örneğini oluşturur <xref:System.Activities.Statements.Sequence> , tasarımcı meta verilerini tüm yerleşik etkinlikler için tasarımcı desteği sağlamak üzere kaydeder ve WPF uygulamasında iş akışı Tasarımcısı barındırır.</span><span class="sxs-lookup"><span data-stu-id="d72c8-105">The procedure configures the **Grid** control that contains the designer, programmatically creates an instance of the <xref:System.Activities.Presentation.WorkflowDesigner> that contains a default <xref:System.Activities.Statements.Sequence> activity, registers the designer metadata to provide designer support for all built-in activities, and hosts the Workflow Designer in the WPF application.</span></span>

## <a name="to-host-the-workflow-designer"></a><span data-ttu-id="d72c8-106">İş akışı tasarımcısını barındırmak için</span><span class="sxs-lookup"><span data-stu-id="d72c8-106">To host the workflow designer</span></span>

1. <span data-ttu-id="d72c8-107">Görev 1 ' de oluşturduğunuz HostingApplication projesini açın [: yeni bir Windows Presentation Foundation uygulaması oluşturun](task-1-create-a-new-wpf-app.md).</span><span class="sxs-lookup"><span data-stu-id="d72c8-107">Open the HostingApplication project you created in [Task 1: Create a New Windows Presentation Foundation Application](task-1-create-a-new-wpf-app.md).</span></span>

2. <span data-ttu-id="d72c8-108">İş Akışı Tasarımcısı kullanımını kolaylaştırmak için pencerenin boyutunu ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d72c8-108">Adjust the size of the window to make it easier to use the Workflow Designer.</span></span> <span data-ttu-id="d72c8-109">Bunu yapmak için tasarımcıda **MainWindow** ' i seçin, **Özellikler** penceresini göstermek için F4 tuşuna basın ve **düzen** bölümünde, **Genişlik** değerini 600 değerine ve **yüksekliği** 350 değerine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d72c8-109">To do this, select **MainWindow** in the designer, press F4 to display the **Properties** window, and, in the **Layout** section there, set the **Width** to a value of 600 and the **Height** to a value of 350.</span></span>

3. <span data-ttu-id="d72c8-110">Tasarımcı 'daki **kılavuz** panelini seçerek ızgara adını ayarlayın ( **MainWindow** içindeki kutuya tıklayın) ve **Özellikler** penceresinin üst kısmındaki **Name** özelliğini "grid1" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d72c8-110">Set the grid name by selecting the **Grid** panel in the designer (click the box inside the **MainWindow**) and setting the **Name** property at the top of the **Properties** window to "grid1".</span></span>

4. <span data-ttu-id="d72c8-111">**Özellikler** penceresinde, koleksiyon Düzenleyicisi iletişim kutusunu açmak için özelliğin yanındaki üç nokta (**...**) simgesine tıklayın `ColumnDefinitions`  .</span><span class="sxs-lookup"><span data-stu-id="d72c8-111">In the **Properties** window, click the ellipsis (**…**) next to the `ColumnDefinitions` property to open the **Collection Editor** dialog box.</span></span>

5. <span data-ttu-id="d72c8-112">Düzen **Düzenleyici** iletişim kutusunda, mizanpaja üç sütun eklemek için **Ekle** düğmesine üç kez tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d72c8-112">In the **Collection Editor** dialog box, click the **Add** button three times to insert three columns into the layout.</span></span> <span data-ttu-id="d72c8-113">İlk sütunda **araç kutusu** bulunur, ikinci sütun iş akışı Tasarımcısı barındırır ve üçüncü sütun Özellik denetçisi için kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="d72c8-113">The first column will contain the **Toolbox**, the second column will host the Workflow Designer, and the third column will be used for the property inspector.</span></span>

6. <span data-ttu-id="d72c8-114">`Width`Orta sütunun özelliğini "4 \*" değeri olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d72c8-114">Set the `Width` property of the middle column to the value "4\*".</span></span>

7. <span data-ttu-id="d72c8-115">Değişiklikleri kaydetmek için **Tamam**’a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d72c8-115">Click **OK** to save the changes.</span></span> <span data-ttu-id="d72c8-116">Aşağıdaki XAML, *MainWindow. xaml* dosyanıza eklenir:</span><span class="sxs-lookup"><span data-stu-id="d72c8-116">The following XAML is added to your *MainWindow.xaml* file:</span></span>

    ```xaml
    <Grid Name="grid1">
        <Grid.ColumnDefinitions>
            <ColumnDefinition />
            <ColumnDefinition Width="4*" />
            <ColumnDefinition />
        </Grid.ColumnDefinitions>
    </Grid>
    ```

8. <span data-ttu-id="d72c8-117">**Çözüm Gezgini**, *MainWindow. xaml* öğesine sağ tıklayın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="d72c8-117">In **Solution Explorer**, right-click *MainWindow.xaml* and select **View Code**.</span></span> <span data-ttu-id="d72c8-118">Aşağıdaki adımları izleyerek kodu değiştirin:</span><span class="sxs-lookup"><span data-stu-id="d72c8-118">Modify the code by following these steps:</span></span>

    1. <span data-ttu-id="d72c8-119">Aşağıdaki ad alanlarını ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d72c8-119">Add the following namespaces:</span></span>

        ```csharp
        using System.Activities;
        using System.Activities.Core.Presentation;
        using System.Activities.Presentation;
        using System.Activities.Presentation.Metadata;
        using System.Activities.Presentation.Toolbox;
        using System.Activities.Statements;
        using System.ComponentModel;
        ```

    2. <span data-ttu-id="d72c8-120">Bir örneğini tutacak bir özel üye alanı bildirmek için <xref:System.Activities.Presentation.WorkflowDesigner> , sınıfına aşağıdaki kodu ekleyin `MainWindow` :</span><span class="sxs-lookup"><span data-stu-id="d72c8-120">To declare a private member field to hold an instance of the <xref:System.Activities.Presentation.WorkflowDesigner>, add the following code to the `MainWindow` class:</span></span>

        ```csharp
        public partial class MainWindow : Window
        {
            private WorkflowDesigner wd;

            public MainWindow()
            {
                InitializeComponent();
            }
        }
        ```

    3. <span data-ttu-id="d72c8-121">`MainWindow` sınıfına aşağıdaki `AddDesigner` yöntemini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d72c8-121">Add the following `AddDesigner` method to the `MainWindow` class.</span></span> <span data-ttu-id="d72c8-122">Uygulama öğesinin bir örneğini oluşturur <xref:System.Activities.Presentation.WorkflowDesigner> , buna bir etkinlik ekler <xref:System.Activities.Statements.Sequence> ve grid1 **Grid**'in orta sütununa yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="d72c8-122">The implementation creates an instance of the <xref:System.Activities.Presentation.WorkflowDesigner>, adds a <xref:System.Activities.Statements.Sequence> activity to it, and places it in middle column of the grid1 **Grid**.</span></span>

        ```csharp
        private void AddDesigner()
        {
            // Create an instance of WorkflowDesigner class.
            this.wd = new WorkflowDesigner();

            // Place the designer canvas in the middle column of the grid.
            Grid.SetColumn(this.wd.View, 1);

            // Load a new Sequence as default.
            this.wd.Load(new Sequence());

            // Add the designer canvas to the grid.
            grid1.Children.Add(this.wd.View);
        }
        ```

    4. <span data-ttu-id="d72c8-123">Tüm yerleşik etkinlikler için tasarımcı desteği eklemek üzere tasarımcı meta verilerini kaydedin.</span><span class="sxs-lookup"><span data-stu-id="d72c8-123">Register the designer metadata to add designer support for all the  built-in activities.</span></span> <span data-ttu-id="d72c8-124">Bu, içindeki etkinlikleri, İş Akışı Tasarımcısı araç kutusundan özgün etkinliğe düşürüetmenize olanak sağlar <xref:System.Activities.Statements.Sequence> .</span><span class="sxs-lookup"><span data-stu-id="d72c8-124">This enables you to drop activities from the toolbox onto the original <xref:System.Activities.Statements.Sequence> activity in the Workflow Designer.</span></span> <span data-ttu-id="d72c8-125">Bunu yapmak için `RegisterMetadata` yöntemini `MainWindow` sınıfına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d72c8-125">To do this, add the `RegisterMetadata` method to the `MainWindow` class:</span></span>

        ```csharp
        private void RegisterMetadata()
        {
            var dm = new DesignerMetadata();
            dm.Register();
        }
        ```

        <span data-ttu-id="d72c8-126">Etkinlik tasarımcılarını kaydetme hakkında daha fazla bilgi için bkz. [nasıl yapılır: özel etkinlik Tasarımcısı oluşturma](how-to-create-a-custom-activity-designer.md).</span><span class="sxs-lookup"><span data-stu-id="d72c8-126">For more information about registering activity designers, see [How to: Create a Custom Activity Designer](how-to-create-a-custom-activity-designer.md).</span></span>

    5. <span data-ttu-id="d72c8-127">`MainWindow`Sınıf oluşturucusunda, tasarımcı desteğinin meta verilerini kaydetmek ve oluşturmak için daha önce belirtilen yöntemlere çağrılar ekleyin <xref:System.Activities.Presentation.WorkflowDesigner> .</span><span class="sxs-lookup"><span data-stu-id="d72c8-127">In the `MainWindow` class constructor, add calls to the methods declared previously to register the metadata for designer support and to create the <xref:System.Activities.Presentation.WorkflowDesigner>.</span></span>

        ```csharp
        public MainWindow()
        {
            InitializeComponent();

            // Register the metadata.
            RegisterMetadata();

            // Add the WFF Designer.
            AddDesigner();
        }
        ```

        > [!NOTE]
        > <span data-ttu-id="d72c8-128">`RegisterMetadata`Yöntemi, etkinlik dahil yerleşik etkinliklerin tasarımcı meta verilerini kaydeder <xref:System.Activities.Statements.Sequence> .</span><span class="sxs-lookup"><span data-stu-id="d72c8-128">The `RegisterMetadata` method registers the designer metadata of built-in activities including the <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="d72c8-129">`AddDesigner`Yöntemi <xref:System.Activities.Statements.Sequence> etkinliğini kullandığından, `RegisterMetadata` önce yönteminin çağrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d72c8-129">Because the `AddDesigner` method uses the <xref:System.Activities.Statements.Sequence> activity, the `RegisterMetadata` method must be called first.</span></span>

9. <span data-ttu-id="d72c8-130">Çözümü derlemek ve çalıştırmak için <kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d72c8-130">Press <kbd>F5</kbd> to build and run the solution.</span></span>

10. <span data-ttu-id="d72c8-131">Yeniden barındırılan iş akışı tasarımcısına **araç kutusu** ve **PropertyGrid** desteğinin nasıl ekleneceğini öğrenmek için bkz. [görev 3: araç kutusu ve PropertyGrid bölmelerini oluşturma](task-3-create-the-toolbox-and-propertygrid-panes.md) .</span><span class="sxs-lookup"><span data-stu-id="d72c8-131">See [Task 3: Create the Toolbox and PropertyGrid Panes](task-3-create-the-toolbox-and-propertygrid-panes.md) to learn how to add **Toolbox** and **PropertyGrid** support to your rehosted workflow designer.</span></span>

## <a name="see-also"></a><span data-ttu-id="d72c8-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d72c8-132">See also</span></span>

- [<span data-ttu-id="d72c8-133">İş Akışı Tasarımcısını Yeniden Barındırma</span><span class="sxs-lookup"><span data-stu-id="d72c8-133">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)
- [<span data-ttu-id="d72c8-134">Görev 1: Yeni Bir Windows Presentation Foundation Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d72c8-134">Task 1: Create a New Windows Presentation Foundation Application</span></span>](task-1-create-a-new-wpf-app.md)
- [<span data-ttu-id="d72c8-135">Görev 3: Araç Kutusu ve PropertyGrid Bölmeleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d72c8-135">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>](task-3-create-the-toolbox-and-propertygrid-panes.md)
