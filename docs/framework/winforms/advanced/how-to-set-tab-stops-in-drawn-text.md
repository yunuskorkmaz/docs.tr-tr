---
title: 'Nasıl yapılır: Çizilmiş metinde sekme durakları ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing with tab stops
- tabs [Windows Forms], drawn text
ms.assetid: 64878f98-39ba-4303-b63f-0859ab682eeb
ms.openlocfilehash: 2b3d019db1fd3e9eeb9def1c18b54d293e5faca9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722431"
---
# <a name="how-to-set-tab-stops-in-drawn-text"></a>Nasıl yapılır: Çizilmiş metinde sekme durakları ayarlama
Metin için sekme durakları çağırarak ayarlayabilirsiniz <xref:System.Drawing.StringFormat.SetTabStops%2A> yöntemi bir <xref:System.Drawing.StringFormat> nesnesi ve ardından geçirmeden <xref:System.Drawing.StringFormat> nesnesini <xref:System.Drawing.Graphics.DrawString%2A> yöntemi <xref:System.Drawing.Graphics> sınıfı.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType> Sekme duraklarını çizilen metni, mevcut sekmesini genişletebilirsiniz rağmen ekleme desteği kullanarak durdurur mu <xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType> bayrağı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, 150, 250 ve 350 sekme durakları ayarlar. Ardından, kod adları ve test puanlarını sekmeli listesini görüntüler.  
  
 Aşağıdaki çizim sekmeli metni gösterir.  
  
 ![Yazı tipleri metin](./media/fontstext4.png "fontstext4")  
  
 Aşağıdaki kod iki bağımsız değişken geçirir <xref:System.Drawing.StringFormat.SetTabStops%2A> yöntemi. İkinci bağımsız değişkeni sekmesini uzaklıkları içeren bir dizidir. Geçirilen ilk bağımsız değişken <xref:System.Drawing.StringFormat.SetTabStops%2A> dizideki ilk uzaklığını konumu 0, sınırlayıcı dikdörtgenini sol kenarı ölçülür belirten, 0'dır.  
  
 [!code-csharp[System.Drawing.FontsAndText#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.FontsAndText#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yazı Tipleri ve Metin Kullanma](using-fonts-and-text.md)
- [Nasıl yapılır: GDI ile metin çizme](how-to-draw-text-with-gdi.md)
