---
title: '3\. görev: araç kutusu ve PropertyGrid bölmelerini oluşturma'
ms.date: 03/30/2017
ms.assetid: 72c1546a-eed5-4f0f-a616-719a163414f4
ms.openlocfilehash: 402a25c1cb82c245afa94f58cefc180515622ea9
ms.sourcegitcommit: 992f80328b51b165051c42ff5330788627abe973
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72275868"
---
# <a name="task-3-create-the-toolbox-and-propertygrid-panes"></a><span data-ttu-id="1bc53-102">3\. görev: araç kutusu ve PropertyGrid bölmelerini oluşturma</span><span class="sxs-lookup"><span data-stu-id="1bc53-102">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>

<span data-ttu-id="1bc53-103">Bu görevde, **araç kutusu** ve **PropertyGrid** bölmelerini oluşturacak ve bunları yeniden barındırılan [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] ' ye ekleyecek.</span><span class="sxs-lookup"><span data-stu-id="1bc53-103">In this task, you will create the **Toolbox** and **PropertyGrid** panes and add them to the rehosted [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span></span>

<span data-ttu-id="1bc53-104">Başvuru için, İş Akışı Tasarımcısı dizi konunun [yeniden barındırmada](rehosting-the-workflow-designer.md) yer alan üç görevi tamamladıktan sonra MainWindow.xaml.cs dosyasında olması gereken kod bu konunun sonunda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1bc53-104">For reference, the code that should be in the MainWindow.xaml.cs file after completing the three tasks in the [Rehosting the Workflow Designer](rehosting-the-workflow-designer.md) series of topics is provided at the end of this topic.</span></span>

## <a name="to-create-the-toolbox-and-add-it-to-the-grid"></a><span data-ttu-id="1bc53-105">Araç kutusunu oluşturmak ve kılavuza eklemek için</span><span class="sxs-lookup"><span data-stu-id="1bc53-105">To create the Toolbox and add it to the grid</span></span>

1. <span data-ttu-id="1bc53-106">Görev 2 ' de açıklanan yordamı izleyerek edindiğiniz HostingApplication projesini açın [: iş akışı Tasarımcısı barındırın](task-2-host-the-workflow-designer.md).</span><span class="sxs-lookup"><span data-stu-id="1bc53-106">Open the HostingApplication project you obtained by following the procedure described in [Task 2: Host the Workflow Designer](task-2-host-the-workflow-designer.md).</span></span>

2. <span data-ttu-id="1bc53-107">**Çözüm Gezgini** bölmesinde, *MainWindow. xaml* dosyasına sağ tıklayın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="1bc53-107">In the **Solution Explorer** pane, right-click the *MainWindow.xaml* file and select **View Code**.</span></span>

3. <span data-ttu-id="1bc53-108">@No__t-2 oluşturan `MainWindow` sınıfına `GetToolboxControl` yöntemi ekleyin, **araç kutusuna**yeni bir **araç kutusu** kategorisi ekler ve <xref:System.Activities.Statements.Assign> ve <xref:System.Activities.Statements.Sequence> etkinlik türlerini bu kategoriye atar.</span><span class="sxs-lookup"><span data-stu-id="1bc53-108">Add a `GetToolboxControl` method to the `MainWindow` class that creates a <xref:System.Activities.Presentation.Toolbox.ToolboxControl>, adds a new **Toolbox** category to the **Toolbox**, and assigns the <xref:System.Activities.Statements.Assign> and <xref:System.Activities.Statements.Sequence> activity types to that category.</span></span>

    ```csharp
    private ToolboxControl GetToolboxControl()
    {
        // Create the ToolBoxControl.
        var ctrl = new ToolboxControl();

        // Create a category.
        var category = new ToolboxCategory("category1");

        // Create Toolbox items.
        var tool1 =
            new ToolboxItemWrapper("System.Activities.Statements.Assign",
            typeof(Assign).Assembly.FullName, null, "Assign");

        var tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",
            typeof(Sequence).Assembly.FullName, null, "Sequence");

        // Add the Toolbox items to the category.
        category.Add(tool1);
        category.Add(tool2);

        // Add the category to the ToolBox control.
        ctrl.Categories.Add(category);
        return ctrl;
    }
    ```

4. <span data-ttu-id="1bc53-109">**Araç kutusunu** kılavuzdaki sol sütuna yerleştiren `MainWindow` sınıfına özel bir `AddToolbox` yöntemi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1bc53-109">Add a private `AddToolbox` method to the `MainWindow` class that places the **Toolbox** in the left column on the grid.</span></span>

    ```csharp
    private void AddToolBox()
    {
        ToolboxControl tc = GetToolboxControl();
        Grid.SetColumn(tc, 0);
        grid1.Children.Add(tc);
    }
    ```

5. <span data-ttu-id="1bc53-110">Aşağıdaki kodda gösterildiği gibi, `MainWindow()` sınıf oluşturucusunda `AddToolBox` yöntemine bir çağrı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1bc53-110">Add a call to the `AddToolBox` method in the `MainWindow()` class constructor as shown in the following code:</span></span>

    ```csharp
    public MainWindow()
    {
        InitializeComponent();
        this.RegisterMetadata();
        this.AddDesigner();

        this.AddToolBox();
    }
    ```

6. <span data-ttu-id="1bc53-111">Çözümünüzü derlemek ve çalıştırmak için <kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1bc53-111">Press <kbd>F5</kbd> to build and run your solution.</span></span> <span data-ttu-id="1bc53-112">@No__t-1 ve <xref:System.Activities.Statements.Sequence> etkinliklerinin bulunduğu **araç kutusu** görüntülenmelidir.</span><span class="sxs-lookup"><span data-stu-id="1bc53-112">The **Toolbox** containing the <xref:System.Activities.Statements.Assign> and <xref:System.Activities.Statements.Sequence> activities should be displayed.</span></span>

