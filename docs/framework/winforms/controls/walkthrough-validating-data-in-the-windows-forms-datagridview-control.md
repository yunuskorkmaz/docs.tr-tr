---
title: 'İzlenecek yol: Windows Forms DataGridView Denetimindeki Verileri Doğrulama'
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
ms.openlocfilehash: 89569feb0cb741f56d09f4e58154b4eecb5a89d4
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046375"
---
# <a name="walkthrough-validating-data-in-the-windows-forms-datagridview-control"></a>İzlenecek yol: Windows Forms DataGridView Denetimindeki Verileri Doğrulama

Kullanıcılara veri girişi işlevlerini görüntülediğinizde, formunuza girilen verileri sıkça doğrulamanız gerekir. <xref:System.Windows.Forms.DataGridView> Sınıfı, veriler veri deposuna kaydedilmeden önce doğrulama gerçekleştirmek için kullanışlı bir yol sağlar. Geçerli hücre değiştiğinde <xref:System.Windows.Forms.DataGridView.CellValidating> <xref:System.Windows.Forms.DataGridView> tarafından oluşturulan olayı işleyerek verileri doğrulayabilirsiniz.

Bu izlenecek yolda, Northwind örnek veritabanındaki `Customers` tablodan satırları alacak ve bunları bir <xref:System.Windows.Forms.DataGridView> denetimde görüntüleriz. Bir Kullanıcı `CompanyName` sütundaki bir hücreyi düzenler ve hücreden ayrılmaya çalışırsa <xref:System.Windows.Forms.DataGridView.CellValidating> , olay işleyicisi boş olmadığından emin olmak için yeni şirket adı dizesini inceler; yeni değer boş <xref:System.Windows.Forms.DataGridView> bir dizeyse, kullanıcının imlece engel olur boş olmayan bir dize girilene kadar hücreden ayrılmaya.

Bu konudaki kodu tek bir liste olarak kopyalamak için bkz [. nasıl yapılır: Windows Forms DataGridView Denetimindeki](how-to-validate-data-in-the-windows-forms-datagridview-control.md)verileri doğrulayın.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için şunlar gerekir:

- Northwind SQL Server örnek veritabanına sahip bir sunucuya erişim.

## <a name="creating-the-form"></a>Form Oluşturma

#### <a name="to-validate-data-entered-in-a-datagridview"></a>DataGridView içinde girilen verileri doğrulamak için

1. Öğesinden <xref:System.Windows.Forms.Form> türetilen ve bir <xref:System.Windows.Forms.DataGridView> denetim ve <xref:System.Windows.Forms.BindingSource> bileşen içeren bir sınıf oluşturun.

    Aşağıdaki kod örneği temel başlatma sağlar ve bir `Main` yöntemi içerir.

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#02)]

