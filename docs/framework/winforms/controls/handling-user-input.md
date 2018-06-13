---
title: Kullanıcı Girişini İşleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], user input using code
- custom controls [Windows Forms], keyboard events using code
- custom controls [Windows Forms], mouse events using code
ms.assetid: d9b12787-86f6-4022-8e0f-e12d312c4af2
ms.openlocfilehash: a230611bfbb0a7f21a96de22674377887cc93c2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527806"
---
# <a name="handling-user-input"></a>Kullanıcı Girişini İşleme
Bu konu, tarafından sağlanan ana klavye ve fare olaylarını açıklar <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Bir olay işlenirken denetim yazarları korumalı kılmalıdır `On` *EventName* olaya bir temsilci ekleme yerine yöntemi. Olayları gözden geçirmek için bkz: [oluşturma olayları bir bileşenin](http://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).  
  
> [!NOTE]
>  Temel sınıfının bir örneği bir olayla ilişkili veri olup olmadığını <xref:System.EventArgs> bağımsız değişken olarak geçirilen `On` *EventName* yöntemi.  
  
## <a name="keyboard-events"></a>Klavye olayları  
 Denetim işleyebilir ortak klavye olaylar <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, ve <xref:System.Windows.Forms.Control.KeyUp>.  
  
|Olay adı|Geçersiz kılma yöntemi|Olay açıklaması|  
|----------------|------------------------|--------------------------|  
|`KeyDown`|`void OnKeyDown(KeyEventArgs)`|Yalnızca zaman bir anahtar başlangıçta basıldığında oluşturuldu.|  
|`KeyPress`|`void OnKeyPress`<br /><br /> `(KeyPressEventArgs)`|Bir tuşa her zaman oluşturulur. Bir anahtar aşağı tutulursa bir <xref:System.Windows.Forms.Control.KeyPress> olayı, işletim sistemi tarafından tanımlanan yineleme oranı oluşturulur.|  
|`KeyUp`|`void OnKeyUp(KeyEventArgs)`|Bir anahtar yayımlandığında oluşturulur.|  
  
> [!NOTE]
>  Klavye girişini işleme yukarıdaki tabloda olayları geçersiz kılma daha önemli ölçüde daha karmaşıktır ve bu konunun kapsamı dışındadır. Daha fazla bilgi için bkz: [Windows Forms uygulamasında kullanıcı girdisi](../../../../docs/framework/winforms/user-input-in-windows-forms.md).  
  
## <a name="mouse-events"></a>Fare olayları  
 Denetim işleyebilir fare olaylar <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave>, <xref:System.Windows.Forms.Control.MouseMove>, ve <xref:System.Windows.Forms.Control.MouseUp>.  
  
|Olay adı|Geçersiz kılma yöntemi|Olay açıklaması|  
|----------------|------------------------|--------------------------|  
|`MouseDown`|`void OnMouseDown(MouseEventArgs)`|İşaretçinin üzerinde denetim durumdayken fare düğmesini basılı tetiklenir.|  
|`MouseEnter`|`void OnMouseEnter(EventArgs)`|İşaretçinin ilk denetimi bölge girdiğinde oluşturuldu.|  
|`MouseHover`|`void OnMouseHover(EventArgs)`|İşaretçi denetimin üzerine geldiğinde oluşturulur.|  
|`MouseLeave`|`void OnMouseLeave(EventArgs)`|İşaretçi denetimi bölge ayrıldığında oluşturuldu.|  
|`MouseMove`|`void OnMouseMove(MouseEventArgs)`|İşaretçi denetimi bölgede geldiğinde oluşturulur.|  
|`MouseUp`|`void OnMouseUp(MouseEventArgs)`|Fare düğmesini işaretçinin üzerinde denetim veya işaretçinin denetimi bölge bırakır kullanımdayken yayımlandığında oluşturulur.|  
  
 Aşağıdaki kod parçası geçersiz kılma örneği gösterir <xref:System.Windows.Forms.Control.MouseDown> olay.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#7)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#7)]  
  
 Aşağıdaki kod parçası geçersiz kılma örneği gösterir <xref:System.Windows.Forms.Control.MouseMove> olay.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#8)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#8)]  
  
 Aşağıdaki kod parçası geçersiz kılma örneği gösterir <xref:System.Windows.Forms.Control.MouseUp> olay.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#9)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#9)]  
  
 İçin tam kaynak kodu `FlashTrackBar` örnek için bkz: [nasıl yapılır: Windows Forms denetimi olduğunu gösteren ilerlemesi oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms Denetimlerindeki Olaylar](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 [Olay Tanımlama](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)  
 [Olaylar](../../../../docs/standard/events/index.md)  
 [Windows Forms'ta Kullanıcı Girdisi](../../../../docs/framework/winforms/user-input-in-windows-forms.md)
