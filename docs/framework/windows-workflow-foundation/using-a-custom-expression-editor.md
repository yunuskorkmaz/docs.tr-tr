---
title: "Bir özel ifade Düzenleyicisi'ni kullanarak"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0901b58b-e037-44a8-8281-f6f54361cfca
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3a809c1d0eeb8f45d55f4e1f436b70ceb01b4a2f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="using-a-custom-expression-editor"></a><span data-ttu-id="53505-102">Bir özel ifade Düzenleyicisi'ni kullanarak</span><span class="sxs-lookup"><span data-stu-id="53505-102">Using a Custom Expression Editor</span></span>
<span data-ttu-id="53505-103">Özel ifade Düzenleyicisi düzenleme deneyimi daha zengin ya da daha basit bir ifade sağlamak üzere uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="53505-103">A custom expression editor can be implemented to provide a richer or simpler expression editing experience.</span></span> <span data-ttu-id="53505-104">Özel ifade Düzenleyicisi kullanmak isteyebilirsiniz birkaç senaryo vardır:</span><span class="sxs-lookup"><span data-stu-id="53505-104">There are several scenarios in which you might want to use a custom expression editor:</span></span>  
  
-   <span data-ttu-id="53505-105">İçin IntelliSense ve diğer zengin düzenleme rehosted iş akışı Tasarımcısı'nda özellikleri için destek sağlama.</span><span class="sxs-lookup"><span data-stu-id="53505-105">To provide support for IntelliSense and other rich editing features in a rehosted workflow designer.</span></span> <span data-ttu-id="53505-106">Bu işlev sağlanmalıdır varsayılan [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ifade Düzenleyicisi rehosted uygulamalarda kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="53505-106">This functionality must be provided because the default [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] expression editor cannot be used in rehosted applications.</span></span>  
  
-   <span data-ttu-id="53505-107">Böylece, örneğin, bilgi edinmek için gerekli değildir, iş analisti kullanıcılar için deneyimi düzenleme ifade basitleştirmek için [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] veya uğraşmanız [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] ifadeler.</span><span class="sxs-lookup"><span data-stu-id="53505-107">To simplify the expression editing experience for the business analyst users, so that they are not, for example, required to learn [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] or deal with [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] expressions.</span></span>  
  
 <span data-ttu-id="53505-108">Bir özel ifade Düzenleyicisi'ni uygulamak için üç temel adımlar gerekir:</span><span class="sxs-lookup"><span data-stu-id="53505-108">Three basic steps are needed to implement a custom expression editor:</span></span>  
  
1.  <span data-ttu-id="53505-109">Uygulama <xref:System.Activities.Presentation.View.IExpressionEditorService> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="53505-109">Implement the <xref:System.Activities.Presentation.View.IExpressionEditorService> interface.</span></span> <span data-ttu-id="53505-110">Bu arabirim oluşturma ve yok etme ifade Düzenleyicileri'nin yönetir.</span><span class="sxs-lookup"><span data-stu-id="53505-110">This interface manages the creation and destruction of expression editors.</span></span>  
  
2.  <span data-ttu-id="53505-111">Uygulama <xref:System.Activities.Presentation.View.IExpressionEditorInstance> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="53505-111">Implement the <xref:System.Activities.Presentation.View.IExpressionEditorInstance> interface.</span></span> <span data-ttu-id="53505-112">Bu arabirim UI düzenleme ifadesi için kullanıcı arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="53505-112">This interface implements the UI for expression editing UI.</span></span>  
  
3.  <span data-ttu-id="53505-113">Yayımlama <xref:System.Activities.Presentation.View.IExpressionEditorService> rehosted iş akışı uygulamanızda.</span><span class="sxs-lookup"><span data-stu-id="53505-113">Publish the <xref:System.Activities.Presentation.View.IExpressionEditorService> in your rehosted workflow application.</span></span>  
  
