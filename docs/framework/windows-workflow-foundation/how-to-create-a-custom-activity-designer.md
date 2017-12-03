---
title: "Nasıl yapılır: Özel Etkinlik Tasarımcısı oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f3aade6-facc-44ef-9657-a407ef8b9b31
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f0b1f27af6b4ec372b9dbd63e4bc89a5c435efe6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-custom-activity-designer"></a>Nasıl yapılır: Özel Etkinlik Tasarımcısı oluşturma
Özel Etkinlik tasarımcıları, bunların ilişkili etkinliklerini onlarla tasarım yüzeyi açın, tasarımcıları bırakılabilir diğer etkinlikleri ile birleştirilebilir; böylece genellikle uygulanır. Bu işlev bir özel etkinlik Tasarımcısı "isteğe bağlı bir etkinlik nereye yerleştirileceğini bırakma bölgesi" ve ayrıca tasarım yüzeyine öğelerde elde edilen koleksiyonunu yönetmenizi anlamına gelir sağlaması gerekir. Bu konuda, bu tür bir bırakma bölgesi içeren bir özel etkinlik Tasarımcısı oluşturma ve düzenleme işlevi Tasarımcı öğe koleksiyonunu yönetmek gerekli olduğunu sağlayan bir özel etkinlik Tasarımcısı oluşturma açıklanmaktadır.  
  
 Özel Etkinlik tasarımcıları genellikle devral <xref:System.Activities.Presentation.ActivityDesigner> belirli bir tasarımcı olmadan tüm etkinlikler için varsayılan taban etkinlik Tasarımcısı türü değil. Bu tür özellik Kılavuzu ile etkileşim ve renkleri ve simgeleri yönetme gibi temel özelliklerini yapılandırma tasarım zamanı deneyimi sağlar.  
  
 <xref:System.Activities.Presentation.ActivityDesigner>iki Yardımcısı denetimleri kullanan <xref:System.Activities.Presentation.WorkflowItemPresenter> ve <xref:System.Activities.Presentation.WorkflowItemsPresenter> özel etkinlik tasarımcıları geliştirmek daha kolay. Bunlar, alt öğelerini, silme, seçim ve ayrıca bu alt öğelerini sürükleyip gibi ortak işlevselliği işleyin. <xref:System.Activities.Presentation.WorkflowItemPresenter> "Açılan bölge", sağlayarak kullanıcı Arabirimi öğesi içinde tek bir alt sağlar, çalışırken <xref:System.Activities.Presentation.WorkflowItemsPresenter> destekleyen birden çok kullanıcı Arabirimi öğeleri, sıralama gibi dahil olmak üzere ek işlevsellik sağlayabilir, taşıma, silme ve alt öğeleri ekleme.  
  
 Özel Etkinlik Tasarımcısı uygulamasında vurgulama gereken Öykü diğer anahtar parçası içinde visual düzenlemeleri bağlı kullanarak şekliyle ilgilidir [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] ne biz Tasarımcısı'nda düzenliyorsanız, bellekte örnek veri bağlama. Bu, ayrıca değişiklik bildirimi ve olayları durumları değişiklikleri gibi izlenmesini etkinleştirmek için sorumlu olan Model öğesi ağacı tarafından gerçekleştirilir.  
  
 Bu konuda iki yordamları özetlemektedir.  
  
1.  İlk yordamı bir özel etkinlik Tasarımcısı ile oluşturmayı açıklar bir <xref:System.Activities.Presentation.WorkflowItemPresenter> diğer etkinlikler alır bırakma bölgesi sağlar. Bu yordamı dayanır [özel bileşik tasarımcıları - iş akışı öğesi sunum](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-designers-workflow-item-presenter.md) örnek.  
  
2.  İkinci yordamı bir özel etkinlik Tasarımcısı ile oluşturmayı açıklar bir <xref:System.Activities.Presentation.WorkflowItemsPresenter> içerilen öğelerin koleksiyonunu düzenlenmesi için gerekli işlevselliği sağlar. Bu yordamı dayanır [özel bileşik tasarımcıları - iş akışı öğeleri sunum](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-designers-workflow-items-presenter.md) örnek.  
  
### <a name="to-create-a-custom-activity-designer-with-a-drop-zone-using-workflowitempresenter"></a>Özel Etkinlik Tasarımcısı WorkflowItemPresenter kullanarak bir açılan bölgeyle oluşturmak için  
  
