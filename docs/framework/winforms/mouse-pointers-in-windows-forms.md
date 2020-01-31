---
title: Fare Işaretçileri
ms.date: 03/30/2017
helpviewer_keywords:
- pointers [Windows Forms], setting
- mouse pointers
- mouse cursors
- mouse pointers [Windows Forms], setting
- cursors [Windows Forms], setting
- mouse [Windows Forms], cursors
ms.assetid: c3400d85-de5b-42e8-abc3-d6088d69ee53
ms.openlocfilehash: 4e8349effcd9b59045e39b763b4cb8b7d2fceb91
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740963"
---
# <a name="mouse-pointers-in-windows-forms"></a>Windows Forms'ta Fare İşaretçileri
Bazen imleç olarak adlandırılan fare *işaretçisi*, fare ile Kullanıcı girişi için ekranda bir odak noktasını belirten bir bit eşlemdir. Bu konu, Windows Forms fare işaretçisine genel bir bakış sağlar ve fare işaretçisini değiştirme ve denetleme yöntemlerinden bazılarını açıklar.  
  
## <a name="accessing-the-mouse-pointer"></a>Fare Işaretçisine erişme  
 Fare işaretçisi <xref:System.Windows.Forms.Cursor> sınıfı tarafından temsil edilir ve her <xref:System.Windows.Forms.Control>, bu denetimin işaretçisini belirten bir <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> özelliğine sahiptir. <xref:System.Windows.Forms.Cursor> sınıfı, <xref:System.Windows.Forms.Cursor.Position%2A> ve <xref:System.Windows.Forms.Cursor.HotSpot%2A> özellikleri gibi işaretçiyi tanımlayan özellikleri ve <xref:System.Windows.Forms.Cursor.Show%2A>, <xref:System.Windows.Forms.Cursor.Hide%2A>ve <xref:System.Windows.Forms.Cursor.DrawStretched%2A> yöntemleri gibi işaretçinin görünümünü değiştirebilen yöntemleri içerir.  
  
## <a name="controlling-the-mouse-pointer"></a>Fare Işaretçisini denetleme  
 Bazen, fare işaretçisinin kullanılabileceği alanı sınırlamak veya fare konumunu değiştirmek isteyebilirsiniz. <xref:System.Windows.Forms.Cursor><xref:System.Windows.Forms.Cursor.Position%2A> özelliğini kullanarak farenin geçerli konumunu alabilir veya ayarlayabilirsiniz. Ayrıca, fare işaretçisinin <xref:System.Windows.Forms.Cursor.Clip%2A> özelliğini ayarlamak için kullanılacak alanı sınırlayabilirsiniz. Klip alanı varsayılan olarak tüm ekrandır.  
  
## <a name="changing-the-mouse-pointer"></a>Fare Işaretçisini değiştirme  
 Fare işaretçisini değiştirmek, kullanıcıya geri bildirim sağlamanın önemli bir yoludur. Örneğin, fare işaretçisi, kullanıcıya hesaplamaların oluştuğunu söylemek ve denetimdeki kullanıcı etkileşimini sınırlamak için <xref:System.Windows.Forms.Control.MouseEnter> işleyicilerde değiştirilebilir ve olayları <xref:System.Windows.Forms.Control.MouseLeave>. Bazen, uygulamanız bir sürükle ve bırak işleminde yer alırken olduğu gibi sistem olayları nedeniyle fare işaretçisi değişecektir.  
  
 Fare işaretçisini değiştirmek için birincil yol, bir denetimin <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> veya <xref:System.Windows.Forms.Control.DefaultCursor%2A> özelliğini yeni bir <xref:System.Windows.Forms.Cursor>ayarlamadır. Fare işaretçisini değiştirme örnekleri için <xref:System.Windows.Forms.Cursor> sınıfındaki kod örneğine bakın. Ayrıca, <xref:System.Windows.Forms.Cursors> sınıfı, bir el ile benzeyen bir işaretçi gibi birçok farklı işaretçi türü için <xref:System.Windows.Forms.Cursor> nesneleri kümesi sunar. Bir kum saati gibi bekleme işaretçisini göstermek için, fare işaretçisi denetimde olduğunda, <xref:System.Windows.Forms.Control> sınıfının <xref:System.Windows.Forms.Control.UseWaitCursor%2A> özelliğini kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Cursor>
- [Bir Windows Forms Uygulamasında Fare Girdisi](mouse-input-in-a-windows-forms-application.md)
- [Windows Forms'ta Sürükle ve Bırak İşlevi](drag-and-drop-functionality-in-windows-forms.md)
