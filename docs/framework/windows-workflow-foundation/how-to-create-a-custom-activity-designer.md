---
title: 'Nasıl yapılır: Özel Etkinlik Tasarımcısı oluşturma'
ms.date: 03/30/2017
ms.assetid: 2f3aade6-facc-44ef-9657-a407ef8b9b31
ms.openlocfilehash: e4aab60a598be2d6df5546ab1c98a289b4aef04a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520350"
---
# <a name="how-to-create-a-custom-activity-designer"></a><span data-ttu-id="d35e7-102">Nasıl yapılır: Özel Etkinlik Tasarımcısı oluşturma</span><span class="sxs-lookup"><span data-stu-id="d35e7-102">How to: Create a Custom Activity Designer</span></span>
<span data-ttu-id="d35e7-103">Özel Etkinlik tasarımcıları, bunların ilişkili etkinliklerini onlarla tasarım yüzeyi açın, tasarımcıları bırakılabilir diğer etkinlikleri ile birleştirilebilir; böylece genellikle uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d35e7-103">Custom activity designers are typically implemented so that their associated activities are composable with other activities whose designers can be dropped on to the design surface with them.</span></span> <span data-ttu-id="d35e7-104">Bu işlev bir özel etkinlik Tasarımcısı "isteğe bağlı bir etkinlik nereye yerleştirileceğini bırakma bölgesi" ve ayrıca tasarım yüzeyine öğelerde elde edilen koleksiyonunu yönetmenizi anlamına gelir sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d35e7-104">This functionality requires that a custom activity designer provide a "drop zone" where an arbitrary activity can be placed and also the means to manage the resulting collection of elements on the design surface.</span></span> <span data-ttu-id="d35e7-105">Bu konuda, bu tür bir bırakma bölgesi içeren bir özel etkinlik Tasarımcısı oluşturma ve düzenleme işlevi Tasarımcı öğe koleksiyonunu yönetmek gerekli olduğunu sağlayan bir özel etkinlik Tasarımcısı oluşturma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d35e7-105">This topic describes how to create a custom activity designer that contains such a drop zone and how to create a custom activity designer that provides that editing functionality needed to manage the collection of designer elements.</span></span>  
  
 <span data-ttu-id="d35e7-106">Özel Etkinlik tasarımcıları genellikle devral <xref:System.Activities.Presentation.ActivityDesigner> belirli bir tasarımcı olmadan tüm etkinlikler için varsayılan taban etkinlik Tasarımcısı türü değil.</span><span class="sxs-lookup"><span data-stu-id="d35e7-106">Custom activity designers typically inherit from <xref:System.Activities.Presentation.ActivityDesigner> which is the default base activity designer type for any activities without a specific designer.</span></span> <span data-ttu-id="d35e7-107">Bu tür özellik Kılavuzu ile etkileşim ve renkleri ve simgeleri yönetme gibi temel özelliklerini yapılandırma tasarım zamanı deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d35e7-107">This type provides the design-time experience of interacting with the property grid and configuring basic aspects such as managing colors and icons.</span></span>  
  
 <span data-ttu-id="d35e7-108"><xref:System.Activities.Presentation.ActivityDesigner> iki Yardımcısı denetimleri kullanan <xref:System.Activities.Presentation.WorkflowItemPresenter> ve <xref:System.Activities.Presentation.WorkflowItemsPresenter> özel etkinlik tasarımcıları geliştirmek daha kolay.</span><span class="sxs-lookup"><span data-stu-id="d35e7-108"><xref:System.Activities.Presentation.ActivityDesigner> uses two helper controls, <xref:System.Activities.Presentation.WorkflowItemPresenter> and <xref:System.Activities.Presentation.WorkflowItemsPresenter> to make it easier to develop custom activity designers.</span></span> <span data-ttu-id="d35e7-109">Bunlar, alt öğelerini, silme, seçim ve ayrıca bu alt öğelerini sürükleyip gibi ortak işlevselliği işleyin.</span><span class="sxs-lookup"><span data-stu-id="d35e7-109">They handle common functionality like dragging and dropping of child elements, deletion, selection, and addition of those child elements.</span></span> <span data-ttu-id="d35e7-110"><xref:System.Activities.Presentation.WorkflowItemPresenter> "Açılan bölge", sağlayarak kullanıcı Arabirimi öğesi içinde tek bir alt sağlar, çalışırken <xref:System.Activities.Presentation.WorkflowItemsPresenter> destekleyen birden çok kullanıcı Arabirimi öğeleri, sıralama gibi dahil olmak üzere ek işlevsellik sağlayabilir, taşıma, silme ve alt öğeleri ekleme.</span><span class="sxs-lookup"><span data-stu-id="d35e7-110">The <xref:System.Activities.Presentation.WorkflowItemPresenter> allows a single child UI element inside, providing the "drop zone", it while the <xref:System.Activities.Presentation.WorkflowItemsPresenter> can provide support multiple UI elements, including additional functionality like the ordering, moving, deleting, and adding of child elements.</span></span>  
  
 <span data-ttu-id="d35e7-111">Özel Etkinlik Tasarımcısı uygulamasında vurgulama gereken Öykü diğer anahtar parçası içinde visual düzenlemeleri bağlı kullanarak şekliyle ilgilidir [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] ne biz Tasarımcısı'nda düzenliyorsanız, bellekte örnek veri bağlama.</span><span class="sxs-lookup"><span data-stu-id="d35e7-111">The other key part of the story that needs highlighting in the implementation of a custom activity designer concerns the way in which the visual edits are bound using [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] data binding to the instance stored in memory of what we are editing in the designer.</span></span> <span data-ttu-id="d35e7-112">Bu, ayrıca değişiklik bildirimi ve olayları durumları değişiklikleri gibi izlenmesini etkinleştirmek için sorumlu olan Model öğesi ağacı tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d35e7-112">This is accomplished by the Model Item tree, which is also responsible for enabling change notification and the tracking of events like changes in states.</span></span>  
  
 <span data-ttu-id="d35e7-113">Bu konuda iki yordamları özetlemektedir.</span><span class="sxs-lookup"><span data-stu-id="d35e7-113">This topic outlines two procedures.</span></span>  
  
