---
title: 'Nasıl Yapılır: Özel Etkinlik Tasarımcısı Oluşturma'
description: Bu makalede, rastgele bir etkinliğin yerleştirilebileceği bir bırakma bölgesine sahip bir Workflow Foundation özel etkinlik Tasarımcısı oluşturma işlemi açıklanmaktadır.
ms.date: 03/30/2017
ms.assetid: 2f3aade6-facc-44ef-9657-a407ef8b9b31
ms.openlocfilehash: 015efd1e482e2b531d28b9caec411c76116c9653
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419791"
---
# <a name="how-to-create-a-custom-activity-designer"></a>Nasıl Yapılır: Özel Etkinlik Tasarımcısı Oluşturma

Özel etkinlik tasarımcıları, genellikle kendileriyle tasarım yüzeyine uygulanabilen diğer etkinliklerle ilişkili etkinliklerin birleştirilebilmesi için uygulanır. Bu işlevsellik, bir özel etkinlik tasarımcısının rastgele bir etkinliğin yerleştirilebileceği "bırakma bölgesi" ve ayrıca tasarım yüzeyinde oluşturulan öğe koleksiyonunu yönetme anlamına gelir. Bu konu, böyle bir bırakma bölgesi içeren özel bir etkinlik tasarımcısının ve tasarımcı öğelerinin toplanmasını yönetmek için gerekli olan bu işlevselliği sağlayan özel bir etkinlik tasarımcısının nasıl oluşturulacağını açıklamaktadır.

Özel etkinlik tasarımcıları genellikle <xref:System.Activities.Presentation.ActivityDesigner> , belirli bir tasarımcı olmadan herhangi bir etkinlik için varsayılan temel etkinlik Tasarımcısı türü olan öğesinden devralınır. Bu tür, Özellik kılavuzuyla etkileşim kurma ve renkleri ve simgeleri yönetme gibi temel yönleri yapılandırma gibi tasarım zamanı deneyimini sağlar.

<xref:System.Activities.Presentation.ActivityDesigner>iki yardımcı denetim kullanır <xref:System.Activities.Presentation.WorkflowItemPresenter> ve <xref:System.Activities.Presentation.WorkflowItemsPresenter> özel etkinlik tasarımcıları geliştirmeyi kolaylaştırmak için. Alt öğeleri sürükleme ve bırakma, silme, seçme ve bu alt öğelerin eklenmesi gibi yaygın işlevleri ele alırlar. , <xref:System.Activities.Presentation.WorkflowItemPresenter> "Bırakma bölgesi" sağlayan içinde tek bir alt Kullanıcı arabirimi öğesine izin verir, ancak, <xref:System.Activities.Presentation.WorkflowItemsPresenter> alt öğeleri sıralama, taşıma, silme ve ekleme gibi ek işlevler de dahil olmak üzere bırden çok UI öğesini destekler.

Hikayenin özel bir etkinlik Tasarımcısı uygulamasında vurgulanması gereken diğer anahtar bölümü görsel düzenlemelerin, tasarımcıda düzenlemekte olduğumuz bellekte depolanan örneğe WPF veri bağlama kullanılarak nasıl ilişkili olduğu konusunda kaygılara sahiptir. Bu, değişiklik bildirimini etkinleştirme ve durumlardaki değişiklikler gibi olayların izlenmesini de sorumlu olan model öğe ağacı tarafından gerçekleştirilir.

Bu konuda iki yordam özetlenmektedir.

1. İlk yordam, <xref:System.Activities.Presentation.WorkflowItemPresenter> diğer etkinlikleri alan bırakma bölgesini sağlayan, ile özel bir etkinlik tasarımcısının nasıl oluşturulacağını açıklar. Bu yordam, [özel bileşik tasarımcılar-Iş akışı öğe sunum](./samples/custom-composite-designers-workflow-item-presenter.md) örneğine dayalıdır.

2. İkinci yordam, <xref:System.Activities.Presentation.WorkflowItemsPresenter> içerilen öğelerin bir koleksiyonunu düzenlemek için gereken işlevselliği sağlayan, ile özel bir etkinlik tasarımcısının nasıl oluşturulacağını açıklar. Bu yordam, [özel bileşik tasarımcılar-Iş akışı öğeleri sunan](./samples/custom-composite-designers-workflow-items-presenter.md) örneğine dayalıdır.

