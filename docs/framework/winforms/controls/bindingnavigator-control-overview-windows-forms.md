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
ms.openlocfilehash: ad63f622aae55cb4175eddc93ab5e086965a8fe8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011794"
---
# <a name="bindingnavigator-control-overview-windows-forms"></a>BindingNavigator Denetimine Genel Bakış (Windows Forms)
Kullanabileceğiniz <xref:System.Windows.Forms.BindingNavigator> aramak ve bir Windows Form üzerinde verileri değiştirmek kullanıcılar için standartlaştırılmış bir yol oluşturmak için denetimi. Sık kullandığınız <xref:System.Windows.Forms.BindingNavigator> ile <xref:System.Windows.Forms.BindingSource> kullanıcıların bir form üzerinde veri Kayıtlarda gezinmek ve kayıtlarla etkileşimde etkinleştirmek için bileşen.  
  
## <a name="how-the-bindingnavigator-works"></a>BindingNavigator nasıl çalışır?  

 <xref:System.Windows.Forms.BindingNavigator> Denetim oluşan bir <xref:System.Windows.Forms.ToolStrip> bir dizi <xref:System.Windows.Forms.ToolStripItem> nesneler için ortak verilerle ilgili işlemlerin çoğu: veri ekleme, verileri silme ve verilerine gezinme. Varsayılan olarak, <xref:System.Windows.Forms.BindingNavigator> denetimi bu standart düğmeleri içerir. Aşağıdaki ekran görüntüsü gösterildiği <xref:System.Windows.Forms.BindingNavigator> form denetimi:
  
 ![BindingNavigator denetimi gösteren ekran görüntüsü.](./media/bindingnavigator-control-overview-windows-forms/bindingnavigator-control-form.gif)  
  
 Aşağıdaki tablo, denetimleri listeler ve bunların işlevleri açıklanır.  
  
|Denetim|İşlev|  
|-------------|--------------|  
|<xref:System.Windows.Forms.BindingNavigator.AddNewItem%2A> Düğme|Temel alınan veri kaynağına yeni bir satır ekler.|  
|<xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> Düğme|Geçerli satırı temel alınan veri kaynağından siler.|  
|<xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> Düğme|Temel alınan veri kaynağına ilk öğesinde taşır.|  
|<xref:System.Windows.Forms.BindingNavigator.MoveLastItem%2A> Düğme|Son öğe temel alınan veri kaynağında taşır.|  
|<xref:System.Windows.Forms.BindingNavigator.MoveNextItem%2A> Düğme|Temel alınan veri kaynağı'na taşır.|  
|<xref:System.Windows.Forms.BindingNavigator.MovePreviousItem%2A> Düğme|Temel alınan veri kaynağı önceki öğede taşır.|  
|<xref:System.Windows.Forms.BindingNavigator.PositionItem%2A> metin kutusu|Temel alınan veri kaynağı içindeki geçerli konumu döndürür.|  
|<xref:System.Windows.Forms.BindingNavigator.CountItem%2A> metin kutusu|Temel alınan veri kaynağında toplam öğe sayısını döndürür.|  
  
 Bu koleksiyondaki her bir denetim için karşılık gelen bir üye yoktur <xref:System.Windows.Forms.BindingSource> bileşeni programlı olarak aynı işlevselliği sağlar. Örneğin, <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> düğmesi karşılık gelen <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> yöntemi <xref:System.Windows.Forms.BindingSource> bileşeni <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> düğmesi karşılık gelen <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> yöntemi ve benzeri.  
  
 Varsayılan düğme, uygulamanız için uygun olmayan ya da diğer işlevleri türlerini desteklemek için ek düğmeler ihtiyacınız varsa, kendi sağlayabilirsiniz <xref:System.Windows.Forms.ToolStrip> düğmeleri. Ayrıca bkz: [nasıl yapılır: Yükleme, kaydetme ve ekleme İptal düğmeleri Windows Forms BindingNavigator denetimi](load-save-and-cancel-bindingnavigator.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- [BindingNavigator Denetimi](bindingnavigator-control-windows-forms.md)
