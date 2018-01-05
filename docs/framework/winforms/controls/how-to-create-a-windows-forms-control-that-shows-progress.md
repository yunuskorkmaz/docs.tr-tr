---
title: "Nasıl yapılır: İlerleme Durumunu Gösteren Windows Forms Denetimi Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], progress tracking
- controls [Windows Forms], creating
- progress [Windows Forms], reporting [Windows Forms]
- FlashTrackBar custom control
ms.assetid: 24c5a2e3-058c-4b8d-a217-c06e6a130c2f
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 76ce5cd67b66dea47f5bd12e78bb27179b391257
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-windows-forms-control-that-shows-progress"></a>Nasıl yapılır: İlerleme Durumunu Gösteren Windows Forms Denetimi Oluşturma
Aşağıdaki kod örneğinde adlı özel bir denetim gösterilir `FlashTrackBar` kullanıcı düzeyinde veya uygulama ilerlemesini göstermek için kullanılabilir. Gradyan ilerleme görsel olarak sunmak için kullanır.  
  
 `FlashTrackBar` Denetim aşağıdaki kavramlar gösterilmektedir:  
  
-   Özel özellikler tanımlama.  
  
-   Özel olaylar tanımlama. (`FlashTrackBar` tanımlar `ValueChanged` olay.)  
  
-   Geçersiz kılma <xref:System.Windows.Forms.Control.OnPaint%2A> denetimi çizmek için mantığın yöntemi.  
  
-   Alan kullanarak denetim çizim için kullanılabilir bilgi işlem kendi <xref:System.Windows.Forms.Control.ClientRectangle%2A> özelliği. `FlashTrackBar`bunu yapar, `OptimizedInvalidate` yöntemi.  
  
-   Windows Forms Tasarımcısı'nda değiştirildiğinde serileştirme ya da kalıcılığı bir özellik için uygulama. `FlashTrackBar`tanımlar `ShouldSerializeStartColor` ve `ShouldSerializeEndColor` seri hale getirme yöntemleri kendi `StartColor` ve `EndColor` özellikleri.  
  
 Tarafından tanımlanan özel özellikler aşağıdaki tabloda gösterilmektedir `FlashTrackBar`.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|`AllowUserEdit`|Kullanıcı tıklatıp sürükleyerek flash izleme çubuğu değerini değiştirebilir olup olmadığını gösterir.|  
|`EndColor`|İzleme çubuğu Bitiş rengini belirtir.|  
|`DarkenBy`|Ön plan gradyan göre arka plan koyu için ne kadar belirtir.|  
|`Max`|İzleme çubuğu en büyük değerini belirtir.|  
|`Min`|İzleme çubuğu en küçük değerini belirtir.|  
|`StartColor`|Geçişin başlangıç rengini belirtir.|  
|`ShowPercentage`|Yüzde geçişin görüntülenip görüntülenmeyeceğini gösterir.|  
|`ShowValue`|Geçerli değeri geçişin görüntülenip görüntülenmeyeceğini gösterir.|  
|`ShowGradient`|İzleme çubuğu geçerli değerini gösteren bir renk gradyan görüntüleyip görüntülemeyeceğini gösterir.|  
|-   `Value`|İzleme çubuğu geçerli değeri belirtir.|  
  
 Aşağıdaki tabloda ek üyeleri tarafından tanımlanan gösterilmektedir `FlashTrackBar:` özellik değişti olayı ve olayını yöntemi.  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`ValueChanged`|Olan olay zaman yükseltilmiş `Value` çubuğu değişiklikleri izleme özelliği.|  
|`OnValueChanged`|Başlatır yöntemi `ValueChanged` olay.|  
  
> [!NOTE]
>  `FlashTrackBar`kullanan <xref:System.EventArgs> olay verileri için sınıf ve <xref:System.EventHandler> olay temsilci için.  
  
 Karşılık gelen işlemek için *EventName* olayları `FlashTrackBar` öğesinden devralınan aşağıdaki yöntemlerini geçersiz kılar <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:  
  
-   <xref:System.Windows.Forms.Control.OnPaint%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseDown%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseMove%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseUp%2A>  
  
-   <xref:System.Windows.Forms.Control.OnResize%2A>  
  
 Karşılık gelen özellik değişti olayları işlemek için `FlashTrackBar` öğesinden devralınan aşağıdaki yöntemlerini geçersiz kılar <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:  
  
-   <xref:System.Windows.Forms.Control.OnBackColorChanged%2A>  
  
-   <xref:System.Windows.Forms.Control.OnBackgroundImageChanged%2A>  
  
-   <xref:System.Windows.Forms.Control.OnTextChanged%2A>  
  
## <a name="example"></a>Örnek  
 `FlashTrackBar` Denetim tanımlayan iki UI türü düzenleyici `FlashTrackBarValueEditor` ve `FlashTrackBarDarkenByEditor`, aşağıdaki kod listesinde gösterilir. `HostApp` Sınıfını kullanan `FlashTrackBar` bir Windows formunda denetimi.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#1)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#1)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarDarkenByEditor.cs#10)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarDarkenByEditor.vb#10)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarValueEditor.cs#20)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarValueEditor.vb#20)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/HostApp.cs#30)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/HostApp.vb#30)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tasarım zamanı desteği genişletme](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 [Windows Forms Denetimi Geliştirmenin Esasları](../../../../docs/framework/winforms/controls/windows-forms-control-development-basics.md)
