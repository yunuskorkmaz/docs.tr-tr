---
title: 'Nasıl yapılır: Sürüklenen GridView Sütun Başlığı için Stil Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 0b999645-0313-4b33-80b9-19ece08b5459
ms.openlocfilehash: 2e57b4cb1b8ddb90e8e6e0abc6db3e7f0b864cfa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-style-for-a-dragged-gridview-column-header"></a>Nasıl yapılır: Sürüklenen GridView Sütun Başlığı için Stil Oluşturma
Bu örnek sürüklenen görünüşünü değiştirme gösterilmektedir <xref:System.Windows.Controls.GridViewColumnHeader> kullanıcı bir sütunun konumunu değiştiğinde.  
  
## <a name="example"></a>Örnek  
 Başka bir konumda bir sütun başlığını sürüklediğinizde bir <xref:System.Windows.Controls.ListView> kullanan <xref:System.Windows.Controls.GridView> görünüm modu için sütun yeni bir konuma taşır. Sütun başlığını sürükleme sırasında üstbilgi kayan bir kopyasını özgün üstbilgisi yanı sıra görünür. Bir sütun başlığına bir <xref:System.Windows.Controls.GridView> tarafından temsil edilen bir <xref:System.Windows.Controls.GridViewColumnHeader> nesnesi.  
  
 Kayan ve özgün başlıkların görünümünü özelleştirmek için ayarlayabileceğiniz <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> değiştirmek için <xref:System.Windows.Controls.GridViewColumnHeader> <xref:System.Windows.Style>. Bunlar <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> ne zaman uygulanacağını <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> özellik değeri `true` ve <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> özellik değeri <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.  
  
 Ne zaman kullanıcının fare düğmesini tıklatıp üzerinde fare duraklatır sırada tuttuğu <xref:System.Windows.Controls.GridViewColumnHeader>, <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> özellik değeri değişiklikleri `true`. Benzer şekilde, kullanıcı başladığı sürükleme işlemi <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> özelliği değişiklikler <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.  
  
 Aşağıdaki örnekte nasıl ayarlanacağını gösterir <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> değiştirmek için <xref:System.Windows.Controls.Control.Foreground%2A> ve <xref:System.Windows.Controls.Control.Background%2A> kullanıcı yeni bir konuma bir sütun sürüklendiğinde özgün ve kayan başlıkların renklerini.  
  
 [!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplatestart)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersstart)]  
[!code-xaml[ListViewHeaderRoleStyle#IsPressed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#ispressed)]  
[!code-xaml[ListViewHeaderRoleStyle#Floating](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#floating)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersend)]  
[!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplateend)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.GridViewColumnHeader>  
 <xref:System.Windows.Controls.GridViewColumnHeaderRole>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [ListView Genel Bakış](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [GridView Genel Bakış](../../../../docs/framework/wpf/controls/gridview-overview.md)
