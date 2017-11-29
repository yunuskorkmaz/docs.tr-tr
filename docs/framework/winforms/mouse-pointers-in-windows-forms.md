---
title: "Windows Forms'ta Fare İşaretçileri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pointers [Windows Forms], setting
- mouse pointers
- mouse cursors
- mouse pointers [Windows Forms], setting
- cursors [Windows Forms], setting
- mouse [Windows Forms], cursors
ms.assetid: c3400d85-de5b-42e8-abc3-d6088d69ee53
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4fb0e193ccbced719f30ede91cb59cd51dd349a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="mouse-pointers-in-windows-forms"></a>Windows Forms'ta Fare İşaretçileri
Fare *işaretçi*, ekranında fareyle kullanıcı girişi için odak noktası belirten bir bit eşlem olduğundan, bazen imleci adlandırılır. Bu konu Windows Forms'ta fare işaretçisini genel bir bakış sağlar ve bazı değiştirebilir ve fare işaretçisini denetim yolları açıklanmaktadır.  
  
## <a name="accessing-the-mouse-pointer"></a>Fare işaretçisini erişme  
 Fare işaretçisini tarafından temsil edilen <xref:System.Windows.Forms.Cursor> sınıfı ve her <xref:System.Windows.Forms.Control> sahip bir <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> denetleyen işaretçisi belirten özellik. <xref:System.Windows.Forms.Cursor> Sınıfı içeriyor gibi işaretçi tanımlayan özelliği <xref:System.Windows.Forms.Cursor.Position%2A> ve <xref:System.Windows.Forms.Cursor.HotSpot%2A> özellikleri ve işaretçi görünümünü gibi değiştirebilirsiniz yöntemleri <xref:System.Windows.Forms.Cursor.Show%2A>, <xref:System.Windows.Forms.Cursor.Hide%2A>, ve <xref:System.Windows.Forms.Cursor.DrawStretched%2A> yöntemleri.  
  
## <a name="controlling-the-mouse-pointer"></a>Fare işaretçisini denetleme  
 Bazen, fare işaretçisini kullanılabilir veya fare konumunu değiştirme alanı sınırlamak isteyebilirsiniz. Almak veya Fare kullanmada geçerli konumu ayarlamak <xref:System.Windows.Forms.Cursor.Position%2A> özelliği <xref:System.Windows.Forms.Cursor>. Ayrıca, fare işaretçisini kullanılabilir alanı sınırlayabilirsiniz ayarı <xref:System.Windows.Forms.Cursor.Clip%2A> özelliği. Küçük, varsayılan olarak, tüm ekranı alanıdır.  
  
## <a name="changing-the-mouse-pointer"></a>Fare işaretçisini değiştirme  
 Fare işaretçisini değiştirme kullanıcıya geri bildirim sağlama önemli bir yoludur. Örneğin, fare işaretçisini işleyiciler değiştirilebilir <xref:System.Windows.Forms.Control.MouseEnter> ve <xref:System.Windows.Forms.Control.MouseLeave> olayları hesaplamalar yaşanan kullanıcıya bildirmek için ve kullanıcı etkileşimi denetiminde sınırlamak için. Bazı durumlarda, fare işaretçisini, uygulamanızı bir Sürükle ve bırak işlemi zaman söz konusu gibi sistem olayları nedeniyle değiştirir.  
  
 Fare işaretçisini değiştirmek için birincil ayarlayarak yoludur <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> veya <xref:System.Windows.Forms.Control.DefaultCursor%2A> yeni bir denetimin özelliğini <xref:System.Windows.Forms.Cursor>. Fare işaretçisini değiştirme örnekleri görmek için aşağıdaki kod örneğinde <xref:System.Windows.Forms.Cursor> sınıfı. Ayrıca, <xref:System.Windows.Forms.Cursors> sınıfı kullanıma sunan bir dizi <xref:System.Windows.Forms.Cursor> işaretçileri el benzer bir işaretçi gibi birçok farklı türde nesneleri. Fare işaretçisini denetiminde olduğunda bir kum saati benzer, bekleme işaretçisi görüntülemek için kullanın <xref:System.Windows.Forms.Control.UseWaitCursor%2A> özelliği <xref:System.Windows.Forms.Control> sınıfı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Cursor>  
 [Forms bir Windows uygulamasında fare girdisi](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)  
 [Windows Forms'ta sürükle ve bırak işlevi](../../../docs/framework/winforms/drag-and-drop-functionality-in-windows-forms.md)
