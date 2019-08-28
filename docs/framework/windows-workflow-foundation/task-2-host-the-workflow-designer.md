---
title: 'Görev 2: İş Akışı Tasarımcısını Barındırma'
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: 92c5fa347cc7a2c0088ab8f4fbdfddf25ffb83c1
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70037864"
---
# <a name="task-2-host-the-workflow-designer"></a><span data-ttu-id="a21d9-102">Görev 2: İş Akışı Tasarımcısını Barındırma</span><span class="sxs-lookup"><span data-stu-id="a21d9-102">Task 2: Host the Workflow Designer</span></span>

<span data-ttu-id="a21d9-103">Bu konu, [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] bir Windows Presentation Foundation (WPF) uygulamasında örneğini barındırmak için yordamı açıklar.</span><span class="sxs-lookup"><span data-stu-id="a21d9-103">This topic describes the procedure for hosting an instance of the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] in a Windows Presentation Foundation (WPF) application.</span></span>

<span data-ttu-id="a21d9-104">Yordam, tasarımcı içeren **kılavuz** denetimini yapılandırır, program aracılığıyla varsayılan <xref:System.Activities.Presentation.WorkflowDesigner> <xref:System.Activities.Statements.Sequence> bir etkinlik içeren bir örneğini oluşturur, tasarımcı meta verilerini tümü için tasarımcı desteği sağlamak üzere kaydeder. yerleşik etkinlikler ve WPF uygulamasında barındırır [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a21d9-104">The procedure configures the **Grid** control that contains the designer, programmatically creates an instance of the <xref:System.Activities.Presentation.WorkflowDesigner> that contains a default <xref:System.Activities.Statements.Sequence> activity, registers the designer metadata to provide designer support for all built-in activities, and hosts the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] in the WPF application.</span></span>

### <a name="to-host-the-workflow-designer"></a><span data-ttu-id="a21d9-105">İş akışı tasarımcısını barındırmak için</span><span class="sxs-lookup"><span data-stu-id="a21d9-105">To host the workflow designer</span></span>

1. <span data-ttu-id="a21d9-106">Görev 1 ' de [oluşturduğunuz HostingApplication projesini açın: Yeni bir Windows Presentation Foundation uygulaması](task-1-create-a-new-wpf-app.md)oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a21d9-106">Open the HostingApplication project you created in [Task 1: Create a New Windows Presentation Foundation Application](task-1-create-a-new-wpf-app.md).</span></span>

2. <span data-ttu-id="a21d9-107">Uygulamasının kullanımını [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]kolaylaştırmak için pencerenin boyutunu ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a21d9-107">Adjust the size of the window to make it easier to use the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span></span> <span data-ttu-id="a21d9-108">Bunu yapmak için tasarımcıda **MainWindow** ' i seçin, **Özellikler** penceresini göstermek için F4 tuşuna basın ve **düzen** bölümünde, **Genişlik** değerini 600 değerine ve **yüksekliği** 350 değerine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a21d9-108">To do this, select **MainWindow** in the designer, press F4 to display the **Properties** window, and, in the **Layout** section there, set the **Width** to a value of 600 and the **Height** to a value of 350.</span></span>

3. <span data-ttu-id="a21d9-109">Tasarımcı 'daki **kılavuz** panelini seçerek ızgara adını ayarlayın ( **MainWindow**içindeki kutuya tıklayın) ve **Özellikler** penceresinin üst kısmındaki **Name** özelliğini "grid1" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a21d9-109">Set the grid name by selecting the **Grid** panel in the designer (click the box inside the **MainWindow**) and setting the **Name** property at the top of the **Properties** window to "grid1".</span></span>

4. <span data-ttu-id="a21d9-110">**Özellikler** penceresinde, **koleksiyon Düzenleyicisi** iletişim kutusunu açmak için `ColumnDefinitions` özelliğin yanındaki üç nokta ( **...** ) simgesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a21d9-110">In the **Properties** window, click the ellipsis (**…**) next to the `ColumnDefinitions` property to open the **Collection Editor** dialog box.</span></span>

5. <span data-ttu-id="a21d9-111">Düzen **Düzenleyici** iletişim kutusunda, mizanpaja üç sütun eklemek için **Ekle** düğmesine üç kez tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a21d9-111">In the **Collection Editor** dialog box, click the **Add** button three times to insert three columns into the layout.</span></span> <span data-ttu-id="a21d9-112">İlk sütunda **araç kutusu**bulunur, ikinci sütun [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]' ı barındırır ve üçüncü sütun Özellik denetçisi için kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="a21d9-112">The first column will contain the **Toolbox**, the second column will host the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], and the third column will be used for the property inspector.</span></span>

6. <span data-ttu-id="a21d9-113">Orta sütunun `Width` özelliğini "4 \*" değeri olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a21d9-113">Set the `Width` property of the middle column to the value "4\*".</span></span>

7. <span data-ttu-id="a21d9-114">Değişiklikleri kaydetmek için **Tamam** 'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a21d9-114">Click **OK** to save the changes.</span></span> <span data-ttu-id="a21d9-115">Aşağıdaki XAML, MainWindow. xaml dosyanıza eklenir:</span><span class="sxs-lookup"><span data-stu-id="a21d9-115">The following XAML is added to your MainWindow.xaml file:</span></span>

    ```xml
    <Grid Name="grid1">
        <Grid.ColumnDefinitions>
            <ColumnDefinition />
            <ColumnDefinition Width="4*" />
            <ColumnDefinition />
        </Grid.ColumnDefinitions>
    </Grid>
    ```

8. <span data-ttu-id="a21d9-116">**Çözüm Gezgini**, MainWindow. xaml öğesine sağ tıklayın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="a21d9-116">In **Solution Explorer**, right-click MainWindow.xaml and select **View Code**.</span></span> <span data-ttu-id="a21d9-117">Aşağıdaki adımları izleyerek kodu değiştirin:</span><span class="sxs-lookup"><span data-stu-id="a21d9-117">Modify the code by following these steps:</span></span>

    1. <span data-ttu-id="a21d9-118">Aşağıdaki ad alanlarını ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a21d9-118">Add the following namespaces:</span></span>

        ```csharp
        using System.Activities;
        using System.Activities.Core.Presentation;
        using System.Activities.Presentation;
        using System.Activities.Presentation.Metadata;
        using System.Activities.Presentation.Toolbox;
        using System.Activities.Statements;
        using System.ComponentModel;
        ```

    2. <span data-ttu-id="a21d9-119">Bir örneğini <xref:System.Activities.Presentation.WorkflowDesigner>tutacak bir özel üye alanı bildirmek için, `MainWindow` sınıfına aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a21d9-119">To declare a private member field to hold an instance of the <xref:System.Activities.Presentation.WorkflowDesigner>, add the following code to the `MainWindow` class.</span></span>

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

    3. <span data-ttu-id="a21d9-120">`MainWindow` Sınıfına aşağıdaki `AddDesigner` yöntemi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a21d9-120">Add the following `AddDesigner` method to the `MainWindow` class.</span></span> <span data-ttu-id="a21d9-121">Uygulama öğesinin <xref:System.Activities.Presentation.WorkflowDesigner>bir örneğini oluşturur, buna bir <xref:System.Activities.Statements.Sequence> etkinlik ekler ve grid1 **Grid**'in orta sütununa yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="a21d9-121">The implementation creates an instance of the <xref:System.Activities.Presentation.WorkflowDesigner>, adds a <xref:System.Activities.Statements.Sequence> activity to it, and places it in middle column of the grid1 **Grid**.</span></span>

        ```csharp
        private void AddDesigner()
        {
            //Create an instance of WorkflowDesigner class.
            this.wd = new WorkflowDesigner();

            //Place the designer canvas in the middle column of the grid.
            Grid.SetColumn(this.wd.View, 1);

            //Load a new Sequence as default.
            this.wd.Load(new Sequence());

            //Add the designer canvas to the grid.
            grid1.Children.Add(this.wd.View);
        }
        ```

    4. <span data-ttu-id="a21d9-122">Tüm yerleşik etkinlikler için tasarımcı desteği eklemek üzere tasarımcı meta verilerini kaydedin.</span><span class="sxs-lookup"><span data-stu-id="a21d9-122">Register the designer metadata to add designer support for all the  built-in activities.</span></span> <span data-ttu-id="a21d9-123">Bu, <xref:System.Activities.Statements.Sequence> [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]içindeki etkinlikleri araç kutusundan özgün etkinliğe düşürübilmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a21d9-123">This enables you to drop activities from the toolbox onto the original <xref:System.Activities.Statements.Sequence> activity in the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span></span> <span data-ttu-id="a21d9-124">Bunu yapmak için `RegisterMetadata` yöntemini `MainWindow` sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a21d9-124">To do this, add the `RegisterMetadata` method to the `MainWindow` class.</span></span>

        ```csharp
        private void RegisterMetadata()
        {
            DesignerMetadata dm = new DesignerMetadata();
            dm.Register();
        }
        ```

        <span data-ttu-id="a21d9-125">Etkinlik tasarımcılarını kaydetme hakkında daha fazla bilgi için [bkz. nasıl yapılır: Özel bir etkinlik Tasarımcısı](how-to-create-a-custom-activity-designer.md)oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a21d9-125">For more information about registering activity designers, see [How to: Create a Custom Activity Designer](how-to-create-a-custom-activity-designer.md).</span></span>

    5. <span data-ttu-id="a21d9-126">Sınıf oluşturucusunda, tasarımcı desteğinin meta verilerini kaydetmek ve <xref:System.Activities.Presentation.WorkflowDesigner>oluşturmak için daha önce belirtilen yöntemlere çağrılar ekleyin. `MainWindow`</span><span class="sxs-lookup"><span data-stu-id="a21d9-126">In the `MainWindow` class constructor, add calls to the methods declared previously to register the metadata for designer support and to create the <xref:System.Activities.Presentation.WorkflowDesigner>.</span></span>

        ```csharp
        public MainWindow()
        {
            InitializeComponent();

            // Register the metadata
            RegisterMetadata();

            // Add the WFF Designer
            AddDesigner();
        }
        ```

        > [!NOTE]
        > <span data-ttu-id="a21d9-127">Yöntemi, <xref:System.Activities.Statements.Sequence> etkinlik dahil yerleşik etkinliklerin tasarımcı meta verilerini kaydeder. `RegisterMetadata`</span><span class="sxs-lookup"><span data-stu-id="a21d9-127">The `RegisterMetadata` method registers the designer metadata of built-in activities including the <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="a21d9-128">Yöntemi etkinliğini kullandığından ,`RegisterMetadata` önce yönteminin çağrılması gerekir. <xref:System.Activities.Statements.Sequence> `AddDesigner`</span><span class="sxs-lookup"><span data-stu-id="a21d9-128">Because the `AddDesigner` method uses the <xref:System.Activities.Statements.Sequence> activity, the `RegisterMetadata` method must be called first.</span></span>

9. <span data-ttu-id="a21d9-129">Çözümü derlemek ve çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a21d9-129">Press F5 to build and run the solution.</span></span>

10. <span data-ttu-id="a21d9-130">Bkz [. görev 3: Yeniden barındırılan iş akışı tasarımcısına](task-3-create-the-toolbox-and-propertygrid-panes.md) **araç kutusu** ve **PropertyGrid** desteğinin nasıl ekleneceğini öğrenmek için araç kutusu ve PropertyGrid bölmelerini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a21d9-130">See [Task 3: Create the Toolbox and PropertyGrid Panes](task-3-create-the-toolbox-and-propertygrid-panes.md) to learn how to add **Toolbox** and **PropertyGrid** support to your rehosted workflow designer.</span></span>

## <a name="see-also"></a><span data-ttu-id="a21d9-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a21d9-131">See also</span></span>

- [<span data-ttu-id="a21d9-132">İş Akışı Tasarımcısını Yeniden Barındırma</span><span class="sxs-lookup"><span data-stu-id="a21d9-132">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)
- [<span data-ttu-id="a21d9-133">Görev 1: Yeni bir Windows Presentation Foundation uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="a21d9-133">Task 1: Create a New Windows Presentation Foundation Application</span></span>](task-1-create-a-new-wpf-app.md)
- [<span data-ttu-id="a21d9-134">Görev 3: Araç kutusu ve PropertyGrid bölmelerini oluşturma</span><span class="sxs-lookup"><span data-stu-id="a21d9-134">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>](task-3-create-the-toolbox-and-propertygrid-panes.md)
