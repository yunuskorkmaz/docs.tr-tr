---
title: 'Görev 3: Araç Kutusu ve PropertyGrid Bölmeleri Oluşturma'
ms.date: 03/30/2017
ms.assetid: 72c1546a-eed5-4f0f-a616-719a163414f4
ms.openlocfilehash: 6339969c52a5c4eedfb0e89eebdc982ca3fe6686
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988707"
---
# <a name="task-3-create-the-toolbox-and-propertygrid-panes"></a>Görev 3: Araç Kutusu ve PropertyGrid Bölmeleri Oluşturma
Bu görevde, **araç kutusu** ve **PropertyGrid** bölmelerini oluşturacak ve bunları yeniden barındırılan [!INCLUDE[wfd1](../../../includes/wfd1-md.md)]olarak ekleyecek.  
  
 Başvuru için, İş Akışı Tasarımcısı dizi konunun [yeniden barındırmada](rehosting-the-workflow-designer.md) yer alan üç görevi tamamladıktan sonra MainWindow.xaml.cs dosyasında olması gereken kod bu konunun sonunda verilmiştir.  
  
### <a name="to-create-the-toolbox-and-add-it-to-the-grid"></a>Araç kutusunu oluşturmak ve kılavuza eklemek için  
  
1. Görev 2 ' de [açıklanan yordamı izleyerek edindiğiniz HostingApplication projesini açın: İş Akışı Tasarımcısı](task-2-host-the-workflow-designer.md)barındırın.  
  
2. **Çözüm Gezgini** bölmesinde, MainWindow. xaml dosyasına sağ tıklayın ve **kodu görüntüle**' yi seçin.  
  
3. `MainWindow` <xref:System.Activities.Statements.Assign> <xref:System.Activities.Statements.Sequence> Oluşturan sınıfına bir `GetToolboxControl` yöntem ekleyin ,araçkutusunayenibiraraçkutusukategorisieklerveveetkinliktürlerini<xref:System.Activities.Presentation.Toolbox.ToolboxControl>bu kategoriye atar.  
  
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
  
4. Kılavuza, kılavuz `AddToolbox` üzerinde sol sütuna `MainWindow` **araç kutusu** yerleştiren özel bir yöntem ekleyin.  
  
    ```csharp  
    private void AddToolBox()  
    {  
        ToolboxControl tc = GetToolboxControl();  
        Grid.SetColumn(tc, 0);  
        grid1.Children.Add(tc);  
    }  
    ```  
  
5. Aşağıdaki kodda gösterildiği gibi `AddToolBox` `MainWindow()` sınıf oluşturucusunda yöntemine bir çağrı ekleyin.  
  
    ```csharp  
    public MainWindow()  
    {  
        InitializeComponent();  
        this.RegisterMetadata();  
        this.AddDesigner();  
  
        this.AddToolBox();  
    }  
    ```  
  
6. Çözümünüzü derlemek ve çalıştırmak için F5 tuşuna basın. <xref:System.Activities.Statements.Assign> Ve<xref:System.Activities.Statements.Sequence> etkinliklerini içeren araç kutusu görüntülenmelidir.  
  
### <a name="to-create-the-propertygrid"></a>PropertyGrid oluşturmak için  
  
1. **Çözüm Gezgini** bölmesinde, MainWindow. xaml dosyasına sağ tıklayın ve **kodu görüntüle**' yi seçin.  
  
2. PropertyGrid bölmesini kılavuzdaki en sağdaki `MainWindow` sütuna yerleştirmek için sınıfına yönteminiekleyin.`AddPropertyInspector`  
  
    ```csharp  
    private void AddPropertyInspector()  
    {  
        Grid.SetColumn(wd.PropertyInspectorView, 2);  
        grid1.Children.Add(wd.PropertyInspectorView);              
    }  
    ```  
  
3. Aşağıdaki kodda gösterildiği gibi `AddPropertyInspector` `MainWindow()` sınıf oluşturucusunda yöntemine bir çağrı ekleyin.  
  
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
  
4. Çözümü derlemek ve çalıştırmak için F5 tuşuna basın. **Araç kutusu**, iş akışı tasarım tuvali ve **PropertyGrid** bölmeleri hepsi görüntülenmelidir ve bir <xref:System.Activities.Statements.Assign> etkinliği veya <xref:System.Activities.Statements.Sequence> etkinliği tasarım tuvaline sürüklediğinizde, özellik Kılavuzu, şu değere bağlı olarak güncelleştirilecek Vurgulanan etkinlik.  
  
## <a name="example"></a>Örnek  
 MainWindow.xaml.cs dosyası artık aşağıdaki kodu içermelidir.  
  
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

- [İş Akışı Tasarımcısını Yeniden Barındırma](rehosting-the-workflow-designer.md)
- [Görev 1: Yeni bir Windows Presentation Foundation uygulaması oluşturma](task-1-create-a-new-wpf-app.md)
- [Görev 2: İş Akışı Tasarımcısı barındırın](task-2-host-the-workflow-designer.md)
