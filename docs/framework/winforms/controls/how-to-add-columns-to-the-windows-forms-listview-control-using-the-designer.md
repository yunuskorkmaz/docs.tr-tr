---
title: "Nasıl yapılır: Tasarımcı Kullanarak Windows Formları ListView Denetimine Sütunlar Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7223fc47c885b7e659b9bab00c276759410d2567
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları ListView Denetimine Sütunlar Ekleme
Windows Forms <xref:System.Windows.Forms.ListView> denetimi her listesi için birden çok sütun görüntüleyebilir durumlarda öğesi **ayrıntıları** görünümü. Sütunları, çeşitli her liste öğesi hakkında bilgi görüntülemek için kullanabilirsiniz. Örneğin, dosya adı, dosya türü, boyutu ve dosyanın en son değiştirildiği tarih dosyaların bir listesini görüntüleyebilirsiniz. Oluşturulduktan sonra sütun doldurma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms ListView denetimiyle sütunlardaki alt öğeleri görüntüleme](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).  
  
 Aşağıdaki yordam gerektiren bir **Windows uygulaması** içeren bir form ile proje bir <xref:System.Windows.Forms.ListView> denetim. Böyle bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) ve [nasıl yapılır: Windows Forms denetimlerine ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-columns-in-the-designer"></a>Tasarımcıda sütun eklemek için  
  
1.  İçinde **özellikleri** penceresindeki ayarlayın denetimin <xref:System.Windows.Forms.ListView.View%2A> özelliğine <xref:System.Windows.Forms.View.Details>.  
  
2.  İçinde **özellikleri** penceresinde tıklatın **üç nokta** düğmesi (![VisualStudioEllipsesButton ekran görüntüsü](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) yanındaki <xref:System.Windows.Forms.ListView.Columns%2A> özelliği.  
  
     **Sütun üstbilgisi Koleksiyonu Düzenleyicisi** görüntülenir.  
  
3.  Kullanım **Ekle** yeni sütun ekleme düğmesi. Ardından sütun başlığını seçin ve metin (sütun başlığını), metin hizalamasını ve genişlik ayarlayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ListView denetimine genel bakış](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Nasıl yapılır: ekleme ve kaldırma öğeleri Windows Forms ListView denetimi](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [Nasıl yapılır: Windows sütunlardaki alt öğeleri görüntüleme Forms ListView denetimi](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 [Nasıl yapılır: Windows Forms ListView denetimi için simgeler görüntüleme](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [Nasıl yapılır: bir TreeView veya ListView denetimi (Windows Forms) özel bilgi ekleme](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