1.  <span data-ttu-id="d35e7-114">İlk yordamı bir özel etkinlik Tasarımcısı ile oluşturmayı açıklar bir <xref:System.Activities.Presentation.WorkflowItemPresenter> diğer etkinlikler alır bırakma bölgesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d35e7-114">The first procedure describes how to create a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter> that provides the drop zone that receives other activities.</span></span> <span data-ttu-id="d35e7-115">Bu yordamı dayanır [özel bileşik tasarımcıları - iş akışı öğesi sunum](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-designers-workflow-item-presenter.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="d35e7-115">This procedure is based on the [Custom Composite Designers - Workflow Item Presenter](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-designers-workflow-item-presenter.md) sample.</span></span>  
  
2.  <span data-ttu-id="d35e7-116">İkinci yordamı bir özel etkinlik Tasarımcısı ile oluşturmayı açıklar bir <xref:System.Activities.Presentation.WorkflowItemsPresenter> içerilen öğelerin koleksiyonunu düzenlenmesi için gerekli işlevselliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="d35e7-116">The second procedure describes how to create a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter> that provides the functionality needed to edit of a collection of contained elements.</span></span> <span data-ttu-id="d35e7-117">Bu yordamı dayanır [özel bileşik tasarımcıları - iş akışı öğeleri sunum](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-designers-workflow-items-presenter.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="d35e7-117">This procedure is based on the [Custom Composite Designers - Workflow Items Presenter](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-designers-workflow-items-presenter.md) sample.</span></span>  
  
### <a name="to-create-a-custom-activity-designer-with-a-drop-zone-using-workflowitempresenter"></a><span data-ttu-id="d35e7-118">Özel Etkinlik Tasarımcısı WorkflowItemPresenter kullanarak bir açılan bölgeyle oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d35e7-118">To create a custom activity designer with a drop zone using WorkflowItemPresenter</span></span>  
  
1.  <span data-ttu-id="d35e7-119">Başlat [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d35e7-119">Start [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="d35e7-120">Üzerinde **dosya** menüsündeki **yeni**ve ardından **proje...** .</span><span class="sxs-lookup"><span data-stu-id="d35e7-120">On the **File** menu, point to **New**, and then select **Project…**.</span></span>  
  
     <span data-ttu-id="d35e7-121">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="d35e7-121">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="d35e7-122">İçinde **yüklü şablonlar** bölmesinde, **Windows** , tercih edilen dili kategorisinden.</span><span class="sxs-lookup"><span data-stu-id="d35e7-122">In the **Installed Templates** pane, select **Windows** from your preferred language category.</span></span>  
  
4.  <span data-ttu-id="d35e7-123">İçinde **şablonları** bölmesinde, **WPF uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="d35e7-123">In the **Templates** pane, select **WPF Application**.</span></span>  
  
5.  <span data-ttu-id="d35e7-124">İçinde **adı** kutusuna `UsingWorkflowItemPresenter`.</span><span class="sxs-lookup"><span data-stu-id="d35e7-124">In the **Name** box, enter `UsingWorkflowItemPresenter`.</span></span>  
  
6.  <span data-ttu-id="d35e7-125">İçinde **konumu** kutusunda, istediğiniz tıklayın veya projenizi kaydetmek istediğiniz dizini girin **Gözat** gitmek için.</span><span class="sxs-lookup"><span data-stu-id="d35e7-125">In the **Location** box, enter the directory in which you want to save your project, or click **Browse** to navigate to it.</span></span>  
  
7.  <span data-ttu-id="d35e7-126">İçinde **çözüm** kutusunda, varsayılan değeri kabul edin.</span><span class="sxs-lookup"><span data-stu-id="d35e7-126">In the **Solution** box, accept the default value.</span></span>  
  
8.  <span data-ttu-id="d35e7-127">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="d35e7-127">Click **OK**.</span></span>  
  
9. <span data-ttu-id="d35e7-128">MainWindows.xaml dosyasında sağ **Çözüm Gezgini**seçin **silmek** ve onaylayın **Tamam** içinde **Microsoft Visual Studio**iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="d35e7-128">Right-click the MainWindows.xaml file in the **Solution Explorer**, select **Delete** and confirm **OK** in the **Microsoft Visual Studio** dialogue box.</span></span>  
  
10. <span data-ttu-id="d35e7-129">' Nde UsingWorkflowItemPresenter projeye sağ **Çözüm Gezgini**seçin **Ekle**, ardından **yeni öğe...**</span><span class="sxs-lookup"><span data-stu-id="d35e7-129">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="d35e7-130">ortaya çıkarmak için **Yeni Öğe Ekle** iletişim kutusunda ve seçin **WPF** kategoriden **yüklü şablonlar** sol bölümü.</span><span class="sxs-lookup"><span data-stu-id="d35e7-130">to bring up the **Add New Item** dialogue and select the **WPF** category from the **Installed Templates** section on the left.</span></span>  
  
11. <span data-ttu-id="d35e7-131">Seçin **penceresi (WPF)** şablon adlandırın `RehostingWFDesigner`, tıklatıp **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="d35e7-131">Select the  **Window (WPF)** template, name it `RehostingWFDesigner`, and click **Add**.</span></span>  
  
12. <span data-ttu-id="d35e7-132">RehostingWFDesigner.xaml dosyasını açın ve bu uygulama için kullanıcı Arabirimi tanımlamak için aşağıdaki kodu yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="d35e7-132">Open the RehostingWFDesigner.xaml file and paste the following code into it to define the UI for the application.</span></span>  
  
    ```xml  
    <Window x:Class=" UsingWorkflowItemPresenter.RehostingWFDesigner"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            xmlns:sapt="clr-namespace:System.Activities.Presentation.Toolbox;assembly=System.Activities.Presentation"  
            xmlns:sys="clr-namespace:System;assembly=mscorlib"  
            Title="Window1" Height="600" Width="900">  
        <Window.Resources>  
            <sys:String x:Key="AssemblyName">System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35</sys:String>  
        </Window.Resources>  
        <Grid>  
            <Grid.ColumnDefinitions>  
                <ColumnDefinition Width="2*"/>  
                <ColumnDefinition Width="7*"/>  
                <ColumnDefinition Width="3*"/>  
            </Grid.ColumnDefinitions>  
            <Border Grid.Column="0">  
                <sapt:ToolboxControl Name="Toolbox">  
                    <sapt:ToolboxCategory CategoryName="Basic">  
                        <sapt:ToolboxItemWrapper AssemblyName="{StaticResource AssemblyName}" >  
                            <sapt:ToolboxItemWrapper.ToolName>  
                                System.Activities.Statements.Sequence  
                            </sapt:ToolboxItemWrapper.ToolName>  
                           </sapt:ToolboxItemWrapper>  
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                            <sapt:ToolboxItemWrapper.ToolName>  
                                System.Activities.Statements.WriteLine  
                            </sapt:ToolboxItemWrapper.ToolName>  
  
                        </sapt:ToolboxItemWrapper>  
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                            <sapt:ToolboxItemWrapper.ToolName>  
                                System.Activities.Statements.If  
                            </sapt:ToolboxItemWrapper.ToolName>  
  
                        </sapt:ToolboxItemWrapper>  
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                            <sapt:ToolboxItemWrapper.ToolName>  
                                System.Activities.Statements.While  
                            </sapt:ToolboxItemWrapper.ToolName>  
  
                        </sapt:ToolboxItemWrapper>  
                    </sapt:ToolboxCategory>  
                </sapt:ToolboxControl>  
            </Border>  
            <Border Grid.Column="1" Name="DesignerBorder"/>  
            <Border Grid.Column="2" Name="PropertyBorder"/>  
        </Grid>  
    </Window>  
    ```  
  
13. <span data-ttu-id="d35e7-133">Bir etkinlik Tasarımcısı bir etkinlik türü ile ilişkilendirmek için bu etkinlik Tasarımcısı ile meta veri deposu kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d35e7-133">To associate an activity designer with an activity type, you must register that activity designer with the metadata store.</span></span> <span data-ttu-id="d35e7-134">Bunu yapmak için ekleyin `RegisterMetadata` yönteme `RehostingWFDesigner` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d35e7-134">To do this, add the `RegisterMetadata` method to the `RehostingWFDesigner` class.</span></span> <span data-ttu-id="d35e7-135">Kapsamında `RegisterMetadata` yöntemi oluşturma bir <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> nesne ve çağrı <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> öznitelikleri ekleme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d35e7-135">Within the scope of the  `RegisterMetadata` method, create an <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> object and call the <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> method to add the attributes to it.</span></span> <span data-ttu-id="d35e7-136">Çağrı <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> ekleme yöntemi <xref:System.Activities.Presentation.Metadata.AttributeTable> meta veri deposuna.</span><span class="sxs-lookup"><span data-stu-id="d35e7-136">Call the <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> method to add the <xref:System.Activities.Presentation.Metadata.AttributeTable> to the metadata store.</span></span> <span data-ttu-id="d35e7-137">Aşağıdaki kod Tasarımcı rehosting mantığını içerir.</span><span class="sxs-lookup"><span data-stu-id="d35e7-137">The following code contains the rehosting logic for the designer.</span></span> <span data-ttu-id="d35e7-138">Meta veriler kaydeder, koyar `SimpleNativeActivity` araç içine ve iş akışını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d35e7-138">It registers the metadata, puts the `SimpleNativeActivity` into the toolbox, and creates the workflow.</span></span> <span data-ttu-id="d35e7-139">Bu kod RehostingWFDesigner.xaml.cs dosyasına yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="d35e7-139">Put this code into the RehostingWFDesigner.xaml.cs file.</span></span>  
  
    ```  
    using System;  
    using System.Activities.Core.Presentation;  
    using System.Activities.Presentation;  
    using System.Activities.Presentation.Metadata;  
    using System.Activities.Presentation.Toolbox;  
    using System.Activities.Statements;  
    using System.ComponentModel;  
    using System.Windows;  
  
    namespace UsingWorkflowItemPresenter  
    {  
        // Interaction logic for RehostingWFDesigner.xaml  
        public partial class RehostingWFDesigner  
        {  
            public RehostingWFDesigner()  
            {  
                InitializeComponent();  
            }  
  
            protected override void OnInitialized(EventArgs e)  
            {  
                base.OnInitialized(e);  
                // register metadata  
                (new DesignerMetadata()).Register();  
                RegisterCustomMetadata();  
                // add custom activity to toolbox  
                Toolbox.Categories.Add(new ToolboxCategory("Custom activities"));  
                Toolbox.Categories[1].Add(new ToolboxItemWrapper(typeof(SimpleNativeActivity)));  
  
                // create the workflow designer  
                WorkflowDesigner wd = new WorkflowDesigner();  
                wd.Load(new Sequence());  
                DesignerBorder.Child = wd.View;  
                PropertyBorder.Child = wd.PropertyInspectorView;  
  
            }  
  
            void RegisterCustomMetadata()  
            {  
                AttributeTableBuilder builder = new AttributeTableBuilder();  
                builder.AddCustomAttributes(typeof(SimpleNativeActivity), new DesignerAttribute(typeof(SimpleNativeDesigner)));  
                MetadataStore.AddAttributeTable(builder.CreateTable());  
            }  
        }  
    }  
    ```  
  
14. <span data-ttu-id="d35e7-140">Çözüm Gezgini'nde başvuruları dizini sağ tıklatın ve seçin **Başvuru Ekle...**</span><span class="sxs-lookup"><span data-stu-id="d35e7-140">Right-click the References directory in Solution Explorer and select **Add Reference …**</span></span> <span data-ttu-id="d35e7-141">ortaya çıkarmak için **Başvuru Ekle** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="d35e7-141">to bring up the **Add Reference** dialogue.</span></span>  
  
15. <span data-ttu-id="d35e7-142">Tıklatın **.NET** sekmesinde, adlı derleme bulun **System.Activities.Core.Presentation**, seçin ve **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="d35e7-142">Click the **.NET** tab, locate the assembly named **System.Activities.Core.Presentation**, select it and click **OK**.</span></span>  
  
16. <span data-ttu-id="d35e7-143">Yordamın aynısını kullanarak, aşağıdaki derlemelerine başvurular ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d35e7-143">Using the same procedure, add references to the following assemblies:</span></span>  
  
    1.  <span data-ttu-id="d35e7-144">System.Data.DataSetExtensions.dll</span><span class="sxs-lookup"><span data-stu-id="d35e7-144">System.Data.DataSetExtensions.dll</span></span>  
  
    2.  <span data-ttu-id="d35e7-145">System.Activities.Presentation.dll</span><span class="sxs-lookup"><span data-stu-id="d35e7-145">System.Activities.Presentation.dll</span></span>  
  
    3.  <span data-ttu-id="d35e7-146">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="d35e7-146">System.ServiceModel.Activities.dll</span></span>  
  
17. <span data-ttu-id="d35e7-147">App.xaml dosyasını açın ve "RehostingWFDesigner.xaml" StartUpUri değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d35e7-147">Open the App.xaml file and change the value of the StartUpUri to "RehostingWFDesigner.xaml".</span></span>  
  
18. <span data-ttu-id="d35e7-148">' Nde UsingWorkflowItemPresenter projeye sağ **Çözüm Gezgini**seçin **Ekle**, ardından **yeni öğe...**</span><span class="sxs-lookup"><span data-stu-id="d35e7-148">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="d35e7-149">ortaya çıkarmak için **Yeni Öğe Ekle** iletişim kutusunda ve seçin **iş akışı** kategori form **yüklü şablonlar** sol bölümü.</span><span class="sxs-lookup"><span data-stu-id="d35e7-149">to bring up the **Add New Item** dialogue and select the **Workflow** category form the **Installed Templates** section on the left.</span></span>  
  
19. <span data-ttu-id="d35e7-150">Seçin **etkinlik Tasarımcısı** şablon adlandırın `SimpleNativeDesigner`, tıklatıp **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="d35e7-150">Select the **Activity Designer** template, name it `SimpleNativeDesigner`, and click **Add**.</span></span>  
  
20. <span data-ttu-id="d35e7-151">SimpleNativeDesigner.xaml dosyasını açın ve aşağıdaki kodu yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="d35e7-151">Open the SimpleNativeDesigner.xaml file and paste the following code into it.</span></span> <span data-ttu-id="d35e7-152">Bu kod kullandığına dikkat edin <xref:System.Activities.Presentation.ActivityDesigner> nasıl bağlama tümleştirmek için kullanılan gösterir ve kök öğesi olarak <xref:System.Activities.Presentation.WorkflowItemPresenter> alt türe bileşik etkinlik Tasarımcısı'nda görüntülenebilir böylece, tasarımcısı içine.</span><span class="sxs-lookup"><span data-stu-id="d35e7-152">Note this code uses <xref:System.Activities.Presentation.ActivityDesigner> as your root element and shows how binding is used to integrate <xref:System.Activities.Presentation.WorkflowItemPresenter> into your designer so a child type can be displayed in your composite activity designer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d35e7-153">İçin şemayı <xref:System.Activities.Presentation.ActivityDesigner> özel etkinlik Tasarımcısı tanımınızı; yalnızca bir alt öğeye eklenmesini sağlar ancak, bu öğenin olabilir bir `StackPanel`, `Grid`, ya da diğer bazı bir bileşik UI öğesi.</span><span class="sxs-lookup"><span data-stu-id="d35e7-153">The schema for <xref:System.Activities.Presentation.ActivityDesigner> allows the addition of only one child element to your custom activity designer definition; however, this element could be a `StackPanel`, `Grid`, or some other composite UI element.</span></span>  
  
    ```xml  
    <sap:ActivityDesigner x:Class=" UsingWorkflowItemPresenter.SimpleNativeDesigner"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"  
        xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">  
        <sap:ActivityDesigner.Resources>  
            <DataTemplate x:Key="Collapsed">  
                <StackPanel>  
                    <TextBlock>This is the collapsed view</TextBlock>  
                </StackPanel>  
            </DataTemplate>  
            <DataTemplate x:Key="Expanded">  
                <StackPanel>  
                    <TextBlock>Custom Text</TextBlock>  
                    <sap:WorkflowItemPresenter Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"  
                                            HintText="Please drop an activity here" />  
                </StackPanel>  
            </DataTemplate>  
            <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">  
                <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>  
                <Style.Triggers>  
                    <DataTrigger Binding="{Binding Path=ShowExpanded}" Value="true">  
                        <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>  
                    </DataTrigger>  
                </Style.Triggers>  
            </Style>  
        </sap:ActivityDesigner.Resources>  
        <Grid>  
            <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}" />  
        </Grid>  
    </sap:ActivityDesigner>  
    ```  
  
21. <span data-ttu-id="d35e7-154">' Nde UsingWorkflowItemPresenter projeye sağ **Çözüm Gezgini**seçin **Ekle**, ardından **yeni öğe...**</span><span class="sxs-lookup"><span data-stu-id="d35e7-154">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="d35e7-155">ortaya çıkarmak için **Yeni Öğe Ekle** iletişim kutusunda ve seçin **iş akışı** kategori form **yüklü şablonlar** sol bölümü.</span><span class="sxs-lookup"><span data-stu-id="d35e7-155">to bring up the **Add New Item** dialogue and select the **Workflow** category form the **Installed Templates** section on the left.</span></span>  
  
22. <span data-ttu-id="d35e7-156">Seçin **kodunu aktivite** şablon adlandırın `SimpleNativeActivity`, tıklatıp **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="d35e7-156">Select the  **Code Activity** template, name it `SimpleNativeActivity`, and click **Add**.</span></span>  
  
23. <span data-ttu-id="d35e7-157">Uygulama `SimpleNativeActivity` SimpleNativeActivity.cs dosyasına aşağıdaki kodu girerek sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d35e7-157">Implement the `SimpleNativeActivity` class by entering the following code into the SimpleNativeActivity.cs file.</span></span>  
  
    ```  
    using System.Activities;  
  
    namespace UsingWorkflowItemPresenter  
    {  
        public sealed class SimpleNativeActivity : NativeActivity  
        {  
            // this property contains an activity that will be scheduled in the execute method  
    // the WorkflowItemPresenter in the designer is bound to this to enable editing  
    // of the value  
            public Activity Body { get; set; }  
  
            protected override void CacheMetadata(NativeActivityMetadata metadata)  
            {  
               metadata.AddChild(Body);  
               base.CacheMetadata(metadata);  
  
            }  
  
            protected override void Execute(NativeActivityContext context)  
            {  
                context.ScheduleActivity(Body);  
            }  
        }  
    }  
    ```  
  
24. <span data-ttu-id="d35e7-158">Seçin **yapı çözümü** gelen **yapı** menüsü.</span><span class="sxs-lookup"><span data-stu-id="d35e7-158">Select **Build Solution** from the **Build** menu.</span></span>  
  
25. <span data-ttu-id="d35e7-159">Seçin **hata ayıklama olmadan Başlat** gelen **hata ayıklama** menü rehosted özel tasarım penceresini açın.</span><span class="sxs-lookup"><span data-stu-id="d35e7-159">Select **Start Without Debugging** from the **Debug** menu to open the rehosted custom design window.</span></span>  
  
### <a name="to-create-a-custom-activity-designer-using-workflowitemspresenter"></a><span data-ttu-id="d35e7-160">Özel Etkinlik Tasarımcısı WorkflowItemsPresenter kullanarak oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d35e7-160">To create a custom activity designer using WorkflowItemsPresenter</span></span>  
  
1.  <span data-ttu-id="d35e7-161">Bazı değişiklikler, ilk başta olan ikinci uygulama adı için parallels yordamdır ikinci özel etkinlik Tasarımcısı için `UsingWorkflowItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="d35e7-161">The procedure for the second custom activity designer is the parallels the first with a few modifications, the first of which is to name the second application `UsingWorkflowItemsPresenter`.</span></span> <span data-ttu-id="d35e7-162">Ayrıca bu uygulamayı yeni bir özel etkinlik tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="d35e7-162">Also this application does not define a new custom activity.</span></span>  
  
2.  <span data-ttu-id="d35e7-163">Temel farklılıklar CustomParallelDesigner.xaml ve RehostingWFDesigner.xaml.cs dosyalarında yer alır.</span><span class="sxs-lookup"><span data-stu-id="d35e7-163">Key differences are contained in the CustomParallelDesigner.xaml and RehostingWFDesigner.xaml.cs files.</span></span> <span data-ttu-id="d35e7-164">Kullanıcı arabirimini tanımlar CustomParallelDesigne.xaml dosyasından kod aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="d35e7-164">Here is the code from the CustomParallelDesigne.xaml file that defines the UI.</span></span>  
  
    ```xml  
    <sap:ActivityDesigner x:Class=" UsingWorkflowItemsPresenter.CustomParallelDesigner"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"  
        xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">  
        <sap:ActivityDesigner.Resources>  
            <DataTemplate x:Key="Collapsed">  
                <TextBlock>This is the Collapsed View</TextBlock>  
            </DataTemplate>  
            <DataTemplate x:Key="Expanded">  
                <StackPanel>  
                    <TextBlock HorizontalAlignment="Center">This is the</TextBlock>  
                    <TextBlock HorizontalAlignment="Center">extended view</TextBlock>  
                    <sap:WorkflowItemsPresenter HintText="Drop Activities Here"  
                                        Items="{Binding Path=ModelItem.Branches}">  
                        <sap:WorkflowItemsPresenter.SpacerTemplate>  
                            <DataTemplate>  
                                <Ellipse Width="10" Height="10" Fill="Black"/>  
                            </DataTemplate>  
                        </sap:WorkflowItemsPresenter.SpacerTemplate>  
                        <sap:WorkflowItemsPresenter.ItemsPanel>  
                            <ItemsPanelTemplate>  
                                <StackPanel Orientation="Horizontal"/>  
                            </ItemsPanelTemplate>  
                        </sap:WorkflowItemsPresenter.ItemsPanel>  
                    </sap:WorkflowItemsPresenter>  
                </StackPanel>  
            </DataTemplate>  
            <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">  
                <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>  
                <Style.Triggers>  
                    <DataTrigger Binding="{Binding Path=ShowExpanded}" Value="true">  
                        <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>  
                    </DataTrigger>  
                </Style.Triggers>  
            </Style>  
        </sap:ActivityDesigner.Resources>  
        <Grid>  
            <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}"/>  
        </Grid>  
    </sap:ActivityDesigner>  
    ```  
  
3.  <span data-ttu-id="d35e7-165">Kod rehosting mantığı sağlayan RehostingWFDesigner.xaml.cs dosyasından aşağıdadır.</span><span class="sxs-lookup"><span data-stu-id="d35e7-165">Here is the code from the RehostingWFDesigner.xaml.cs file that provides the rehosting logic.</span></span>  
  
    ```  
    using System;  
    using System.Activities.Core.Presentation;  
    using System.Activities.Presentation;  
    using System.Activities.Presentation.Metadata;  
    using System.Activities.Statements;  
    using System.ComponentModel;  
    using System.Windows;  
  
    namespaceUsingWorkflowItemsPresenter  
    {  
        public partial class RehostingWfDesigner : Window  
        {  
            public RehostingWfDesigner()  
            {  
                InitializeComponent();  
            }  
  
            protected override void OnInitialized(EventArgs e)  
            {  
                base.OnInitialized(e);  
                // register metadata  
                (new DesignerMetadata()).Register();  
                RegisterCustomMetadata();  
  
                // create the workflow designer  
                WorkflowDesigner wd = new WorkflowDesigner();  
                wd.Load(new Sequence());  
                DesignerBorder.Child = wd.View;  
                PropertyBorder.Child = wd.PropertyInspectorView;  
  
            }  
  
            void RegisterCustomMetadata()  
            {  
                AttributeTableBuilder builder = new AttributeTableBuilder();  
                builder.AddCustomAttributes(typeof(Parallel), new DesignerAttribute(typeof(CustomParallelDesigner)));  
                MetadataStore.AddAttributeTable(builder.CreateTable());  
            }  
        }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d35e7-166">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d35e7-166">See Also</span></span>  
 <xref:System.Activities.Presentation.ActivityDesigner>  
 <xref:System.Activities.Presentation.WorkflowItemPresenter>  
 <xref:System.Activities.Presentation.WorkflowItemsPresenter>  
 <xref:System.Activities.Presentation.WorkflowViewElement>  
 <xref:System.Activities.Presentation.Model.ModelItem>  
 [<span data-ttu-id="d35e7-167">İş Akışı Tasarım Deneyimini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="d35e7-167">Customizing the Workflow Design Experience</span></span>](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md)
