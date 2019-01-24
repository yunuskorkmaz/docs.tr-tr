---
title: 'Nasıl yapılır: Özel Etkinlik Tasarımcısı oluşturma'
ms.date: 03/30/2017
ms.assetid: 2f3aade6-facc-44ef-9657-a407ef8b9b31
ms.openlocfilehash: 034b8b8be828288f840dbfd902725c4f63c779ac
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638190"
---
# <a name="how-to-create-a-custom-activity-designer"></a>Nasıl yapılır: Özel Etkinlik Tasarımcısı oluşturma

Özel Etkinlik tasarımcıları, genellikle kendi ilişkili etkinlikleri, tasarımcılar, bunları tasarım yüzeyi açın bırakılabilir diğer etkinlikler ile birleştirilebilir, böylece uygulanır. Bu işlev bir özel etkinlik Tasarımcısı "bir bırakma bölge rastgele bir etkinlik nereye yerleştirilmesi" ve ayrıca anlamına gelir elde edilen tasarım yüzeyinde öğelerinin koleksiyonunu yönetmenizi sağlaması gerekir. Bu konu, bu tür bir bırakma bölge içeren bir özel etkinlik Tasarımcısı oluşturma ve düzenleme işlevi Tasarımcı öğelerinin koleksiyonunu yönetmek gerekli olduğunu sağlayan bir özel etkinlik Tasarımcısı oluşturma işlemini açıklar.

 Özel Etkinlik tasarımcıları genellikle devralınan <xref:System.Activities.Presentation.ActivityDesigner> belirli bir tasarımcı olmadan herhangi bir etkinlik için varsayılan taban etkinlik Tasarımcısı türü. Bu özellik kılavuzunda ile etkileşim kurma ve renkleri ve simgeleri yönetme gibi temel özellikleri yapılandırma tasarım zamanı deneyimi sağlar.

 <xref:System.Activities.Presentation.ActivityDesigner> iki Yardımcısı denetimlerini kullanır <xref:System.Activities.Presentation.WorkflowItemPresenter> ve <xref:System.Activities.Presentation.WorkflowItemsPresenter> özel etkinlik tasarımcıları geliştirmeyi daha kolay hale getirmek için. Bunlar alt öğeleri, silme, seçimi ve söz konusu alt öğelerin eklenmesi sürükleyip gibi ortak işlevselliği işleyin. <xref:System.Activities.Presentation.WorkflowItemPresenter> "Bırakma bölge", sağlayarak kullanıcı Arabirimi öğesi içinde tek bir alt sağlar, çalışırken <xref:System.Activities.Presentation.WorkflowItemsPresenter> destekleyen birden çok kullanıcı Arabirimi öğeleri, sıralama gibi dahil olmak üzere ek işlevler sağlayabilir, taşıma, silme ve alt öğeleri ekleme.

 Özel Etkinlik Tasarımcısı uygulamasında vurgulama gereken yazının diğer önemli parçası visual düzenlemeler, bağlı kullanarak şekliyle ilgilidir [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] ne biz tasarımcıda düzenleme bellek depolanan örnek veri bağlama. Bu, aynı zamanda değişiklik bildirimi ve durum değişiklikleri gibi olaylar izlenmesini etkinleştirmek için sorumlu olan Model öğesi ağacı tarafından gerçekleştirilir.

 Bu konu iki yordam açıklanmaktadır.

1.  Birinci yordamda açıklanan özel etkinlik Tasarımcısı ile oluşturmak nasıl bir <xref:System.Activities.Presentation.WorkflowItemPresenter> diğer etkinlikleri alan açılan bölge sağlar. Bu yordamı dayanır [özel bileşik tasarımcılar - iş akışı öğesi sunucu](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-designers-workflow-item-presenter.md) örnek.

2.  İkinci yordam özel etkinlik Tasarımcısı ile oluşturma işlemini açıklamaktadır bir <xref:System.Activities.Presentation.WorkflowItemsPresenter> düzenlemek kapsanan öğelerin koleksiyonunu için gereken işlevselliği sağlar. Bu yordamı dayanır [özel bileşik tasarımcılar - iş akışı öğeleri sunucu](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-designers-workflow-items-presenter.md) örnek.

## <a name="to-create-a-custom-activity-designer-with-a-drop-zone-using-workflowitempresenter"></a>Bir alt bölge WorkflowItemPresenter kullanarak özel bir etkinlik Tasarımcısı oluşturmak için

1.  Visual Studio 2010'u başlatın.

2.  Üzerinde **dosya** menüsünde **yeni**ve ardından **proje...** .

     **Yeni proje** iletişim kutusu açılır.

3.  İçinde **yüklü şablonlar** bölmesinde **Windows** , tercih edilen dil kategorisinden.

4.  İçinde **şablonları** bölmesinde **WPF uygulaması**.

5.  İçinde **adı** kutusuna `UsingWorkflowItemPresenter`.

6.  İçinde **konumu** kutusunda, projeyi kaydedin veya istediğiniz dizin girin **Gözat** gitmek için.

7.  İçinde **çözüm** kutusunda, varsayılan değeri kabul edin.

8.  **Tamam**'ı tıklatın.

9. MainWindows.xaml dosyaya sağ **Çözüm Gezgini**seçin **Sil** ve onaylayın **Tamam** içinde **Microsoft Visual Studio**iletişim kutusu.