2. Veritabanına bağlanma ayrıntılarını işlemek için formunuzun sınıf tanımına bir yöntem uygulayın.

    Bu kod örneği, doldurulmuş `GetData` <xref:System.Data.DataTable> bir nesne döndüren bir yöntemi kullanır. Değişkeni, `connectionString` veritabanınız için uygun bir değere ayarladığınızdan emin olun.

    > [!IMPORTANT]
    > Parola gibi hassas bilgileri, bağlantı dizesi içinde depolamak, uygulamanızın güvenliğini etkileyebilir. Tümleşik güvenlik olarak da bilinen Windows kimlik doğrulaması kullanmak, bir veritabanına erişimi denetlemek için daha güvenli bir yoldur. Daha fazla bilgi için bkz. [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#30)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#30)]

3. <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.Form.Load> Ve<xref:System.Windows.Forms.BindingSource> ' i başlatan ve veri bağlamayı ayarlayan formunuzun olayı için bir işleyici uygulayın.

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#10)]

4. <xref:System.Windows.Forms.DataGridView> Denetim ve Olaylar<xref:System.Windows.Forms.DataGridView.CellEndEdit> için işleyicileri uygulayın. <xref:System.Windows.Forms.DataGridView.CellValidating>

    Olay işleyicisi, `CompanyName` sütundaki bir hücrenin değerinin boş olup olmadığını belirlediğiniz yerdir. <xref:System.Windows.Forms.DataGridView.CellValidating> Hücre değeri doğrulama başarısız olursa, <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> <xref:System.Windows.Forms.DataGridViewCellValidatingEventArgs?displayProperty=nameWithType> sınıfının özelliğini olarak `true`ayarlayın. Bu, <xref:System.Windows.Forms.DataGridView> denetimin hücreden ayrılmasını engellemesine neden olur. <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> Satırdaki özelliğini açıklayıcı bir dizeye ayarlayın. Bu, hata metnini içeren bir araç Ipucuyla birlikte bir hata simgesi görüntüler. Olay işleyicisinde, satırdaki <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> özelliğini boş dizeye ayarlayın. <xref:System.Windows.Forms.DataGridView.CellEndEdit> <xref:System.Windows.Forms.DataGridView.CellEndEdit> Olay, yalnızca hücre düzenleme modundan çıktığında oluşur ve doğrulama başarısız olursa bunu yapamazlar.

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#20)]

## <a name="testing-the-application"></a>Uygulamayı Test Etme

Artık, beklenen şekilde davrandığından emin olmak için formu test edebilirsiniz.

#### <a name="to-test-the-form"></a>Formu test etmek için

- Uygulamayı derleyin ve çalıştırın.

  Tablodaki`Customers` verileri <xref:System.Windows.Forms.DataGridView> doldurulmuş olarak görürsünüz. `CompanyName` Sütundaki bir hücreyi çift tıklattığınızda, değeri düzenleyebilirsiniz. Tüm karakterleri siler ve hücreden çıkmak için Tab tuşuna ulaşırsanız, <xref:System.Windows.Forms.DataGridView> çıkış yapmanız önlenir. Hücreye boş olmayan bir dize yazdığınızda <xref:System.Windows.Forms.DataGridView> denetim, hücreden çıkmanıza izin verir.

## <a name="next-steps"></a>Sonraki Adımlar

Bu uygulama, <xref:System.Windows.Forms.DataGridView> denetimin yeteneklerini temel olarak öğrenmenizi sağlar. <xref:System.Windows.Forms.DataGridView> Denetimin görünümünü ve davranışını çeşitli yollarla özelleştirebilirsiniz:

- Kenarlık ve başlık stillerini değiştirin. Daha fazla bilgi için [nasıl yapılır: Windows Forms DataGridView Denetimindeki](change-the-border-and-gridline-styles-in-the-datagrid.md)kenarlık ve kılavuz çizgisi stillerini değiştirin.

- <xref:System.Windows.Forms.DataGridView> Denetim için Kullanıcı girişini etkinleştirin veya kısıtlayın. Daha fazla bilgi için [nasıl yapılır: Windows Forms DataGridView denetiminde](prevent-row-addition-and-deletion-datagridview.md)satır eklemeyi ve silmeyi önleyin ve [şunları yapın: Sütunları Windows Forms DataGridView denetiminde](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)salt okunurdur.

- Veritabanıyla ilgili hatalar için Kullanıcı girişini denetleyin. Daha fazla bilgi için bkz [. İzlenecek yol: Windows Forms DataGridView Denetimindeki](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)veri girişi sırasında oluşan hataları işleme.

- Sanal modu kullanarak çok büyük veri kümelerini işleyin. Daha fazla bilgi için bkz [. İzlenecek yol: Windows Forms DataGridView denetiminde](implementing-virtual-mode-wf-datagridview-control.md)sanal mod uygulama.

- Hücrelerin görünümünü özelleştirin. Daha fazla bilgi için [nasıl yapılır: Windows Forms DataGridView Denetimindeki](customize-the-appearance-of-cells-in-the-datagrid.md) hücrelerin görünümünü özelleştirin ve [şunları yapın: Windows Forms DataGridView denetiminde](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)yazı tipi ve renk stillerini ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Windows Forms DataGridView Denetiminde Veri Girişi](data-entry-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Denetimindeki verileri doğrulama](how-to-validate-data-in-the-windows-forms-datagridview-control.md)
- [İzlenecek yol: Windows Forms DataGridView Denetimindeki veri girişi sırasında oluşan hataları işleme](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Bağlantı Bilgilerini Koruma](../../data/adonet/protecting-connection-information.md)
