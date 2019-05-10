---
title: Özel İfade Düzenleyicisi Kullanma
ms.date: 03/30/2017
ms.assetid: 0901b58b-e037-44a8-8281-f6f54361cfca
ms.openlocfilehash: 9d73134c3f17fad618d26f335d89fdab2d99dbdf
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650911"
---
# <a name="using-a-custom-expression-editor"></a><span data-ttu-id="1ad09-102">Özel İfade Düzenleyicisi Kullanma</span><span class="sxs-lookup"><span data-stu-id="1ad09-102">Using a Custom Expression Editor</span></span>
<span data-ttu-id="1ad09-103">Özel ifade düzenleyicisini düzenleme deneyimi daha zengin ya da daha basit bir ifade sağlamak üzere uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="1ad09-103">A custom expression editor can be implemented to provide a richer or simpler expression editing experience.</span></span> <span data-ttu-id="1ad09-104">Özel ifade düzenleyicisini kullanma isteyebilirsiniz birçok senaryo vardır:</span><span class="sxs-lookup"><span data-stu-id="1ad09-104">There are several scenarios in which you might want to use a custom expression editor:</span></span>  
  
- <span data-ttu-id="1ad09-105">IntelliSense ve diğer zengin düzenleme yeniden barındırılan iş akışı Tasarımcısı'nda özellikleri için destek sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="1ad09-105">To provide support for IntelliSense and other rich editing features in a rehosted workflow designer.</span></span> <span data-ttu-id="1ad09-106">Varsayılan Visual Studio ifade Düzenleyicisi'ni yeniden barındırılan uygulamalarda kullanılamaz çünkü bu işlevselliği sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1ad09-106">This functionality must be provided because the default Visual Studio expression editor cannot be used in rehosted applications.</span></span>  
  
- <span data-ttu-id="1ad09-107">Böylece, örneğin, Visual Basic öğrenin veya Visual Basic deyimleri ile uğraşmanız gerekmez, düzenleme deneyimi iş analisti kullanıcıları için ifade basitleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="1ad09-107">To simplify the expression editing experience for the business analyst users, so that they are not, for example, required to learn Visual Basic or deal with Visual Basic expressions.</span></span>  
  
 <span data-ttu-id="1ad09-108">Özel ifade düzenleyicisini uygulamak için üç temel adımlar gerekir:</span><span class="sxs-lookup"><span data-stu-id="1ad09-108">Three basic steps are needed to implement a custom expression editor:</span></span>  
  
1. <span data-ttu-id="1ad09-109"><xref:System.Activities.Presentation.View.IExpressionEditorService> arabirimini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="1ad09-109">Implement the <xref:System.Activities.Presentation.View.IExpressionEditorService> interface.</span></span> <span data-ttu-id="1ad09-110">Bu arabirim, oluşturulmasını ve ifade Düzenleyicisi yok edilmesini yönetir.</span><span class="sxs-lookup"><span data-stu-id="1ad09-110">This interface manages the creation and destruction of expression editors.</span></span>  
  
2. <span data-ttu-id="1ad09-111"><xref:System.Activities.Presentation.View.IExpressionEditorInstance> arabirimini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="1ad09-111">Implement the <xref:System.Activities.Presentation.View.IExpressionEditorInstance> interface.</span></span> <span data-ttu-id="1ad09-112">Bu arabirim, düzenleme UI'si ifadesi için kullanıcı arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="1ad09-112">This interface implements the UI for expression editing UI.</span></span>  
  
3. <span data-ttu-id="1ad09-113">Yayımlama <xref:System.Activities.Presentation.View.IExpressionEditorService> yeniden barındırılan iş akışı uygulamanızdaki.</span><span class="sxs-lookup"><span data-stu-id="1ad09-113">Publish the <xref:System.Activities.Presentation.View.IExpressionEditorService> in your rehosted workflow application.</span></span>  
  
