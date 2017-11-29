---
title: "Nasıl yapılır: Bir MenuStrip İçinde Seçenek Düğmeleri Görüntüleme (Windows Forms)"
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
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 15f2d1492148a4b00a4b96844f546a4dc968eef6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a>Nasıl yapılır: Bir MenuStrip İçinde Seçenek Düğmeleri Görüntüleme (Windows Forms)
Seçenek düğmeleri, olarak da bilinen radyo düğmeleri, kullanıcılar yalnızca birer birer seçebilirsiniz onay kutularını benzerdir. Ancak varsayılan olarak <xref:System.Windows.Forms.ToolStripMenuItem> sınıfı seçenek düğmesi davranışı sağlamaz, sınıf menü öğeleri için seçenek düğmesi davranışı uygulamak için özelleştirebileceğiniz onay kutusu davranışı sağlamak bir <xref:System.Windows.Forms.MenuStrip> denetim.  
  
 Zaman <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> menü öğesi özelliği `true`, kullanıcıların bir onay işareti görüntüsünü geçiş yapmak için öğeyi tıklatabilirsiniz. <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> Özelliği öğesi geçerli durumunu gösterir. Temel seçenek düğmesi davranışı uygulamak için bir öğe seçildiğinde, ayarladığınız sağlamanız gerekir. <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> özelliği daha önce seçilen öğeye için `false`.  
  
 Aşağıdaki yordamlar bu uygulamak nasıl açıklar ve ek işlevsellik devralan bir sınıf <xref:System.Windows.Forms.ToolStripMenuItem> sınıfı. `ToolStripRadioButtonMenuItem` Sınıfı üyeleri gibi geçersiz kılmaları <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> ve <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> seçme davranışı ve seçenek düğmeleri görünümünü sağlamak için. Ayrıca, bu sınıfı geçersiz kılan <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> üst öğesi seçmediğiniz sürece bir alt menüsündeki Seçenekler özelliğini devre dışı.  
  
### <a name="to-implement-option-button-selection-behavior"></a>Seçenek düğmesi seçimi davranışı uygulamak için  
  
1.  Initialize <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> özelliğine `true` öğe seçimi etkinleştirmek için.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]  
  
2.  Geçersiz kılma <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> yeni bir öğe seçildiğinde daha önce seçilen öğenin seçimini yöntemi.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]  
  
3.  Geçersiz kılma <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> o zaten seçilmiş bir öğeyi tıklatarak emin olmak için yöntem değil seçimi temizleyin.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]  
  
### <a name="to-modify-the-appearance-of-the-option-button-items"></a>Seçenek düğmesi öğelerinin görünümünü değiştirmek için  
  
1.  Geçersiz kılma <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> yöntemi kullanarak bir seçenek düğmesine sahip varsayılan onay işareti yerine <xref:System.Windows.Forms.RadioButtonRenderer> sınıfı.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]  
  
2.  Geçersiz kılma <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>, ve <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> fare durumunu izlemek ve emin olmak için yöntemler <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> yöntemi doğru seçenek düğmesi durumu boyar.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]  
  
### <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a>Üst öğe seçilmediğinde menüdeki seçenekleri devre dışı bırakmak için  
  
1.  Geçersiz kılma <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> özelliği böylece her ikisi de sahip bir üst öğesi varsa öğesi devre dışı bir <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> değerini `true` ve <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> değerini `false`.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]  
  
2.  Geçersiz kılma <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> abone olmak için yöntem <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> üst öğenin olay.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]  
  
3.  Üst öğesi için işleyicisinde <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> olay, yeni etkin durumu ile görüntü güncellenecek öğe geçersiz.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde eksiksiz `ToolStripRadioButtonMenuItem` sınıfı ve bir <xref:System.Windows.Forms.Form> sınıfı ve `Program` sınıfı seçenek düğmesi davranışı sergiler.  
  
 [!code-csharp[ToolStripRadioButtonMenuItem#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
 [!code-vb[ToolStripRadioButtonMenuItem#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Drawing ve System.Windows.Forms derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.RadioButtonRenderer>  
 [MenuStrip denetimi](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)  
 [Nasıl yapılır: özel ToolStripRenderer uygulama](../../../../docs/framework/winforms/controls/how-to-implement-a-custom-toolstriprenderer.md)
