---
title: '2. Görev: İş akışı tasarımcısını barındırma'
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: e8895e4b2c90f189c88ec3a803615e736dada455
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572779"
---
# <a name="task-2-host-the-workflow-designer"></a><span data-ttu-id="aaaf9-102">2. Görev: İş akışı tasarımcısını barındırma</span><span class="sxs-lookup"><span data-stu-id="aaaf9-102">Task 2: Host the Workflow Designer</span></span>
<span data-ttu-id="aaaf9-103">Bu konuda bir örneğini barındıran yordamı açıklanır [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] bir Windows Presentation Foundation (WPF) uygulamasındaki.</span><span class="sxs-lookup"><span data-stu-id="aaaf9-103">This topic describes the procedure for hosting an instance of the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] in a Windows Presentation Foundation (WPF) application.</span></span>  
  
 <span data-ttu-id="aaaf9-104">Yordam yapılandırır **kılavuz** Tasarımcısı içeren denetimi program aracılığıyla bir örneğini oluşturur <xref:System.Activities.Presentation.WorkflowDesigner> varsayılan içeren <xref:System.Activities.Statements.Sequence> etkinliğini kaydeder sağlamak için tasarımcı meta verisi tüm yerleşik etkinlikler ve ana bilgisayarlar için tasarımcı desteği [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] içinde [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="aaaf9-104">The procedure configures the **Grid** control that contains the designer, programmatically creates an instance of the <xref:System.Activities.Presentation.WorkflowDesigner> that contains a default <xref:System.Activities.Statements.Sequence> activity, registers the designer metadata to provide designer support for all built-in activities, and hosts the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] in the [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] application.</span></span>  
  
### <a name="to-host-the-workflow-designer"></a><span data-ttu-id="aaaf9-105">İş akışı tasarımcısını barındırma için</span><span class="sxs-lookup"><span data-stu-id="aaaf9-105">To host the workflow designer</span></span>  
  
1.  <span data-ttu-id="aaaf9-106">Açık HostingApplication proje oluşturduğunuz [görev 1: Yeni bir Windows Presentation Foundation uygulaması oluşturma](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md).</span><span class="sxs-lookup"><span data-stu-id="aaaf9-106">Open the HostingApplication project you created in [Task 1: Create a New Windows Presentation Foundation Application](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md).</span></span>  
  
2.  <span data-ttu-id="aaaf9-107">Kullanımını kolaylaştırmak için penceresinin boyutunu ayarlayın [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="aaaf9-107">Adjust the size of the window to make it easier to use the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span></span> <span data-ttu-id="aaaf9-108">Bunu yapmak için **MainWindow** Tasarımcısı'nda görüntülenecek F4 tuşuna basın **özellikleri** penceresinde hem de **Düzen** var. bölümünde, **genişliği** 600 değerini ve **yükseklik** 350 değerini.</span><span class="sxs-lookup"><span data-stu-id="aaaf9-108">To do this, select **MainWindow** in the designer, press F4 to display the **Properties** window, and, in the **Layout** section there, set the **Width** to a value of 600 and the **Height** to a value of 350.</span></span>  
  
3.  <span data-ttu-id="aaaf9-109">Kılavuz adı seçerek ayarlayın **kılavuz** Tasarımcı panelinde (kutusunun içine tıklayın **MainWindow**) ve ayarı **adı** en üstündeki özellik  **Özellikleri** "grid1" penceresine.</span><span class="sxs-lookup"><span data-stu-id="aaaf9-109">Set the grid name by selecting the **Grid** panel in the designer (click the box inside the **MainWindow**) and setting the **Name** property at the top of the **Properties** window to "grid1".</span></span>  
  
4.  <span data-ttu-id="aaaf9-110">İçinde **özellikleri** penceresinde üç noktaya tıklayın (**...** ) yanındaki `ColumnDefinitions` açmak için özellik **Koleksiyonu Düzenleyicisi** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="aaaf9-110">In the **Properties** window, click the ellipsis (**…**) next to the `ColumnDefinitions` property to open the **Collection Editor** dialog box.</span></span>  
  
5.  <span data-ttu-id="aaaf9-111">İçinde **Koleksiyonu Düzenleyicisi** iletişim kutusu, tıklayın **Ekle** düğmesini düzene üç sütun eklemek için üç kez.</span><span class="sxs-lookup"><span data-stu-id="aaaf9-111">In the **Collection Editor** dialog box, click the **Add** button three times to insert three columns into the layout.</span></span> <span data-ttu-id="aaaf9-112">İlk sütun içerecek **araç kutusu**, ikinci sütun barındıracak [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], ve üçüncü sütunda Özellik denetçisi için kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="aaaf9-112">The first column will contain the **Toolbox**, the second column will host the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], and the third column will be used for the property inspector.</span></span>  
  
