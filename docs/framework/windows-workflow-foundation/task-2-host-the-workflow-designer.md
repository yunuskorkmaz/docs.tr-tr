---
description: 'Hakkında daha fazla bilgi edinin: 1. görev: İş Akışı Tasarımcısı barındırma'
title: 'Görev 2: İş Akışı Tasarımcısını Barındırma'
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: 5a00c9db831575dfe7f6f2b6e041f18877c60118
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755206"
---
# <a name="task-2-host-the-workflow-designer"></a>Görev 2: İş Akışı Tasarımcısını Barındırma

Bu konu, bir Windows Presentation Foundation (WPF) uygulamasında Windows İş Akışı Tasarımcısı örneğini barındırma yordamını açıklamaktadır.

Yordam, tasarımcı içeren **kılavuz** denetimini yapılandırır, program aracılığıyla <xref:System.Activities.Presentation.WorkflowDesigner> varsayılan bir etkinlik içeren bir örneğini oluşturur <xref:System.Activities.Statements.Sequence> , tasarımcı meta verilerini tüm yerleşik etkinlikler için tasarımcı desteği sağlamak üzere kaydeder ve WPF uygulamasında iş akışı Tasarımcısı barındırır.

## <a name="to-host-the-workflow-designer"></a>İş akışı tasarımcısını barındırmak için

1. Görev 1 ' de oluşturduğunuz HostingApplication projesini açın [: yeni bir Windows Presentation Foundation uygulaması oluşturun](task-1-create-a-new-wpf-app.md).

2. İş Akışı Tasarımcısı kullanımını kolaylaştırmak için pencerenin boyutunu ayarlayın. Bunu yapmak için tasarımcıda **MainWindow** ' i seçin, **Özellikler** penceresini göstermek için F4 tuşuna basın ve **düzen** bölümünde, **Genişlik** değerini 600 değerine ve **yüksekliği** 350 değerine ayarlayın.

3. Tasarımcı 'daki **kılavuz** panelini seçerek ızgara adını ayarlayın ( **MainWindow** içindeki kutuya tıklayın) ve **Özellikler** penceresinin üst kısmındaki **Name** özelliğini "grid1" olarak ayarlayın.

4. **Özellikler** penceresinde, koleksiyon Düzenleyicisi iletişim kutusunu açmak için özelliğin yanındaki üç nokta (**...**) simgesine tıklayın `ColumnDefinitions`  .

5. Düzen **Düzenleyici** iletişim kutusunda, mizanpaja üç sütun eklemek için **Ekle** düğmesine üç kez tıklayın. İlk sütunda **araç kutusu** bulunur, ikinci sütun iş akışı Tasarımcısı barındırır ve üçüncü sütun Özellik denetçisi için kullanılacaktır.

6. `Width`Orta sütunun özelliğini "4 *" değeri olarak ayarlayın.

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

    2. Bir örneğini tutacak bir özel üye alanı bildirmek için <xref:System.Activities.Presentation.WorkflowDesigner> , sınıfına aşağıdaki kodu ekleyin `MainWindow` :

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

    3. `MainWindow` sınıfına aşağıdaki `AddDesigner` yöntemini ekleyin. Uygulama öğesinin bir örneğini oluşturur <xref:System.Activities.Presentation.WorkflowDesigner> , buna bir etkinlik ekler <xref:System.Activities.Statements.Sequence> ve grid1 **Grid**'in orta sütununa yerleştirir.

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

    4. Tüm yerleşik etkinlikler için tasarımcı desteği eklemek üzere tasarımcı meta verilerini kaydedin. Bu, içindeki etkinlikleri, İş Akışı Tasarımcısı araç kutusundan özgün etkinliğe düşürüetmenize olanak sağlar <xref:System.Activities.Statements.Sequence> . Bunu yapmak için `RegisterMetadata` yöntemini `MainWindow` sınıfına ekleyin:

        ```csharp
        private void RegisterMetadata()
        {
            var dm = new DesignerMetadata();
            dm.Register();
        }
        ```

        Etkinlik tasarımcılarını kaydetme hakkında daha fazla bilgi için bkz. [nasıl yapılır: özel etkinlik Tasarımcısı oluşturma](how-to-create-a-custom-activity-designer.md).

    5. `MainWindow`Sınıf oluşturucusunda, tasarımcı desteğinin meta verilerini kaydetmek ve oluşturmak için daha önce belirtilen yöntemlere çağrılar ekleyin <xref:System.Activities.Presentation.WorkflowDesigner> .

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
        > `RegisterMetadata`Yöntemi, etkinlik dahil yerleşik etkinliklerin tasarımcı meta verilerini kaydeder <xref:System.Activities.Statements.Sequence> . `AddDesigner`Yöntemi <xref:System.Activities.Statements.Sequence> etkinliğini kullandığından, `RegisterMetadata` önce yönteminin çağrılması gerekir.

9. Çözümü derlemek ve çalıştırmak için <kbd>F5</kbd> tuşuna basın.

10. Yeniden barındırılan iş akışı tasarımcısına **araç kutusu** ve **PropertyGrid** desteğinin nasıl ekleneceğini öğrenmek için bkz. [görev 3: araç kutusu ve PropertyGrid bölmelerini oluşturma](task-3-create-the-toolbox-and-propertygrid-panes.md) .

## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Tasarımcısını Yeniden Barındırma](rehosting-the-workflow-designer.md)
- [Görev 1: Yeni Bir Windows Presentation Foundation Uygulaması Oluşturma](task-1-create-a-new-wpf-app.md)
- [Görev 3: Araç Kutusu ve PropertyGrid Bölmeleri Oluşturma](task-3-create-the-toolbox-and-propertygrid-panes.md)
