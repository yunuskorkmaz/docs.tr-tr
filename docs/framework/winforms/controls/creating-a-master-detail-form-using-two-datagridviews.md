---
title: 'İzlenecek yol: Iki Windows Forms DataGridView denetimi kullanarak ana ayrıntı formu oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], displaying on Windows Forms
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: c5fa29e8-47f7-4691-829b-0e697a691f36
ms.openlocfilehash: 4212c7223aca6a5e7de3189d5f6b2757453cc438
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046089"
---
# <a name="walkthrough-creating-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>İzlenecek yol: İki Windows Forms DataGridView Denetimi Kullanarak Ana/Ayrıntı Formu Oluşturma

<xref:System.Windows.Forms.DataGridView> Denetimi kullanmanın en yaygın senaryolarından biri, iki veritabanı tablosu arasındaki üst/alt ilişkinin görüntülendiği *ana/ayrıntı* formundadır. Ana tablodaki satırları seçmek ayrıntı tablosunun karşılık gelen alt verilerle güncelleştirilmesini sağlar.

Ana/ayrıntı formunun uygulanması, <xref:System.Windows.Forms.DataGridView> denetim <xref:System.Windows.Forms.BindingSource> ve bileşen arasındaki etkileşim kullanılarak kolayca yapılır. Bu kılavuzda, iki <xref:System.Windows.Forms.DataGridView> denetimi ve iki <xref:System.Windows.Forms.BindingSource> bileşeni kullanarak formu oluşturacaksınız. Form, Northwind SQL Server örnek veritabanında bulunan iki ilişkili tabloyu gösterir: `Customers` ve. `Orders` İşiniz bittiğinde, ana <xref:System.Windows.Forms.DataGridView> formdaki veritabanındaki tüm müşterileri ve seçilen müşteri için tüm siparişleri ayrıntılı <xref:System.Windows.Forms.DataGridView>olarak gösteren bir formunuza sahip olursunuz.

Bu konudaki kodu tek bir liste olarak kopyalamak için bkz [. nasıl yapılır: Iki Windows Forms DataGridView denetimi](create-a-master-detail-form-using-two-datagridviews.md)kullanarak ana/ayrıntı formu oluşturun.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için şunlar gerekir:

- Northwind SQL Server örnek veritabanına sahip bir sunucuya erişim.

## <a name="creating-the-form"></a>Formu oluşturma

#### <a name="to-create-a-masterdetail-form"></a>Ana/ayrıntı formu oluşturmak için

1. Öğesinden <xref:System.Windows.Forms.Form> türetilen ve iki <xref:System.Windows.Forms.DataGridView> denetim ve iki <xref:System.Windows.Forms.BindingSource> bileşen içeren bir sınıf oluşturun. Aşağıdaki kod temel form başlatması sağlar ve bir `Main` yöntemi içerir. Formunuzu oluşturmak için Visual Studio tasarımcısını kullanırsanız, bu kod yerine tasarımcı tarafından oluşturulan kodu kullanabilirsiniz, ancak burada değişken bildirimlerinde gösterilen adları kullandığınızdan emin olun.

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#02)]

2. Veritabanına bağlanma ayrıntılarını işlemek için formunuzun sınıf tanımına bir yöntem uygulayın. Bu örnek, bir `GetData` <xref:System.Data.DataSet> nesneyi dolduran bir yöntemi kullanır, veri kümesine <xref:System.Data.DataRelation> bir nesne ekler ve <xref:System.Windows.Forms.BindingSource> bileşenleri bağlar. Değişkeni, `connectionString` veritabanınız için uygun bir değere ayarladığınızdan emin olun.

    > [!IMPORTANT]
    > Parola gibi hassas bilgileri, bağlantı dizesi içinde depolamak, uygulamanızın güvenliğini etkileyebilir. Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur. Daha fazla bilgi için bkz. [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#20)]

3. Formunuza <xref:System.Windows.Forms.Form.Load> <xref:System.Windows.Forms.DataGridView> `GetData` denetimleri bileşenlerebağlayanveyöntemiçağıranformunuzunolayıiçinbirişleyiciuygulayın.<xref:System.Windows.Forms.BindingSource> Aşağıdaki örnek, sütunları görüntülenen verilere sığacak <xref:System.Windows.Forms.DataGridView> şekilde yeniden boyutlandırabilecek kodu içerir.

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#10)]

## <a name="testing-the-application"></a>Uygulamayı Test Etme

Artık, beklenen şekilde davrandığından emin olmak için formu test edebilirsiniz.

#### <a name="to-test-the-form"></a>Formu test etmek için

- Uygulamayı derleyin ve çalıştırın.

  Diğeri üzerinde bir tane <xref:System.Windows.Forms.DataGridView> olmak üzere iki denetim görürsünüz. En üstte, Northwind `Customers` tablosundaki müşteriler, en altta `Orders` ise seçilen müşteriye karşılık gelir. Üstteki <xref:System.Windows.Forms.DataGridView>farklı satırları seçerken, daha düşük <xref:System.Windows.Forms.DataGridView> değişikliğin içerikleri buna göre değişir.

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
- [Windows Forms DataGridView Denetiminde Verileri Görüntüleme](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Iki Windows Forms DataGridView denetimi kullanarak ana/ayrıntı formu oluşturma](create-a-master-detail-form-using-two-datagridviews.md)
- [Bağlantı Bilgilerini Koruma](../../data/adonet/protecting-connection-information.md)
