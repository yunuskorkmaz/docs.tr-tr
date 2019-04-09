---
title: 'Nasıl yapılır: Sürüklenen GridView Sütun Başlığı için Stil Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 0b999645-0313-4b33-80b9-19ece08b5459
ms.openlocfilehash: dbcdd38e0397b8e637aff962420a2959f33203df
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090101"
---
# <a name="how-to-create-a-style-for-a-dragged-gridview-column-header"></a>Nasıl yapılır: Sürüklenen GridView Sütun Başlığı için Stil Oluşturma
Bu örnekte, sürüklenen görünümünü değiştirmek gösterilmektedir <xref:System.Windows.Controls.GridViewColumnHeader> kullanıcı, bir sütunun konumunu değiştiğinde.  
  
## <a name="example"></a>Örnek  
 Sütun üst bilgisine başka bir konuma sürüklediğinizde bir <xref:System.Windows.Controls.ListView> kullanan <xref:System.Windows.Controls.GridView> görünüm modu için sütunu yeni konuma taşır. Sütun üst bilgisine sürükleme sırasında üstbilgi kayan bir kopyasını ek olarak özgün üstbilgi görünür. Bir sütun başlığına bir <xref:System.Windows.Controls.GridView> tarafından temsil edilen bir <xref:System.Windows.Controls.GridViewColumnHeader> nesne.  
  
 Kayan ve özgün üstbilgileri görünümünü özelleştirmek için ayarlayabileceğiniz <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> değiştirilecek <xref:System.Windows.Controls.GridViewColumnHeader> <xref:System.Windows.Style>. Bunlar <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> ne zaman uygulanacağına <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> özellik değeri `true` ve <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> özellik değeri <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.  
  
 Kullanıcı fare düğmesine bastığında ve üzerinde fareyi duraklatır sırada başvuruysa <xref:System.Windows.Controls.GridViewColumnHeader>, <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> özellik değeri değişiklikleri `true`. Benzer şekilde, kullanıcı başladığı sürükleme işlemi <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> özellik değişiklikleri <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.  
  
 Aşağıdaki örnek nasıl ayarlanacağını gösterir <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> değiştirmek için <xref:System.Windows.Controls.Control.Foreground%2A> ve <xref:System.Windows.Controls.Control.Background%2A> kullanıcı yeni bir konuma bir sütun sürüklediğinde özgün ve kayan başlıklarının renkleri.  
  
 [!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplatestart)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersstart)]  
[!code-xaml[ListViewHeaderRoleStyle#IsPressed](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#ispressed)]  
[!code-xaml[ListViewHeaderRoleStyle#Floating](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#floating)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersend)]  
[!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplateend)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.GridViewColumnHeader>
- <xref:System.Windows.Controls.GridViewColumnHeaderRole>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [Nasıl Yapılır Konuları](listview-how-to-topics.md)
- [ListView Genel Bakışı](listview-overview.md)
- [GridView Genel Bakışı](gridview-overview.md)
