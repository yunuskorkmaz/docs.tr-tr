---
title: 'İzlenecek yol: DataGridView denetiminde veri girişi sırasında oluşan hataları Işleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- error handling [Windows Forms], dataGridView control
- data grids [Windows Forms], error handling
- DataGridView control [Windows Forms], error handling
- data entry [Windows Forms], error handling
- error handling [Windows Forms], data entry
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 30a68b85-d3af-4946-83c1-1e2d010d0511
ms.openlocfilehash: 77a4dcd9cf069ed8bbee6c49aa41db619c8e12ff
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738730"
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a>İzlenecek yol: Windows Forms DataGridView Denetimine Veri Girişi Sırasında Oluşan Hataları Ele Alma

Temel alınan veri deposundaki hataları işleme, veri girişi uygulaması için gerekli bir özelliktir. Windows Forms <xref:System.Windows.Forms.DataGridView> denetimi, veri deposu bir kısıtlama ihlali veya bozuk bir iş kuralı algıladığında oluşan <xref:System.Windows.Forms.DataGridView.DataError> olayını açığa çıkaran bu işlemi kolaylaştırır.

Bu kılavuzda, Northwind örnek veritabanındaki `Customers` tablosundan satırlar alacak ve bunları bir <xref:System.Windows.Forms.DataGridView> denetiminde görüntüleriz. Yeni bir satırda veya düzenlenmiş mevcut bir satırda yinelenen bir `CustomerID` değeri algılandığında, özel durumu açıklayan bir <xref:System.Windows.Forms.MessageBox> görüntüleyerek işlenecek <xref:System.Windows.Forms.DataGridView.DataError> olay oluşur.

Bu konudaki kodu tek bir liste olarak kopyalamak için, bkz. [nasıl yapılır: Windows Forms DataGridView Denetimindeki veri girişi sırasında oluşan hataları işleme](handle-errors-that-occur-during-data-entry-in-the-datagrid.md).

## <a name="prerequisites"></a>Prerequisites

Bu izlenecek yolu tamamlamak için şunlar gerekir:

- Northwind SQL Server örnek veritabanına sahip bir sunucuya erişim.

## <a name="creating-the-form"></a>Form Oluşturma

#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a>DataGridView Denetimindeki veri girişi hatalarını işlemek için

1. <xref:System.Windows.Forms.Form> türetilen ve bir <xref:System.Windows.Forms.DataGridView> denetimi ve <xref:System.Windows.Forms.BindingSource> bileşeni içeren bir sınıf oluşturun.

    Aşağıdaki kod örneği temel başlatma sağlar ve bir `Main` yöntemi içerir.

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]

2. Veritabanına bağlanma ayrıntılarını işlemek için formunuzun sınıf tanımına bir yöntem uygulayın.

    Bu kod örneği, doldurulmuş bir <xref:System.Data.DataTable> nesnesini döndüren `GetData` yöntemini kullanır. `connectionString` değişkenini veritabanınız için uygun bir değere ayarladığınızdan emin olun.

    > [!IMPORTANT]
    > Parola gibi hassas bilgileri, bağlantı dizesi içinde depolamak, uygulamanızın güvenliğini etkileyebilir. Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur. Daha fazla bilgi için bkz. [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]

3. <xref:System.Windows.Forms.DataGridView> ve <xref:System.Windows.Forms.BindingSource> başlatan ve veri bağlamayı ayarlayan formunuzun <xref:System.Windows.Forms.Form.Load> olayı için bir işleyici uygulayın.

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]

4. <xref:System.Windows.Forms.DataGridView><xref:System.Windows.Forms.DataGridView.DataError> olayı işleyin.

    Hatanın bağlamı bir işleme işlemi ise, hatayı bir <xref:System.Windows.Forms.MessageBox>görüntüleyin.

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]

## <a name="testing-the-application"></a>Uygulamayı Test Etme

Artık, beklenen şekilde davrandığından emin olmak için formu test edebilirsiniz.

#### <a name="to-test-the-form"></a>Formu test etmek için

- Uygulamayı çalıştırmak için F5'e basın.

  Müşteriler tablosundaki verilerle doldurulmuş bir <xref:System.Windows.Forms.DataGridView> denetimi göreceksiniz. `CustomerID` için yinelenen bir değer girip düzenlemeyi çalıştırırsanız, hücre değeri otomatik olarak döndürülür ve veri girişi hatasını görüntüleyen bir <xref:System.Windows.Forms.MessageBox> görürsünüz.

## <a name="next-steps"></a>Sonraki Adımlar

Bu uygulama, <xref:System.Windows.Forms.DataGridView> denetimin yeteneklerini temel olarak öğrenmenizi sağlar. <xref:System.Windows.Forms.DataGridView> denetiminin görünümünü ve davranışını çeşitli yollarla özelleştirebilirsiniz:

- Kenarlık ve başlık stillerini değiştirin. Daha fazla bilgi için, bkz. [nasıl yapılır: Windows Forms DataGridView Denetimindeki sınır ve kılavuz çizgisi stillerini değiştirme](change-the-border-and-gridline-styles-in-the-datagrid.md).

- <xref:System.Windows.Forms.DataGridView> denetimine Kullanıcı girişini etkinleştirin veya kısıtlayın. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms DataGridView denetiminde satır eklemeyi ve silmeyi engelleme](prevent-row-addition-and-deletion-datagridview.md)ve [Windows Forms DataGridView denetiminde sütunları salt okuma yapma](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).

- <xref:System.Windows.Forms.DataGridView> denetimine Kullanıcı girişini doğrulayın. Daha fazla bilgi için bkz. [Izlenecek yol: Windows Forms DataGridView Denetimindeki verileri doğrulama](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).

- Sanal modu kullanarak çok büyük veri kümelerini işleyin. Daha fazla bilgi için bkz. [Izlenecek yol: Windows Forms DataGridView denetiminde sanal mod uygulama](implementing-virtual-mode-wf-datagridview-control.md).

- Hücrelerin görünümünü özelleştirin. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms DataGridView Denetimindeki hücrelerin görünümünü özelleştirme](customize-the-appearance-of-cells-in-the-datagrid.md) ve [nasıl yapılır: Windows Forms DataGridView denetimi Için varsayılan hücre stillerini ayarlama](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Windows Forms DataGridView Denetiminde Veri Girişi](data-entry-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Denetimine Veri Girişi Sırasında Oluşan Hataları Ele Alma](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [İzlenecek yol: Windows Forms DataGridView Denetiminde Verileri Doğrulama](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [Bağlantı Bilgilerini Koruma](../../data/adonet/protecting-connection-information.md)
