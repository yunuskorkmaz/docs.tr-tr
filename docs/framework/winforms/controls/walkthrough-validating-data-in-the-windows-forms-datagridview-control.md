---
title: 'İzlenecek yol: Windows Forms DataGridView Denetiminde Verileri Doğrulama'
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
ms.openlocfilehash: 8ad8caef5db13b1f917a6c27da523d3ded915d84
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540969"
---
# <a name="walkthrough-validating-data-in-the-windows-forms-datagridview-control"></a>İzlenecek yol: Windows Forms DataGridView Denetiminde Verileri Doğrulama
Kullanıcılara veri girişi işlevlerini görüntülediğinizde, sık formunuza girilen veri doğrulama gerekir. <xref:System.Windows.Forms.DataGridView> Sınıfı verileri veri deposuna yürütülmeden önce doğrulama gerçekleştirmek için kullanışlı bir yöntem sağlar. İşleyerek veri doğrulama <xref:System.Windows.Forms.DataGridView.CellValidating> tarafından gerçekleştirilen olay <xref:System.Windows.Forms.DataGridView> geçerli hücreyi değiştiğinde.  
  
 Bu kılavuzda, satırları alacak `Customers` tablo Northwind örnek veritabanında ve bunları görüntülemek bir <xref:System.Windows.Forms.DataGridView> denetim. Kullanıcının bir hücreye zaman düzenlediğini `CompanyName` sütun ve hücre bırakın denediğinde <xref:System.Windows.Forms.DataGridView.CellValidating> olay işleyicisi boş değil; yeni değer boş bir dize ise olduğundan emin olmak için yeni şirket adı dizesi inceleyin <xref:System.Windows.Forms.DataGridView> kullanıcının imleç engeller boş olmayan bir dize girilene kadar hücre bırakmasını.  
  
 Bu konuda tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: Windows Forms DataGridView denetiminde verileri doğrulama](../../../../docs/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu kılavuzu tamamlamak için gerekir:  
  
-   Northwind SQL Server örnek veritabanı olan bir sunucuya erişim.  
  
## <a name="creating-the-form"></a>Form Oluşturma  
  
#### <a name="to-validate-data-entered-in-a-datagridview"></a>Bir DataGridView girilen verileri doğrulamak için  
  
1.  Türeyen bir sınıf oluşturun <xref:System.Windows.Forms.Form> ve içeren bir <xref:System.Windows.Forms.DataGridView> denetim ve <xref:System.Windows.Forms.BindingSource> bileşeni.  
  
     Aşağıdaki kod örneğinde temel başlatma sağlar ve içeren bir `Main` yöntemi.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#02)]  
  
2.  Veritabanına bağlanırken ayrıntılarını işlemek için formun sınıf tanımında yöntemi uygulayabilirsiniz.  
  
     Bu kod örneği kullanan bir `GetData` doldurulan bir döndüren yöntem <xref:System.Data.DataTable> nesnesi. Ayarladığınız mutlaka `connectionString` değişken veritabanınız için uygun olan bir değer.  
  
    > [!IMPORTANT]
    >  Bağlantı dizesindeki bir parola gibi hassas bilgileri depolamak, uygulamanızın güvenliğini etkileyebilir. Windows kimlik doğrulaması olarak da bilinen tümleşik güvenlik kullanan bir veritabanına erişimi denetlemek için daha güvenli bir yoludur. Daha fazla bilgi için bkz: [koruma bağlantı bilgilerini](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#30)]  
  
3.  Form için bir işleyici uygulamak <xref:System.Windows.Forms.Form.Load> başlatır olay <xref:System.Windows.Forms.DataGridView> ve <xref:System.Windows.Forms.BindingSource> ve veri bağlamanın ayarlar.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#10)]  
  
4.  Uygulama için işleyiciler <xref:System.Windows.Forms.DataGridView> denetimin <xref:System.Windows.Forms.DataGridView.CellValidating> ve <xref:System.Windows.Forms.DataGridView.CellEndEdit> olaylar.  
  
     <xref:System.Windows.Forms.DataGridView.CellValidating> Olay işleyicisidir burada saptamanıza olup olmadığını bir hücrenin değerini `CompanyName` sütun boştur. Hücre değerini doğrulama başarısız olursa, ayarlamak <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> özelliği <xref:System.Windows.Forms.DataGridViewCellValidatingEventArgs?displayProperty=nameWithType> sınıfının `true`. Bu neden <xref:System.Windows.Forms.DataGridView> imlecin hücre bırakmasını önlemek için denetim. Ayarlama <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> satır için açıklayıcı bir dize özelliği. Bu hata metni içeren bir araç ipucu ile bir hata simgesi görüntüler. İçinde <xref:System.Windows.Forms.DataGridView.CellEndEdit> olay işleyici ayarlamayı <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> boş dize satıra özelliği. <xref:System.Windows.Forms.DataGridView.CellEndEdit> Olayı, yalnızca hücre doğrulama başarısız olursa, bunu yapamayacağı düzenleme modundan çıktığında oluşur.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#20)]  
  
## <a name="testing-the-application"></a>Uygulamayı Test Etme  
 Artık formun beklendiği gibi davranır emin olmak için test edebilirsiniz.  
  
#### <a name="to-test-the-form"></a>Formu sınamak için  
  
-   Derleme ve uygulamayı çalıştırın.  
  
     Göreceğiniz bir <xref:System.Windows.Forms.DataGridView> verilerle doldurulur `Customers` tablo. Çift tıkladığınızda bir hücreye `CompanyName` sütun değeri düzenleyebilirsiniz. Tüm karakterleri silerseniz ve hücre çıkmak için SEKME tuşuna basın <xref:System.Windows.Forms.DataGridView> çıkmasını engeller. Boş olmayan bir dize hücreye yazarken <xref:System.Windows.Forms.DataGridView> denetim hücre çıkmak olanak sağlar.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu uygulama, temel bir anlayış sağlar <xref:System.Windows.Forms.DataGridView> denetimin özellikleri. Görünümünü ve davranışını özelleştirebilirsiniz <xref:System.Windows.Forms.DataGridView> çeşitli şekillerde denetimi:  
  
-   Kenarlık ve üstbilgi stilleri değiştirin. Daha fazla bilgi için bkz: [nasıl yapılır: kenarlık ve kılavuz çizgisi stilleri Windows Forms DataGridView denetiminde değiştirme](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
-   Etkinleştirmek veya kullanıcı girişini kısıtlamak <xref:System.Windows.Forms.DataGridView> denetim. Daha fazla bilgi için bkz: [nasıl yapılır: önlemek satır ekleme ve silme Windows Forms DataGridView denetiminde](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md), ve [nasıl yapılır: Windows Forms DataGridView denetiminde sütunları salt okunur hale](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
-   Kullanıcı girişi veritabanı ile ilgili hataları denetleyin. Daha fazla bilgi için bkz: [izlenecek yol: Windows Forms DataGridView denetimine veri girişi sırasında bu Occur hataları işleme](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
-   Sanal mod kullanarak çok büyük veri kümeleri işleyin. Daha fazla bilgi için bkz: [izlenecek yol: Windows Forms DataGridView denetiminde sanal modu uygulama](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
-   Hücrelerin görünüşünü özelleştirme. Daha fazla bilgi için bkz: [nasıl yapılır: görünümü hücre Windows Forms DataGridView denetiminde özelleştirme](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md) ve [nasıl yapılır: ayarlama yazı tipi ve renk stillerini Windows Forms DataGridView denetiminde](../../../../docs/framework/winforms/controls/how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [Windows Forms DataGridView Denetiminde Veri Girişi](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [Nasıl yapılır: Windows Forms DataGridView Denetiminde Verileri Doğrulama](../../../../docs/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control.md)  
 [İzlenecek yol: Windows Forms DataGridView Denetimine Veri Girişi Sırasında Oluşan Hataları Ele Alma](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 [Bağlantı Bilgilerini Koruma](../../../../docs/framework/data/adonet/protecting-connection-information.md)
