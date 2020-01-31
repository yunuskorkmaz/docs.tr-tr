---
title: 'İzlenecek yol: DataGridView Denetimindeki verileri doğrulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validating data [Windows Forms], Windows Forms
- data [Windows Forms], validation
- DataGridView control [Windows Forms], data validation
- data grids [Windows Forms], validating data
- data validation [Windows Forms], Windows Forms
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: a4f1d015-2969-430c-8ea2-b612d179c290
ms.openlocfilehash: 45753fb206ad58616c9a727bd81bd2458db6053e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740096"
---
# <a name="walkthrough-validating-data-in-the-windows-forms-datagridview-control"></a>İzlenecek yol: Windows Forms DataGridView Denetiminde Verileri Doğrulama

Kullanıcılara veri girişi işlevlerini görüntülediğinizde, formunuza girilen verileri sıkça doğrulamanız gerekir. <xref:System.Windows.Forms.DataGridView> sınıfı, veriler veri deposuna kaydedilmeden önce doğrulama gerçekleştirmek için kullanışlı bir yol sağlar. Geçerli hücre değiştiğinde <xref:System.Windows.Forms.DataGridView> tarafından oluşturulan <xref:System.Windows.Forms.DataGridView.CellValidating> olayını işleyerek verileri doğrulayabilirsiniz.

Bu kılavuzda, Northwind örnek veritabanındaki `Customers` tablosundan satırlar alacak ve bunları bir <xref:System.Windows.Forms.DataGridView> denetiminde görüntüleriz. Kullanıcı `CompanyName` sütununda bir hücreyi düzenler ve hücreyi bırakmaya çalışırsa, <xref:System.Windows.Forms.DataGridView.CellValidating> olay işleyicisi boş olmadığından emin olmak için yeni şirket adı dizesini inceler; Yeni değer boş bir dize ise, <xref:System.Windows.Forms.DataGridView> boş olmayan bir dize girilene kadar kullanıcının imlecinizin hücreden ayrılmasını önler.

Bu konudaki kodu tek bir liste olarak kopyalamak için bkz. [nasıl yapılır: verileri doğrulama Windows Forms DataGridView Denetimindeki](how-to-validate-data-in-the-windows-forms-datagridview-control.md).

## <a name="prerequisites"></a>Prerequisites

Bu izlenecek yolu tamamlamak için şunlar gerekir:

- Northwind SQL Server örnek veritabanına sahip bir sunucuya erişim.

## <a name="creating-the-form"></a>Form Oluşturma

#### <a name="to-validate-data-entered-in-a-datagridview"></a>DataGridView içinde girilen verileri doğrulamak için

1. <xref:System.Windows.Forms.Form> türetilen ve bir <xref:System.Windows.Forms.DataGridView> denetimi ve <xref:System.Windows.Forms.BindingSource> bileşeni içeren bir sınıf oluşturun.

    Aşağıdaki kod örneği temel başlatma sağlar ve bir `Main` yöntemi içerir.

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#02)]

