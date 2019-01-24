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
ms.openlocfilehash: a60ad943edae3775b00be99c08ad992af935ac13
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636462"
---
# <a name="handling-user-input"></a>Kullanıcı Girişini İşleme
Bu konu tarafından sağlanan ana klavye ve fare olayları açıklar <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Bir olay işleme, denetim yazarları korumalı geçersiz kılmalıdır `On` *EventName* bir temsilci olaya eklemek yerine yöntemi. Olayları gözden geçirmek için bkz: [Raising Events bir bileşenin](https://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).  
  
> [!NOTE]
>  Bir olay, temel sınıfın bir örneği ile ilişkili hiçbir veri olup olmadığını <xref:System.EventArgs> bağımsız değişken olarak geçirilen `On` *EventName* yöntemi.  
  
## <a name="keyboard-events"></a>Klavye olayları  
 Denetiminiz işleyebileceği ortak klavye olayları <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, ve <xref:System.Windows.Forms.Control.KeyUp>.  
  
|Olay adı|Geçersiz kılma yöntemi|Olay açıklaması|  
|----------------|------------------------|--------------------------|  
|`KeyDown`|`void OnKeyDown(KeyEventArgs)`|Yalnızca bir anahtar başlangıçta basıldığında oluşturulur.|  
|`KeyPress`|`void OnKeyPress`<br /><br /> `(KeyPressEventArgs)`|Bir tuşa basıldığında her zaman oluşturulur. Bir anahtar aşağı yapılmazsa bir <xref:System.Windows.Forms.Control.KeyPress> olayı işletim sistemi tarafından tanımlanan yineleme hızında oluşturulur.|  
|`KeyUp`|`void OnKeyUp(KeyEventArgs)`|Bir tuş bırakıldığında oluşturulur.|  
  
> [!NOTE]
>  Klavye girişini işleme olayları önceki tabloda geçersiz kılma daha önemli ölçüde daha karmaşıktır ve bu konunun kapsamı dışındadır. Daha fazla bilgi için [Windows Forms'ta kullanıcı girdisi](../../../../docs/framework/winforms/user-input-in-windows-forms.md).  
  
## <a name="mouse-events"></a>Fare olayları  
 Denetiminiz işleyebilir fare olayları <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave>, <xref:System.Windows.Forms.Control.MouseMove>, ve <xref:System.Windows.Forms.Control.MouseUp>.  
  
|Olay adı|Geçersiz kılma yöntemi|Olay açıklaması|  
|----------------|------------------------|--------------------------|  
|`MouseDown`|`void OnMouseDown(MouseEventArgs)`|İşaretçi denetimin üzerine üzerindeyken fare düğmesine basıldığında oluşturulur.|  
|`MouseEnter`|`void OnMouseEnter(EventArgs)`|İşaretçi denetimin bölge ilk girdiğinde oluşturulur.|  
|`MouseHover`|`void OnMouseHover(EventArgs)`|İşaretçi denetimin üzerine geldiğinde oluşturulur.|  
|`MouseLeave`|`void OnMouseLeave(EventArgs)`|İşaretçi denetimin bölge ayrıldığında oluşturulur.|  
|`MouseMove`|`void OnMouseMove(MouseEventArgs)`|İşaretçiyi denetimin bölgede hareket ettiğinde oluşturulur.|  
|`MouseUp`|`void OnMouseUp(MouseEventArgs)`|Fare düğmesi denetimin üzerine işaretçiyse veya işaretçiyi denetimin bölge ayrıldığında bırakıldığında oluşturulur.|  
  
 Aşağıdaki kod parçası, geçersiz kılma bir örnek gösterilmektedir <xref:System.Windows.Forms.Control.MouseDown> olay.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#7)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#7)]  
  
 Aşağıdaki kod parçası, geçersiz kılma bir örnek gösterilmektedir <xref:System.Windows.Forms.Control.MouseMove> olay.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#8)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#8)]  
  
 Aşağıdaki kod parçası, geçersiz kılma bir örnek gösterilmektedir <xref:System.Windows.Forms.Control.MouseUp> olay.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#9)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#9)]  
  
 İçin tam kaynak kodu `FlashTrackBar` örnek için bkz: [nasıl yapılır: İlerleme durumunu gösteren Windows Forms denetimi oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Windows Forms Denetimlerindeki Olaylar](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)
- [Olay Tanımlama](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)
- [Olaylar](../../../../docs/standard/events/index.md)
- [Windows Forms'ta Kullanıcı Girdisi](../../../../docs/framework/winforms/user-input-in-windows-forms.md)
