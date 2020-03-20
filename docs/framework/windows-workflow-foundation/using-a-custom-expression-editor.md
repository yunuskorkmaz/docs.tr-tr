---
title: Özel İfade Düzenleyicisi Kullanma
ms.date: 03/30/2017
ms.assetid: 0901b58b-e037-44a8-8281-f6f54361cfca
ms.openlocfilehash: a1cd92766c8897868920c1465ddb3eeabae1aa97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182709"
---
# <a name="using-a-custom-expression-editor"></a>Özel İfade Düzenleyicisi Kullanma
Daha zengin veya daha basit bir ifade düzenleme deneyimi sağlamak için özel bir ifade düzenleyicisi uygulanabilir. Özel bir ifade düzenleyicisi kullanmak isteyebileceğin birkaç senaryo vardır:  
  
- Yeniden barındırılan iş akışı tasarımcısında IntelliSense ve diğer zengin düzenleme özellikleri için destek sağlamak. Varsayılan Visual Studio ifade düzenleyicisi yeniden barındırılan uygulamalarda kullanılamadığından, bu işlevsellik sağlanmalıdır.  
  
- İş analisti kullanıcılar için ifade düzenleme deneyimini basitleştirmek için, örneğin Visual Basic'i öğrenmeleri veya Visual Basic ifadeleriyle ilgilenmeleri gerekmesin.  
  
 Özel bir ifade düzenleyicisi uygulamak için üç temel adım gereklidir:  
  
1. <xref:System.Activities.Presentation.View.IExpressionEditorService> arabirimini gerçekleştirin. Bu arabirim, ifade editörlerinin oluşturulmasını ve yok edilmesini yönetir.  
  
2. <xref:System.Activities.Presentation.View.IExpressionEditorInstance> arabirimini gerçekleştirin. Bu arabirim, ifade düzenleme UI için UI uygular.  
  
3. Yeniden <xref:System.Activities.Presentation.View.IExpressionEditorService> barındırılan iş akışı uygulamanızda yayımlayın.  
  
## <a name="implementing-a-custom-expression-editor-in-a-class-library"></a>Sınıf Kitaplığında Özel İfade Düzenleyicisi Uygulama  
 Burada `MyEditorService` <xref:System.Activities.Presentation.View.IExpressionEditorService> arabirimi uygulayan bir (kavram kanıtı) sınıfı için kod örneği MyExpressionEditorService kitaplık projesinde yer almaktadır.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Activities.Presentation.View;  
using System.Activities.Presentation.Hosting;  
using System.Activities.Presentation.Model;  
  
namespace MyExpressionEditorService  
{  
    public class MyEditorService : IExpressionEditorService  
    {  
        public void CloseExpressionEditors()  
        {  
  
        }  
        public IExpressionEditorInstance CreateExpressionEditor(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces, List<ModelItem> variables, string text)  
        {  
            MyExpressionEditorInstance instance = new MyExpressionEditorInstance();  
            return instance;  
        }  
        public IExpressionEditorInstance CreateExpressionEditor(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces, List<ModelItem> variables, string text, System.Windows.Size initialSize)  
                {  
            MyExpressionEditorInstance instance = new MyExpressionEditorInstance();  
            return instance;  
        }  
        public IExpressionEditorInstance CreateExpressionEditor(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces, List<ModelItem> variables, string text, Type expressionType)  
            {  
            MyExpressionEditorInstance instance = new MyExpressionEditorInstance();  
            return instance;  
        }  
        public IExpressionEditorInstance CreateExpressionEditor(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces, List<ModelItem> variables, string text, Type expressionType, System.Windows.Size initialSize)  
        {  
            MyExpressionEditorInstance instance = new MyExpressionEditorInstance();  
            return instance;  
        }  
        public void UpdateContext(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces)  
        {  
  
        }  
  
    }  
}  
```  
  
 Burada MyExpressionEditorService `MyExpressionEditorInstance` kitaplık projesinde <xref:System.Activities.Presentation.View.IExpressionEditorInstance> arabirimi uygulayan bir sınıfın kodu verilmiştir.  
  
```csharp  
using System;  
using System.Activities.Presentation.View;  
using System.Windows;  
using System.Reflection;  
using System.Windows.Controls;  
  
namespace MyExpressionEditorService  
{  
    public class MyExpressionEditorInstance : IExpressionEditorInstance  
    {  
        private TextBox textBox = new TextBox();  
  
