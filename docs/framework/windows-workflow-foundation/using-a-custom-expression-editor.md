---
title: Özel İfade Düzenleyicisi Kullanma
ms.date: 03/30/2017
ms.assetid: 0901b58b-e037-44a8-8281-f6f54361cfca
ms.openlocfilehash: 9e179914a56874ddc9f3f170d35ae04c97dd859e
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988787"
---
# <a name="using-a-custom-expression-editor"></a><span data-ttu-id="cf1c4-102">Özel İfade Düzenleyicisi Kullanma</span><span class="sxs-lookup"><span data-stu-id="cf1c4-102">Using a Custom Expression Editor</span></span>
<span data-ttu-id="cf1c4-103">Bir özel ifade Düzenleyicisi, daha zengin veya daha basit bir ifade düzenleme deneyimi sağlamak için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="cf1c4-103">A custom expression editor can be implemented to provide a richer or simpler expression editing experience.</span></span> <span data-ttu-id="cf1c4-104">Özel ifade Düzenleyicisi kullanmak isteyebileceğiniz birkaç senaryo vardır:</span><span class="sxs-lookup"><span data-stu-id="cf1c4-104">There are several scenarios in which you might want to use a custom expression editor:</span></span>  
  
- <span data-ttu-id="cf1c4-105">Bir yeniden barındırılan iş akışı tasarımcısında IntelliSense ve diğer zengin düzen özelliklerine yönelik destek sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="cf1c4-105">To provide support for IntelliSense and other rich editing features in a rehosted workflow designer.</span></span> <span data-ttu-id="cf1c4-106">Bu işlev, varsayılan Visual Studio ifade Düzenleyicisi yeniden barındırılan uygulamalarda kullanılamadığından sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cf1c4-106">This functionality must be provided because the default Visual Studio expression editor cannot be used in rehosted applications.</span></span>  
  
- <span data-ttu-id="cf1c4-107">İş analistlerine yönelik ifade düzenlemesi deneyimini basitleştirmek için, örneğin, Visual Basic öğrenmek veya Visual Basic ifadelerle uğraşmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="cf1c4-107">To simplify the expression editing experience for the business analyst users, so that they are not, for example, required to learn Visual Basic or deal with Visual Basic expressions.</span></span>  
  
 <span data-ttu-id="cf1c4-108">Özel ifade Düzenleyicisi uygulamak için üç temel adım gereklidir:</span><span class="sxs-lookup"><span data-stu-id="cf1c4-108">Three basic steps are needed to implement a custom expression editor:</span></span>  
  
1. <span data-ttu-id="cf1c4-109"><xref:System.Activities.Presentation.View.IExpressionEditorService> arabirimini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="cf1c4-109">Implement the <xref:System.Activities.Presentation.View.IExpressionEditorService> interface.</span></span> <span data-ttu-id="cf1c4-110">Bu arabirim, ifade düzenleyicilerinin oluşturulmasını ve yok edilmesini yönetir.</span><span class="sxs-lookup"><span data-stu-id="cf1c4-110">This interface manages the creation and destruction of expression editors.</span></span>  
  
2. <span data-ttu-id="cf1c4-111"><xref:System.Activities.Presentation.View.IExpressionEditorInstance> arabirimini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="cf1c4-111">Implement the <xref:System.Activities.Presentation.View.IExpressionEditorInstance> interface.</span></span> <span data-ttu-id="cf1c4-112">Bu arabirim, ifade düzenlemesi Kullanıcı arabirimi için Kullanıcı arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="cf1c4-112">This interface implements the UI for expression editing UI.</span></span>  
  
3. <span data-ttu-id="cf1c4-113"><xref:System.Activities.Presentation.View.IExpressionEditorService> ' İ yeniden barındırılan iş akışı uygulamanızda yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="cf1c4-113">Publish the <xref:System.Activities.Presentation.View.IExpressionEditorService> in your rehosted workflow application.</span></span>  
  
