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
# <a name="task-3-create-the-toolbox-and-propertygrid-panes"></a>3\. görev: araç kutusu ve PropertyGrid bölmelerini oluşturma

Bu görevde, **araç kutusu** ve **PropertyGrid** bölmelerini oluşturacak ve bunları yeniden barındırılan [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] ' ye ekleyecek.

Başvuru için, İş Akışı Tasarımcısı dizi konunun [yeniden barındırmada](rehosting-the-workflow-designer.md) yer alan üç görevi tamamladıktan sonra MainWindow.xaml.cs dosyasında olması gereken kod bu konunun sonunda verilmiştir.

## <a name="to-create-the-toolbox-and-add-it-to-the-grid"></a>Araç kutusunu oluşturmak ve kılavuza eklemek için

1. Görev 2 ' de açıklanan yordamı izleyerek edindiğiniz HostingApplication projesini açın [: iş akışı Tasarımcısı barındırın](task-2-host-the-workflow-designer.md).

2. **Çözüm Gezgini** bölmesinde, *MainWindow. xaml* dosyasına sağ tıklayın ve **kodu görüntüle**' yi seçin.

3. @No__t-2 oluşturan `MainWindow` sınıfına `GetToolboxControl` yöntemi ekleyin, **araç kutusuna**yeni bir **araç kutusu** kategorisi ekler ve <xref:System.Activities.Statements.Assign> ve <xref:System.Activities.Statements.Sequence> etkinlik türlerini bu kategoriye atar.

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

4. **Araç kutusunu** kılavuzdaki sol sütuna yerleştiren `MainWindow` sınıfına özel bir `AddToolbox` yöntemi ekleyin.

    ```csharp
    private void AddToolBox()
    {
        ToolboxControl tc = GetToolboxControl();
        Grid.SetColumn(tc, 0);
        grid1.Children.Add(tc);
    }
    ```

5. Aşağıdaki kodda gösterildiği gibi, `MainWindow()` sınıf oluşturucusunda `AddToolBox` yöntemine bir çağrı ekleyin:

    ```csharp
    public MainWindow()
    {
        InitializeComponent();
        this.RegisterMetadata();
        this.AddDesigner();

        this.AddToolBox();
    }
    ```

6. Çözümünüzü derlemek ve çalıştırmak için <kbd>F5</kbd> tuşuna basın. @No__t-1 ve <xref:System.Activities.Statements.Sequence> etkinliklerinin bulunduğu **araç kutusu** görüntülenmelidir.

## <a name="to-create-the-propertygrid"></a>PropertyGrid oluşturmak için

1. **Çözüm Gezgini** bölmesinde, *MainWindow. xaml* dosyasına sağ tıklayın ve **kodu görüntüle**' yi seçin.

2. **PropertyGrid** bölmesini kılavuzun en sağdaki sütununa yerleştirmek için `AddPropertyInspector` yöntemini `MainWindow` sınıfına ekleyin:

    ```csharp
    private void AddPropertyInspector()
    {
        Grid.SetColumn(wd.PropertyInspectorView, 2);
        grid1.Children.Add(wd.PropertyInspectorView);
    }
    ```

3. Aşağıdaki kodda gösterildiği gibi, `MainWindow()` sınıf oluşturucusunda `AddPropertyInspector` yöntemine bir çağrı ekleyin:

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

4. Çözümü derlemek ve çalıştırmak için <kbd>F5</kbd> tuşuna basın. **Araç kutusu**, iş akışı tasarım tuvali ve **PropertyGrid** bölmeleri hepsi görüntülenmelidir ve tasarım tuvaline bir <xref:System.Activities.Statements.Assign> etkinliği veya <xref:System.Activities.Statements.Sequence> etkinliği sürüklediğinizde, özellik kılavuzunun, vurgulanan etkinliğe bağlı olarak güncelleştirilmesi gerekir.

## <a name="example"></a>Örnek

*MainWindow.xaml.cs* dosyası artık aşağıdaki kodu içermelidir:

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

## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Tasarımcısı yeniden barındırma](rehosting-the-workflow-designer.md)
- [Görev 1: yeni bir Windows Presentation Foundation uygulaması oluşturma](task-1-create-a-new-wpf-app.md)
- [Görev 2: İş Akışı Tasarımcısı barındırın](task-2-host-the-workflow-designer.md)