## <a name="implementing-a-custom-expression-editor-in-a-class-library"></a><span data-ttu-id="53505-114">Bir sınıf kitaplığı'nda bir özel ifade Düzenleyicisi uygulama</span><span class="sxs-lookup"><span data-stu-id="53505-114">Implementing a Custom Expression Editor in a Class Library</span></span>  
 <span data-ttu-id="53505-115">Örnek kod (kavram kanıtı) için işte `MyEditorService` uygulayan sınıf <xref:System.Activities.Presentation.View.IExpressionEditorService> arabirimi MyExpressionEditorService kitaplığında bulunan.</span><span class="sxs-lookup"><span data-stu-id="53505-115">Here is a sample of code for a (proof of concept) `MyEditorService` class that implements the <xref:System.Activities.Presentation.View.IExpressionEditorService> interface is contained in a MyExpressionEditorService library project.</span></span>  
  
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
  
 <span data-ttu-id="53505-116">Kodunu İşte bir `MyExpressionEditorInstance` uygulayan sınıf <xref:System.Activities.Presentation.View.IExpressionEditorInstance> MyExpressionEditorService kitaplığı projesinde arabirimi.</span><span class="sxs-lookup"><span data-stu-id="53505-116">Here is the code for a `MyExpressionEditorInstance` class that implements the <xref:System.Activities.Presentation.View.IExpressionEditorInstance> interface in a MyExpressionEditorService library project.</span></span>  
  
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
  
### <a name="publishing-a-custom-expression-editor-in-a-wpf-project"></a><span data-ttu-id="53505-117">Bir özel ifade Düzenleyici bir WPF projesi yayımlama</span><span class="sxs-lookup"><span data-stu-id="53505-117">Publishing a Custom Expression Editor in a WPF Project</span></span>  
 <span data-ttu-id="53505-118">Tasarımcıda yeniden barındırma gösteren kod İşte bir [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] uygulama ve oluşturmak ve yayımlamak nasıl `MyEditorService` hizmet.</span><span class="sxs-lookup"><span data-stu-id="53505-118">Here is the code that shows how to rehost the designer in a [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] application and how to create and publish the `MyEditorService` service.</span></span> <span data-ttu-id="53505-119">Bu kodu kullanmadan önce avalon2 uygulamayı içeren projeden MyExpressionEditorService kitaplığı projesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="53505-119">Before using this code, add a reference to the MyExpressionEditorService library project from the project that contains the avalon2 application.</span></span>  
  
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
  
### <a name="notes"></a><span data-ttu-id="53505-120">Notlar</span><span class="sxs-lookup"><span data-stu-id="53505-120">Notes</span></span>  
 <span data-ttu-id="53505-121">Kullanıyorsanız bir **ExpressionTextBox** denetim özel etkinlik Tasarımcısı'nda oluşturma ve kullanma ifade düzenleyicileri yok etmek ise gerekli değildir <xref:System.Activities.Presentation.View.IExpressionEditorService.CreateExpressionEditor%2A> ve <xref:System.Activities.Presentation.View.IExpressionEditorService.CloseExpressionEditors%2A> yöntemlerinin <xref:System.Activities.Presentation.View.IExpressionEditorService> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="53505-121">If you are using an **ExpressionTextBox** control in a custom activity designer, it is not necessary to create and destroy expression editors using the <xref:System.Activities.Presentation.View.IExpressionEditorService.CreateExpressionEditor%2A> and <xref:System.Activities.Presentation.View.IExpressionEditorService.CloseExpressionEditors%2A> methods of the <xref:System.Activities.Presentation.View.IExpressionEditorService> interface.</span></span> <span data-ttu-id="53505-122"><xref:System.Activities.Presentation.View.ExpressionTextBox> Sınıfı yönetir bu sizin için.</span><span class="sxs-lookup"><span data-stu-id="53505-122">The <xref:System.Activities.Presentation.View.ExpressionTextBox> class manages this for you.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53505-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="53505-123">See Also</span></span>  
 <xref:System.Activities.Presentation.View.IExpressionEditorService>  
 <xref:System.Activities.Presentation.View.IExpressionEditorInstance>  
 [<span data-ttu-id="53505-124">Özel Etkinlik Tasarımcısı'nda ExpressionTextBox kullanma</span><span class="sxs-lookup"><span data-stu-id="53505-124">Using the ExpressionTextBox in a Custom Activity Designer</span></span>](../../../docs/framework/windows-workflow-foundation/samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
