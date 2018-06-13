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
ms.openlocfilehash: 92525d1818160f5645b95948910547c7d1541897
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529240"
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a>İzlenecek yol: Windows Forms DataGridView Denetimine Veri Girişi Sırasında Oluşan Hataları Ele Alma
Temel alınan veri deposundan hataları işleme, veri girişi uygulama için gerekli bir özelliktir. Windows Forms <xref:System.Windows.Forms.DataGridView> denetim kolaylaştırır bu göstererek <xref:System.Windows.Forms.DataGridView.DataError> veri deposunda bir kısıtlama ihlali veya bozuk iş kuralı algıladığında oluşan olayı,.  
  
 Bu kılavuzda, satırları alacak `Customers` tablo Northwind örnek veritabanında ve bunları görüntülemek bir <xref:System.Windows.Forms.DataGridView> denetim. Yinelenen zaman `CustomerID` değeri, yeni bir satır veya düzenlenen varolan bir satır, algılandığında <xref:System.Windows.Forms.DataGridView.DataError> olay gerçekleşeceği, hangi görüntüleyerek işlenecek bir <xref:System.Windows.Forms.MessageBox> özel durumu açıklayan.  
  
 Bu konuda tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: işlemek hatalar olduğunu ortaya sırasında veri girişi Windows Forms DataGridView denetiminde](../../../../docs/framework/winforms/controls/handle-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu kılavuzu tamamlamak için gerekir:  
  
-   Northwind SQL Server örnek veritabanı olan bir sunucuya erişim.  
  
## <a name="creating-the-form"></a>Form Oluşturma  
  
#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a>DataGridView denetimindeki veri girişi sırasında oluşan hataları işlemek için  
  
1.  Türeyen bir sınıf oluşturun <xref:System.Windows.Forms.Form> ve içeren bir <xref:System.Windows.Forms.DataGridView> denetim ve <xref:System.Windows.Forms.BindingSource> bileşeni.  
  
     Aşağıdaki kod örneğinde temel başlatma sağlar ve içeren bir `Main` yöntemi.  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]  
  
2.  Veritabanına bağlanırken ayrıntılarını işlemek için formun sınıf tanımında yöntemi uygulayabilirsiniz.  
  
     Bu kod örneği kullanan bir `GetData` doldurulan bir döndüren yöntem <xref:System.Data.DataTable> nesnesi. Ayarladığınız mutlaka `connectionString` değişken veritabanınız için uygun olan bir değer.  
  
    > [!IMPORTANT]
    >  Bağlantı dizesindeki bir parola gibi hassas bilgileri depolamak, uygulamanızın güvenliğini etkileyebilir. Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur. Daha fazla bilgi için bkz: [koruma bağlantı bilgilerini](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]  
  
3.  Form için bir işleyici uygulamak <xref:System.Windows.Forms.Form.Load> başlatır olay <xref:System.Windows.Forms.DataGridView> ve <xref:System.Windows.Forms.BindingSource> ve veri bağlamanın ayarlar.  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]  
  
4.  İşleme <xref:System.Windows.Forms.DataGridView.DataError> olayı <xref:System.Windows.Forms.DataGridView>.  
  
     Bağlamın hata için bir kaydetme işlemi ise, hatayı görüntüler bir <xref:System.Windows.Forms.MessageBox>.  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]  
  
## <a name="testing-the-application"></a>Uygulamayı Test Etme  
 Artık formun beklendiği gibi davranır emin olmak için test edebilirsiniz.  
  
#### <a name="to-test-the-form"></a>Formu sınamak için  
  
-   Uygulamayı çalıştırmak için F5 tuşuna basın.  
  
     Göreceğiniz bir <xref:System.Windows.Forms.DataGridView> denetim doldurulmuş Müşteriler tablosundan gelen verilerle. İçin yinelenen bir değer girerseniz, `CustomerID` ve düzenleme yürütme, hücre değeri otomatik olarak döner ve görürsünüz bir <xref:System.Windows.Forms.MessageBox> veri girişi hatasını görüntüler.  
  
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
 [Windows Forms DataGridView Denetiminde Veri Girişi](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [Nasıl yapılır: Windows Forms DataGridView Denetimine Veri Girişi Sırasında Oluşan Hataları Ele Alma](../../../../docs/framework/winforms/controls/handle-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 [İzlenecek yol: Windows Forms DataGridView Denetiminde Verileri Doğrulama](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)  
 [Bağlantı Bilgilerini Koruma](../../../../docs/framework/data/adonet/protecting-connection-information.md)