## <a name="implementing-a-custom-expression-editor-in-a-class-library"></a><span data-ttu-id="1ad09-114">Özel ifade Düzenleyicisi uygulayan bir sınıf kitaplığında</span><span class="sxs-lookup"><span data-stu-id="1ad09-114">Implementing a Custom Expression Editor in a Class Library</span></span>  
 <span data-ttu-id="1ad09-115">(Kavram kanıtı) kod örneği aşağıdadır `MyEditorService` uygulayan sınıf <xref:System.Activities.Presentation.View.IExpressionEditorService> arabirimi MyExpressionEditorService kitaplığı projesinde yer alan.</span><span class="sxs-lookup"><span data-stu-id="1ad09-115">Here is a sample of code for a (proof of concept) `MyEditorService` class that implements the <xref:System.Activities.Presentation.View.IExpressionEditorService> interface is contained in a MyExpressionEditorService library project.</span></span>  
  
```  
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
  
 <span data-ttu-id="1ad09-116">Kodu için bir `MyExpressionEditorInstance` uygulayan sınıf <xref:System.Activities.Presentation.View.IExpressionEditorInstance> MyExpressionEditorService kitaplığı projesinde arabirimi.</span><span class="sxs-lookup"><span data-stu-id="1ad09-116">Here is the code for a `MyExpressionEditorInstance` class that implements the <xref:System.Activities.Presentation.View.IExpressionEditorInstance> interface in a MyExpressionEditorService library project.</span></span>  
  
```  
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
  
### <a name="publishing-a-custom-expression-editor-in-a-wpf-project"></a><span data-ttu-id="1ad09-117">Özel ifade düzenleyicisi içinde bir WPF projesi yayımlama</span><span class="sxs-lookup"><span data-stu-id="1ad09-117">Publishing a Custom Expression Editor in a WPF Project</span></span>  
 <span data-ttu-id="1ad09-118">Tasarımcıda yeniden barındırma gösteren kodunu bir [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] uygulama ve oluşturma ve yayımlama `MyEditorService` hizmeti.</span><span class="sxs-lookup"><span data-stu-id="1ad09-118">Here is the code that shows how to rehost the designer in a [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] application and how to create and publish the `MyEditorService` service.</span></span> <span data-ttu-id="1ad09-119">Bu kodu kullanmadan önce avalon2 uygulamayı içeren projeden MyExpressionEditorService kitaplığı projesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1ad09-119">Before using this code, add a reference to the MyExpressionEditorService library project from the project that contains the avalon2 application.</span></span>  
  
```  
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
  
### <a name="notes"></a><span data-ttu-id="1ad09-120">Notlar</span><span class="sxs-lookup"><span data-stu-id="1ad09-120">Notes</span></span>  
 <span data-ttu-id="1ad09-121">Kullanıyorsanız bir **ExpressionTextBox** denetimi bir özel etkinlik Tasarımcısı'nda oluşturup ifade düzenleyicileri kullanarak yok etmek ise gerekli değildir <xref:System.Activities.Presentation.View.IExpressionEditorService.CreateExpressionEditor%2A> ve <xref:System.Activities.Presentation.View.IExpressionEditorService.CloseExpressionEditors%2A> yöntemlerinin <xref:System.Activities.Presentation.View.IExpressionEditorService> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="1ad09-121">If you are using an **ExpressionTextBox** control in a custom activity designer, it is not necessary to create and destroy expression editors using the <xref:System.Activities.Presentation.View.IExpressionEditorService.CreateExpressionEditor%2A> and <xref:System.Activities.Presentation.View.IExpressionEditorService.CloseExpressionEditors%2A> methods of the <xref:System.Activities.Presentation.View.IExpressionEditorService> interface.</span></span> <span data-ttu-id="1ad09-122"><xref:System.Activities.Presentation.View.ExpressionTextBox> Sınıfı yönetir bu sizin için.</span><span class="sxs-lookup"><span data-stu-id="1ad09-122">The <xref:System.Activities.Presentation.View.ExpressionTextBox> class manages this for you.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ad09-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ad09-123">See also</span></span>

- <xref:System.Activities.Presentation.View.IExpressionEditorService>
- <xref:System.Activities.Presentation.View.IExpressionEditorInstance>
- [<span data-ttu-id="1ad09-124">Özel Etkinlik Tasarımcısında ExpressionTextBox Kullanma</span><span class="sxs-lookup"><span data-stu-id="1ad09-124">Using the ExpressionTextBox in a Custom Activity Designer</span></span>](./samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
