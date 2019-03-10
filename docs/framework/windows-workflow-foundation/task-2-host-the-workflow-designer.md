---
title: '2. Görev: İş akışı tasarımcısını barındırma'
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: e02134408b38e5c9aee9c59d86b1dfce032653d1
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708645"
---
# <a name="task-2-host-the-workflow-designer"></a>2. Görev: İş akışı tasarımcısını barındırma
Bu konuda bir örneğini barındıran yordamı açıklanır [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] bir Windows Presentation Foundation (WPF) uygulamasındaki.  
  
 Yordam yapılandırır **kılavuz** Tasarımcısı içeren denetimi program aracılığıyla bir örneğini oluşturur <xref:System.Activities.Presentation.WorkflowDesigner> varsayılan içeren <xref:System.Activities.Statements.Sequence> etkinliğini kaydeder sağlamak için tasarımcı meta verisi tüm yerleşik etkinlikler ve ana bilgisayarlar için tasarımcı desteği [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] içinde [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] uygulama.  
  
### <a name="to-host-the-workflow-designer"></a>İş akışı tasarımcısını barındırma için  
  
1.  Açık HostingApplication proje oluşturduğunuz [görev 1: Yeni bir Windows Presentation Foundation uygulaması oluşturma](task-1-create-a-new-wpf-app.md).  
  
2.  Kullanımını kolaylaştırmak için penceresinin boyutunu ayarlayın [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]. Bunu yapmak için **MainWindow** Tasarımcısı'nda görüntülenecek F4 tuşuna basın **özellikleri** penceresinde hem de **Düzen** var. bölümünde, **genişliği** 600 değerini ve **yükseklik** 350 değerini.  
  
3.  Kılavuz adı seçerek ayarlayın **kılavuz** Tasarımcı panelinde (kutusunun içine tıklayın **MainWindow**) ve ayarı **adı** en üstündeki özellik  **Özellikleri** "grid1" penceresine.  
  
4.  İçinde **özellikleri** penceresinde üç noktaya tıklayın (**...** ) yanındaki `ColumnDefinitions` açmak için özellik **Koleksiyonu Düzenleyicisi** iletişim kutusu.  
  
5.  İçinde **Koleksiyonu Düzenleyicisi** iletişim kutusu, tıklayın **Ekle** düğmesini düzene üç sütun eklemek için üç kez. İlk sütun içerecek **araç kutusu**, ikinci sütun barındıracak [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], ve üçüncü sütunda Özellik denetçisi için kullanılacaktır.  
  
6.  Ayarlama `Width` Ortadaki sütun değerine özelliğini "4 *".  
  
7.  Değişiklikleri kaydetmek için **Tamam** 'a tıklayın. Aşağıdaki XAML MainWindow.xaml dosyanıza eklenir:  
  
    ```xml  
    <Grid Name="grid1">  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition />  
            <ColumnDefinition Width="4*" />  
            <ColumnDefinition />  
        </Grid.ColumnDefinitions>  
    </Grid>  
    ```  
  
8.  İçinde **Çözüm Gezgini**, MainWindow.xaml sağ tıklayıp **kodu görüntüle**. Aşağıdaki adımları izleyerek kodu değiştirin:  
  
    1.  Aşağıdaki ad alanlarını ekleyin:  
  
        ```csharp  
        using System.Activities;  
        using System.Activities.Core.Presentation;  
        using System.Activities.Presentation;  
        using System.Activities.Presentation.Metadata;  
        using System.Activities.Presentation.Toolbox;  
        using System.Activities.Statements;  
        using System.ComponentModel;  
        ```  
  
    2.  Örneği tutmak için bir özel üye alanı bildirmek için <xref:System.Activities.Presentation.WorkflowDesigner>, aşağıdaki kodu ekleyin `MainWindow` sınıfı.  
  
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
  
    3.  Aşağıdaki `AddDesigner` yönteme `MainWindow` sınıfı. Uygulama örneği oluşturur <xref:System.Activities.Presentation.WorkflowDesigner>, ekler bir <xref:System.Activities.Statements.Sequence> , etkinliğini ve grid1 Orta sütundaki yerleştirir **kılavuz**.  
  
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
  
    4.  Tüm yerleşik etkinlikler için tasarımcı desteği eklemek için tasarımcı meta verisi kaydedin. Bu sayede özgün araç kutusundan etkinlikleri bırakmak <xref:System.Activities.Statements.Sequence> etkinliğinde [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]. Bunu yapmak için ekleme `RegisterMetadata` yönteme `MainWindow` sınıfı.  
  
        ```csharp  
        private void RegisterMetadata()  
        {               
            DesignerMetadata dm = new DesignerMetadata();  
            dm.Register();  
        }  
        ```  
  
         Etkinlik tasarımcıları kaydetme hakkında daha fazla bilgi için bkz. [nasıl yapılır: Özel Etkinlik Tasarımcısı oluşturma](how-to-create-a-custom-activity-designer.md).  
  
    5.  İçinde `MainWindow` sınıfının oluşturucusu, tasarımcı desteği için meta verileri kaydetmek ve oluşturmak için daha önce bildirilen yöntemlere yapılan çağrılar ekleyin <xref:System.Activities.Presentation.WorkflowDesigner>.  
  
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
        >  `RegisterMetadata` Yöntemi de içeren yerleşik etkinlikler Tasarımcı meta verilerini kaydeder <xref:System.Activities.Statements.Sequence> etkinlik. Çünkü `AddDesigner` yöntemi kullanan <xref:System.Activities.Statements.Sequence> etkinliği `RegisterMetadata` metodu önce çağrılmalıdır.  
  
9. Derleme ve çözümü çalıştırmak için F5 tuşuna basın.  
  
10. Bkz: [görev 3: Araç kutusu ve PropertyGrid bölmeleri oluşturma](task-3-create-the-toolbox-and-propertygrid-panes.md) ekleme hakkında bilgi edinmek için **araç kutusu** ve **PropertyGrid** , yeniden barındırılan iş akışı Tasarımcısı için destek.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [İş Akışı Tasarımcısını Yeniden Barındırma](rehosting-the-workflow-designer.md)
- [1. Görev: Yeni bir Windows Presentation Foundation uygulaması oluşturma](task-1-create-a-new-wpf-app.md)
- [3. Görev: Araç kutusu ve PropertyGrid bölmeleri oluşturma](task-3-create-the-toolbox-and-propertygrid-panes.md)
