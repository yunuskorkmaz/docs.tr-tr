---
title: 'Nasıl yapılır: Özel Etkinlik Tasarımcısı oluşturma'
ms.date: 03/30/2017
ms.assetid: 2f3aade6-facc-44ef-9657-a407ef8b9b31
ms.openlocfilehash: 86cd3544e9117cca273b6c8dde8454672f14a36a
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48777688"
---
# <a name="how-to-create-a-custom-activity-designer"></a><span data-ttu-id="c37ac-102">Nasıl yapılır: Özel Etkinlik Tasarımcısı oluşturma</span><span class="sxs-lookup"><span data-stu-id="c37ac-102">How to: Create a Custom Activity Designer</span></span>

<span data-ttu-id="c37ac-103">Özel Etkinlik tasarımcıları, genellikle kendi ilişkili etkinlikleri, tasarımcılar, bunları tasarım yüzeyi açın bırakılabilir diğer etkinlikler ile birleştirilebilir, böylece uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c37ac-103">Custom activity designers are typically implemented so that their associated activities are composable with other activities whose designers can be dropped on to the design surface with them.</span></span> <span data-ttu-id="c37ac-104">Bu işlev bir özel etkinlik Tasarımcısı "bir bırakma bölge rastgele bir etkinlik nereye yerleştirilmesi" ve ayrıca anlamına gelir elde edilen tasarım yüzeyinde öğelerinin koleksiyonunu yönetmenizi sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c37ac-104">This functionality requires that a custom activity designer provide a "drop zone" where an arbitrary activity can be placed and also the means to manage the resulting collection of elements on the design surface.</span></span> <span data-ttu-id="c37ac-105">Bu konu, bu tür bir bırakma bölge içeren bir özel etkinlik Tasarımcısı oluşturma ve düzenleme işlevi Tasarımcı öğelerinin koleksiyonunu yönetmek gerekli olduğunu sağlayan bir özel etkinlik Tasarımcısı oluşturma işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c37ac-105">This topic describes how to create a custom activity designer that contains such a drop zone and how to create a custom activity designer that provides that editing functionality needed to manage the collection of designer elements.</span></span>

 <span data-ttu-id="c37ac-106">Özel Etkinlik tasarımcıları genellikle devralınan <xref:System.Activities.Presentation.ActivityDesigner> belirli bir tasarımcı olmadan herhangi bir etkinlik için varsayılan taban etkinlik Tasarımcısı türü.</span><span class="sxs-lookup"><span data-stu-id="c37ac-106">Custom activity designers typically inherit from <xref:System.Activities.Presentation.ActivityDesigner> which is the default base activity designer type for any activities without a specific designer.</span></span> <span data-ttu-id="c37ac-107">Bu özellik kılavuzunda ile etkileşim kurma ve renkleri ve simgeleri yönetme gibi temel özellikleri yapılandırma tasarım zamanı deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c37ac-107">This type provides the design-time experience of interacting with the property grid and configuring basic aspects such as managing colors and icons.</span></span>

 <span data-ttu-id="c37ac-108"><xref:System.Activities.Presentation.ActivityDesigner> iki Yardımcısı denetimlerini kullanır <xref:System.Activities.Presentation.WorkflowItemPresenter> ve <xref:System.Activities.Presentation.WorkflowItemsPresenter> özel etkinlik tasarımcıları geliştirmeyi daha kolay hale getirmek için.</span><span class="sxs-lookup"><span data-stu-id="c37ac-108"><xref:System.Activities.Presentation.ActivityDesigner> uses two helper controls, <xref:System.Activities.Presentation.WorkflowItemPresenter> and <xref:System.Activities.Presentation.WorkflowItemsPresenter> to make it easier to develop custom activity designers.</span></span> <span data-ttu-id="c37ac-109">Bunlar alt öğeleri, silme, seçimi ve söz konusu alt öğelerin eklenmesi sürükleyip gibi ortak işlevselliği işleyin.</span><span class="sxs-lookup"><span data-stu-id="c37ac-109">They handle common functionality like dragging and dropping of child elements, deletion, selection, and addition of those child elements.</span></span> <span data-ttu-id="c37ac-110"><xref:System.Activities.Presentation.WorkflowItemPresenter> "Bırakma bölge", sağlayarak kullanıcı Arabirimi öğesi içinde tek bir alt sağlar, çalışırken <xref:System.Activities.Presentation.WorkflowItemsPresenter> destekleyen birden çok kullanıcı Arabirimi öğeleri, sıralama gibi dahil olmak üzere ek işlevler sağlayabilir, taşıma, silme ve alt öğeleri ekleme.</span><span class="sxs-lookup"><span data-stu-id="c37ac-110">The <xref:System.Activities.Presentation.WorkflowItemPresenter> allows a single child UI element inside, providing the "drop zone", it while the <xref:System.Activities.Presentation.WorkflowItemsPresenter> can provide support multiple UI elements, including additional functionality like the ordering, moving, deleting, and adding of child elements.</span></span>

 <span data-ttu-id="c37ac-111">Özel Etkinlik Tasarımcısı uygulamasında vurgulama gereken yazının diğer önemli parçası visual düzenlemeler, bağlı kullanarak şekliyle ilgilidir [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] ne biz tasarımcıda düzenleme bellek depolanan örnek veri bağlama.</span><span class="sxs-lookup"><span data-stu-id="c37ac-111">The other key part of the story that needs highlighting in the implementation of a custom activity designer concerns the way in which the visual edits are bound using [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] data binding to the instance stored in memory of what we are editing in the designer.</span></span> <span data-ttu-id="c37ac-112">Bu, aynı zamanda değişiklik bildirimi ve durum değişiklikleri gibi olaylar izlenmesini etkinleştirmek için sorumlu olan Model öğesi ağacı tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c37ac-112">This is accomplished by the Model Item tree, which is also responsible for enabling change notification and the tracking of events like changes in states.</span></span>

 <span data-ttu-id="c37ac-113">Bu konu iki yordam açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c37ac-113">This topic outlines two procedures.</span></span>

