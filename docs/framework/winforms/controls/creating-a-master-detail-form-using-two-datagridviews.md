---
title: 'İzlenecek yol: iki DataGridView denetimi kullanarak ana ayrıntı formu oluşturma'
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
ms.openlocfilehash: bb3da36430c7493b941f3711cb584b4517d5bd54
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740577"
---
# <a name="walkthrough-creating-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>İzlenecek yol: İki Windows Forms DataGridView Denetimi Kullanarak Ana/Ayrıntı Formu Oluşturma

<xref:System.Windows.Forms.DataGridView> denetimini kullanmanın en yaygın senaryolarından biri, iki veritabanı tablosu arasındaki üst/alt ilişkinin görüntülendiği *ana/ayrıntı* formundadır. Ana tablodaki satırları seçmek ayrıntı tablosunun karşılık gelen alt verilerle güncelleştirilmesini sağlar.

Ana/ayrıntı formunun uygulanması, <xref:System.Windows.Forms.DataGridView> denetimi ve <xref:System.Windows.Forms.BindingSource> bileşeni arasındaki etkileşim kullanılarak kolayca yapılır. Bu kılavuzda, iki <xref:System.Windows.Forms.DataGridView> denetimi ve iki <xref:System.Windows.Forms.BindingSource> bileşeni kullanarak formu oluşturacaksınız. Form, Northwind SQL Server örnek veritabanında iki ilişkili tablo gösterir: `Customers` ve `Orders`. İşiniz bittiğinde, ana <xref:System.Windows.Forms.DataGridView> veritabanındaki tüm müşterileri ve ayrıntı <xref:System.Windows.Forms.DataGridView>seçilen müşteriye ait tüm siparişleri gösteren bir formunuz olur.

Bu konudaki kodu tek bir liste olarak kopyalamak için, bkz. [nasıl yapılır: iki Windows Forms DataGridView denetimi kullanarak ana/ayrıntı formu oluşturma](create-a-master-detail-form-using-two-datagridviews.md).

## <a name="prerequisites"></a>Prerequisites

Bu izlenecek yolu tamamlamak için şunlar gerekir:

- Northwind SQL Server örnek veritabanına sahip bir sunucuya erişim.

## <a name="creating-the-form"></a>Formu oluşturma

#### <a name="to-create-a-masterdetail-form"></a>Ana/ayrıntı formu oluşturmak için

1. <xref:System.Windows.Forms.Form> türetilen ve iki <xref:System.Windows.Forms.DataGridView> denetimi ve iki <xref:System.Windows.Forms.BindingSource> bileşeni içeren bir sınıf oluşturun. Aşağıdaki kod temel form başlatması sağlar ve bir `Main` yöntemi içerir. Formunuzu oluşturmak için Visual Studio tasarımcısını kullanırsanız, bu kod yerine tasarımcı tarafından oluşturulan kodu kullanabilirsiniz, ancak burada değişken bildirimlerinde gösterilen adları kullandığınızdan emin olun.

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#02)]

2. Veritabanına bağlanma ayrıntılarını işlemek için formunuzun sınıf tanımına bir yöntem uygulayın. Bu örnek, bir <xref:System.Data.DataSet> nesnesini dolduran `GetData` yöntemi kullanır, veri kümesine <xref:System.Data.DataRelation> nesnesi ekler ve <xref:System.Windows.Forms.BindingSource> bileşenleri bağlar. `connectionString` değişkenini veritabanınız için uygun bir değere ayarladığınızdan emin olun.

    > [!IMPORTANT]
    > Parola gibi hassas bilgileri, bağlantı dizesi içinde depolamak, uygulamanızın güvenliğini etkileyebilir. Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur. Daha fazla bilgi için bkz. [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#20)]

3. <xref:System.Windows.Forms.DataGridView> denetimlerini <xref:System.Windows.Forms.BindingSource> bileşenlerine bağlayan ve `GetData` yöntemini çağıran formunuzun <xref:System.Windows.Forms.Form.Load> olayı için bir işleyici uygulayın. Aşağıdaki örnek, <xref:System.Windows.Forms.DataGridView> sütunları görüntülenen verilere sığacak şekilde yeniden boyutlandırabilecek kodu içerir.

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#10)]

## <a name="testing-the-application"></a>Uygulamayı Test Etme

Artık, beklenen şekilde davrandığından emin olmak için formu test edebilirsiniz.

#### <a name="to-test-the-form"></a>Formu test etmek için

- Uygulamayı derleyin ve çalıştırın.

  Diğeri üzerinde bir tane olmak üzere iki <xref:System.Windows.Forms.DataGridView> denetimi göreceksiniz. En üstte, Northwind `Customers` tablosundaki müşteriler, en altta ise seçilen müşteriye karşılık gelen `Orders`. Büyük <xref:System.Windows.Forms.DataGridView>farklı satırları seçerken, alt <xref:System.Windows.Forms.DataGridView> içerikleri buna uygun şekilde değişir.

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
- [Windows Forms DataGridView Denetiminde Verileri Görüntüleme](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Nasıl Yapılır: İki Windows Forms DataGridView Denetimi Kullanarak Ana/Ayrıntı Formu Oluşturma](create-a-master-detail-form-using-two-datagridviews.md)
- [Bağlantı Bilgilerini Koruma](../../data/adonet/protecting-connection-information.md)
