---
title: 'İzlenecek yol: İki Windows Forms DataGridView denetimi kullanarak ana / ayrıntı formu oluşturma'
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
ms.openlocfilehash: 38f7c6197fb3ee79119e41ab9620bc3aa2b21900
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-creating-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>İzlenecek yol: İki Windows Forms DataGridView Denetimi Kullanarak Ana/Ayrıntı Formu Oluşturma
Kullanmak için en sık karşılaşılan senaryolardan biri, <xref:System.Windows.Forms.DataGridView> denetimi *ana/ayrıntı* form, iki veritabanı tabloları arasında bir üst/alt ilişkisi görüntülenir. Ana tablodaki satırları seçmek ayrıntı tablosunda karşılık gelen alt verilerle güncelleştirmeye neden olur.  
  
 Ana/ayrıntı formu uygulama arasındaki etkileşimi kullanarak kolay <xref:System.Windows.Forms.DataGridView> denetim ve <xref:System.Windows.Forms.BindingSource> bileşeni. Bu kılavuzda, iki kullanarak form oluşturacak <xref:System.Windows.Forms.DataGridView> denetimleri ve iki <xref:System.Windows.Forms.BindingSource> bileşenleri. Form iki ilişkili Northwind SQL Server örnek veritabanındaki tablolarda gösterecektir: `Customers` ve `Orders`. İşiniz bittiğinde, ana veritabanındaki tüm müşteriler gösteren bir form olacaktır <xref:System.Windows.Forms.DataGridView> ve ayrıntılı seçili müşteri için tüm siparişleri <xref:System.Windows.Forms.DataGridView>.  
  
 Bu konuda tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: bir ana öğe/ayrıntı formu kullanarak iki Windows Forms DataGridView denetimi oluşturma](../../../../docs/framework/winforms/controls/create-a-master-detail-form-using-two-datagridviews.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu kılavuzu tamamlamak için gerekir:  
  
-   Northwind SQL Server örnek veritabanı olan bir sunucuya erişim.  
  
## <a name="creating-the-form"></a>Form oluşturma  
  
#### <a name="to-create-a-masterdetail-form"></a>Ana/ayrıntı formu oluşturmak için  
  
1.  Türeyen bir sınıf oluşturun <xref:System.Windows.Forms.Form> ve iki içeren <xref:System.Windows.Forms.DataGridView> denetimleri ve iki <xref:System.Windows.Forms.BindingSource> bileşenleri. Aşağıdaki kod temel form başlatma sağlar ve içeren bir `Main` yöntemi. Formunuzu oluşturmak için Visual Studio designer kullanırsanız, Tasarımcı oluşturulan kod yerine bu kodu kullanın, ancak burada değişken bildirimleri gösterilen adları kullandığınızdan emin olun.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#02)]  
  
2.  Veritabanına bağlanmak için ayrıntı işlemek için formun sınıf tanımında yöntemi uygulayabilirsiniz. Bu örnekte bir `GetData` doldurur yöntemi bir <xref:System.Data.DataSet> nesne, ekler bir <xref:System.Data.DataRelation> veri kümesi ve bağlamalar nesnesine <xref:System.Windows.Forms.BindingSource> bileşenleri. Ayarladığınızdan emin olun `connectionString` değişken veritabanınız için uygun olan bir değer.  
  
    > [!IMPORTANT]
    >  Bağlantı dizesindeki bir parola gibi hassas bilgileri depolamak, uygulamanızın güvenliğini etkileyebilir. Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur. Daha fazla bilgi için bkz: [koruma bağlantı bilgilerini](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#20)]  
  
3.  Form için bir işleyici uygulamak <xref:System.Windows.Forms.Form.Load> bağlar olay <xref:System.Windows.Forms.DataGridView> için denetimler <xref:System.Windows.Forms.BindingSource> bileşenleri ve çağrıları `GetData` yöntemi. Aşağıdaki örnek, yeniden boyutlandırır kodu içerir <xref:System.Windows.Forms.DataGridView> sütunları görüntülenen verileri sığdırmak için.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#10)]  
  
## <a name="testing-the-application"></a>Uygulamayı Test Etme  
 Artık formun beklendiği gibi davranır emin olmak için test edebilirsiniz.  
  
#### <a name="to-test-the-form"></a>Formu sınamak için  
  
-   Derleme ve uygulamayı çalıştırın.  
  
     İki görürsünüz <xref:System.Windows.Forms.DataGridView> denetimleri, birbirinin üzerine. Northwind müşterilerden üsttedir `Customers` tablo ve en altında olan `Orders` seçili müşteriye karşılık gelen. Üst farklı satırlarla seçerken <xref:System.Windows.Forms.DataGridView>, alt içeriğini <xref:System.Windows.Forms.DataGridView> uygun şekilde değiştirin.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu uygulama, temel bir anlayış sağlar <xref:System.Windows.Forms.DataGridView> denetimin özellikleri. Görünümünü ve davranışını özelleştirebilirsiniz <xref:System.Windows.Forms.DataGridView> çeşitli şekillerde denetimi:  
  
-   Kenarlık ve üstbilgi stilleri değiştirin. Daha fazla bilgi için bkz: [nasıl yapılır: kenarlık ve kılavuz çizgisi stilleri Windows Forms DataGridView denetiminde değiştirme](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
-   Etkinleştirmek veya kullanıcı girişini kısıtlamak <xref:System.Windows.Forms.DataGridView> denetim. Daha fazla bilgi için bkz: [nasıl yapılır: önlemek satır ekleme ve silme Windows Forms DataGridView denetiminde](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md), ve [nasıl yapılır: Windows Forms DataGridView denetiminde sütunları salt okunur hale](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
-   Kullanıcı girişini doğrulama <xref:System.Windows.Forms.DataGridView> denetim. Daha fazla bilgi için bkz: [izlenecek yol: Windows Forms DataGridView denetiminde verileri doğrulama](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
-   Sanal mod kullanarak çok büyük veri kümeleri işleyin. Daha fazla bilgi için bkz: [izlenecek yol: Windows Forms DataGridView denetiminde sanal modu uygulama](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
-   Hücrelerin görünüşünü özelleştirme. Daha fazla bilgi için bkz [nasıl yapılır: görünümü hücre Windows Forms DataGridView denetiminde özelleştirme](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md) ve [nasıl yapılır: ayarlama varsayılan hücre stilleri Windows Forms DataGridView denetimi için](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [Windows Forms DataGridView Denetiminde Verileri Görüntüleme](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Nasıl Yapılır: İki Windows Forms DataGridView Denetimi Kullanarak Ana/Ayrıntı Formu Oluşturma](../../../../docs/framework/winforms/controls/create-a-master-detail-form-using-two-datagridviews.md)  
 [Bağlantı Bilgilerini Koruma](../../../../docs/framework/data/adonet/protecting-connection-information.md)
