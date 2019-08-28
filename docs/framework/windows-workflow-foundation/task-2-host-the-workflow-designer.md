---
title: 'Görev 2: İş Akışı Tasarımcısını Barındırma'
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: 92c5fa347cc7a2c0088ab8f4fbdfddf25ffb83c1
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70037864"
---
# <a name="task-2-host-the-workflow-designer"></a>Görev 2: İş Akışı Tasarımcısını Barındırma

Bu konu, [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] bir Windows Presentation Foundation (WPF) uygulamasında örneğini barındırmak için yordamı açıklar.

Yordam, tasarımcı içeren **kılavuz** denetimini yapılandırır, program aracılığıyla varsayılan <xref:System.Activities.Presentation.WorkflowDesigner> <xref:System.Activities.Statements.Sequence> bir etkinlik içeren bir örneğini oluşturur, tasarımcı meta verilerini tümü için tasarımcı desteği sağlamak üzere kaydeder. yerleşik etkinlikler ve WPF uygulamasında barındırır [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] .

### <a name="to-host-the-workflow-designer"></a>İş akışı tasarımcısını barındırmak için

1. Görev 1 ' de [oluşturduğunuz HostingApplication projesini açın: Yeni bir Windows Presentation Foundation uygulaması](task-1-create-a-new-wpf-app.md)oluşturun.

2. Uygulamasının kullanımını [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]kolaylaştırmak için pencerenin boyutunu ayarlayın. Bunu yapmak için tasarımcıda **MainWindow** ' i seçin, **Özellikler** penceresini göstermek için F4 tuşuna basın ve **düzen** bölümünde, **Genişlik** değerini 600 değerine ve **yüksekliği** 350 değerine ayarlayın.

3. Tasarımcı 'daki **kılavuz** panelini seçerek ızgara adını ayarlayın ( **MainWindow**içindeki kutuya tıklayın) ve **Özellikler** penceresinin üst kısmındaki **Name** özelliğini "grid1" olarak ayarlayın.

4. **Özellikler** penceresinde, **koleksiyon Düzenleyicisi** iletişim kutusunu açmak için `ColumnDefinitions` özelliğin yanındaki üç nokta ( **...** ) simgesine tıklayın.

5. Düzen **Düzenleyici** iletişim kutusunda, mizanpaja üç sütun eklemek için **Ekle** düğmesine üç kez tıklayın. İlk sütunda **araç kutusu**bulunur, ikinci sütun [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]' ı barındırır ve üçüncü sütun Özellik denetçisi için kullanılacaktır.

6. Orta sütunun `Width` özelliğini "4 *" değeri olarak ayarlayın.

7. Değişiklikleri kaydetmek için **Tamam** 'a tıklayın. Aşağıdaki XAML, MainWindow. xaml dosyanıza eklenir:

    ```xml
    <Grid Name="grid1">
        <Grid.ColumnDefinitions>
            <ColumnDefinition />
            <ColumnDefinition Width="4*" />
            <ColumnDefinition />
        </Grid.ColumnDefinitions>
    </Grid>
    ```

8. **Çözüm Gezgini**, MainWindow. xaml öğesine sağ tıklayın ve **kodu görüntüle**' yi seçin. Aşağıdaki adımları izleyerek kodu değiştirin:

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

    2. Bir örneğini <xref:System.Activities.Presentation.WorkflowDesigner>tutacak bir özel üye alanı bildirmek için, `MainWindow` sınıfına aşağıdaki kodu ekleyin.

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

    3. `MainWindow` Sınıfına aşağıdaki `AddDesigner` yöntemi ekleyin. Uygulama öğesinin <xref:System.Activities.Presentation.WorkflowDesigner>bir örneğini oluşturur, buna bir <xref:System.Activities.Statements.Sequence> etkinlik ekler ve grid1 **Grid**'in orta sütununa yerleştirir.

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

    4. Tüm yerleşik etkinlikler için tasarımcı desteği eklemek üzere tasarımcı meta verilerini kaydedin. Bu, <xref:System.Activities.Statements.Sequence> [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]içindeki etkinlikleri araç kutusundan özgün etkinliğe düşürübilmenizi sağlar. Bunu yapmak için `RegisterMetadata` yöntemini `MainWindow` sınıfına ekleyin.

        ```csharp
        private void RegisterMetadata()
        {
            DesignerMetadata dm = new DesignerMetadata();
            dm.Register();
        }
        ```

        Etkinlik tasarımcılarını kaydetme hakkında daha fazla bilgi için [bkz. nasıl yapılır: Özel bir etkinlik Tasarımcısı](how-to-create-a-custom-activity-designer.md)oluşturun.

    5. Sınıf oluşturucusunda, tasarımcı desteğinin meta verilerini kaydetmek ve <xref:System.Activities.Presentation.WorkflowDesigner>oluşturmak için daha önce belirtilen yöntemlere çağrılar ekleyin. `MainWindow`

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
        > Yöntemi, <xref:System.Activities.Statements.Sequence> etkinlik dahil yerleşik etkinliklerin tasarımcı meta verilerini kaydeder. `RegisterMetadata` Yöntemi etkinliğini kullandığından ,`RegisterMetadata` önce yönteminin çağrılması gerekir. <xref:System.Activities.Statements.Sequence> `AddDesigner`

9. Çözümü derlemek ve çalıştırmak için F5 tuşuna basın.

10. Bkz [. görev 3: Yeniden barındırılan iş akışı tasarımcısına](task-3-create-the-toolbox-and-propertygrid-panes.md) **araç kutusu** ve **PropertyGrid** desteğinin nasıl ekleneceğini öğrenmek için araç kutusu ve PropertyGrid bölmelerini oluşturun.

## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Tasarımcısını Yeniden Barındırma](rehosting-the-workflow-designer.md)
- [Görev 1: Yeni bir Windows Presentation Foundation uygulaması oluşturma](task-1-create-a-new-wpf-app.md)
- [Görev 3: Araç kutusu ve PropertyGrid bölmelerini oluşturma](task-3-create-the-toolbox-and-propertygrid-panes.md)
