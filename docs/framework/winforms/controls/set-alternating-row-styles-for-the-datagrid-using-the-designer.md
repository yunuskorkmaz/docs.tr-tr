---
title: "Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGridView Denetimi İçin Alternatif Satır Stillerini Ayarlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ledger-like formats
- DataGridView control [Windows Forms], row style alternation
- Windows Forms, rows
- rows [Windows Forms], alternating
- data [Windows Forms], displaying
ms.assetid: 02373442-bf94-4470-9f8a-e44c4a9d5b88
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bdd208d589c6b38088074f6d94045651df7049e8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGridView Denetimi İçin Alternatif Satır Stillerini Ayarlama
Tablo verisi sık sık değişen satırları farklı arka plan renklerini sahip olduğu bir defter benzeri biçiminde sunulur. Bu biçim, kullanıcıların her satırda, özellikle çok sayıda sütuna sahip geniş tablolar ile hangi hücrelerin olduğunu bildirir kolaylaştırır.  
  
 İle <xref:System.Windows.Forms.DataGridView> denetimi satırların değişerek için tam stil bilgilerini belirtebilirsiniz. Ön plan rengini ve arka plan rengi, ek olarak yazı tipi gibi stil özellikleri değişen satırları ayırt etmek için kullanabilirsiniz. Daha fazla bilgi için bkz: [Windows Forms DataGridView denetimindeki hücre stilleri](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
 Aşağıdaki yordam gerektiren bir **Windows uygulaması** içeren bir form ile proje bir <xref:System.Windows.Forms.DataGridView> denetim. Böyle bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) ve [nasıl yapılır: Windows Forms denetimlerine ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="define-styles-for-alternating-rows"></a>Satırların değişerek stilleri tanımlama  
  
1.  Seçin <xref:System.Windows.Forms.DataGridView> Denetim Tasarımcısı'nda.  
  
2.  İçinde **özellikleri** penceresinde, üç nokta düğmesini (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) yanındaki <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> özelliği.  
  
3.  İçinde **CellStyle Oluşturucu** iletişim kutusu, stil özellikleri ayarlayarak tanımlama ve kullanma **Önizleme** bölmesinde seçimlerinizi onaylayın. Belirttiğiniz stilleri ile ikinci bir başlangıç denetiminde görüntülenen her satır için kullanılır.  
  
4.  Adım 2 ve 3 kullanarak yineleyin kalan satırlar için stiller tanımlamak için <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> özelliği.  
  
    > [!NOTE]
    >  Hücre stilleri birden çok özelliklerinden devralınan kullanarak görüntülenir. Stil devralma hakkında daha fazla bilgi için bkz: [Windows Forms DataGridView denetimindeki hücre stilleri](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 [Windows Forms DataGridView Denetimindeki Hücre Stilleri](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView Denetimi ile Tasarımcı Kullanımı](../../../../docs/framework/winforms/controls/using-the-designer-with-the-windows-forms-datagridview-control.md)  
 [Nasıl yapılır: bir Windows uygulaması projesi oluşturma](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [Nasıl yapılır: Windows Forms’a Denetimler Ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