## <a name="implementing-a-custom-expression-editor-in-a-class-library"></a><span data-ttu-id="cf1c4-114">Bir sınıf kitaplığında özel Ifade Düzenleyicisi uygulama</span><span class="sxs-lookup"><span data-stu-id="cf1c4-114">Implementing a Custom Expression Editor in a Class Library</span></span>  
 <span data-ttu-id="cf1c4-115">Bir myexpressioneditorservice kitaplık projesinde, `MyEditorService` <xref:System.Activities.Presentation.View.IExpressionEditorService> arabirimi uygulayan bir (kavram kanıtı kanıtlama) sınıfı için kod örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cf1c4-115">Here is a sample of code for a (proof of concept) `MyEditorService` class that implements the <xref:System.Activities.Presentation.View.IExpressionEditorService> interface is contained in a MyExpressionEditorService library project.</span></span>  
  
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
  
 <span data-ttu-id="cf1c4-116">Bir myexpressioneditorservice kitaplık `MyExpressionEditorInstance` projesinde <xref:System.Activities.Presentation.View.IExpressionEditorInstance> arabirimi uygulayan bir sınıf için kod aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cf1c4-116">Here is the code for a `MyExpressionEditorInstance` class that implements the <xref:System.Activities.Presentation.View.IExpressionEditorInstance> interface in a MyExpressionEditorService library project.</span></span>  
  
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
  
### <a name="publishing-a-custom-expression-editor-in-a-wpf-project"></a><span data-ttu-id="cf1c4-117">WPF projesinde özel Ifade Düzenleyicisi yayımlama</span><span class="sxs-lookup"><span data-stu-id="cf1c4-117">Publishing a Custom Expression Editor in a WPF Project</span></span>  
 <span data-ttu-id="cf1c4-118">Tasarımcı 'nın WPF uygulamasında nasıl yeniden barındırılacağını ve `MyEditorService` hizmetin nasıl oluşturulacağını ve yayınlanalınacağını gösteren kod aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cf1c4-118">Here is the code that shows how to rehost the designer in a WPF application and how to create and publish the `MyEditorService` service.</span></span> <span data-ttu-id="cf1c4-119">Bu kodu kullanmadan önce, avalon2 uygulamasını içeren projeden MyExpressionEditorService kitaplık projesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cf1c4-119">Before using this code, add a reference to the MyExpressionEditorService library project from the project that contains the avalon2 application.</span></span>  
  
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
  
### <a name="notes"></a><span data-ttu-id="cf1c4-120">Notlar</span><span class="sxs-lookup"><span data-stu-id="cf1c4-120">Notes</span></span>  
 <span data-ttu-id="cf1c4-121">Özel bir etkinlik tasarımcısında bir **ExpressionTextBox** denetimi kullanıyorsanız, bu <xref:System.Activities.Presentation.View.IExpressionEditorService.CreateExpressionEditor%2A> <xref:System.Activities.Presentation.View.IExpressionEditorService> arabirimin ve <xref:System.Activities.Presentation.View.IExpressionEditorService.CloseExpressionEditors%2A> yöntemlerini kullanarak ifade düzenleyicilerinin oluşturulması ve yok olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="cf1c4-121">If you are using an **ExpressionTextBox** control in a custom activity designer, it is not necessary to create and destroy expression editors using the <xref:System.Activities.Presentation.View.IExpressionEditorService.CreateExpressionEditor%2A> and <xref:System.Activities.Presentation.View.IExpressionEditorService.CloseExpressionEditors%2A> methods of the <xref:System.Activities.Presentation.View.IExpressionEditorService> interface.</span></span> <span data-ttu-id="cf1c4-122"><xref:System.Activities.Presentation.View.ExpressionTextBox> Sınıfı bunu sizin için yönetir.</span><span class="sxs-lookup"><span data-stu-id="cf1c4-122">The <xref:System.Activities.Presentation.View.ExpressionTextBox> class manages this for you.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf1c4-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf1c4-123">See also</span></span>

- <xref:System.Activities.Presentation.View.IExpressionEditorService>
- <xref:System.Activities.Presentation.View.IExpressionEditorInstance>
- [<span data-ttu-id="cf1c4-124">Özel Etkinlik Tasarımcısında ExpressionTextBox Kullanma</span><span class="sxs-lookup"><span data-stu-id="cf1c4-124">Using the ExpressionTextBox in a Custom Activity Designer</span></span>](./samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