2. Veritabanına bağlanma ayrıntılarını işlemek için formunuzun sınıf tanımına bir yöntem uygulayın.

    Bu kod örneği, doldurulmuş bir <xref:System.Data.DataTable> nesnesini döndüren `GetData` yöntemini kullanır. `connectionString` değişkenini veritabanınız için uygun bir değere ayarladığınızdan emin olun.

    > [!IMPORTANT]
    > Parola gibi hassas bilgileri, bağlantı dizesi içinde depolamak, uygulamanızın güvenliğini etkileyebilir. Tümleşik güvenlik olarak da bilinen Windows kimlik doğrulaması kullanmak, bir veritabanına erişimi denetlemek için daha güvenli bir yoldur. Daha fazla bilgi için bkz. [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#30)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#30)]

3. <xref:System.Windows.Forms.DataGridView> ve <xref:System.Windows.Forms.BindingSource> başlatan ve veri bağlamayı ayarlayan formunuzun <xref:System.Windows.Forms.Form.Load> olayı için bir işleyici uygulayın.

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#10)]

4. <xref:System.Windows.Forms.DataGridView> denetiminin <xref:System.Windows.Forms.DataGridView.CellValidating> ve <xref:System.Windows.Forms.DataGridView.CellEndEdit> olayları için işleyicileri uygulayın.

    <xref:System.Windows.Forms.DataGridView.CellValidating> olay işleyicisi, `CompanyName` sütunundaki bir hücrenin değerinin boş olup olmadığını belirlediğiniz yerdir. Hücre değeri doğrulanamazsa, <xref:System.Windows.Forms.DataGridViewCellValidatingEventArgs?displayProperty=nameWithType> sınıfının <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> özelliğini `true`olarak ayarlayın. Bu, <xref:System.Windows.Forms.DataGridView> denetiminin hücreden ayrılmasını engellemesine neden olur. Satırdaki <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> özelliğini açıklayıcı bir dizeye ayarlayın. Bu, hata metnini içeren bir araç Ipucuyla birlikte bir hata simgesi görüntüler. <xref:System.Windows.Forms.DataGridView.CellEndEdit> olay işleyicisinde, satırdaki <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> özelliğini boş dizeye ayarlayın. <xref:System.Windows.Forms.DataGridView.CellEndEdit> olay, yalnızca hücre düzenleme modundan çıktığında oluşur, bu durum doğrulamanın başarısız olması durumunda gerçekleştirilemez.

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#20)]

## <a name="testing-the-application"></a>Uygulamayı Test Etme

Artık, beklenen şekilde davrandığından emin olmak için formu test edebilirsiniz.

#### <a name="to-test-the-form"></a>Formu test etmek için

- Uygulamayı derleyin ve çalıştırın.

  `Customers` tablosundan verilerle doldurulmuş bir <xref:System.Windows.Forms.DataGridView> görürsünüz. `CompanyName` sütununda bir hücreyi çift tıklattığınızda, değeri düzenleyebilirsiniz. Tüm karakterleri siler ve hücreden çıkmak için TAB tuşuna ulaşırsanız <xref:System.Windows.Forms.DataGridView>, çıkış yapmanız önlenir. Hücreye boş olmayan bir dize yazdığınızda, <xref:System.Windows.Forms.DataGridView> denetimi hücreden çıkmanıza olanak sağlar.

## <a name="next-steps"></a>Sonraki Adımlar

Bu uygulama, <xref:System.Windows.Forms.DataGridView> denetimin yeteneklerini temel olarak öğrenmenizi sağlar. <xref:System.Windows.Forms.DataGridView> denetiminin görünümünü ve davranışını çeşitli yollarla özelleştirebilirsiniz:

- Kenarlık ve başlık stillerini değiştirin. Daha fazla bilgi için, bkz. [nasıl yapılır: Windows Forms DataGridView Denetimindeki sınır ve kılavuz çizgisi stillerini değiştirme](change-the-border-and-gridline-styles-in-the-datagrid.md).

- <xref:System.Windows.Forms.DataGridView> denetimine Kullanıcı girişini etkinleştirin veya kısıtlayın. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms DataGridView denetiminde satır eklemeyi ve silmeyi engelleme](prevent-row-addition-and-deletion-datagridview.md)ve [Windows Forms DataGridView denetiminde sütunları salt okuma yapma](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).

- Veritabanıyla ilgili hatalar için Kullanıcı girişini denetleyin. Daha fazla bilgi için bkz. [Izlenecek yol: Windows Forms DataGridView Denetimindeki veri girişi sırasında oluşan hataları işleme](handling-errors-that-occur-during-data-entry-in-the-datagrid.md).

- Sanal modu kullanarak çok büyük veri kümelerini işleyin. Daha fazla bilgi için bkz. [Izlenecek yol: Windows Forms DataGridView denetiminde sanal mod uygulama](implementing-virtual-mode-wf-datagridview-control.md).

- Hücrelerin görünümünü özelleştirin. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms DataGridView Denetimindeki hücrelerin görünümünü özelleştirme](customize-the-appearance-of-cells-in-the-datagrid.md) ve [Windows Forms DataGridView denetiminde yazı tipi ve renk stillerini ayarlama](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Windows Forms DataGridView Denetiminde Veri Girişi](data-entry-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Denetiminde Verileri Doğrulama](how-to-validate-data-in-the-windows-forms-datagridview-control.md)
- [İzlenecek yol: Windows Forms DataGridView Denetimine Veri Girişi Sırasında Oluşan Hataları Ele Alma](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Bağlantı Bilgilerini Koruma](../../data/adonet/protecting-connection-information.md)
