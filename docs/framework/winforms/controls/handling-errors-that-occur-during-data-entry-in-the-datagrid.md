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
ms.openlocfilehash: 9e803b6450fb8c9ade4adde5bf98fb1c3c62c861
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971281"
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a>İzlenecek yol: Windows Forms DataGridView Denetimine Veri Girişi Sırasında Oluşan Hataları Ele Alma
Temel alınan veri deposundan hataları işleme, veri girişi uygulama için gerekli bir özelliktir. Windows Forms <xref:System.Windows.Forms.DataGridView> denetim kolaylaştırır bu göstererek <xref:System.Windows.Forms.DataGridView.DataError> veri deposunu bir kısıtlama ihlali veya bir ihlal iş kuralı algıladığında gerçekleşmek üzereyken olay.  
  
 Bu kılavuzda, tablosundan satırları alır `Customers` Northwind örnek veritabanındaki tablo ve bunları görüntüleme bir <xref:System.Windows.Forms.DataGridView> denetimi. Yinelenen zaman `CustomerID` değeri, yeni bir satır veya düzenlenmiş bir var olan satır algılandığında <xref:System.Windows.Forms.DataGridView.DataError> olay gerçekleşir, hangi görüntüleyerek işlenecek bir <xref:System.Windows.Forms.MessageBox> özel durumu açıklayan.  
  
 Bu konudaki tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: Windows veri girişi sırasında oluşan hataları ele Forms DataGridView denetiminde](handle-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için şunlar gerekir:  
  
- SQL Server Northwind örnek veritabanını bir sunucu erişim.  
  
## <a name="creating-the-form"></a>Form Oluşturma  
  
#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a>DataGridView denetimine veri girişi sırasında oluşan hataları işlemek için  
  
1. Türetilen bir sınıf oluşturmanız <xref:System.Windows.Forms.Form> ve içeren bir <xref:System.Windows.Forms.DataGridView> denetimi ve bir <xref:System.Windows.Forms.BindingSource> bileşeni.  
  
     Aşağıdaki kod örneği içerir ve temel başlatma sağlar bir `Main` yöntemi.  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]  
  
2. Veritabanına bağlanırken ayrıntılarını işlemek için form denetiminin sınıf tanımında bir yöntem uygulayın.  
  
     Bu kod örneği kullanan bir `GetData` doldurulmuş bir döndüren yöntem <xref:System.Data.DataTable> nesne. Ayarladığınız mutlaka `connectionString` değişken veritabanınız için uygun olan bir değer.  
  
    > [!IMPORTANT]
    >  Depolama bağlantı dizesi içinde bir parola gibi hassas bilgileri, uygulamanızın güvenliğini etkileyebilir. Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur. Daha fazla bilgi için [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]  
  
3. Form için bir işleyici uygulamak <xref:System.Windows.Forms.Form.Load> başlatan olay <xref:System.Windows.Forms.DataGridView> ve <xref:System.Windows.Forms.BindingSource> ve veri bağlamasını ayarlamak ayarlar.  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]  
  
4. Tanıtıcı <xref:System.Windows.Forms.DataGridView.DataError> olayda <xref:System.Windows.Forms.DataGridView>.  
  
     Bir işleme hata bağlamı ise hata görüntüleme bir <xref:System.Windows.Forms.MessageBox>.  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]  
  
## <a name="testing-the-application"></a>Uygulamayı Test Etme  
 Şimdi beklendiği gibi davrandığından emin olmak için form test edebilirsiniz.  
  
#### <a name="to-test-the-form"></a>Formu sınamak için  
  
- Uygulamayı çalıştırmak için F5'e basın.  
  
     Göreceğiniz bir <xref:System.Windows.Forms.DataGridView> denetim doldurulmuş Müşteriler tablosundan verileri. İçin yinelenen bir değer girerseniz `CustomerID` ve Düzenle işleyin, hücre değerini otomatik olarak geri döner ve göreceğiniz bir <xref:System.Windows.Forms.MessageBox> görüntüleyen veri girişi hatası.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu uygulamayı size temel bir anlayış <xref:System.Windows.Forms.DataGridView> denetimin özellikleri. Görünümünü ve davranışını özelleştirebilirsiniz <xref:System.Windows.Forms.DataGridView> çeşitli şekillerde denetimi:  
  
- Kenarlık ve üstbilgi stilleri değiştirin. Daha fazla bilgi için [nasıl yapılır: Değiştirme kenarlık ve kılavuz çizgi stillerini Windows Forms DataGridView denetiminde](change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
- Etkinleştirmek veya kısıtlamak için kullanıcı girişi <xref:System.Windows.Forms.DataGridView> denetimi. Daha fazla bilgi için [nasıl yapılır: Önlemek satır eklemeyi ve silmeyi Windows Forms DataGridView denetiminde](prevent-row-addition-and-deletion-datagridview.md), ve [nasıl yapılır: Sütunları yapma salt okunur Windows Forms DataGridView denetiminde](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
- Kullanıcı girişini doğrulama <xref:System.Windows.Forms.DataGridView> denetimi. Daha fazla bilgi için [izlenecek yol: Doğrulama verileri Windows Forms DataGridView denetiminde](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
- Çok büyük veri kümeleri ile sanal modu kullanarak işleyin. Daha fazla bilgi için [izlenecek yol: Sanal modu uygulama içinde Windows Forms DataGridView denetiminde](implementing-virtual-mode-wf-datagridview-control.md).  
  
- Hücrelerin görünüşünü özelleştirme. Daha fazla bilgi için [nasıl yapılır: Windows Forms DataGridView denetiminde hücrelerin görünüşünü özelleştirme](customize-the-appearance-of-cells-in-the-datagrid.md) ve [nasıl yapılır: Windows Forms DataGridView denetimi için varsayılan hücre stillerini ayarlama](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Windows Forms DataGridView Denetiminde Veri Girişi](data-entry-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView denetimine veri girişi sırasında oluşan hataları ele](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [İzlenecek yol: Windows Forms DataGridView denetiminde verileri doğrulama](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [Bağlantı Bilgilerini Koruma](../../data/adonet/protecting-connection-information.md)
