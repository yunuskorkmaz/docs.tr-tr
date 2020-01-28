---
title: Ilerlemeyi gösteren denetim oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], progress tracking
- controls [Windows Forms], creating
- progress [Windows Forms], reporting [Windows Forms]
- FlashTrackBar custom control
ms.assetid: 24c5a2e3-058c-4b8d-a217-c06e6a130c2f
ms.openlocfilehash: 9d2cf353ba2309380221bb51733baaca1b81a5d5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731181"
---
# <a name="how-to-create-a-windows-forms-control-that-shows-progress"></a>Nasıl yapılır: İlerleme Durumunu Gösteren Windows Forms Denetimi Oluşturma
Aşağıdaki kod örneği, kullanıcının bir uygulamanın düzeyini veya ilerlemesini göstermek için kullanılabilecek `FlashTrackBar` adlı özel bir denetimi gösterir. İlerlemeyi görsel olarak göstermek için bir gradyan kullanır.  
  
 `FlashTrackBar` denetimi aşağıdaki kavramları gösterir:  
  
- Özel özellikleri tanımlama.  
  
- Özel olayları tanımlama. (`FlashTrackBar` `ValueChanged` olayını tanımlar.)  
  
- Denetimi çizmek için mantık sağlamak üzere <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemini geçersiz kılma.  
  
- <xref:System.Windows.Forms.Control.ClientRectangle%2A> özelliğini kullanarak, denetimi çizmek için kullanılabilir alan hesaplanıyor. Bunu `OptimizedInvalidate` yönteminde `FlashTrackBar`.  
  
- Windows Form Tasarımcısı değiştirildiğinde bir özellik için serileştirme veya kalıcılık uygulama. `FlashTrackBar`, `StartColor` ve `EndColor` özelliklerini serileştirmek için `ShouldSerializeStartColor` ve `ShouldSerializeEndColor` yöntemlerini tanımlar.  
  
 Aşağıdaki tabloda `FlashTrackBar`tarafından tanımlanan özel özellikler gösterilmektedir.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|`AllowUserEdit`|Kullanıcının, Flash izleme çubuğunun değerini tıklatıp sürükleyerek değiştirip değiştiremeyeceğini gösterir.|  
|`EndColor`|İzleme çubuğunun bitiş rengini belirtir.|  
|`DarkenBy`|Ön plan degradeyle ilgili olarak arka planın ne kadar koyulaştıralınacağını belirtir.|  
|`Max`|İzleme çubuğunun en büyük değerini belirtir.|  
|`Min`|İzleme çubuğunun en küçük değerini belirtir.|  
|`StartColor`|Degradenin başlangıç rengini belirtir.|  
|`ShowPercentage`|Gradyan üzerinde bir yüzde görüntülenip görüntülenmeyeceğini gösterir.|  
|`ShowValue`|Geçerli değerin gradyan üzerinde görüntülenip görüntülenmeyeceğini gösterir.|  
|`ShowGradient`|İzleme çubuğunun geçerli değeri gösteren bir renk gradyanı görüntülenip görüntülenmeyeceğini gösterir.|  
|-   `Value`|İzleme çubuğunun geçerli değerini belirtir.|  
  
 Aşağıdaki tabloda, özellik değiştirilen olay ve olayı oluşturan yöntemi `FlashTrackBar:` tarafından tanımlanan ek Üyeler gösterilmektedir.  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`ValueChanged`|İzleme çubuğunun `Value` özelliği değiştiğinde harekete geçirilen olay.|  
|`OnValueChanged`|`ValueChanged` olayını oluşturan yöntem.|  
  
> [!NOTE]
> `FlashTrackBar`, olay verileri için <xref:System.EventArgs> sınıfını ve olay temsilcisi için <xref:System.EventHandler> kullanır.  
  
 Karşılık gelen *EventName* olaylarını işlemek için `FlashTrackBar` <xref:System.Windows.Forms.Control?displayProperty=nameWithType>devralan aşağıdaki yöntemleri geçersiz kılar:  
  
- <xref:System.Windows.Forms.Control.OnPaint%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseDown%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseMove%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseUp%2A>  
  
- <xref:System.Windows.Forms.Control.OnResize%2A>  
  
 Karşılık gelen özellik tarafından değiştirilen olayları işlemek için `FlashTrackBar` <xref:System.Windows.Forms.Control?displayProperty=nameWithType>devraldığı aşağıdaki yöntemleri geçersiz kılar:  
  
- <xref:System.Windows.Forms.Control.OnBackColorChanged%2A>  
  
- <xref:System.Windows.Forms.Control.OnBackgroundImageChanged%2A>  
  
- <xref:System.Windows.Forms.Control.OnTextChanged%2A>  
  
## <a name="example"></a>Örnek  
 `FlashTrackBar` denetimi, aşağıdaki kod listelerinde gösterilen iki UI türü düzenleyicilerini `FlashTrackBarValueEditor` ve `FlashTrackBarDarkenByEditor`tanımlar. `HostApp` sınıfı bir Windows formunda `FlashTrackBar` denetimini kullanır.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#1)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#1)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarDarkenByEditor.cs#10)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarDarkenByEditor.vb#10)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarValueEditor.cs#20)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarValueEditor.vb#20)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/HostApp.cs#30)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/HostApp.vb#30)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tasarım zamanı desteğini genişletme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))
- [Windows Forms Denetimi Geliştirmenin Esasları](windows-forms-control-development-basics.md)
