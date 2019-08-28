---
title: 'İzlenecek yol: Windows Forms DataGridView Denetimine Veri Girişi Sırasında Oluşan Hataları Ele Alma'
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
ms.openlocfilehash: cee6fe3b049378fa7bbe2585a3607049eaf231bc
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046084"
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a>İzlenecek yol: Windows Forms DataGridView Denetimine Veri Girişi Sırasında Oluşan Hataları Ele Alma

Temel alınan veri deposundaki hataları işleme, veri girişi uygulaması için gerekli bir özelliktir. Windows Forms <xref:System.Windows.Forms.DataGridView> denetimi, veri deposu bir kısıtlama ihlali algıladığında <xref:System.Windows.Forms.DataGridView.DataError> veya bozuk bir iş kuralı algıladığında oluşan olayını ortaya çıkaran şekilde kolaylaştırır.

Bu izlenecek yolda, Northwind örnek veritabanındaki `Customers` tablodan satırları alacak ve bunları bir <xref:System.Windows.Forms.DataGridView> denetimde görüntüleriz. Yeni bir satırda `CustomerID` veya düzenlenmiş var olan bir satırda yinelenen bir değer algılandığında <xref:System.Windows.Forms.DataGridView.DataError> , bu durum, özel durumu açıklayan bir <xref:System.Windows.Forms.MessageBox> görüntüleyerek işlenecek olan olay oluşur.

Bu konudaki kodu tek bir liste olarak kopyalamak için bkz [. nasıl yapılır: Windows Forms DataGridView Denetimindeki](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)veri girişi sırasında oluşan hataları işleyin.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için şunlar gerekir:

- Northwind SQL Server örnek veritabanına sahip bir sunucuya erişim.

## <a name="creating-the-form"></a>Form Oluşturma

#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a>DataGridView Denetimindeki veri girişi hatalarını işlemek için

1. Öğesinden <xref:System.Windows.Forms.Form> türetilen ve bir <xref:System.Windows.Forms.DataGridView> denetim ve <xref:System.Windows.Forms.BindingSource> bileşen içeren bir sınıf oluşturun.

    Aşağıdaki kod örneği temel başlatma sağlar ve bir `Main` yöntemi içerir.

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]

2. Veritabanına bağlanma ayrıntılarını işlemek için formunuzun sınıf tanımına bir yöntem uygulayın.

    Bu kod örneği, doldurulmuş `GetData` <xref:System.Data.DataTable> bir nesne döndüren bir yöntemi kullanır. Değişkeni, `connectionString` veritabanınız için uygun bir değere ayarladığınızdan emin olun.

    > [!IMPORTANT]
    > Parola gibi hassas bilgileri, bağlantı dizesi içinde depolamak, uygulamanızın güvenliğini etkileyebilir. Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur. Daha fazla bilgi için bkz. [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]

3. <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.Form.Load> Ve<xref:System.Windows.Forms.BindingSource> ' i başlatan ve veri bağlamayı ayarlayan formunuzun olayı için bir işleyici uygulayın.

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]

4. Üzerinde olayı işleyin. <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.DataGridView.DataError>

    Hatanın bağlamı bir işleme işlemi ise, hatayı bir <xref:System.Windows.Forms.MessageBox>ile görüntüleyin.

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]

## <a name="testing-the-application"></a>Uygulamayı Test Etme

Artık, beklenen şekilde davrandığından emin olmak için formu test edebilirsiniz.

#### <a name="to-test-the-form"></a>Formu test etmek için

- Uygulamayı çalıştırmak için F5'e basın.

  Müşteriler tablosundan alınan verilerle <xref:System.Windows.Forms.DataGridView> doldurulmuş bir denetim görürsünüz. İçin `CustomerID` yinelenen bir değer girerseniz ve düzenleme hareketi yaparsanız, hücre değeri otomatik olarak döndürülür ve veri girişi hatasını görüntüleyen bir <xref:System.Windows.Forms.MessageBox> görürsünüz.

## <a name="next-steps"></a>Sonraki Adımlar

Bu uygulama, <xref:System.Windows.Forms.DataGridView> denetimin yeteneklerini temel olarak öğrenmenizi sağlar. <xref:System.Windows.Forms.DataGridView> Denetimin görünümünü ve davranışını çeşitli yollarla özelleştirebilirsiniz:

- Kenarlık ve başlık stillerini değiştirin. Daha fazla bilgi için [nasıl yapılır: Windows Forms DataGridView Denetimindeki](change-the-border-and-gridline-styles-in-the-datagrid.md)kenarlık ve kılavuz çizgisi stillerini değiştirin.

- <xref:System.Windows.Forms.DataGridView> Denetim için Kullanıcı girişini etkinleştirin veya kısıtlayın. Daha fazla bilgi için [nasıl yapılır: Windows Forms DataGridView denetiminde](prevent-row-addition-and-deletion-datagridview.md)satır eklemeyi ve silmeyi önleyin ve [şunları yapın: Sütunları Windows Forms DataGridView denetiminde](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)salt okunurdur.

- <xref:System.Windows.Forms.DataGridView> Denetim için Kullanıcı girişini doğrulayın. Daha fazla bilgi için bkz [. İzlenecek yol: Windows Forms DataGridView Denetimindeki](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)veriler doğrulanıyor.

- Sanal modu kullanarak çok büyük veri kümelerini işleyin. Daha fazla bilgi için bkz [. İzlenecek yol: Windows Forms DataGridView denetiminde](implementing-virtual-mode-wf-datagridview-control.md)sanal mod uygulama.

- Hücrelerin görünümünü özelleştirin. Daha fazla bilgi için [nasıl yapılır: Windows Forms DataGridView Denetimindeki](customize-the-appearance-of-cells-in-the-datagrid.md) hücrelerin görünümünü özelleştirin ve [şunları yapın: Windows Forms DataGridView denetimi](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)Için varsayılan hücre stillerini ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Windows Forms DataGridView Denetiminde Veri Girişi](data-entry-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Denetimindeki veri girişi sırasında oluşan hataları işleme](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [İzlenecek yol: Windows Forms DataGridView Denetimindeki verileri doğrulama](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [Bağlantı Bilgilerini Koruma](../../data/adonet/protecting-connection-information.md)