## <a name="to-create-a-custom-activity-designer-with-a-drop-zone-using-workflowitempresenter"></a>Workflowwıtempresenter kullanarak bir bırakma bölgesi ile özel bir etkinlik Tasarımcısı oluşturmak için

1. Visual Studio 2010 ' i başlatın.

2. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **proje...** öğesini seçin.

     **Yeni proje** iletişim kutusu açılır.

3. **Yüklü şablonlar** bölmesinde, tercih ettiğiniz dil kategorisinden **Windows** ' u seçin.

4. **Şablonlar** bölmesinde **WPF uygulaması**' nı seçin.

5. **Ad** kutusuna girin `UsingWorkflowItemPresenter` .

6. **Konum** kutusunda, projenizi kaydetmek istediğiniz dizini girin veya git ' e tıklayarak bu dosyayı **gösterin** .

7. **Çözüm** kutusunda, varsayılan değeri kabul edin.

8. **Tamam**'a tıklayın.

9. **Çözüm Gezgini** *MainWindows. xaml* dosyasına sağ tıklayın, **sil** ' i seçin ve **Microsoft Visual Studio** iletişim kutusunda **Tamam** ' ı onaylayın.

10. **Çözüm Gezgini**' de Usingworkflowwitempresenter projesine sağ tıklayın, **Ekle**' yi ve ardından **Yeni öğe...** öğesini seçin. **Yeni öğe Ekle** iletişim kutusunu açmak için sol taraftaki **yüklü şablonlar** bölümünden **WPF** kategorisini seçin.

11. **Pencere (WPF)** şablonunu seçin, adlandırın `RehostingWFDesigner` ve **Ekle**' ye tıklayın.

12. *RehostingWFDesigner. xaml* dosyasını açın ve uygulama için Kullanıcı arabirimini tanımlamak üzere aşağıdaki kodu buraya yapıştırın:

    ```xaml
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

13. Etkinlik tasarımcısını bir etkinlik türüyle ilişkilendirmek için, bu etkinlik tasarımcısını meta veri deposu ile kaydetmeniz gerekir. Bunu yapmak için `RegisterMetadata` yöntemini `RehostingWFDesigner` sınıfına ekleyin. Yönteminin kapsamı içinde `RegisterMetadata` , bir <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> nesnesi oluşturun ve <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> öznitelikleri eklemek için yöntemini çağırın. <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A>Meta veri deposuna eklemek için yöntemini çağırın <xref:System.Activities.Presentation.Metadata.AttributeTable> . Aşağıdaki kod, tasarımcı için yeniden barındırma mantığını içerir. Meta verileri kaydeder, `SimpleNativeActivity` araç kutusuna koyar ve iş akışını oluşturur. Bu kodu *RehostingWFDesigner.xaml.cs* dosyasına koyun.

    ```csharp
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
                // Register metadata.
                (new DesignerMetadata()).Register();
                RegisterCustomMetadata();
                // Add custom activity to toolbox.
                Toolbox.Categories.Add(new ToolboxCategory("Custom activities"));
                Toolbox.Categories[1].Add(new ToolboxItemWrapper(typeof(SimpleNativeActivity)));

                // Create the workflow designer.
                var wd = new WorkflowDesigner();
                wd.Load(new Sequence());
                DesignerBorder.Child = wd.View;
                PropertyBorder.Child = wd.PropertyInspectorView;

            }

            void RegisterCustomMetadata()
            {
                var builder = new AttributeTableBuilder();
                builder.AddCustomAttributes(typeof(SimpleNativeActivity), new DesignerAttribute(typeof(SimpleNativeDesigner)));
                MetadataStore.AddAttributeTable(builder.CreateTable());
            }
        }
    }
    ```

14. Çözüm Gezgini ' deki başvurular dizinine sağ tıklayın ve **Başvuru Ekle...** öğesini seçin. **Başvuru Ekle** iletişim kutusunu açmak için.

15. **.Net** sekmesine tıklayın, **System. Activities. Core. Presentation**adlı derlemeyi bulun, seçin ve **Tamam**' a tıklayın.

16. Aynı yordamı kullanarak, aşağıdaki derlemelere başvurular ekleyin:

    1. System. Data. Datase, sions. dll

    2. System. Activities. Presentation. dll

    3. System. ServiceModel. Activities. dll

17. *App. xaml* dosyasını açın ve StartupUri değerini "RehostingWFDesigner. xaml" olarak değiştirin.

18. **Çözüm Gezgini**' de Usingworkflowwitempresenter projesine sağ tıklayın, **Ekle**' yi ve ardından **Yeni öğe...** öğesini seçin. **Yeni öğe Ekle** iletişim kutusunu açmak için sol taraftaki **yüklü şablonlar** bölümüne **iş akışı** kategorisi formunu seçin.

19. **Etkinlik Tasarımcısı** şablonunu seçin, adlandırın `SimpleNativeDesigner` ve **Ekle**' ye tıklayın.

20. *SimpleNativeDesigner. xaml* dosyasını açın ve aşağıdaki kodu içine yapıştırın. Bu kod <xref:System.Activities.Presentation.ActivityDesigner> , kök öğesi olarak kullanır ve <xref:System.Activities.Presentation.WorkflowItemPresenter> bileşik etkinlik tasarımcısında bir alt türün görüntülenebilmesi için bir bağlamanın tasarımcı ile tümleştirme için nasıl kullanılacağını gösterir.

    > [!NOTE]
    > Şeması, <xref:System.Activities.Presentation.ActivityDesigner> özel etkinlik Tasarımcısı tanımınıza yalnızca bir alt öğe eklenmesini sağlar; ancak, bu öğe bir `StackPanel` , `Grid` veya başka bir bileşik Kullanıcı arabirimi öğesi olabilir.

    ```xaml
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

