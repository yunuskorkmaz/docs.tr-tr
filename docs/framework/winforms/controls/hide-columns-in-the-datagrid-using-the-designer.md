---
title: "Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGridView Denetimindeki Sütunları Gizleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], hiding
- DataGridView control [Windows Forms], column hiding
- data [Windows Forms], displaying
ms.assetid: a81c38e6-2527-426a-bcb1-be691403be04
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6deefcfb4a1fcf0c1a3bd0d521e6a69ea6902dd4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGridView Denetimindeki Sütunları Gizleme
Bazı durumlarda yalnızca bazı Windows Forms'ta kullanılabilir olan sütunları görüntülemek isteyeceksiniz <xref:System.Windows.Forms.DataGridView> denetim. Örneğin, bir çalışan görüntülemek isteyebilirsiniz maaş sütun diğer kullanıcılardan gizleme sırasında yönetim kimlik bilgilerine sahip kullanıcılar için. Alternatif olarak, yalnızca bazıları görüntülemek istediğiniz sayıda sütun içeren bir veri kaynağına denetimi bağlamak isteyebilirsiniz. Bu durumda, genellikle görüntüleme yerine gizleyip ilgilenen olmayan sütunları kaldırır. Daha fazla bilgi için bkz: [nasıl yapılır: ekleme ve kaldırma sütunları Windows Forms DataGridView denetimi kullanarak Tasarımcı](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md).  
  
 Aşağıdaki yordam gerektiren bir **Windows uygulaması** içeren bir form ile proje bir <xref:System.Windows.Forms.DataGridView> denetim. Böyle bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) ve [nasıl yapılır: Windows Forms denetimlerine ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-hide-a-column-using-the-designer"></a>Tasarımcı kullanarak bir sütunu gizlemek için  
  
1.  Akıllı etiket karakteri tıklayın (![akıllı etiket karakteri](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) sağ üst köşesindeki <xref:System.Windows.Forms.DataGridView> denetlemek ve ardından **Edit Columns**.  
  
2.  Bir sütun seçin **seçili sütun** listesi.  
  
3.  İçinde **sütun özellikleri** kılavuzunu, ayarlamak <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> özelliğine `false`.  
  
    > [!NOTE]
    >  Bir sütun temizleyerek eklerken gizleyebilirsiniz **görünür** onay kutusuna **Sütun Ekle** iletişim kutusu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>  
 [Nasıl yapılır: ekleme ve kaldırma sütunları Windows Forms DataGridView denetiminde Tasarımcısı'nı kullanarak](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 [Nasıl yapılır: bir Windows uygulaması projesi oluşturma](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [Nasıl yapılır: Windows formlarına denetimler ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
