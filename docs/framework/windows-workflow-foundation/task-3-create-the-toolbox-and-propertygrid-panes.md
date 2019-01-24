---
title: '3. Görev: Araç kutusu ve PropertyGrid bölmeleri oluşturma'
ms.date: 03/30/2017
ms.assetid: 72c1546a-eed5-4f0f-a616-719a163414f4
ms.openlocfilehash: 8e332c2caa43e1c9703272d7f2be16b545c44fd3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558429"
---
# <a name="task-3-create-the-toolbox-and-propertygrid-panes"></a>3. Görev: Araç kutusu ve PropertyGrid bölmeleri oluşturma
Bu görevde, oluşturacağınız **araç kutusu** ve **PropertyGrid** bölmeleri ve bunları yeniden barındırılan için ekleme [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].  
  
 Başvuru için üç tamamladıktan sonra MainWindow.xaml.cs dosyasında olmalıdır kodu görevleri de [iş akışı tasarımcısını yeniden barındırma](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md) konuları dizi, bu konunun sonunda sağlanır.  
  
### <a name="to-create-the-toolbox-and-add-it-to-the-grid"></a>Araç kutusu oluşturmak ve bu kılavuza eklemek için  
  
1.  Elde edilen açıklanan yordamı izleyerek HostingApplication projeyi açın [görev 2: İş akışı tasarımcısını barındırma](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md).  
  
2.  İçinde **Çözüm Gezgini** bölmesinde MainWindow.xaml dosyasını sağ tıklatın ve seçin **kodu görüntüle**.  
  
3.  Ekleme bir `GetToolboxControl` yönteme `MainWindow` oluşturan sınıf bir <xref:System.Activities.Presentation.Toolbox.ToolboxControl>, yeni bir ekler **araç kutusu** kategorisine **araç kutusu**ve atar <xref:System.Activities.Statements.Assign> ve <xref:System.Activities.Statements.Sequence> etkinlik türleri için kategori.  
  
    ```csharp  
    private ToolboxControl GetToolboxControl()  
    {  
        // Create the ToolBoxControl.  
        ToolboxControl ctrl = new ToolboxControl();  
  
        // Create a category.  
        ToolboxCategory category = new ToolboxCategory("category1");  
  
        // Create Toolbox items.  
        ToolboxItemWrapper tool1 =   
            new ToolboxItemWrapper("System.Activities.Statements.Assign",   
            typeof(Assign).Assembly.FullName, null, "Assign");  
  
        ToolboxItemWrapper tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",   
            typeof(Sequence).Assembly.FullName, null, "Sequence");  
  
        // Add the Toolbox items to the category.  
        category.Add(tool1);  
        category.Add(tool2);  
  
        // Add the category to the ToolBox control.  
        ctrl.Categories.Add(category);  
        return ctrl;  
    }  
    ```  
  
4.  Özel bir ekleme `AddToolbox` yönteme `MainWindow` yerleştirir sınıfı **araç kutusu** kılavuzundaki sol sütunda.  
  
    ```csharp  
    private void AddToolBox()  
    {  
        ToolboxControl tc = GetToolboxControl();  
        Grid.SetColumn(tc, 0);  
        grid1.Children.Add(tc);  
    }  
    ```  
  
5.  Bir çağrı ekleyin `AddToolBox` yönteminde `MainWindow()` aşağıdaki kodda gösterildiği gibi sınıf oluşturucusu.  
  
    ```csharp  
    public MainWindow()  
    {  
        InitializeComponent();  
        this.RegisterMetadata();  
        this.AddDesigner();  
  
        this.AddToolBox();  
    }  
    ```  
  
6.  Derleme ve çözümünüzü çalıştırmak için F5 tuşuna basın. **Araç kutusu** içeren <xref:System.Activities.Statements.Assign> ve <xref:System.Activities.Statements.Sequence> etkinlikleri görüntülenmesi gerekir.  
  
### <a name="to-create-the-propertygrid"></a>PropertyGrid oluşturmak için  
  
1.  İçinde **Çözüm Gezgini** bölmesinde MainWindow.xaml dosyasını sağ tıklatın ve seçin **kodu görüntüle**.  
  
2.  Ekleme `AddPropertyInspector` yönteme `MainWindow` yerleştirmek için sınıf **PropertyGrid** en sağdaki sütunda Kılavuz bölmesinde.  
  
    ```csharp  
    private void AddPropertyInspector()  
    {  
        Grid.SetColumn(wd.PropertyInspectorView, 2);  
        grid1.Children.Add(wd.PropertyInspectorView);              
    }  
    ```  
  
3.  Bir çağrı ekleyin `AddPropertyInspector` yönteminde `MainWindow()` aşağıdaki kodda gösterildiği gibi sınıf oluşturucusu.  
  
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
  
4.  Derleme ve çözümü çalıştırmak için F5 tuşuna basın. **Araç kutusu**, iş akışı tasarım tuvali ve **PropertyGrid** bölmeleri tüm görüntülenecek ve sürüklediğinizde bir <xref:System.Activities.Statements.Assign> etkinlik veya <xref:System.Activities.Statements.Sequence> tasarım tuvale etkinliği Özellik Kılavuzu vurgulanan etkinlik bağlı olarak güncelleştirmeniz gerekir.  
  
## <a name="example"></a>Örnek  
 MainWindow.xaml.cs dosyası artık şu kodu içermesi gerekir.  
  
```  
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
//dlls added  
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
            //Create an instance of WorkflowDesigner class.  
            this.wd = new WorkflowDesigner();  
  
            //Place the designer canvas in the middle column of the grid.  
            Grid.SetColumn(this.wd.View, 1);  
  
            //Load a new Sequence as default.  
            this.wd.Load(new Sequence());  
  
            //Add the designer canvas to the grid.  
            grid1.Children.Add(this.wd.View);  
        }  
  
        private void RegisterMetadata()  
        {  
            DesignerMetadata dm = new DesignerMetadata();  
            dm.Register();  
        }  
  
        private ToolboxControl GetToolboxControl()  
        {  
            // Create the ToolBoxControl.  
            ToolboxControl ctrl = new ToolboxControl();  
  
            // Create a category.  
            ToolboxCategory category = new ToolboxCategory("category1");  
  
            // Create Toolbox items.  
            ToolboxItemWrapper tool1 =  
                new ToolboxItemWrapper("System.Activities.Statements.Assign",  
                typeof(Assign).Assembly.FullName, null, "Assign");  
  
            ToolboxItemWrapper tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",  
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
- [İş Akışı Tasarımcısını Yeniden Barındırma](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)
- [1. Görev: Yeni bir Windows Presentation Foundation uygulaması oluşturma](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md)
- [2. Görev: İş akışı tasarımcısını barındırma](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)