1.  Başlat [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Üzerinde **dosya** menüsündeki **yeni**ve ardından **proje...** .  
  
     **Yeni proje** iletişim kutusu açılır.  
  
3.  İçinde **yüklü şablonlar** bölmesinde, **Windows** , tercih edilen dili kategorisinden.  
  
4.  İçinde **şablonları** bölmesinde, **WPF uygulaması**.  
  
5.  İçinde **adı** kutusuna `UsingWorkflowItemPresenter`.  
  
6.  İçinde **konumu** kutusunda, istediğiniz tıklayın veya projenizi kaydetmek istediğiniz dizini girin **Gözat** gitmek için.  
  
7.  İçinde **çözüm** kutusunda, varsayılan değeri kabul edin.  
  
8.  **Tamam**'ı tıklatın.  
  
9. MainWindows.xaml dosyasında sağ **Çözüm Gezgini**seçin **silmek** ve onaylayın **Tamam** içinde **Microsoft Visual Studio**iletişim kutusu.  
  
10. ' Nde UsingWorkflowItemPresenter projeye sağ **Çözüm Gezgini**seçin **Ekle**, ardından **yeni öğe...** ortaya çıkarmak için **Yeni Öğe Ekle** iletişim kutusunda ve seçin **WPF** kategoriden **yüklü şablonlar** sol bölümü.  
  
11. Seçin **penceresi (WPF)** şablon adlandırın `RehostingWFDesigner`, tıklatıp **Ekle**.  
  
12. RehostingWFDesigner.xaml dosyasını açın ve bu uygulama için kullanıcı Arabirimi tanımlamak için aşağıdaki kodu yapıştırın.  
  
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
  
13. Bir etkinlik Tasarımcısı bir etkinlik türü ile ilişkilendirmek için bu etkinlik Tasarımcısı ile meta veri deposu kaydetmeniz gerekir. Bunu yapmak için ekleyin `RegisterMetadata` yönteme `RehostingWFDesigner` sınıfı. Kapsamında `RegisterMetadata` yöntemi oluşturma bir <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> nesne ve çağrı <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> öznitelikleri ekleme yöntemi. Çağrı <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> ekleme yöntemi <xref:System.Activities.Presentation.Metadata.AttributeTable> meta veri deposuna. Aşağıdaki kod Tasarımcı rehosting mantığını içerir. Meta veriler kaydeder, koyar `SimpleNativeActivity` araç içine ve iş akışını oluşturur. Bu kod RehostingWFDesigner.xaml.cs dosyasına yerleştirin.  
  
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
  
14. Çözüm Gezgini'nde başvuruları dizini sağ tıklatın ve seçin **Başvuru Ekle...** ortaya çıkarmak için **Başvuru Ekle** iletişim kutusu.  
  
15. Tıklatın **.NET** sekmesinde, adlı derleme bulun **System.Activities.Core.Presentation**, seçin ve **Tamam**.  
  
16. Yordamın aynısını kullanarak, aşağıdaki derlemelerine başvurular ekleyin:  
  
    1.  System.Data.DataSetExtensions.dll  
  
    2.  System.Activities.Presentation.dll  
  
    3.  System.ServiceModel.Activities.dll  
  
17. App.xaml dosyasını açın ve "RehostingWFDesigner.xaml" StartUpUri değerini değiştirin.  
  
18. ' Nde UsingWorkflowItemPresenter projeye sağ **Çözüm Gezgini**seçin **Ekle**, ardından **yeni öğe...** ortaya çıkarmak için **Yeni Öğe Ekle** iletişim kutusunda ve seçin **iş akışı** kategori form **yüklü şablonlar** sol bölümü.  
  
19. Seçin **etkinlik Tasarımcısı** şablon adlandırın `SimpleNativeDesigner`, tıklatıp **Ekle**.  
  
20. SimpleNativeDesigner.xaml dosyasını açın ve aşağıdaki kodu yapıştırın. Bu kod kullandığına dikkat edin <xref:System.Activities.Presentation.ActivityDesigner> nasıl bağlama tümleştirmek için kullanılan gösterir ve kök öğesi olarak <xref:System.Activities.Presentation.WorkflowItemPresenter> alt türe bileşik etkinlik Tasarımcısı'nda görüntülenebilir böylece, tasarımcısı içine.  
  
    > [!NOTE]
    >  İçin şemayı <xref:System.Activities.Presentation.ActivityDesigner> özel etkinlik Tasarımcısı tanımınızı; yalnızca bir alt öğeye eklenmesini sağlar ancak, bu öğenin olabilir bir `StackPanel`, `Grid`, ya da diğer bazı bir bileşik UI öğesi.  
  
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
  
21. ' Nde UsingWorkflowItemPresenter projeye sağ **Çözüm Gezgini**seçin **Ekle**, ardından **yeni öğe...** ortaya çıkarmak için **Yeni Öğe Ekle** iletişim kutusunda ve seçin **iş akışı** kategori form **yüklü şablonlar** sol bölümü.  
  
22. Seçin **kodunu aktivite** şablon adlandırın `SimpleNativeActivity`, tıklatıp **Ekle**.  
  
23. Uygulama `SimpleNativeActivity` SimpleNativeActivity.cs dosyasına aşağıdaki kodu girerek sınıfı.  
  
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
  
24. Seçin **yapı çözümü** gelen **yapı** menüsü.  
  
25. Seçin **hata ayıklama olmadan Başlat** gelen **hata ayıklama** menü rehosted özel tasarım penceresini açın.  
  
### <a name="to-create-a-custom-activity-designer-using-workflowitemspresenter"></a>Özel Etkinlik Tasarımcısı WorkflowItemsPresenter kullanarak oluşturmak için  
  
1.  Bazı değişiklikler, ilk başta olan ikinci uygulama adı için parallels yordamdır ikinci özel etkinlik Tasarımcısı için `UsingWorkflowItemsPresenter`. Ayrıca bu uygulamayı yeni bir özel etkinlik tanımlamıyor.  
  
2.  Temel farklılıklar CustomParallelDesigner.xaml ve RehostingWFDesigner.xaml.cs dosyalarında yer alır. Kullanıcı arabirimini tanımlar CustomParallelDesigne.xaml dosyasından kod aşağıdaki gibidir.  
  
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
  
3.  Kod rehosting mantığı sağlayan RehostingWFDesigner.xaml.cs dosyasından aşağıdadır.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Activities.Presentation.ActivityDesigner>  
 <xref:System.Activities.Presentation.WorkflowItemPresenter>  
 <xref:System.Activities.Presentation.WorkflowItemsPresenter>  
 <xref:System.Activities.Presentation.WorkflowViewElement>  
 <xref:System.Activities.Presentation.Model.ModelItem>  
 [İş akışı tasarım deneyimini özelleştirme](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md)
