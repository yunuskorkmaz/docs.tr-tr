---
title: BindingNavigator Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- DataNavigator
helpviewer_keywords:
- BindingNavigator control [Windows Forms], about BindingNavigator control
- records [Windows Forms], navigating on a form
- data [Windows Forms], navigating
- data navigation
ms.assetid: 4423eede-f8d1-4d02-822f-5bf8432680d0
ms.openlocfilehash: ae1e8273c39122e094817e28379e52c19c573a3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528788"
---
# <a name="bindingnavigator-control-overview-windows-forms"></a>BindingNavigator Denetimine Genel Bakış (Windows Forms)
Kullanabileceğiniz <xref:System.Windows.Forms.BindingNavigator> aramak ve bir Windows formunda veri değiştirmek kullanıcılar için standartlaştırılmış bir yol oluşturmak için denetim. Sık kullandığınız <xref:System.Windows.Forms.BindingNavigator> ile <xref:System.Windows.Forms.BindingSource> bir form üzerinde veri kayıtlarda taşımak ve kayıtlarıyla etkileşim kullanıcılar etkinleştirmek için bileşen.  
  
## <a name="how-the-bindingnavigator-works"></a>BindingNavigator nasıl çalışır?  
 <xref:System.Windows.Forms.BindingNavigator> Denetim oluşan bir <xref:System.Windows.Forms.ToolStrip> bir dizi <xref:System.Windows.Forms.ToolStripItem> nesneleri için ortak veri ile ilgili eylemler çoğunu: veri ekleme, verileri siliniyor ve verilerine gezinme. Varsayılan olarak, <xref:System.Windows.Forms.BindingNavigator> denetimi bu standart düğmeler içerir. Aşağıdaki ekran görüntüsü gösterildiği <xref:System.Windows.Forms.BindingNavigator> bir form üzerinde denetim.  
  
 ![BindingNavigator denetimi](../../../../docs/framework/winforms/controls/media/cpdatacontainerctrl.gif "cpDataContainerCtrl")  
  
 Aşağıdaki tabloda denetimlerini listeler ve bunların işlevleri açıklanır.  
  
|Denetim|İşlev|  
|-------------|--------------|  
|<xref:System.Windows.Forms.BindingNavigator.AddNewItem%2A> Düğmesi|Temel alınan veri kaynağında yeni bir satır ekler.|  
|<xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> Düğmesi|Geçerli satırda temel alınan veri kaynağından siler.|  
|<xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> Düğmesi|Veri kaynağındaki ilk öğenin taşır.|  
|<xref:System.Windows.Forms.BindingNavigator.MoveLastItem%2A> Düğmesi|Son temel alınan veri kaynağında öğesi taşır.|  
|<xref:System.Windows.Forms.BindingNavigator.MoveNextItem%2A> Düğmesi|Temel alınan veri kaynağında bir sonraki öğeye taşır.|  
|<xref:System.Windows.Forms.BindingNavigator.MovePreviousItem%2A> Düğmesi|Temel alınan veri kaynağı önceki öğede taşır.|  
|<xref:System.Windows.Forms.BindingNavigator.PositionItem%2A> Metin kutusu|Temel alınan veri kaynağı içindeki geçerli konumu döndürür.|  
|<xref:System.Windows.Forms.BindingNavigator.CountItem%2A> Metin kutusu|Temel alınan veri kaynağında toplam öğe sayısını döndürür.|  
  
 Bu koleksiyondaki her denetim için karşılık gelen bir üyesi yok <xref:System.Windows.Forms.BindingSource> program aracılığıyla aynı işlevselliği sunar bileşeni. Örneğin, <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> düğmesi karşılık gelen <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> yöntemi <xref:System.Windows.Forms.BindingSource> bileşeni <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> düğmesi karşılık gelen <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> yöntemi ve benzeri.  
  
 Varsayılan düğmeleri uygulamanız için uygun değilse ya da diğer işlevleri türlerini desteklemek için ek düğmeler ihtiyacınız varsa, kendi sağlayabilirsiniz <xref:System.Windows.Forms.ToolStrip> düğmeler. Ayrıca bkz. [nasıl yapılır: yükleme, kaydetme ve ekleme İptal düğmeleri Windows Forms BindingNavigator denetimi](../../../../docs/framework/winforms/controls/load-save-and-cancel-bindingnavigator.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.BindingSource>  
 [BindingNavigator Denetimi](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)