6.  <span data-ttu-id="aaaf9-113">Ayarlama `Width` Ortadaki sütun değerine özelliğini "4 \*".</span><span class="sxs-lookup"><span data-stu-id="aaaf9-113">Set the `Width` property of the middle column to the value "4\*".</span></span>  
  
7.  <span data-ttu-id="aaaf9-114">Değişiklikleri kaydetmek için **Tamam** 'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="aaaf9-114">Click **OK** to save the changes.</span></span> <span data-ttu-id="aaaf9-115">Aşağıdaki XAML MainWindow.xaml dosyanıza eklenir:</span><span class="sxs-lookup"><span data-stu-id="aaaf9-115">The following XAML is added to your MainWindow.xaml file:</span></span>  
  
    ```xml  
    <Grid Name="grid1">  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition />  
            <ColumnDefinition Width="4*" />  
            <ColumnDefinition />  
        </Grid.ColumnDefinitions>  
    </Grid>  
    ```  
  
8.  <span data-ttu-id="aaaf9-116">İçinde **Çözüm Gezgini**, MainWindow.xaml sağ tıklayıp **kodu görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="aaaf9-116">In **Solution Explorer**, right-click MainWindow.xaml and select **View Code**.</span></span> <span data-ttu-id="aaaf9-117">Aşağıdaki adımları izleyerek kodu değiştirin:</span><span class="sxs-lookup"><span data-stu-id="aaaf9-117">Modify the code by following these steps:</span></span>  
  
    1.  <span data-ttu-id="aaaf9-118">Aşağıdaki ad alanlarını ekleyin:</span><span class="sxs-lookup"><span data-stu-id="aaaf9-118">Add the following namespaces:</span></span>  
  
        ```csharp  
        using System.Activities;  
        using System.Activities.Core.Presentation;  
        using System.Activities.Presentation;  
        using System.Activities.Presentation.Metadata;  
        using System.Activities.Presentation.Toolbox;  
        using System.Activities.Statements;  
        using System.ComponentModel;  
        ```  
  
    2.  <span data-ttu-id="aaaf9-119">Örneği tutmak için bir özel üye alanı bildirmek için <xref:System.Activities.Presentation.WorkflowDesigner>, aşağıdaki kodu ekleyin `MainWindow` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="aaaf9-119">To declare a private member field to hold an instance of the <xref:System.Activities.Presentation.WorkflowDesigner>, add the following code to the `MainWindow` class.</span></span>  
  
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
  
    3.  <span data-ttu-id="aaaf9-120">Aşağıdaki `AddDesigner` yönteme `MainWindow` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="aaaf9-120">Add the following `AddDesigner` method to the `MainWindow` class.</span></span> <span data-ttu-id="aaaf9-121">Uygulama örneği oluşturur <xref:System.Activities.Presentation.WorkflowDesigner>, ekler bir <xref:System.Activities.Statements.Sequence> , etkinliğini ve grid1 Orta sütundaki yerleştirir **kılavuz**.</span><span class="sxs-lookup"><span data-stu-id="aaaf9-121">The implementation creates an instance of the <xref:System.Activities.Presentation.WorkflowDesigner>, adds a <xref:System.Activities.Statements.Sequence> activity to it, and places it in middle column of the grid1 **Grid**.</span></span>  
  
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
  
    4.  <span data-ttu-id="aaaf9-122">Tüm yerleşik etkinlikler için tasarımcı desteği eklemek için tasarımcı meta verisi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="aaaf9-122">Register the designer metadata to add designer support for all the  built-in activities.</span></span> <span data-ttu-id="aaaf9-123">Bu sayede özgün araç kutusundan etkinlikleri bırakmak <xref:System.Activities.Statements.Sequence> etkinliğinde [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="aaaf9-123">This enables you to drop activities from the toolbox onto the original <xref:System.Activities.Statements.Sequence> activity in the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span></span> <span data-ttu-id="aaaf9-124">Bunu yapmak için ekleme `RegisterMetadata` yönteme `MainWindow` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="aaaf9-124">To do this, add the `RegisterMetadata` method to the `MainWindow` class.</span></span>  
  
        ```csharp  
        private void RegisterMetadata()  
        {               
            DesignerMetadata dm = new DesignerMetadata();  
            dm.Register();  
        }  
        ```  
  
         <span data-ttu-id="aaaf9-125">Etkinlik tasarımcıları kaydetme hakkında daha fazla bilgi için bkz. [nasıl yapılır: Özel Etkinlik Tasarımcısı oluşturma](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer.md).</span><span class="sxs-lookup"><span data-stu-id="aaaf9-125">For more information about registering activity designers, see [How to: Create a Custom Activity Designer](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer.md).</span></span>  
  
    5.  <span data-ttu-id="aaaf9-126">İçinde `MainWindow` sınıfının oluşturucusu, tasarımcı desteği için meta verileri kaydetmek ve oluşturmak için daha önce bildirilen yöntemlere yapılan çağrılar ekleyin <xref:System.Activities.Presentation.WorkflowDesigner>.</span><span class="sxs-lookup"><span data-stu-id="aaaf9-126">In the `MainWindow` class constructor, add calls to the methods declared previously to register the metadata for designer support and to create the <xref:System.Activities.Presentation.WorkflowDesigner>.</span></span>  
  
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
        >  <span data-ttu-id="aaaf9-127">`RegisterMetadata` Yöntemi de içeren yerleşik etkinlikler Tasarımcı meta verilerini kaydeder <xref:System.Activities.Statements.Sequence> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="aaaf9-127">The `RegisterMetadata` method registers the designer metadata of built-in activities including the <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="aaaf9-128">Çünkü `AddDesigner` yöntemi kullanan <xref:System.Activities.Statements.Sequence> etkinliği `RegisterMetadata` metodu önce çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aaaf9-128">Because the `AddDesigner` method uses the <xref:System.Activities.Statements.Sequence> activity, the `RegisterMetadata` method must be called first.</span></span>  
  
9. <span data-ttu-id="aaaf9-129">Derleme ve çözümü çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="aaaf9-129">Press F5 to build and run the solution.</span></span>  
  
10. <span data-ttu-id="aaaf9-130">Bkz: [görev 3: Araç kutusu ve PropertyGrid bölmeleri oluşturma](../../../docs/framework/windows-workflow-foundation/task-3-create-the-toolbox-and-propertygrid-panes.md) ekleme hakkında bilgi edinmek için **araç kutusu** ve **PropertyGrid** , yeniden barındırılan iş akışı Tasarımcısı için destek.</span><span class="sxs-lookup"><span data-stu-id="aaaf9-130">See [Task 3: Create the Toolbox and PropertyGrid Panes](../../../docs/framework/windows-workflow-foundation/task-3-create-the-toolbox-and-propertygrid-panes.md) to learn how to add **Toolbox** and **PropertyGrid** support to your rehosted workflow designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaaf9-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aaaf9-131">See also</span></span>
- [<span data-ttu-id="aaaf9-132">İş Akışı Tasarımcısını Yeniden Barındırma</span><span class="sxs-lookup"><span data-stu-id="aaaf9-132">Rehosting the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)
- [<span data-ttu-id="aaaf9-133">1. Görev: Yeni bir Windows Presentation Foundation uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="aaaf9-133">Task 1: Create a New Windows Presentation Foundation Application</span></span>](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md)
- [<span data-ttu-id="aaaf9-134">3. Görev: Araç kutusu ve PropertyGrid bölmeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="aaaf9-134">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>](../../../docs/framework/windows-workflow-foundation/task-3-create-the-toolbox-and-propertygrid-panes.md)
