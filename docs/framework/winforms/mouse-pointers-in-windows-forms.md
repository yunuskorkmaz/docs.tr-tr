---
title: Windows Forms'ta Fare İşaretçileri
ms.date: 03/30/2017
helpviewer_keywords:
- pointers [Windows Forms], setting
- mouse pointers
- mouse cursors
- mouse pointers [Windows Forms], setting
- cursors [Windows Forms], setting
- mouse [Windows Forms], cursors
ms.assetid: c3400d85-de5b-42e8-abc3-d6088d69ee53
ms.openlocfilehash: 02f93a85ecaa13f5f72cd0f31a1f5ffc24c59f68
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491785"
---
# <a name="mouse-pointers-in-windows-forms"></a>Windows Forms'ta Fare İşaretçileri
Fare *işaretçi*, fare ile kullanıcı girişi için ekrandaki bir odak noktası belirten bir bit eşlem olduğundan, bazen bir imleç adlandırılır. Bu konu, Windows Forms'ta fare işaretçisi genel bir bakış sağlar ve bazı değiştirebilir ve fare işaretçisini denetim yolları açıklanmaktadır.  
  
## <a name="accessing-the-mouse-pointer"></a>Fare işaretçisi erişme  
 Fare işaretçisi tarafından temsil edilen <xref:System.Windows.Forms.Cursor> sınıfı ve her <xref:System.Windows.Forms.Control> sahip bir <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> işaretçiyi denetimin belirten özelliği. <xref:System.Windows.Forms.Cursor> Sınıfı gibi işaretçi tanımlayan özellikler içerir <xref:System.Windows.Forms.Cursor.Position%2A> ve <xref:System.Windows.Forms.Cursor.HotSpot%2A> özellikleri ve yöntemleri işaretçisi görünümünü gibi değiştirebileceğiniz <xref:System.Windows.Forms.Cursor.Show%2A>, <xref:System.Windows.Forms.Cursor.Hide%2A>, ve <xref:System.Windows.Forms.Cursor.DrawStretched%2A> yöntemleri.  
  
## <a name="controlling-the-mouse-pointer"></a>Fare işaretçisi denetleme  
 Bazen, fare işaretçisini kullanılabilir veya fare konumunu değiştirme alanı sınırlamak isteyebilirsiniz. Get veya fare kullanarak geçerli konumunu ayarla <xref:System.Windows.Forms.Cursor.Position%2A> özelliği <xref:System.Windows.Forms.Cursor>. Ayrıca, fare işaretçisini kullanılabilir alanı sınırlayabilirsiniz ayarı <xref:System.Windows.Forms.Cursor.Clip%2A> özelliği. Klip alanında, varsayılan olarak, tüm ekrandır.  
  
## <a name="changing-the-mouse-pointer"></a>Fare işaretçisi değiştirme  
 Fare işaretçisi değiştirme, kullanıcıya geri bildirim sağlamanın önemli bir yoludur. Örneğin, fare işaretçisini işleyiciler değiştirilebilir <xref:System.Windows.Forms.Control.MouseEnter> ve <xref:System.Windows.Forms.Control.MouseLeave> hesaplamalar oluşan kullanıcı anlaşılır ve kullanıcı etkileşimi denetiminde sınırlamak için olayları. Bazı durumlarda, fare işaretçisini nedeniyle sistem olayları, uygulamanızın bir Sürükle ve bırak işlemi zaman söz konusu gibi değişecektir.  
  
 Fare işaretçisi değiştirmek için birincil ayarlayarak yoludur <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> veya <xref:System.Windows.Forms.Control.DefaultCursor%2A> denetiminin yeni bir özellik <xref:System.Windows.Forms.Cursor>. Fare işaretçisi değiştirme örnekleri görmek için aşağıdaki kod örneğinde <xref:System.Windows.Forms.Cursor> sınıfı. Ayrıca, <xref:System.Windows.Forms.Cursors> sınıfı bir dizi gösterir <xref:System.Windows.Forms.Cursor> işaretçileri, bir yandan benzer bir işaretçi gibi birçok farklı türde nesneleri. Fare işaretçisini denetim üzerinde olduğunda, bir kum saati benzeyen, bekleme işaretçisi görüntülemek için kullanın <xref:System.Windows.Forms.Control.UseWaitCursor%2A> özelliği <xref:System.Windows.Forms.Control> sınıfı.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.Cursor>
- [Bir Windows Forms Uygulamasında Fare Girdisi](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
- [Windows Forms'ta Sürükle ve Bırak İşlevi](../../../docs/framework/winforms/drag-and-drop-functionality-in-windows-forms.md)
