---
title: 'Görev 2: İş Akışı Tasarımcısı barındırın'
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: 15657ad79632812d3802e4da22b9ef297d08f932
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72180257"
---
# <a name="task-2-host-the-workflow-designer"></a>Görev 2: İş Akışı Tasarımcısı barındırın

Bu konu, bir Windows Presentation Foundation (WPF) uygulamasında [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] örneğini barındırma yordamını açıklamaktadır.

Yordam, tasarımcı içeren **kılavuz** denetimini yapılandırır, programlı olarak varsayılan bir <xref:System.Activities.Statements.Sequence> etkinliği içeren <xref:System.Activities.Presentation.WorkflowDesigner> örneğini oluşturur, tasarımcı meta verilerini tüm yerleşik aktiviteler ve WPF uygulamasında [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] barındırır.

## <a name="to-host-the-workflow-designer"></a>İş akışı tasarımcısını barındırmak için

1. Görev 1 ' de oluşturduğunuz HostingApplication projesini açın [: yeni bir Windows Presentation Foundation uygulaması oluşturun](task-1-create-a-new-wpf-app.md).

2. @No__t-0 kullanımını kolaylaştırmak için pencerenin boyutunu ayarlayın. Bunu yapmak için tasarımcıda **MainWindow** ' i seçin, **Özellikler** penceresini göstermek için F4 tuşuna basın ve **düzen** bölümünde, **Genişlik** değerini 600 değerine ve **yüksekliği** 350 değerine ayarlayın.

3. Tasarımcı 'daki **kılavuz** panelini seçerek ızgara adını ayarlayın ( **MainWindow**içindeki kutuya tıklayın) ve **Özellikler** penceresinin üst kısmındaki **Name** özelliğini "grid1" olarak ayarlayın.

4. **Özellikler** penceresinde, **koleksiyon Düzenleyicisi** iletişim kutusunu açmak için `ColumnDefinitions` özelliğinin yanındaki üç nokta ( **...** ) simgesine tıklayın.

5. Düzen **Düzenleyici** iletişim kutusunda, mizanpaja üç sütun eklemek için **Ekle** düğmesine üç kez tıklayın. İlk sütunda **araç kutusu**bulunur, ikinci sütun [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] ' i barındıracak ve üçüncü sütun Özellik denetçisi için kullanılacaktır.

6. Orta sütunun `Width` özelliğini "4 *" değerine ayarlayın.

7. Değişiklikleri kaydetmek için **Tamam**’a tıklayın. Aşağıdaki XAML, *MainWindow. xaml* dosyanıza eklenir:

    ```xaml
    <Grid Name="grid1">
        <Grid.ColumnDefinitions>
            <ColumnDefinition />
            <ColumnDefinition Width="4*" />
            <ColumnDefinition />
        </Grid.ColumnDefinitions>
    </Grid>
    ```

8. **Çözüm Gezgini**, *MainWindow. xaml* öğesine sağ tıklayın ve **kodu görüntüle**' yi seçin. Aşağıdaki adımları izleyerek kodu değiştirin:

    1. Aşağıdaki ad alanlarını ekleyin:

        ```csharp
        using System.Activities;
        using System.Activities.Core.Presentation;
        using System.Activities.Presentation;
        using System.Activities.Presentation.Metadata;
        using System.Activities.Presentation.Toolbox;
        using System.Activities.Statements;
        using System.ComponentModel;
        ```

    2. Bir özel üye alanını <xref:System.Activities.Presentation.WorkflowDesigner> ' ın bir örneğini tutacak şekilde bildirmek için, `MainWindow` sınıfına aşağıdaki kodu ekleyin:

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

    3. `MainWindow` sınıfına aşağıdaki `AddDesigner` yöntemini ekleyin. Uygulama <xref:System.Activities.Presentation.WorkflowDesigner> ' ın bir örneğini oluşturur, buna bir <xref:System.Activities.Statements.Sequence> etkinliği ekler ve bunu grid1 **Grid**'in orta sütununa yerleştirir.

        ```csharp
        private void AddDesigner()
        {
            // Create an instance of WorkflowDesigner class.
            this.wd = new WorkflowDesigner();

            // Place the designer canvas in the middle column of the grid.
            Grid.SetColumn(this.wd.View, 1);

            // Load a new Sequence as default.
            this.wd.Load(new Sequence());

            // Add the designer canvas to the grid.
            grid1.Children.Add(this.wd.View);
        }
        ```

    4. Tüm yerleşik etkinlikler için tasarımcı desteği eklemek üzere tasarımcı meta verilerini kaydedin. Bu, [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] ' deki özgün <xref:System.Activities.Statements.Sequence> etkinliğine etkinlikleri araç kutusundan bırakmayı sağlar. Bunu yapmak için, `RegisterMetadata` yöntemini `MainWindow` sınıfına ekleyin:

        ```csharp
        private void RegisterMetadata()
        {
            var dm = new DesignerMetadata();
            dm.Register();
        }
        ```

        Etkinlik tasarımcılarını kaydetme hakkında daha fazla bilgi için bkz. [nasıl yapılır: özel etkinlik Tasarımcısı oluşturma](how-to-create-a-custom-activity-designer.md).

    5. @No__t-0 sınıf oluşturucusunda, tasarımcı desteğinin meta verilerini kaydetmek ve <xref:System.Activities.Presentation.WorkflowDesigner> oluşturmak için önceden belirtilen yöntemlere çağrılar ekleyin.

        ```csharp
        public MainWindow()
        {
            InitializeComponent();

            // Register the metadata.
            RegisterMetadata();

            // Add the WFF Designer.
            AddDesigner();
        }
        ```

        > [!NOTE]
        > @No__t-0 yöntemi, <xref:System.Activities.Statements.Sequence> etkinliği dahil yerleşik etkinliklerin tasarımcı meta verilerini kaydeder. @No__t-0 yöntemi <xref:System.Activities.Statements.Sequence> etkinliğini kullandığından, önce `RegisterMetadata` yönteminin çağrılması gerekir.

9. Çözümü derlemek ve çalıştırmak için <kbd>F5</kbd> tuşuna basın.

10. Yeniden barındırılan iş akışı tasarımcısına **araç kutusu** ve **PropertyGrid** desteğinin nasıl ekleneceğini öğrenmek için bkz. [görev 3: araç kutusu ve PropertyGrid bölmelerini oluşturma](task-3-create-the-toolbox-and-propertygrid-panes.md) .

## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Tasarımcısı yeniden barındırma](rehosting-the-workflow-designer.md)
- [Görev 1: yeni bir Windows Presentation Foundation uygulaması oluşturma](task-1-create-a-new-wpf-app.md)
- [3. görev: araç kutusu ve PropertyGrid bölmelerini oluşturma](task-3-create-the-toolbox-and-propertygrid-panes.md)
