---
title: 'Nasıl yapılır: Bir MenuStrip İçinde Seçenek Düğmeleri Görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
ms.openlocfilehash: f3010e71396ce562e9dbdefd4b75b36f3a81ffb3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735517"
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a>Nasıl yapılır: Bir MenuStrip İçinde Seçenek Düğmeleri Görüntüleme (Windows Forms)

Radyo düğmeleri olarak da bilinen seçenek düğmeleri, kullanıcılar tek seferde yalnızca bir tane seçim yapmak dışında onay kutularına benzerdir. Varsayılan olarak <xref:System.Windows.Forms.ToolStripMenuItem> sınıfı seçenek düğmesi davranışı sağlamasa da, sınıf, bir <xref:System.Windows.Forms.MenuStrip> denetimindeki menü öğeleri için seçenek düğmesi davranışını uygulamak üzere özelleştirebileceğiniz onay kutusu davranışı sağlar.

Bir menü öğesinin <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> özelliği `true`olduğunda, kullanıcılar bir onay işaretinin görüntülenmesini değiştirmek için öğeye tıklabilirler. <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> özelliği öğenin geçerli durumunu gösterir. Temel seçenek düğmesi davranışını uygulamak için, bir öğe seçildiğinde, daha önce seçilen öğenin <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> özelliğini `false`olarak ayarlamanız gerekir.

Aşağıdaki yordamlarda, <xref:System.Windows.Forms.ToolStripMenuItem> sınıfını devralan bir sınıfta bu ve ek işlevselliğin nasıl uygulanacağı açıklanır. `ToolStripRadioButtonMenuItem` sınıfı, seçenek düğmelerinin seçim davranışını ve görünümünü sağlamak için <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> ve <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> gibi üyeleri geçersiz kılar. Ayrıca, bu sınıf, üst öğe seçilmediği takdirde bir alt menüdeki seçeneklerin devre dışı bırakılması için <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> özelliğini geçersiz kılar.

## <a name="to-implement-option-button-selection-behavior"></a>Seçenek düğmesi seçimi davranışını uygulamak için

1. Öğe seçimini etkinleştirmek için <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> özelliğini `true` olarak başlatın.

     [!code-csharp[ToolStripRadioButtonMenuItem#110](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]

2. Yeni bir öğe seçildiğinde, daha önce seçilen öğenin seçimini temizlemek için <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> yöntemini geçersiz kılın.

     [!code-csharp[ToolStripRadioButtonMenuItem#120](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]

3. Daha önce seçilmiş olan bir öğeyi tıklatmak seçimi temizlemez olduğundan emin olmak için <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> yöntemini geçersiz kılın.

     [!code-csharp[ToolStripRadioButtonMenuItem#130](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]

## <a name="to-modify-the-appearance-of-the-option-button-items"></a>Seçenek düğmesi öğelerinin görünüşünü değiştirmek için

1. <xref:System.Windows.Forms.RadioButtonRenderer> sınıfını kullanarak varsayılan onay işaretini bir seçenek düğmesiyle değiştirmek için <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> yöntemini geçersiz kılın.

     [!code-csharp[ToolStripRadioButtonMenuItem#140](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]

2. Farenin durumunu izlemek için <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>ve <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> yöntemlerini geçersiz kılın ve <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> yönteminin doğru seçenek düğmesi durumunu boyaytığınızdan emin olun.

     [!code-csharp[ToolStripRadioButtonMenuItem#150](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]

## <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a>Üst öğe seçilmediğinden bir alt menüdeki seçenekleri devre dışı bırakmak için

1. <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> özelliğini, hem <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> `true` hem de `false`<xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> değeri olan bir üst öğe olduğunda öğenin devre dışı bırakılması için geçersiz kılın.

     [!code-csharp[ToolStripRadioButtonMenuItem#160](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]

2. Üst öğenin <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> olayına abone olmak için <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> yöntemini geçersiz kılın.

     [!code-csharp[ToolStripRadioButtonMenuItem#170](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]

3. Üst öğe <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> olayına yönelik İşleyicide, ekranı yeni etkin durumuyla güncelleştirmek için öğeyi geçersiz kılar.

     [!code-csharp[ToolStripRadioButtonMenuItem#180](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, seçenek düğmesi davranışını göstermek için tam `ToolStripRadioButtonMenuItem` sınıfını ve bir <xref:System.Windows.Forms.Form> sınıfı ve `Program` sınıfını sağlar.

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
- [Nasıl yapılır: Özel ToolStripRenderer Uygulama](how-to-implement-a-custom-toolstriprenderer.md)