## <a name="to-create-the-propertygrid"></a><span data-ttu-id="1bc53-113">PropertyGrid oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1bc53-113">To create the PropertyGrid</span></span>

1. <span data-ttu-id="1bc53-114">**Çözüm Gezgini** bölmesinde, *MainWindow. xaml* dosyasına sağ tıklayın ve **kodu görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="1bc53-114">In the **Solution Explorer** pane, right-click the *MainWindow.xaml* file and select **View Code**.</span></span>

2. <span data-ttu-id="1bc53-115">**PropertyGrid** bölmesini kılavuzun en sağdaki sütununa yerleştirmek için `AddPropertyInspector` yöntemini `MainWindow` sınıfına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1bc53-115">Add the `AddPropertyInspector` method to the `MainWindow` class to place the **PropertyGrid** pane in the rightmost column on the grid:</span></span>

    ```csharp
    private void AddPropertyInspector()
    {
        Grid.SetColumn(wd.PropertyInspectorView, 2);
        grid1.Children.Add(wd.PropertyInspectorView);
    }
    ```

3. <span data-ttu-id="1bc53-116">Aşağıdaki kodda gösterildiği gibi, `MainWindow()` sınıf oluşturucusunda `AddPropertyInspector` yöntemine bir çağrı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1bc53-116">Add a call to the `AddPropertyInspector` method in the `MainWindow()` class constructor as shown in the following code:</span></span>

    ```csharp
    public MainWindow()
    {
        InitializeComponent();
        this.RegisterMetadata();
        this.AddDesigner();
        this.AddToolBox();

        this.AddPropertyInspector();
    }
    ```

4. <span data-ttu-id="1bc53-117">Çözümü derlemek ve çalıştırmak için <kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1bc53-117">Press <kbd>F5</kbd> to build and run the solution.</span></span> <span data-ttu-id="1bc53-118">**Araç kutusu**, iş akışı tasarım tuvali ve **PropertyGrid** bölmeleri hepsi görüntülenmelidir ve tasarım tuvaline bir <xref:System.Activities.Statements.Assign> etkinliği veya <xref:System.Activities.Statements.Sequence> etkinliği sürüklediğinizde, özellik kılavuzunun, vurgulanan etkinliğe bağlı olarak güncelleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="1bc53-118">The **Toolbox**, workflow design canvas, and **PropertyGrid** panes should all be displayed, and when you drag an <xref:System.Activities.Statements.Assign> activity or a <xref:System.Activities.Statements.Sequence> activity onto the design canvas, the property grid should update depending on the highlighted activity.</span></span>

## <a name="example"></a><span data-ttu-id="1bc53-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="1bc53-119">Example</span></span>

<span data-ttu-id="1bc53-120">*MainWindow.xaml.cs* dosyası artık aşağıdaki kodu içermelidir:</span><span class="sxs-lookup"><span data-stu-id="1bc53-120">The *MainWindow.xaml.cs* file should now contain the following code:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Documents;
using System.Windows.Input;
using System.Windows.Media;
using System.Windows.Media.Imaging;
using System.Windows.Navigation;
using System.Windows.Shapes;
// dlls added.
using System.Activities;
using System.Activities.Core.Presentation;
using System.Activities.Presentation;
using System.Activities.Presentation.Metadata;
using System.Activities.Presentation.Toolbox;
using System.Activities.Statements;
using System.ComponentModel;

namespace HostingApplication
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {
        private WorkflowDesigner wd;

        public MainWindow()
        {
            InitializeComponent();
            RegisterMetadata();
            AddDesigner();
            this.AddToolBox();
            this.AddPropertyInspector();
        }

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

        private void RegisterMetadata()
        {
            var dm = new DesignerMetadata();
            dm.Register();
        }

        private ToolboxControl GetToolboxControl()
        {
            // Create the ToolBoxControl.
            var ctrl = new ToolboxControl();

            // Create a category.
            var category = new ToolboxCategory("category1");

            // Create Toolbox items.
            var tool1 =
                new ToolboxItemWrapper("System.Activities.Statements.Assign",
                typeof(Assign).Assembly.FullName, null, "Assign");

            var tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",
                typeof(Sequence).Assembly.FullName, null, "Sequence");

            // Add the Toolbox items to the category.
            category.Add(tool1);
            category.Add(tool2);

            // Add the category to the ToolBox control.
            ctrl.Categories.Add(category);
            return ctrl;
        }

        private void AddToolBox()
        {
            ToolboxControl tc = GetToolboxControl();
            Grid.SetColumn(tc, 0);
            grid1.Children.Add(tc);
        }

        private void AddPropertyInspector()
        {
            Grid.SetColumn(wd.PropertyInspectorView, 2);
            grid1.Children.Add(wd.PropertyInspectorView);
        }

    }
}
```

## <a name="see-also"></a><span data-ttu-id="1bc53-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1bc53-121">See also</span></span>

- [<span data-ttu-id="1bc53-122">İş Akışı Tasarımcısı yeniden barındırma</span><span class="sxs-lookup"><span data-stu-id="1bc53-122">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)
- [<span data-ttu-id="1bc53-123">Görev 1: yeni bir Windows Presentation Foundation uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="1bc53-123">Task 1: Create a New Windows Presentation Foundation Application</span></span>](task-1-create-a-new-wpf-app.md)
- [<span data-ttu-id="1bc53-124">Görev 2: İş Akışı Tasarımcısı barındırın</span><span class="sxs-lookup"><span data-stu-id="1bc53-124">Task 2: Host the Workflow Designer</span></span>](task-2-host-the-workflow-designer.md)