        public bool AcceptsReturn { get; set; }  
        public bool AcceptsTab { get; set; }  
        public bool HasAggregateFocus {  
            get  
            {  
                return true;  
            }  
        }  
  
        public System.Windows.Controls.ScrollBarVisibility HorizontalScrollBarVisibility { get; set; }  
        public System.Windows.Controls.Control HostControl {  
            get  
            {  
                return textBox;  
            }  
        }  
        public int MaxLines { get; set; }  
        public int MinLines { get; set; }  
        public string Text { get; set; }  
        public System.Windows.Controls.ScrollBarVisibility VerticalScrollBarVisibility { get; set; }  
  
        public event EventHandler Closing;  
        public event EventHandler GotAggregateFocus;  
        public event EventHandler LostAggregateFocus;  
        public event EventHandler TextChanged;  
  
        public bool CanCompleteWord()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanCopy()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanCut()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanDecreaseFilterLevel()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanGlobalIntellisense()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanIncreaseFilterLevel()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanParameterInfo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanPaste()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanQuickInfo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanRedo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanUndo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
  
        public void ClearSelection()  
        {  
            MessageBox.Show(MethodBase.GetCurrentMethod().Name);  
        }  
        public void Close()  
        {  
            MessageBox.Show(MethodBase.GetCurrentMethod().Name);  
        }  
        public bool CompleteWord()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Copy()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Cut()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool DecreaseFilterLevel()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public void Focus()  
        {  
            MessageBox.Show(MethodBase.GetCurrentMethod().Name);  
        }  
        public string GetCommittedText()  
        {  
            return "CommittedText";  
        }  
        public bool GlobalIntellisense()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool IncreaseFilterLevel()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool ParameterInfo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Paste()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool QuickInfo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Redo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Undo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
    }  
}  
```  
  
### <a name="publishing-a-custom-expression-editor-in-a-wpf-project"></a>WPF Projesinde Özel İfade Düzenleyicisi Yayınlama  
 Burada, tasarımcının WPF uygulamasında nasıl yeniden barındırılabildiğini ve `MyEditorService` hizmetin nasıl oluşturulup yayımlandırılabildiğini gösteren kod ve kod ve readesi aşağıda verebilmektedir. Bu kodu kullanmadan önce, avalon2 uygulamasını içeren projeden MyExpressionEditorService kitaplık projesine bir başvuru ekleyin.  
  
```csharp  
using System.Windows;  
using System.Windows.Controls;  
using System.Activities.Presentation;  
using System.Activities.Statements;  
using System.Activities.Core.Presentation;  
using System.Activities.Presentation.View;  
using MyExpressionEditorService;  
  
namespace WpfApplication1  
{  
    /// <summary>  
    /// Interaction logic for MainWindow.xaml  
    /// </summary>  
    public partial class MainWindow : Window  
    {  
  
        private MyEditorService expressionEditorService;  
        public MainWindow()  
        {  
            InitializeComponent();  
            new DesignerMetadata().Register();  
            createDesigner();  
        }  
  
        public void createDesigner()  
        {  
            WorkflowDesigner designer = new WorkflowDesigner();  
            Sequence root = new Sequence()  
            {  
                Activities = {  
                new Assign(),  
                new WriteLine()}  
            };  
  
            designer.Load(root);  
  
            Grid.SetColumn(designer.View, 0);  
  
            // Create ExpressionEditorService
            this.expressionEditorService = new MyEditorService();  
  
            // Publish the instance of MyEditorService.  
            designer.Context.Services.Publish<IExpressionEditorService>(this.expressionEditorService);  
  
            MyGrid.Children.Add(designer.View);  
        }  
    }  
}  
```  
  
### <a name="notes"></a>Notlar  
 Özel bir etkinlik tasarımcısında **ExpressionTextBox** denetimi kullanıyorsanız, <xref:System.Activities.Presentation.View.IExpressionEditorService.CreateExpressionEditor%2A> <xref:System.Activities.Presentation.View.IExpressionEditorService.CloseExpressionEditors%2A> <xref:System.Activities.Presentation.View.IExpressionEditorService> arabirimin yöntemlerini kullanarak ifade düzenleyicileri oluşturmak ve yok etmek gerekmez. Sınıf <xref:System.Activities.Presentation.View.ExpressionTextBox> bunu senin için yönetiyor.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Presentation.View.IExpressionEditorService>
- <xref:System.Activities.Presentation.View.IExpressionEditorInstance>
- [Özel Etkinlik Tasarımcısında ExpressionTextBox Kullanma](./samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
