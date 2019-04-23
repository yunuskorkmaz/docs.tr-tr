---
title: 'Nasıl yapılır: MenuStrip (Windows Forms) seçenek düğmeleri görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
ms.openlocfilehash: e764c7e181870d8faf6157cacc13164977ce2e3b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59306241"
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a>Nasıl yapılır: MenuStrip (Windows Forms) seçenek düğmeleri görüntüleme
Seçenek düğmeleri, radyo düğmeleri olarak da bilinir, kullanıcılar yalnızca teker teker seçebilir dışında onay kutularını işaretleyin benzerdir. Ancak varsayılan olarak <xref:System.Windows.Forms.ToolStripMenuItem> sınıfı seçenek düğmesini davranışı sağlamaz, sınıfı menü öğeleri için seçenek düğmesini davranışı uygulamak için özelleştirebileceğiniz onay kutusu davranış sağlayan bir <xref:System.Windows.Forms.MenuStrip> denetimi.  
  
 Zaman <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> özelliği bir menü öğesinin `true`, kullanıcılar, bir onay işareti görünümünü değiştirmek için öğeyi tıklatabilirsiniz. <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> Özelliği öğesinin geçerli durumunu gösterir. Temel seçenek düğmesini davranışı uygulamak için bir öğe seçildiğinde, ayarladığınız emin olmalısınız <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> özelliği için daha önce seçilen öğe için `false`.  
  
 Aşağıdaki yordamlarda, bunu uygulamak açıklanır ve devralınan bir sınıf ek işlevsellik <xref:System.Windows.Forms.ToolStripMenuItem> sınıfı. `ToolStripRadioButtonMenuItem` Sınıfı üyeleri gibi geçersiz kılmalar <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> ve <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> seçim davranışı ve seçenek düğmeleri görünümünü sağlamak için. Ayrıca, bu sınıfı geçersiz kılan <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> üst öğe seçili değilse, bir alt menüsünde Seçenekler özelliğini devre dışı.  
  
### <a name="to-implement-option-button-selection-behavior"></a>Seçenek düğmesini seçme davranışı uygulamak için  
  
1. Başlatma <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> özelliğini `true` öğe seçimini etkinleştirmek için.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#110](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]  
  
2. Geçersiz kılma <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> yöntemi yeni bir öğe seçildiğinde daha önce seçilen öğenin seçimini temizleyin.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#120](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]  
  
3. Geçersiz kılma <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> yöntemi zaten seçildi bir öğe sonuçlandığını emin olmak için değil seçimi temizleyin.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#130](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]  
  
### <a name="to-modify-the-appearance-of-the-option-button-items"></a>Seçenek düğmesini öğelerin görünümünü değiştirmek için  
  
1. Geçersiz kılma <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> yöntemini kullanarak varsayılan onay işareti ile bir düğmeyi değiştirin <xref:System.Windows.Forms.RadioButtonRenderer> sınıfı.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#140](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]  
  
2. Geçersiz kılma <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>, ve <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> fare durumunu izlemek ve emin olmak için yöntemleri <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> yöntemi doğru seçenek düğmesini durumu boyar.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#150](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]  
  
### <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a>Üst öğe seçilmediğinde alt menü seçenekleri devre dışı bırakmak için  
  
1. Geçersiz kılma <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> özelliği, böylece her ikisi de sahip bir üst öğesi varsa öğe devre dışı bir <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> değerini `true` ve <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> değerini `false`.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#160](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]  
  
2. Geçersiz kılma <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> abone olmak için yöntem <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> olay üst öğesi.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#170](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]  
  
3. Üst öğenin işleyicisinde <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> olay öğe ekranı ile yeni etkin durumu güncelleştirmek için geçersiz.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#180](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği eksiksiz `ToolStripRadioButtonMenuItem` sınıfı ve <xref:System.Windows.Forms.Form> sınıfı ve `Program` seçenek düğmesini davranışını göstermek için sınıf.  
  
 [!code-csharp[ToolStripRadioButtonMenuItem#000](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
 [!code-vb[ToolStripRadioButtonMenuItem#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Drawing ve System.Windows.Forms derlemelere başvuruları.  
  
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
- [Nasıl yapılır: Özel ToolStripRenderer uygulama](how-to-implement-a-custom-toolstriprenderer.md)
