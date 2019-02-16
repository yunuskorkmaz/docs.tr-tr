---
title: "Nasıl yapılır: Ekleme ve Windows Forms Tasarımcısı'nı kullanarak DataGridView denetimindeki sütunları kaldırma"
ms.date: 03/30/2017
f1_keywords:
- vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
ms.openlocfilehash: 01ae8987f7a92abf79a758e82ed0ac863fad57ce
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/16/2019
ms.locfileid: "56332695"
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Nasıl yapılır: Ekleme ve Windows Forms Tasarımcısı'nı kullanarak DataGridView denetimindeki sütunları kaldırma
Windows Forms <xref:System.Windows.Forms.DataGridView> denetim verilerini görüntülemek için sütunları içermelidir. Bir denetimi el ile doldurmak planlıyorsanız, kendiniz sütunlar eklemeniz gerekir. Alternatif olarak, denetimi oluşturur ve sütunları otomatik olarak dolduran bir veri kaynağına da bağlayabilirsiniz. Veri kaynağı görüntülemek istediğiniz birden fazla sütun içeriyorsa, istenmeyen sütunları kaldırabilirsiniz.  
  
 Aşağıdaki yordamlar gerektiren bir **Windows uygulama** proje içeren bir form ile bir <xref:System.Windows.Forms.DataGridView> denetimi. Bu tür bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir Windows Forms uygulaması projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms'a denetimler ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-a-column-using-the-designer"></a>Tasarımcı kullanarak bir sütun eklemek için  
  
1.  Akıllı etiket karakterini tıklayın (![akıllı etiket karakterini](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) sağ üst köşesindeki <xref:System.Windows.Forms.DataGridView> denetlemek ve ardından **Sütun Ekle**.  
  
2.  İçinde **Sütun Ekle** iletişim kutusunda **sınırlama sütunu** seçeneği ve veri kaynağından bir sütun seçin ya da seçin **bağlantısız sütun** seçenek ve sütun tanımlama Belirtilen alanlara kullanarak.  
  
3.  Tıklayın **Ekle** düğmesini Tasarımcısı'nda mevcut sütunları denetimi görüntüleme alanı zaten doldurmuyorsa görünmesine neden olan bir sütun ekleyin.  
  
    > [!NOTE]
    >  Sütun özellikleri değiştirebilirsiniz **sütunları Düzenle** denetimin akıllı etiketten erişebileceğiniz iletişim kutusu.  
  
### <a name="to-remove-a-column-using-the-designer"></a>Tasarımcı kullanarak bir sütunu kaldırmak için  
  
1.  Seçin **sütunları Düzenle** denetimin akıllı etiketinde.  
  
2.  Bir sütun seçin **seçili sütun** listesi.  
  
3.  Tıklayın **Kaldır** bu Tasarımcısından kaybolmasına neden sütununu Sil düğmesini.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.DataGridView>
- [Nasıl yapılır: Bir Windows Forms uygulaması projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Nasıl yapılır: Windows Forms'a denetimler ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
