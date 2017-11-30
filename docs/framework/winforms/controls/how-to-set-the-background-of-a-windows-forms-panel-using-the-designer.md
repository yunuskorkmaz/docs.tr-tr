---
title: "Nasıl yapılır: Tasarımcı Kullanarak Windows Formları Panelinin Arka Planını Ayarlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 56cb6f7ee9a7c52ff4763c0c310d679e4889dbd2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları Panelinin Arka Planını Ayarlama
Windows Forms <xref:System.Windows.Forms.Panel> denetim arka plan rengi ve arka plan resmini görüntüleyebilirsiniz. <xref:System.Windows.Forms.Control.BackColor%2A> Özelliği ayarlar etiketler gibi Masası'nda bulunan ve radyo düğmeleri denetimleri için arka plan rengi. Varsa <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliği ayarlı değil, <xref:System.Windows.Forms.Control.BackColor%2A> seçim bölmesinin tüm doldurur. Varsa <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliği ayarlanmışsa, resim panelinde bulunan denetimleri arkasında görüntülenir.  
  
 Aşağıdaki yordam gerektiren bir **Windows uygulaması** proje içeren bir form ile bir <xref:System.Windows.Forms.Panel> denetim. Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) ve [nasıl yapılır: Windows Forms denetimlerine ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-set-the-background-in-the-windows-forms-designer"></a>Windows Forms Tasarımcısı'nda arka plan ayarlamak için  
  
1.  Seçin <xref:System.Windows.Forms.Panel> denetim.  
  
2.  İçinde **özellikleri** penceresinde, oku için İleri düğmesini tıklatın <xref:System.Windows.Forms.Control.BackColor%2A> üç sekme penceresiyle görüntülenecek özelliği.  
  
3.  Seçin **özel** renk paletini görüntülenecek sekmesi.  
  
4.  Seçin **Web** veya **sistem** renkler için önceden tanımlanmış adlarının bir listesini görüntülemek için sekmesini ve ardından bir rengi seçin.  
  
5.  İçinde **özellikleri** penceresinde, oku için İleri düğmesini tıklatın <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliği.  
  
6.  İçinde **açık** iletişim kutusunda, görüntülemek istediğiniz dosyayı seçin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Control.BackColor%2A>  
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>  
 [Panel denetimi](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)  
 [Panel denetimine genel bakış](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [Nasıl yapılır: Tasarımcı kullanarak Windows Formları Panel denetimi ile denetimleri gruplandırma](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)
