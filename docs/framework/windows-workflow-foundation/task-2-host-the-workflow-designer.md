---
title: "Görev 2: ana bilgisayar iş akışı Tasarımcısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fffc934bbbd1fc707e0bf5c0afbf79a40fc8c633
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="task-2-host-the-workflow-designer"></a>Görev 2: ana bilgisayar iş akışı Tasarımcısı
Bu konuda bir örneğini barındıran yordamı açıklanmaktadır [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] içinde bir [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] uygulama.  
  
 Yordam yapılandırır **kılavuz** Tasarımcısı içeren denetimi program aracılığıyla bir örneğini oluşturur <xref:System.Activities.Presentation.WorkflowDesigner> varsayılan içeren <xref:System.Activities.Statements.Sequence> etkinliğini kaydeder sağlamak için tasarımcı meta veriler tüm yerleşik etkinlikler ve ana bilgisayarlar için tasarımcı desteği [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] içinde [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] uygulama.  
  
### <a name="to-host-the-workflow-designer"></a>İş Akışı Tasarımcısı'nı barındırmak için  
  
1.  Açık HostingApplication proje içinde oluşturduğunuz [görev 1: yeni bir Windows Presentation Foundation uygulaması oluşturma](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md).  
  
2.  Kullanılacak kolaylaştırmak için Pencere boyutunu Ayarla [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]. Bunu yapmak için seçin **MainWindow** Tasarımcısı'nda görüntülemek için F4 tuşuna basın **özellikleri** penceresinde hem de **düzeni** var. bölümünde, **genişliği** 600 değerine ve **yükseklik** 350 değerine.  
  
3.  Kılavuz adı seçerek ayarlayın **kılavuz** Tasarımcı panelinde (kutusunun içine tıklayın **MainWindow**) ve ayarı **adı** en üstündeki özelliği  **Özellikler** "grid1" penceresine.  
  
4.  İçinde **özellikleri** penceresinde, üç nokta işaretine (**...** ) yanındaki `ColumnDefinitions` açmak için özellik **Koleksiyonu Düzenleyicisi** iletişim kutusu.  
  
5.  İçinde **Koleksiyonu Düzenleyicisi** iletişim kutusu, tıklatın **Ekle** düğmesini Düzen üç sütun eklemek için üç kez. İlk sütun içerecek **araç**, ikinci sütun barındıracak [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], ve üçüncü sütun Özellik denetçisi için kullanılır.  
  
6.  Ayarlama `Width` özelliği orta değer, "4 *".  
  
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
  
8.  İçinde **Çözüm Gezgini**MainWindow.xaml sağ tıklatın ve seçin **görünümü kodu**. Aşağıdaki adımları izleyerek kodu değiştirin:  
  
    1.  Şu ad alanlarından ekleyin:  
  
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
  
    3.  Aşağıdakileri ekleyin `AddDesigner` yönteme `MainWindow` sınıfı. Uygulama bir örneğini oluşturur <xref:System.Activities.Presentation.WorkflowDesigner>, ekler bir <xref:System.Activities.Statements.Sequence> , etkinlik ve grid1 Orta sütunda yerleştirir **kılavuz**.  
  
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
  
    4.  Yerleşik tüm etkinlikler için tasarımcı desteği eklemek için tasarımcı meta verilerini kaydedin. Bu, özgün Kutusu'ndan etkinlikleri bırakın sağlar <xref:System.Activities.Statements.Sequence> etkinliğinde [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]. Bunu yapmak için ekleyin `RegisterMetadata` yönteme `MainWindow` sınıfı.  
  
        ```csharp  
        private void RegisterMetadata()  
        {               
            DesignerMetadata dm = new DesignerMetadata();  
            dm.Register();  
        }  
        ```  
  
         [!INCLUDE[crabout](../../../includes/crabout-md.md)]bkz. etkinlik tasarımcıları kaydetme, [nasıl yapılır: Özel Etkinlik Tasarımcısı oluşturma](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer.md).  
  
    5.  İçinde `MainWindow` sınıf oluşturucu, daha önce tasarımcı desteği için meta verileri kaydetmek ve oluşturmak için bildirilen yöntemler çağrıları ekleme <xref:System.Activities.Presentation.WorkflowDesigner>.  
  
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
        >  `RegisterMetadata` Yöntemi de içeren yerleşik etkinlikler Tasarımcı meta verilerini kaydeder <xref:System.Activities.Statements.Sequence> etkinlik. Çünkü `AddDesigner` yöntemi kullanan <xref:System.Activities.Statements.Sequence> etkinliği `RegisterMetadata` yöntemi önce çağrılmalıdır.  
  
9. Derleme ve çözümü çalıştırmak için F5 tuşuna basın.  
  
10. Bkz: [görev 3: araç kutusu oluşturup PropertyGrid bölmeleri](../../../docs/framework/windows-workflow-foundation/task-3-create-the-toolbox-and-propertygrid-panes.md) nasıl ekleneceğini öğrenmek için **araç** ve **PropertyGrid** desteklemek için rehosted iş akışı Tasarımcısı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş Akışı Tasarımcısı yeniden barındırma](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [Görev 1: yeni bir Windows Presentation Foundation uygulaması oluşturma](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md)  
 [Görev 3: PropertyGrid bölmeleri ve araç kutusu oluşturma](../../../docs/framework/windows-workflow-foundation/task-3-create-the-toolbox-and-propertygrid-panes.md)
