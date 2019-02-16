---
title: "Nasıl yapılır: Windows Forms DataGridView Tasarımcısı'nı kullanarak denetimi için alternatif satır stillerini ayarlama"
ms.date: 03/30/2017
helpviewer_keywords:
- ledger-like formats
- DataGridView control [Windows Forms], row style alternation
- Windows Forms, rows
- rows [Windows Forms], alternating
- data [Windows Forms], displaying
ms.assetid: 02373442-bf94-4470-9f8a-e44c4a9d5b88
ms.openlocfilehash: 786f9e9555e49f7cf8880d571c759f5c85e6b2a1
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/16/2019
ms.locfileid: "56332329"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control-using-the-designer"></a>Nasıl yapılır: Windows Forms DataGridView Tasarımcısı'nı kullanarak denetimi için alternatif satır stillerini ayarlama
Tablosal veri sık sık değişen satırları farklı arka plan renkleri sahip olduğu bir defter benzeri biçiminde sunulur. Bu biçim, özellikle fazla sayıda sütun sahip geniş tabloların ile her bir satırdaki hücreleri olduğunu bildirir kullanıcıların kolaylaştırır.  
  
 İle <xref:System.Windows.Forms.DataGridView> denetimi için alternatif satırlar tam stil bilgilerini belirtebilirsiniz. Stil özellikleri gibi ön plan rengini ve yazı tipi, arka plan rengi yanı sıra, değişen satırları ayırt etmek için kullanabilirsiniz. Daha fazla bilgi için [Windows Forms DataGridView denetimindeki hücre stilleri](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
 Aşağıdaki yordam gerektirir bir **Windows uygulama** proje içeren bir form içeren bir <xref:System.Windows.Forms.DataGridView> denetimi. Bu tür bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir Windows Forms uygulaması projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms'a denetimler ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="define-styles-for-alternating-rows"></a>Alternatif satırlar için stil tanımlayın  
  
1.  Seçin <xref:System.Windows.Forms.DataGridView> Denetim Tasarımcısı'nda.  
  
2.  İçinde **özellikleri** penceresinde üç nokta düğmesini (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) yanındaki <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> özelliği.  
  
3.  İçinde **CellStyle Oluşturucu** iletişim kutusunda, stil özelliklerini ayarlayarak tanımlama ve kullanma **Önizleme** bölmesinde seçimlerinizi onaylayın. Belirttiğiniz stilleri ile ikinci bir başlangıç denetim, görüntülenen her bir satır için kullanılır.  
  
4.  Kalan satırlar için stillerini tanımlamak için yineleyin adım 2 ve 3 kullanarak <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> özelliği.  
  
    > [!NOTE]
    >  Hücreleri birden çok özelliklerinden devralınan stilleri kullanarak görüntülenir. Stil devralımı hakkında daha fazla bilgi için bkz: [Windows Forms DataGridView denetimindeki hücre stilleri](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.DataGridView>
- [Windows Forms DataGridView Denetimindeki Hücre Stilleri](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimi ile Tasarımcı Kullanımı](../../../../docs/framework/winforms/controls/using-the-designer-with-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Bir Windows Forms uygulaması projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Nasıl yapılır: Windows Forms'a denetimler ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
