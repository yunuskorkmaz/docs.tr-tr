---
title: 'Nasıl yapılır: Tasarımcı kullanarak Windows Forms panelinin arka planını ayarlama'
ms.date: 03/30/2017
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
ms.openlocfilehash: 9901b9989afc3602fe4326a2f2360ce894df40e4
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56303302"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a>Nasıl yapılır: Tasarımcı kullanarak Windows Forms panelinin arka planını ayarlama
Bir Windows Forms <xref:System.Windows.Forms.Panel> denetim arka plan rengi hem de arka plan görüntüsü görüntüleyebilirsiniz. <xref:System.Windows.Forms.Control.BackColor%2A> Özelliği etiketler gibi panelinde bulunan ve radyo düğmeleri, denetimleri arka plan rengini ayarlar. Varsa <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliği ayarlı değil, <xref:System.Windows.Forms.Control.BackColor%2A> seçimi tüm panel doldurur. Varsa <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliği ayarlanmışsa, görüntünün arkasındaki panelde bulunan denetimleri görüntülenir.  
  
 Aşağıdaki yordamı gerektiren bir **Windows uygulama** proje içeren bir form bir <xref:System.Windows.Forms.Panel> denetimi. Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir Windows Forms uygulaması projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms'a denetimler ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-set-the-background-in-the-windows-forms-designer"></a>Windows Form Tasarımcısı'nda arka planını ayarlama  
  
1.  Seçin <xref:System.Windows.Forms.Panel> denetimi.  
  
2.  İçinde **özellikleri** penceresinde, oku, İleri düğmesine tıklayın <xref:System.Windows.Forms.Control.BackColor%2A> bir penceresi üç sekme ile görüntülenecek özelliği.  
  
3.  Seçin **özel** renkler paleti görüntülemek için sekmesinde.  
  
4.  Seçin **Web** veya **sistem** renkler için önceden tanımlanmış adlarının bir listesini görüntülemek için sekmesinde ve bir renk seçin.  
  
5.  İçinde **özellikleri** penceresinde, oku, İleri düğmesine tıklayın <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliği.  
  
6.  İçinde **açık** iletişim kutusunda, görüntülemek istediğiniz dosyayı seçin.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [Panel Denetimi](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)
- [Panel Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)
- [Nasıl yapılır: Tasarımcı kullanarak Windows Forms Panel denetimi ile denetimleri gruplandırma](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)