1.  <span data-ttu-id="c37ac-114">Birinci yordamda açıklanan özel etkinlik Tasarımcısı ile oluşturmak nasıl bir <xref:System.Activities.Presentation.WorkflowItemPresenter> diğer etkinlikleri alan açılan bölge sağlar.</span><span class="sxs-lookup"><span data-stu-id="c37ac-114">The first procedure describes how to create a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter> that provides the drop zone that receives other activities.</span></span> <span data-ttu-id="c37ac-115">Bu yordamı dayanır [özel bileşik tasarımcılar - iş akışı öğesi sunucu](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-designers-workflow-item-presenter.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="c37ac-115">This procedure is based on the [Custom Composite Designers - Workflow Item Presenter](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-designers-workflow-item-presenter.md) sample.</span></span>

2.  <span data-ttu-id="c37ac-116">İkinci yordam özel etkinlik Tasarımcısı ile oluşturma işlemini açıklamaktadır bir <xref:System.Activities.Presentation.WorkflowItemsPresenter> düzenlemek kapsanan öğelerin koleksiyonunu için gereken işlevselliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="c37ac-116">The second procedure describes how to create a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter> that provides the functionality needed to edit of a collection of contained elements.</span></span> <span data-ttu-id="c37ac-117">Bu yordamı dayanır [özel bileşik tasarımcılar - iş akışı öğeleri sunucu](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-designers-workflow-items-presenter.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="c37ac-117">This procedure is based on the [Custom Composite Designers - Workflow Items Presenter](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-designers-workflow-items-presenter.md) sample.</span></span>

## <a name="to-create-a-custom-activity-designer-with-a-drop-zone-using-workflowitempresenter"></a><span data-ttu-id="c37ac-118">Bir alt bölge WorkflowItemPresenter kullanarak özel bir etkinlik Tasarımcısı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c37ac-118">To create a custom activity designer with a drop zone using WorkflowItemPresenter</span></span>

1.  <span data-ttu-id="c37ac-119">Visual Studio 2010'u başlatın.</span><span class="sxs-lookup"><span data-stu-id="c37ac-119">Start Visual Studio 2010.</span></span>

2.  <span data-ttu-id="c37ac-120">Üzerinde **dosya** menüsünde **yeni**ve ardından **proje...** .</span><span class="sxs-lookup"><span data-stu-id="c37ac-120">On the **File** menu, point to **New**, and then select **Project…**.</span></span>

     <span data-ttu-id="c37ac-121">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="c37ac-121">The **New Project** dialog box opens.</span></span>

3.  <span data-ttu-id="c37ac-122">İçinde **yüklü şablonlar** bölmesinde **Windows** , tercih edilen dil kategorisinden.</span><span class="sxs-lookup"><span data-stu-id="c37ac-122">In the **Installed Templates** pane, select **Windows** from your preferred language category.</span></span>

4.  <span data-ttu-id="c37ac-123">İçinde **şablonları** bölmesinde **WPF uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="c37ac-123">In the **Templates** pane, select **WPF Application**.</span></span>

5.  <span data-ttu-id="c37ac-124">İçinde **adı** kutusuna `UsingWorkflowItemPresenter`.</span><span class="sxs-lookup"><span data-stu-id="c37ac-124">In the **Name** box, enter `UsingWorkflowItemPresenter`.</span></span>

6.  <span data-ttu-id="c37ac-125">İçinde **konumu** kutusunda, projeyi kaydedin veya istediğiniz dizin girin **Gözat** gitmek için.</span><span class="sxs-lookup"><span data-stu-id="c37ac-125">In the **Location** box, enter the directory in which you want to save your project, or click **Browse** to navigate to it.</span></span>

7.  <span data-ttu-id="c37ac-126">İçinde **çözüm** kutusunda, varsayılan değeri kabul edin.</span><span class="sxs-lookup"><span data-stu-id="c37ac-126">In the **Solution** box, accept the default value.</span></span>

8.  <span data-ttu-id="c37ac-127">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="c37ac-127">Click **OK**.</span></span>

9. <span data-ttu-id="c37ac-128">MainWindows.xaml dosyaya sağ **Çözüm Gezgini**seçin **Sil** ve onaylayın **Tamam** içinde **Microsoft Visual Studio**iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="c37ac-128">Right-click the MainWindows.xaml file in the **Solution Explorer**, select **Delete** and confirm **OK** in the **Microsoft Visual Studio** dialogue box.</span></span>

10. <span data-ttu-id="c37ac-129">UsingWorkflowItemPresenter projeye sağ **Çözüm Gezgini**seçin **Ekle**, ardından **yeni öğe...**</span><span class="sxs-lookup"><span data-stu-id="c37ac-129">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="c37ac-130">ortaya çıkarmak için **Yeni Öğe Ekle** seçin ve iletişim kutusunda **WPF** kategoriden **yüklü şablonlar** soldaki bölümü.</span><span class="sxs-lookup"><span data-stu-id="c37ac-130">to bring up the **Add New Item** dialogue and select the **WPF** category from the **Installed Templates** section on the left.</span></span>

11. <span data-ttu-id="c37ac-131">Seçin **pencere (WPF)** şablon adlandırın `RehostingWFDesigner`, tıklatıp **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="c37ac-131">Select the  **Window (WPF)** template, name it `RehostingWFDesigner`, and click **Add**.</span></span>

12. <span data-ttu-id="c37ac-132">RehostingWFDesigner.xaml dosyasını açın ve bu uygulama için kullanıcı arabirimini tanımlamak için aşağıdaki kodu yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="c37ac-132">Open the RehostingWFDesigner.xaml file and paste the following code into it to define the UI for the application.</span></span>

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

13. <span data-ttu-id="c37ac-133">Bir etkinlik Tasarımcısı bir etkinlik türü ile ilişkilendirmek için bu etkinlik Tasarımcısı ile meta veri deposuna kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c37ac-133">To associate an activity designer with an activity type, you must register that activity designer with the metadata store.</span></span> <span data-ttu-id="c37ac-134">Bunu yapmak için ekleme `RegisterMetadata` yönteme `RehostingWFDesigner` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c37ac-134">To do this, add the `RegisterMetadata` method to the `RehostingWFDesigner` class.</span></span> <span data-ttu-id="c37ac-135">Kapsamında `RegisterMetadata` yöntemi oluşturma bir <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> nesne ve çağrı <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> öznitelikleri eklemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c37ac-135">Within the scope of the  `RegisterMetadata` method, create an <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> object and call the <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> method to add the attributes to it.</span></span> <span data-ttu-id="c37ac-136">Çağrı <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> ekleme yöntemi <xref:System.Activities.Presentation.Metadata.AttributeTable> meta veri deposuna.</span><span class="sxs-lookup"><span data-stu-id="c37ac-136">Call the <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> method to add the <xref:System.Activities.Presentation.Metadata.AttributeTable> to the metadata store.</span></span> <span data-ttu-id="c37ac-137">Aşağıdaki kod, Tasarımcı için rehosting mantığı içerir.</span><span class="sxs-lookup"><span data-stu-id="c37ac-137">The following code contains the rehosting logic for the designer.</span></span> <span data-ttu-id="c37ac-138">Meta veri kaydeder, koyar `SimpleNativeActivity` araç kutusu içine ve iş akışı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c37ac-138">It registers the metadata, puts the `SimpleNativeActivity` into the toolbox, and creates the workflow.</span></span> <span data-ttu-id="c37ac-139">Bu kodu RehostingWFDesigner.xaml.cs dosyanın koyun.</span><span class="sxs-lookup"><span data-stu-id="c37ac-139">Put this code into the RehostingWFDesigner.xaml.cs file.</span></span>

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

14. <span data-ttu-id="c37ac-140">Çözüm Gezgini'ndeki başvurular directory sağ tıklayıp **Başvuru Ekle...**</span><span class="sxs-lookup"><span data-stu-id="c37ac-140">Right-click the References directory in Solution Explorer and select **Add Reference …**</span></span> <span data-ttu-id="c37ac-141">ortaya çıkarmak için **Başvuru Ekle** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="c37ac-141">to bring up the **Add Reference** dialogue.</span></span>

15. <span data-ttu-id="c37ac-142">Tıklayın **.NET** sekmesinde, adlı derleme bulun **System.Activities.Core.Presentation**, onu seçin ve tıklayın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="c37ac-142">Click the **.NET** tab, locate the assembly named **System.Activities.Core.Presentation**, select it and click **OK**.</span></span>

16. <span data-ttu-id="c37ac-143">Yordamın aynısını kullanarak, aşağıdaki derlemelere başvurular ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c37ac-143">Using the same procedure, add references to the following assemblies:</span></span>

    1.  <span data-ttu-id="c37ac-144">System.Data.DataSetExtensions.dll</span><span class="sxs-lookup"><span data-stu-id="c37ac-144">System.Data.DataSetExtensions.dll</span></span>

    2.  <span data-ttu-id="c37ac-145">System.Activities.Presentation.dll</span><span class="sxs-lookup"><span data-stu-id="c37ac-145">System.Activities.Presentation.dll</span></span>

    3.  <span data-ttu-id="c37ac-146">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="c37ac-146">System.ServiceModel.Activities.dll</span></span>

17. <span data-ttu-id="c37ac-147">App.xaml dosyası açın ve "RehostingWFDesigner.xaml için" StartUpUri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c37ac-147">Open the App.xaml file and change the value of the StartUpUri to "RehostingWFDesigner.xaml".</span></span>

18. <span data-ttu-id="c37ac-148">UsingWorkflowItemPresenter projeye sağ **Çözüm Gezgini**seçin **Ekle**, ardından **yeni öğe...**</span><span class="sxs-lookup"><span data-stu-id="c37ac-148">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="c37ac-149">ortaya çıkarmak için **Yeni Öğe Ekle** seçin ve iletişim kutusunda **iş akışı** kategori form **yüklü şablonlar** soldaki bölümü.</span><span class="sxs-lookup"><span data-stu-id="c37ac-149">to bring up the **Add New Item** dialogue and select the **Workflow** category form the **Installed Templates** section on the left.</span></span>

19. <span data-ttu-id="c37ac-150">Seçin **etkinlik Tasarımcısı** şablon adlandırın `SimpleNativeDesigner`, tıklatıp **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="c37ac-150">Select the **Activity Designer** template, name it `SimpleNativeDesigner`, and click **Add**.</span></span>

20. <span data-ttu-id="c37ac-151">SimpleNativeDesigner.xaml dosyasını açın ve aşağıdaki kodu yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="c37ac-151">Open the SimpleNativeDesigner.xaml file and paste the following code into it.</span></span> <span data-ttu-id="c37ac-152">Bu kod kullandığına dikkat edin <xref:System.Activities.Presentation.ActivityDesigner> nasıl bağlama tümleştirmek için kullanılan gösterir ve kök öğe olarak <xref:System.Activities.Presentation.WorkflowItemPresenter> tasarımcınıza bir alt türü birleşik etkinlik Tasarımcısı'nda görüntülenecek şekilde içine.</span><span class="sxs-lookup"><span data-stu-id="c37ac-152">Note this code uses <xref:System.Activities.Presentation.ActivityDesigner> as your root element and shows how binding is used to integrate <xref:System.Activities.Presentation.WorkflowItemPresenter> into your designer so a child type can be displayed in your composite activity designer.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="c37ac-153">İçin şemayı <xref:System.Activities.Presentation.ActivityDesigner> özel etkinlik Tasarımcısı tanımı; yalnızca bir alt öğenin eklenmesi verir ancak bu öğe olabilir bir `StackPanel`, `Grid`, ya da diğer bazı bir bileşik kullanıcı Arabirimi öğesi.</span><span class="sxs-lookup"><span data-stu-id="c37ac-153">The schema for <xref:System.Activities.Presentation.ActivityDesigner> allows the addition of only one child element to your custom activity designer definition; however, this element could be a `StackPanel`, `Grid`, or some other composite UI element.</span></span>

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

21. <span data-ttu-id="c37ac-154">UsingWorkflowItemPresenter projeye sağ **Çözüm Gezgini**seçin **Ekle**, ardından **yeni öğe...**</span><span class="sxs-lookup"><span data-stu-id="c37ac-154">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="c37ac-155">ortaya çıkarmak için **Yeni Öğe Ekle** seçin ve iletişim kutusunda **iş akışı** kategori form **yüklü şablonlar** soldaki bölümü.</span><span class="sxs-lookup"><span data-stu-id="c37ac-155">to bring up the **Add New Item** dialogue and select the **Workflow** category form the **Installed Templates** section on the left.</span></span>

22. <span data-ttu-id="c37ac-156">Seçin **kod etkinliği** şablon adlandırın `SimpleNativeActivity`, tıklatıp **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="c37ac-156">Select the  **Code Activity** template, name it `SimpleNativeActivity`, and click **Add**.</span></span>

23. <span data-ttu-id="c37ac-157">Uygulama `SimpleNativeActivity` SimpleNativeActivity.cs dosyaya aşağıdaki kodu girerek sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c37ac-157">Implement the `SimpleNativeActivity` class by entering the following code into the SimpleNativeActivity.cs file.</span></span>

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

24. <span data-ttu-id="c37ac-158">Seçin **Çözümü Derle** gelen **derleme** menüsü.</span><span class="sxs-lookup"><span data-stu-id="c37ac-158">Select **Build Solution** from the **Build** menu.</span></span>

25. <span data-ttu-id="c37ac-159">Seçin **hata ayıklama olmadan Başlat** gelen **hata ayıklama** menü yeniden barındırılan özel tasarım penceresini açın.</span><span class="sxs-lookup"><span data-stu-id="c37ac-159">Select **Start Without Debugging** from the **Debug** menu to open the rehosted custom design window.</span></span>

### <a name="to-create-a-custom-activity-designer-using-workflowitemspresenter"></a><span data-ttu-id="c37ac-160">WorkflowItemsPresenter kullanarak bir özel etkinlik Tasarımcısı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c37ac-160">To create a custom activity designer using WorkflowItemsPresenter</span></span>

1.  <span data-ttu-id="c37ac-161">İkinci özel etkinlik Tasarımcısı için bazı değişiklikler, ilk başta olan ikinci uygulama adı için parallels oluşan bir yordamdır `UsingWorkflowItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="c37ac-161">The procedure for the second custom activity designer is the parallels the first with a few modifications, the first of which is to name the second application `UsingWorkflowItemsPresenter`.</span></span> <span data-ttu-id="c37ac-162">Ayrıca bu uygulamayı yeni bir özel etkinlik tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="c37ac-162">Also this application does not define a new custom activity.</span></span>

2.  <span data-ttu-id="c37ac-163">Temel farklılıklar CustomParallelDesigner.xaml ve RehostingWFDesigner.xaml.cs dosyaları yer alır.</span><span class="sxs-lookup"><span data-stu-id="c37ac-163">Key differences are contained in the CustomParallelDesigner.xaml and RehostingWFDesigner.xaml.cs files.</span></span> <span data-ttu-id="c37ac-164">Kullanıcı arabirimini tanımlar CustomParallelDesigne.xaml dosyasından kod aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="c37ac-164">Here is the code from the CustomParallelDesigne.xaml file that defines the UI.</span></span>

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

3.  <span data-ttu-id="c37ac-165">İşte kod RehostingWFDesigner.xaml.cs dosyasından rehosting mantığı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c37ac-165">Here is the code from the RehostingWFDesigner.xaml.cs file that provides the rehosting logic.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c37ac-166">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c37ac-166">See Also</span></span>

- <xref:System.Activities.Presentation.ActivityDesigner>
- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- <xref:System.Activities.Presentation.WorkflowViewElement>
- <xref:System.Activities.Presentation.Model.ModelItem>
- [<span data-ttu-id="c37ac-167">İş Akışı Tasarım Deneyimini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="c37ac-167">Customizing the Workflow Design Experience</span></span>](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md)