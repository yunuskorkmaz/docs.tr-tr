---
title: BindingNavigator Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- DataNavigator
helpviewer_keywords:
- BindingNavigator control [Windows Forms], about BindingNavigator control
- records [Windows Forms], navigating on a form
- data [Windows Forms], navigating
- data navigation
ms.assetid: 4423eede-f8d1-4d02-822f-5bf8432680d0
ms.openlocfilehash: c2747a6801d4aa9cfde4227ffd5c29ca1de78d48
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744105"
---
# <a name="bindingnavigator-control-overview-windows-forms"></a>BindingNavigator Denetimine Genel Bakış (Windows Forms)
Kullanıcıların bir Windows formundaki verileri aramasını ve değiştirmesini sağlamak üzere standartlaştırılmış bir yol oluşturmak için <xref:System.Windows.Forms.BindingNavigator> denetimini kullanabilirsiniz. Kullanıcıların bir formdaki veri kayıtları arasında hareket kurmasını ve kayıtlarla etkileşime geçmesini sağlamak için <xref:System.Windows.Forms.BindingSource> bileşeniyle <xref:System.Windows.Forms.BindingNavigator> sık sık kullanırsınız.  
  
## <a name="how-the-bindingnavigator-works"></a>BindingNavigator nasıl kullanılır?  

 <xref:System.Windows.Forms.BindingNavigator> denetimi, veri ekleme, verileri silme ve veriler arasında gezinme gibi <xref:System.Windows.Forms.ToolStripItem> nesne dizileri içeren bir <xref:System.Windows.Forms.ToolStrip> oluşur. Varsayılan olarak, <xref:System.Windows.Forms.BindingNavigator> denetimi bu standart düğmeleri içerir. Aşağıdaki ekran görüntüsünde bir formda <xref:System.Windows.Forms.BindingNavigator> denetimi gösterilmektedir:
  
 ![BindingNavigator denetimini gösteren ekran görüntüsü.](./media/bindingnavigator-control-overview-windows-forms/bindingnavigator-control-form.gif)  
  
 Aşağıdaki tabloda denetimler listelenmiş ve işlevleri açıklanmaktadır.  
  
|Denetim|İşlev|  
|-------------|--------------|  
|<xref:System.Windows.Forms.BindingNavigator.AddNewItem%2A> düğmesi|Temel alınan veri kaynağına yeni bir satır ekler.|  
|<xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> düğmesi|Temel alınan veri kaynağından geçerli satırı siler.|  
|<xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> düğmesi|Temel alınan veri kaynağındaki ilk öğeye gider.|  
|<xref:System.Windows.Forms.BindingNavigator.MoveLastItem%2A> düğmesi|Temel alınan veri kaynağındaki son öğeye gider.|  
|<xref:System.Windows.Forms.BindingNavigator.MoveNextItem%2A> düğmesi|Temel alınan veri kaynağındaki bir sonraki öğeye gider.|  
|<xref:System.Windows.Forms.BindingNavigator.MovePreviousItem%2A> düğmesi|Temel alınan veri kaynağındaki bir önceki öğeye gider.|  
|<xref:System.Windows.Forms.BindingNavigator.PositionItem%2A> metin kutusu|Temel alınan veri kaynağı içindeki geçerli konumu döndürür.|  
|<xref:System.Windows.Forms.BindingNavigator.CountItem%2A> metin kutusu|Temel alınan veri kaynağındaki toplam öğe sayısını döndürür.|  
  
 Bu koleksiyondaki her denetim için, program aracılığıyla aynı işlevselliği sağlayan <xref:System.Windows.Forms.BindingSource> bileşenin karşılık gelen bir üyesi vardır. Örneğin, <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> düğmesi <xref:System.Windows.Forms.BindingSource> bileşenin <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> yöntemine karşılık gelir, <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> düğmesi <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> yöntemine karşılık gelir ve bu şekilde devam eder.  
  
 Varsayılan düğmeler uygulamanıza uygun değilse veya diğer işlev türlerini desteklemek için ek düğmeler gerekiyorsa, kendi <xref:System.Windows.Forms.ToolStrip> düğmelerinizi sağlayabilirsiniz. Ayrıca bkz. [nasıl yapılır: Windows Forms BindingNavigator denetimine yükleme, kaydetme ve Iptal düğmeleri ekleme](load-save-and-cancel-bindingnavigator.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- [BindingNavigator Denetimi](bindingnavigator-control-windows-forms.md)
