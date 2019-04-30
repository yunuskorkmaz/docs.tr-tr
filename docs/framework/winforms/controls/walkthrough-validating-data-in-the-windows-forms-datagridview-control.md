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
ms.openlocfilehash: a4bf0850b28b7101ba76f1c1fedc6633eccb81a1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61759862"
---
# <a name="walkthrough-validating-data-in-the-windows-forms-datagridview-control"></a>İzlenecek yol: Windows Forms DataGridView Denetimindeki Verileri Doğrulama
Kullanıcılara veri girişi işlevi görüntülediğinizde, sık formunuza girilen verileri doğrulamak gerekir. <xref:System.Windows.Forms.DataGridView> Sınıfı veri deposuna veri gerçekleştirilmeden önce doğrulamayı gerçekleştirmek için kolay bir yol sağlar. Verileri işleyerek doğrulayabilirsiniz <xref:System.Windows.Forms.DataGridView.CellValidating> tarafından oluşan olayı <xref:System.Windows.Forms.DataGridView> geçerli hücreyi değiştiğinde.  
  
 Bu kılavuzda, tablosundan satırları alır `Customers` Northwind örnek veritabanındaki tablo ve bunları görüntüleme bir <xref:System.Windows.Forms.DataGridView> denetimi. Kullanıcının bir hücreye zaman düzenlediğini `CompanyName` sütun ve hücre bırakın denediğinde <xref:System.Windows.Forms.DataGridView.CellValidating> yeni şirket adı dizesi boş değil; yeni değer boş bir dize ise olduğundan emin olmak için olay işleyicisini inceleyin <xref:System.Windows.Forms.DataGridView> kullanıcının imleç engeller Hücre bir boş olmayan dize girilene kadar çıkarılmasını.  
  
 Bu konudaki tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: Windows Forms DataGridView denetiminde verileri doğrulama](how-to-validate-data-in-the-windows-forms-datagridview-control.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için şunlar gerekir:  
  
- SQL Server Northwind örnek veritabanını bir sunucu erişim.  
  
## <a name="creating-the-form"></a>Form Oluşturma  
  
#### <a name="to-validate-data-entered-in-a-datagridview"></a>DataGridView üzerinde girilen verileri doğrulamak için  
  
1. Türetilen bir sınıf oluşturmanız <xref:System.Windows.Forms.Form> ve içeren bir <xref:System.Windows.Forms.DataGridView> denetimi ve bir <xref:System.Windows.Forms.BindingSource> bileşeni.  
  
     Aşağıdaki kod örneği içerir ve temel başlatma sağlar bir `Main` yöntemi.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#02)]  
  
2. Veritabanına bağlanırken ayrıntılarını işlemek için form denetiminin sınıf tanımında bir yöntem uygulayın.  
  
     Bu kod örneği kullanan bir `GetData` doldurulmuş bir döndüren yöntem <xref:System.Data.DataTable> nesne. Ayarladığınız mutlaka `connectionString` değişken veritabanınız için uygun olan bir değer.  
  
    > [!IMPORTANT]
    >  Depolama bağlantı dizesi içinde bir parola gibi hassas bilgileri, uygulamanızın güvenliğini etkileyebilir. Olarak da bilinen tümleşik güvenlik Windows kimlik doğrulamasını kullanarak bir veritabanına erişimi denetlemek için daha güvenli bir yoludur. Daha fazla bilgi için [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#30)]  
  
3. Form için bir işleyici uygulamak <xref:System.Windows.Forms.Form.Load> başlatan olay <xref:System.Windows.Forms.DataGridView> ve <xref:System.Windows.Forms.BindingSource> ve veri bağlamasını ayarlamak ayarlar.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#10)]  
  
4. Uygulamak için işleyiciler <xref:System.Windows.Forms.DataGridView> denetimin <xref:System.Windows.Forms.DataGridView.CellValidating> ve <xref:System.Windows.Forms.DataGridView.CellEndEdit> olayları.  
  
     <xref:System.Windows.Forms.DataGridView.CellValidating> Olay işleyicisidir burada belirlediğiniz olmadığını bir hücrenin değerini `CompanyName` sütunu boş. Hücre değerini doğrulama başarısız olursa, ayarlama <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> özelliği <xref:System.Windows.Forms.DataGridViewCellValidatingEventArgs?displayProperty=nameWithType> sınıfının `true`. Bu neden <xref:System.Windows.Forms.DataGridView> imleç hücre bırakmasını önlemek için denetimi. Ayarlama <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> satır için açıklayıcı bir dize özelliği. Bu hata metnini içeren bir araç ipucu ile bir hata simgesi görüntüler. İçinde <xref:System.Windows.Forms.DataGridView.CellEndEdit> olay işleyicisini <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> satırda boş dize özelliği. <xref:System.Windows.Forms.DataGridView.CellEndEdit> Olay yalnızca hücrenin doğrulama başarısız olursa, bunu yapamazsınız düzenleme modundan çıktığında gerçekleşir.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#20)]  
  
## <a name="testing-the-application"></a>Uygulamayı Test Etme  
 Şimdi beklendiği gibi davrandığından emin olmak için form test edebilirsiniz.  
  
#### <a name="to-test-the-form"></a>Formu sınamak için  
  
- Derleme ve uygulamayı çalıştırın.  
  
     Göreceğiniz bir <xref:System.Windows.Forms.DataGridView> verilerle doldurulmuş `Customers` tablo. Bir hücreye çift tıkladığınızda `CompanyName` sütun değeri düzenleyebilirsiniz. Tüm karakterleri silme ve hücre çıkmak için SEKME tuşuna basın, <xref:System.Windows.Forms.DataGridView> çıkmasını engeller. Boş olmayan bir dize hücreye yazarken <xref:System.Windows.Forms.DataGridView> hücre çıkış denetimi sağlar.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu uygulamayı size temel bir anlayış <xref:System.Windows.Forms.DataGridView> denetimin özellikleri. Görünümünü ve davranışını özelleştirebilirsiniz <xref:System.Windows.Forms.DataGridView> çeşitli şekillerde denetimi:  
  
- Kenarlık ve üstbilgi stilleri değiştirin. Daha fazla bilgi için [nasıl yapılır: Değiştirme kenarlık ve kılavuz çizgi stillerini Windows Forms DataGridView denetiminde](change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
- Etkinleştirmek veya kısıtlamak için kullanıcı girişi <xref:System.Windows.Forms.DataGridView> denetimi. Daha fazla bilgi için [nasıl yapılır: Önlemek satır eklemeyi ve silmeyi Windows Forms DataGridView denetiminde](prevent-row-addition-and-deletion-datagridview.md), ve [nasıl yapılır: Sütunları yapma salt okunur Windows Forms DataGridView denetiminde](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
- Kullanıcı girişi için veritabanı ile ilgili hataları kontrol edin. Daha fazla bilgi için [izlenecek yol: Windows veri girişi sırasında oluşan hataları ele alma Forms DataGridView denetiminde](handling-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
- Çok büyük veri kümeleri ile sanal modu kullanarak işleyin. Daha fazla bilgi için [izlenecek yol: Sanal modu uygulama içinde Windows Forms DataGridView denetiminde](implementing-virtual-mode-wf-datagridview-control.md).  
  
- Hücrelerin görünüşünü özelleştirme. Daha fazla bilgi için [nasıl yapılır: Windows Forms DataGridView denetiminde hücrelerin görünüşünü özelleştirme](customize-the-appearance-of-cells-in-the-datagrid.md) ve [nasıl yapılır: Windows Forms DataGridView denetiminde yazı tipi ve renk stillerini ayarlama](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Windows Forms DataGridView Denetiminde Veri Girişi](data-entry-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView denetiminde verileri doğrulama](how-to-validate-data-in-the-windows-forms-datagridview-control.md)
- [İzlenecek yol: Windows Forms DataGridView denetimine veri girişi sırasında oluşan hataları ele alma](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Bağlantı Bilgilerini Koruma](../../data/adonet/protecting-connection-information.md)
