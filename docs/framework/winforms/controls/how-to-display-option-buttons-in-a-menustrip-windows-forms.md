---
title: "Nasıl yapılır: Bir MenuStrip 'te seçenek düğmelerini görüntüleme (Windows Forms)"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
ms.openlocfilehash: 94d683369edd6583ad8b01c2ce3f393567a5ed75
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971932"
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a>Nasıl yapılır: Bir MenuStrip 'te seçenek düğmelerini görüntüleme (Windows Forms)

Radyo düğmeleri olarak da bilinen seçenek düğmeleri, kullanıcılar tek seferde yalnızca bir tane seçim yapmak dışında onay kutularına benzerdir. Varsayılan olarak, <xref:System.Windows.Forms.ToolStripMenuItem> sınıfı seçenek düğmesi davranışı sağlamıyorsa, bir <xref:System.Windows.Forms.MenuStrip> denetimdeki menü öğeleri için seçenek düğmesi davranışını uygulamak üzere özelleştirebileceğiniz onay kutusu davranışı sağlar.

Bir menü öğesinin özelliği olduğunda `true`, kullanıcılar bir onay işaretinin görüntülenmesini değiştirmek için öğeye tıklabilirler. <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> Özelliği, öğenin geçerli durumunu gösterir. Temel seçenek düğmesi davranışını uygulamak için, bir öğe seçildiğinde, daha önce seçilen öğenin <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> özelliğini olarak `false`ayarlamış olmanız gerekir.

Aşağıdaki yordamlar, <xref:System.Windows.Forms.ToolStripMenuItem> sınıfını devralan bir sınıfta bu ve ek işlevselliğin nasıl uygulanacağını açıklamaktadır. Sınıfı, seçenek düğmelerinin seçim davranışını <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> ve <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> görünümünü sağlamak için ve gibi üyeleri geçersiz kılar. `ToolStripRadioButtonMenuItem` Ayrıca, bu sınıf, üst <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> öğe seçilmediği takdirde alt menüdeki seçeneklerin devre dışı bırakılması için özelliği geçersiz kılar.

## <a name="to-implement-option-button-selection-behavior"></a>Seçenek düğmesi seçimi davranışını uygulamak için

1. Öğe seçimini etkinleştirmek için `true` özelliğini'ebaşlatın.<xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A>

     [!code-csharp[ToolStripRadioButtonMenuItem#110](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]

2. Yeni bir <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> öğe seçildiğinde, daha önce seçilen öğenin seçimini temizlemek için yöntemini geçersiz kılın.

     [!code-csharp[ToolStripRadioButtonMenuItem#120](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]

3. Daha önce seçilmiş olan bir öğeye tıklanmanın seçimi temizlemez olduğundan emin olmak için yönteminigeçersizkılın.<xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A>

     [!code-csharp[ToolStripRadioButtonMenuItem#130](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]

## <a name="to-modify-the-appearance-of-the-option-button-items"></a>Seçenek düğmesi öğelerinin görünüşünü değiştirmek için

1. Sınıfını kullanarak varsayılan onay işaretini bir seçenek düğmesiyle değiştirmek için yönteminigeçersizkılın.<xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> <xref:System.Windows.Forms.RadioButtonRenderer>

     [!code-csharp[ToolStripRadioButtonMenuItem#140](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]

2. <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A> <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> Farenin durumunu izlemek<xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>için,, ve yöntemlerini geçersiz kılın ve yöntemindoğruseçenekdüğmesidurumunuboyaytığınızdaneminolun.<xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>

     [!code-csharp[ToolStripRadioButtonMenuItem#150](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]

## <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a>Üst öğe seçilmediğinden bir alt menüdeki seçenekleri devre dışı bırakmak için

1. <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> Öğesinin hem`true` değeri hem de değeri`false`olanbir üst öğesi olduğunda öğenin devre dışı bırakılması için özelliği geçersiz kılın. <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A>

     [!code-csharp[ToolStripRadioButtonMenuItem#160](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]

2. Üst öğenin <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> olayına abone olmak için yönteminigeçersizkılın.<xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A>

     [!code-csharp[ToolStripRadioButtonMenuItem#170](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]

3. Üst öğe <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> olayının işleyicisinde, ekranı yeni etkin durumuyla güncelleştirmek için öğeyi geçersiz kılar.

     [!code-csharp[ToolStripRadioButtonMenuItem#180](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, tam `ToolStripRadioButtonMenuItem` sınıfı ve seçenek düğmesi davranışını göstermek için bir `Program` <xref:System.Windows.Forms.Form> sınıfı ve sınıfı sağlar.

[!code-csharp[ToolStripRadioButtonMenuItem#000](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
[!code-vb[ToolStripRadioButtonMenuItem#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]

## <a name="compiling-the-code"></a>Kod Derleniyor

Bu örnek şunları gerektirir:

- System, System. Drawing ve System. Windows. Forms derlemelerine başvurular.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RadioButtonRenderer>
- [MenuStrip Denetimi](menustrip-control-windows-forms.md)
- [Nasıl yapılır: Özel bir ToolStripRenderer uygulama](how-to-implement-a-custom-toolstriprenderer.md)