10. UsingWorkflowItemPresenter projeye sağ **Çözüm Gezgini**seçin **Ekle**, ardından **yeni öğe...** ortaya çıkarmak için **Yeni Öğe Ekle** seçin ve iletişim kutusunda **WPF** kategoriden **yüklü şablonlar** soldaki bölümü.

11. Seçin **pencere (WPF)** şablon adlandırın `RehostingWFDesigner`, tıklatıp **Ekle**.

12. RehostingWFDesigner.xaml dosyasını açın ve bu uygulama için kullanıcı arabirimini tanımlamak için aşağıdaki kodu yapıştırın.

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

13. Bir etkinlik Tasarımcısı bir etkinlik türü ile ilişkilendirmek için bu etkinlik Tasarımcısı ile meta veri deposuna kaydetmeniz gerekir. Bunu yapmak için ekleme `RegisterMetadata` yönteme `RehostingWFDesigner` sınıfı. Kapsamında `RegisterMetadata` yöntemi oluşturma bir <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> nesne ve çağrı <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> öznitelikleri eklemek için yöntemi. Çağrı <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> ekleme yöntemi <xref:System.Activities.Presentation.Metadata.AttributeTable> meta veri deposuna. Aşağıdaki kod, Tasarımcı için rehosting mantığı içerir. Meta veri kaydeder, koyar `SimpleNativeActivity` araç kutusu içine ve iş akışı oluşturur. Bu kodu RehostingWFDesigner.xaml.cs dosyanın koyun.

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

14. Çözüm Gezgini'ndeki başvurular directory sağ tıklayıp **Başvuru Ekle...** ortaya çıkarmak için **Başvuru Ekle** iletişim kutusu.

15. Tıklayın **.NET** sekmesinde, adlı derleme bulun **System.Activities.Core.Presentation**, onu seçin ve tıklayın **Tamam**.

16. Yordamın aynısını kullanarak, aşağıdaki derlemelere başvurular ekleyin:

    1.  System.Data.DataSetExtensions.dll

    2.  System.Activities.Presentation.dll

    3.  System.ServiceModel.Activities.dll

17. App.xaml dosyası açın ve "RehostingWFDesigner.xaml için" StartUpUri değiştirin.

18. UsingWorkflowItemPresenter projeye sağ **Çözüm Gezgini**seçin **Ekle**, ardından **yeni öğe...** ortaya çıkarmak için **Yeni Öğe Ekle** seçin ve iletişim kutusunda **iş akışı** kategori form **yüklü şablonlar** soldaki bölümü.

19. Seçin **etkinlik Tasarımcısı** şablon adlandırın `SimpleNativeDesigner`, tıklatıp **Ekle**.

20. SimpleNativeDesigner.xaml dosyasını açın ve aşağıdaki kodu yapıştırın. Bu kod kullandığına dikkat edin <xref:System.Activities.Presentation.ActivityDesigner> nasıl bağlama tümleştirmek için kullanılan gösterir ve kök öğe olarak <xref:System.Activities.Presentation.WorkflowItemPresenter> tasarımcınıza bir alt türü birleşik etkinlik Tasarımcısı'nda görüntülenecek şekilde içine.

    > [!NOTE]
    >  İçin şemayı <xref:System.Activities.Presentation.ActivityDesigner> özel etkinlik Tasarımcısı tanımı; yalnızca bir alt öğenin eklenmesi verir ancak bu öğe olabilir bir `StackPanel`, `Grid`, ya da diğer bazı bir bileşik kullanıcı Arabirimi öğesi.

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

21. UsingWorkflowItemPresenter projeye sağ **Çözüm Gezgini**seçin **Ekle**, ardından **yeni öğe...** ortaya çıkarmak için **Yeni Öğe Ekle** seçin ve iletişim kutusunda **iş akışı** kategori form **yüklü şablonlar** soldaki bölümü.

22. Seçin **kod etkinliği** şablon adlandırın `SimpleNativeActivity`, tıklatıp **Ekle**.

23. Uygulama `SimpleNativeActivity` SimpleNativeActivity.cs dosyaya aşağıdaki kodu girerek sınıfı.

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

24. Seçin **Çözümü Derle** gelen **derleme** menüsü.

25. Seçin **hata ayıklama olmadan Başlat** gelen **hata ayıklama** menü yeniden barındırılan özel tasarım penceresini açın.

### <a name="to-create-a-custom-activity-designer-using-workflowitemspresenter"></a>WorkflowItemsPresenter kullanarak bir özel etkinlik Tasarımcısı oluşturmak için

1.  İkinci özel etkinlik Tasarımcısı için bazı değişiklikler, ilk başta olan ikinci uygulama adı için parallels oluşan bir yordamdır `UsingWorkflowItemsPresenter`. Ayrıca bu uygulamayı yeni bir özel etkinlik tanımlamıyor.

2.  Temel farklılıklar CustomParallelDesigner.xaml ve RehostingWFDesigner.xaml.cs dosyaları yer alır. Kullanıcı arabirimini tanımlar CustomParallelDesigne.xaml dosyasından kod aşağıdaki gibidir.

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

3.  İşte kod RehostingWFDesigner.xaml.cs dosyasından rehosting mantığı sağlar.

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

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Presentation.ActivityDesigner>
- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- <xref:System.Activities.Presentation.WorkflowViewElement>
- <xref:System.Activities.Presentation.Model.ModelItem>
- [İş Akışı Tasarım Deneyimini Özelleştirme](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md)