---
title: "Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGridView Denetimine Sütunlar Ekleme ve Kaldırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4fdb57cf2134ee4f221a26db61cfdcc48dc92548
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGridView Denetimine Sütunlar Ekleme ve Kaldırma
Windows Forms <xref:System.Windows.Forms.DataGridView> denetim verileri görüntülemek için sütunları içermelidir. Denetimi el ile doldurmak planlıyorsanız, kendiniz sütunları eklemeniz gerekir. Alternatif olarak, denetim oluşturur ve sütunları otomatik olarak dolduran bir veri kaynağına bağlayabilirsiniz. Veri kaynağını görüntülemek istediğiniz daha fazla sütun içeriyorsa, istenmeyen sütunları kaldırabilirsiniz.  
  
 Aşağıdaki yordamlar gerektiren bir **Windows uygulaması** içeren bir form ile proje bir <xref:System.Windows.Forms.DataGridView> denetim. Böyle bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) ve [nasıl yapılır: Windows Forms denetimlerine ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-a-column-using-the-designer"></a>Tasarımcı kullanarak bir sütun eklemek için  
  
1.  Akıllı etiket karakteri tıklayın (![akıllı etiket karakteri](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) sağ üst köşesindeki <xref:System.Windows.Forms.DataGridView> denetlemek ve ardından **Sütun Ekle**.  
  
2.  İçinde **Sütun Ekle** iletişim kutusunda, seçin **veriye bağlı sütun** seçeneği ve veri kaynağından bir sütun seçin ya da seçin **bağlantısız sütun** seçeneği ve sütun tanımlayın Sağlanan alanları kullanma.  
  
3.  Tıklatın **Ekle** varolan sütunlar denetim görüntüleme alanı zaten doldurmuyorsa Tasarımcısı'nda görüntülenmesine neden sütun eklemek için düğmesi.  
  
    > [!NOTE]
    >  Sütun özelliklerinde değişiklik yapabilirsiniz **Edit Columns** iletişim kutusu, denetimin akıllı etiketten erişebilirsiniz.  
  
### <a name="to-remove-a-column-using-the-designer"></a>Tasarımcı kullanarak bir sütunu kaldırmak için  
  
1.  Seçin **Edit Columns** denetimin akıllı etiket gelen.  
  
2.  Bir sütun seçin **seçili sütun** listesi.  
  
3.  Tıklatın **kaldırmak** Tasarımcısı'ndan kayboluyor kendisine neden sütunu silmek için düğmesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 [Nasıl yapılır: bir Windows uygulaması projesi oluşturma](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [Nasıl yapılır: Windows Forms’a Denetimler Ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