21. **Çözüm Gezgini**' de Usingworkflowwitempresenter projesine sağ tıklayın, **Ekle**' yi ve ardından **Yeni öğe...** öğesini seçin. **Yeni öğe Ekle** iletişim kutusunu açmak için sol taraftaki **yüklü şablonlar** bölümüne **iş akışı** kategorisi formunu seçin.

22. **Kod etkinlik** şablonunu seçin, adlandırın `SimpleNativeActivity` ve **Ekle**' ye tıklayın.

23. `SimpleNativeActivity` *SimpleNativeActivity.cs* dosyasına aşağıdaki kodu girerek sınıfı uygulayın:

    ```csharp
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

24. **Build** menüsünden **Build Solution** öğesini seçin.

25. Yeniden barındırılan özel tasarım penceresini açmak için **hata ayıklama** menüsünden **hata ayıklama olmadan Başlat** ' ı seçin.

### <a name="to-create-a-custom-activity-designer-using-workflowitemspresenter"></a>Workflowwitemspresenter kullanarak özel bir etkinlik Tasarımcısı oluşturmak için

1. İkinci özel etkinlik tasarımcısına yönelik yordam, ilki ikinci uygulamayı ilk kez adlandırmak olan birkaç değişiklik ile ilk olarak paraleldir `UsingWorkflowItemsPresenter` . Ayrıca, bu uygulama yeni bir özel etkinlik tanımlamaz.

2. Önemli farklılıklar, *CustomParallelDesigner. xaml* ve *RehostingWFDesigner.xaml.cs* dosyalarında yer alır. Kullanıcı arabirimini tanımlayan *CustomParallelDesigner. xaml* dosyasındaki kod aşağıda verilmiştir:

    ```xaml
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

3. Yeniden barındırma mantığını sağlayan *RehostingWFDesigner.xaml.cs* dosyasındaki kod aşağıda verilmiştir:

    ```csharp
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
                // Register metadata.
                (new DesignerMetadata()).Register();
                RegisterCustomMetadata();

                // Create the workflow designer.
                var wd = new WorkflowDesigner();
                wd.Load(new Sequence());
                DesignerBorder.Child = wd.View;
                PropertyBorder.Child = wd.PropertyInspectorView;

            }

            void RegisterCustomMetadata()
            {
                var builder = new AttributeTableBuilder();
                builder.AddCustomAttributes(typeof(Parallel), new DesignerAttribute(typeof(CustomParallelDesigner)));
                MetadataStore.AddAttributeTable(builder.CreateTable());
            }
        }
    }
    ```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Presentation.ActivityDesigner>
- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- <xref:System.Activities.Presentation.WorkflowViewElement>
- <xref:System.Activities.Presentation.Model.ModelItem>
- [İş Akışı Tasarım Deneyimini Özelleştirme](customizing-the-workflow-design-experience.md)
