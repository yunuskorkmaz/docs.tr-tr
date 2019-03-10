---
title: 'İzlenecek yol: İki Windows Forms DataGridView denetimi kullanarak ana öğe-ayrıntı formu oluşturma'
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
ms.openlocfilehash: 80ec480b5d45a338c1f15796ae82015d6da24fc9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705538"
---
# <a name="walkthrough-creating-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>İzlenecek yol: İki Windows Forms DataGridView denetimi kullanarak ana/ayrıntı formu oluşturma
Kullanmak için en sık karşılaşılan senaryolardan biri, <xref:System.Windows.Forms.DataGridView> denetimi *ana/ayrıntı* form, iki veritabanı tabloları arasında bir üst/alt ilişkisi görüntülenir. Ana tablodaki satırları seçme ile ilgili alt verileri güncelleştirmek ayrıntı tablosunu neden olur.  
  
 Ana/ayrıntı formu uygulama arasındaki etkileşim kullanarak kolay <xref:System.Windows.Forms.DataGridView> denetimi ve <xref:System.Windows.Forms.BindingSource> bileşeni. Bu kılavuzda, iki kullanarak form oluşturacak <xref:System.Windows.Forms.DataGridView> kontrol eder ve iki <xref:System.Windows.Forms.BindingSource> bileşenleri. Forma iki ilgili SQL Server Northwind örnek veritabanındaki tablolar göster: `Customers` ve `Orders`. İşlemi tamamladığınızda, ana veritabanındaki tüm müşterileri gösteren bir biçimde olacaktır <xref:System.Windows.Forms.DataGridView> ve ayrıntılı Seçilen müşteri için tüm siparişleri <xref:System.Windows.Forms.DataGridView>.  
  
 Bu konudaki tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: İki Windows Forms DataGridView denetimi kullanarak ana/ayrıntı formu oluşturma](create-a-master-detail-form-using-two-datagridviews.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için şunlar gerekir:  
  
-   SQL Server Northwind örnek veritabanını bir sunucu erişim.  
  
## <a name="creating-the-form"></a>Form oluşturma  
  
#### <a name="to-create-a-masterdetail-form"></a>Ana/ayrıntı formu oluşturma  
  
1.  Türetilen bir sınıf oluşturmanız <xref:System.Windows.Forms.Form> ve iki tane <xref:System.Windows.Forms.DataGridView> kontrol eder ve iki <xref:System.Windows.Forms.BindingSource> bileşenleri. Aşağıdaki kod temel biçimi başlatma sağlar ve içeren bir `Main` yöntemi. Formunuza oluşturmak için Visual Studio Tasarımcısı'nı kullanın, Tasarımcı oluşturulan kod kullanmak yerine bu kod, ancak burada değişken bildirimlerinde gösterilen adları kullandığınızdan emin olun.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#02)]  
  
2.  Veritabanına bağlanma ayrıntılı işleme için form denetiminin sınıf tanımında bir yöntem uygulayın. Bu örnekte bir `GetData` dolduran yöntemi bir <xref:System.Data.DataSet> nesne, ekler bir <xref:System.Data.DataRelation> nesnesine bağlar ve veri kümesi <xref:System.Windows.Forms.BindingSource> bileşenleri. Ayarladığınızdan emin olun `connectionString` değişken veritabanınız için uygun olan bir değer.  
  
    > [!IMPORTANT]
    >  Depolama bağlantı dizesi içinde bir parola gibi hassas bilgileri, uygulamanızın güvenliğini etkileyebilir. Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur. Daha fazla bilgi için [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#20)]  
  
3.  Form için bir işleyici uygulamak <xref:System.Windows.Forms.Form.Load> bağlayan olay <xref:System.Windows.Forms.DataGridView> için denetimleri <xref:System.Windows.Forms.BindingSource> bileşenleri ve çağrıları `GetData` yöntemi. Aşağıdaki örnek yeniden boyutlandırır kodu içerir <xref:System.Windows.Forms.DataGridView> görüntülenen verileri sığmayacak sütun.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#10)]  
  
## <a name="testing-the-application"></a>Uygulamayı Test Etme  
 Şimdi beklendiği gibi davrandığından emin olmak için form test edebilirsiniz.  
  
#### <a name="to-test-the-form"></a>Formu sınamak için  
  
-   Derleme ve uygulamayı çalıştırın.  
  
     İki göreceğiniz <xref:System.Windows.Forms.DataGridView> denetimleri, biri diğerinin. Northwind müşterileri üsttedir `Customers` tablosuna sağ tıklayıp altındaki olan `Orders` ise seçili müşterilerle ilgili. Üst farklı satırlar seçerken <xref:System.Windows.Forms.DataGridView>, alt içeriğini <xref:System.Windows.Forms.DataGridView> buna göre değişir.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu uygulamayı size temel bir anlayış <xref:System.Windows.Forms.DataGridView> denetimin özellikleri. Görünümünü ve davranışını özelleştirebilirsiniz <xref:System.Windows.Forms.DataGridView> çeşitli şekillerde denetimi:  
  
-   Kenarlık ve üstbilgi stilleri değiştirin. Daha fazla bilgi için [nasıl yapılır: Değiştirme kenarlık ve kılavuz çizgi stillerini Windows Forms DataGridView denetiminde](change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
-   Etkinleştirmek veya kısıtlamak için kullanıcı girişi <xref:System.Windows.Forms.DataGridView> denetimi. Daha fazla bilgi için [nasıl yapılır: Önlemek satır eklemeyi ve silmeyi Windows Forms DataGridView denetiminde](prevent-row-addition-and-deletion-datagridview.md), ve [nasıl yapılır: Sütunları yapma salt okunur Windows Forms DataGridView denetiminde](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
-   Kullanıcı girişini doğrulama <xref:System.Windows.Forms.DataGridView> denetimi. Daha fazla bilgi için [izlenecek yol: Doğrulama verileri Windows Forms DataGridView denetiminde](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
-   Çok büyük veri kümeleri ile sanal modu kullanarak işleyin. Daha fazla bilgi için [izlenecek yol: Sanal modu uygulama içinde Windows Forms DataGridView denetiminde](implementing-virtual-mode-wf-datagridview-control.md).  
  
-   Hücrelerin görünüşünü özelleştirme. Daha fazla bilgi için [nasıl yapılır: Windows Forms DataGridView denetiminde hücrelerin görünüşünü özelleştirme](customize-the-appearance-of-cells-in-the-datagrid.md) ve [nasıl yapılır: Windows Forms DataGridView denetimi için varsayılan hücre stillerini ayarlama](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Windows Forms DataGridView Denetiminde Verileri Görüntüleme](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: İki Windows Forms DataGridView denetimi kullanarak ana/ayrıntı formu oluşturma](create-a-master-detail-form-using-two-datagridviews.md)
- [Bağlantı Bilgilerini Koruma](../../data/adonet/protecting-connection-information.md)
