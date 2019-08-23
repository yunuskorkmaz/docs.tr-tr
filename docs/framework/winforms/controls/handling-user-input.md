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
ms.openlocfilehash: f92b742c3f6feec72e5b3150204d7d984636281d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934086"
---
# <a name="handling-user-input"></a>Kullanıcı Girişini İşleme
Bu konuda, tarafından <xref:System.Windows.Forms.Control?displayProperty=nameWithType>sunulan ana klavye ve fare olayları açıklanmaktadır. Bir olayı işlerken, Denetim yazarları olaya bir temsilci eklemek yerine `On`Protected *EventName* metodunu geçersiz kılmalıdır. Olayları gözden geçirmek için bkz. [bir bileşenden olayları yükseltme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).  
  
> [!NOTE]
> Bir olayla ilişkili veri yoksa, temel sınıfın <xref:System.EventArgs> bir örneği, *EventName* yöntemine bir bağımsız değişken `On`olarak geçirilir.  
  
## <a name="keyboard-events"></a>Klavye olayları  
 Denetiminizin işleyebileceği ortak klavye olayları, ve <xref:System.Windows.Forms.Control.KeyDown> <xref:System.Windows.Forms.Control.KeyUp>' dir <xref:System.Windows.Forms.Control.KeyPress>.  
  
|Olay adı|Geçersiz kılınacak Yöntem|Olayın açıklaması|  
|----------------|------------------------|--------------------------|  
|`KeyDown`|`void OnKeyDown(KeyEventArgs)`|Yalnızca bir tuşa başlangıçta basıldığında tetiklenir.|  
|`KeyPress`|`void OnKeyPress`<br /><br /> `(KeyPressEventArgs)`|Her tuşa basıldığında oluşturulur. Bir anahtar kapalıysa, işletim sistemi tarafından tanımlanan <xref:System.Windows.Forms.Control.KeyPress> yineleme hızında bir olay oluşturulur.|  
|`KeyUp`|`void OnKeyUp(KeyEventArgs)`|Bir anahtar bırakıldığında tetiklenir.|  
  
> [!NOTE]
> Klavye girişini işlemek, yukarıdaki tablodaki olayları geçersiz kılmadan ve bu konunun kapsamının ötesinde önemli ölçüde karmaşıktır. Daha fazla bilgi için [Windows Forms Içindeki Kullanıcı girişi](../user-input-in-windows-forms.md)bölümüne bakın.  
  
## <a name="mouse-events"></a>Fare olayları  
 Denetiminizin işleyebileceği fare olayları,,,, ve <xref:System.Windows.Forms.Control.MouseDown> <xref:System.Windows.Forms.Control.MouseHover> <xref:System.Windows.Forms.Control.MouseMove> <xref:System.Windows.Forms.Control.MouseEnter> <xref:System.Windows.Forms.Control.MouseLeave> 'dir<xref:System.Windows.Forms.Control.MouseUp>.  
  
|Olay adı|Geçersiz kılınacak Yöntem|Olayın açıklaması|  
|----------------|------------------------|--------------------------|  
|`MouseDown`|`void OnMouseDown(MouseEventArgs)`|İşaretçi denetimin üzerindeyken fare düğmesine basıldığında tetiklenir.|  
|`MouseEnter`|`void OnMouseEnter(EventArgs)`|İşaretçi denetimin bölgesine ilk kez girdiğinde tetiklenir.|  
|`MouseHover`|`void OnMouseHover(EventArgs)`|İşaretçi denetimin üzerine geldiğinde tetiklenir.|  
|`MouseLeave`|`void OnMouseLeave(EventArgs)`|İşaretçi denetimin bölgesinden ayrıldığında tetiklenir.|  
|`MouseMove`|`void OnMouseMove(MouseEventArgs)`|İşaretçi denetimin bölgesinde ne zaman geçerse tetiklenir.|  
|`MouseUp`|`void OnMouseUp(MouseEventArgs)`|İşaretçi denetimin üzerindeyken fare düğmesi bırakıldığında veya işaretçi denetimin bölgesinden ayrıldığında tetiklenir.|  
  
 Aşağıdaki kod parçası, <xref:System.Windows.Forms.Control.MouseDown> olayı geçersiz kılan bir örnek gösterir.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#7)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#7)]  
  
 Aşağıdaki kod parçası, <xref:System.Windows.Forms.Control.MouseMove> olayı geçersiz kılan bir örnek gösterir.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#8)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#8)]  
  
 Aşağıdaki kod parçası, <xref:System.Windows.Forms.Control.MouseUp> olayı geçersiz kılan bir örnek gösterir.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#9)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#9)]  
  
 `FlashTrackBar` Örnek için tüm kaynak kodu için bkz [. nasıl yapılır: Ilerleme durumunu](how-to-create-a-windows-forms-control-that-shows-progress.md)gösteren bir Windows Forms denetimi oluşturun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms Denetimlerindeki Olaylar](events-in-windows-forms-controls.md)
- [Olay Tanımlama](defining-an-event-in-windows-forms-controls.md)
- [Olaylar](../../../standard/events/index.md)
- [Windows Forms'ta Kullanıcı Girdisi](../user-input-in-windows-forms.md)
