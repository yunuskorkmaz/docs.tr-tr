---
title: 'Nasıl yapılır: Yazı Tipi Ölçümleri Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [Windows Forms], obtaining metrics
- font metrics [Windows Forms], obtaining
ms.assetid: ff7c0616-67f7-4fa2-84ee-b8d642f2b09b
ms.openlocfilehash: 24cada3962339cae0608bbe01e070a0b8e256e73
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119060"
---
# <a name="how-to-obtain-font-metrics"></a>Nasıl yapılır: Yazı Tipi Ölçümleri Alma
<xref:System.Drawing.FontFamily> Sınıfı belirli ailesi/stil birleşimi için çeşitli ölçümleri alma aşağıdaki yöntemleri sağlar:  
  
-   <xref:System.Drawing.FontFamily.GetEmHeight%2A>(FontStyle)  
  
-   <xref:System.Drawing.FontFamily.GetCellAscent%2A>(FontStyle)  
  
-   <xref:System.Drawing.FontFamily.GetCellDescent%2A>(FontStyle)  
  
-   <xref:System.Drawing.FontFamily.GetLineSpacing%2A>(FontStyle)  
  
 Bu yöntem tarafından döndürülen sayılara boyutu ve belirli bir ölçü bağımsız oldukları yazı tipi tasarım birimlerinde olduğundan <xref:System.Drawing.Font> nesne.  
  
 Aşağıdaki çizim, çeşitli ölçümleri gösterir.  
  
 ![Yazı tipleri metin](./media/fontstext7a.png "fontstext7A")  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Normal stili Arial yazı tipi ailesinin ölçümleri görüntüler. Kod ayrıca oluşturur bir <xref:System.Drawing.Font> (Arial ailesinde göre) nesne boyutu 16 piksel ve görüntüler (piksel cinsinden) için belirli ölçümleri <xref:System.Drawing.Font> nesne.  
  
 Örnek kodun çıktısı aşağıdaki çizimde gösterilmektedir.  
  
 ![Yazı tipleri metin](./media/csfontstext8.png "csFontsText8")  
  
 Önceki çizimde çıkış ilk iki satırlık unutmayın. <xref:System.Drawing.Font> Nesne döndürür, 16, boyutunu ve <xref:System.Drawing.FontFamily> 2.048 bir em yüksekliğini nesnesini döndürür. Bu iki sayı (16 ve 2.048) yazı tipi tasarım birimleri ve (Bu durum piksel cinsinden) birimleri arasında dönüştürme için önemli olduğu <xref:System.Drawing.Font> nesne.  
  
 Örneğin, ascent tasarım birimlerinden piksel olarak şu şekilde dönüştürebilirsiniz:  
  
 ![Yazı tipleri metin](./media/fontstext9.png "FontsText9")  
  
 Aşağıdaki kod konumlandırır metni dikey olarak ayarlayarak <xref:System.Drawing.PointF.Y%2A> veri üyesi bir <xref:System.Drawing.PointF> nesne. Y koordinatını artırılana `font.Height` her yeni satır metin için. <xref:System.Drawing.Font.Height%2A> Özelliği bir <xref:System.Drawing.Font> nesnesini döndürür (piksel cinsinden) satır aralığı için o belirli <xref:System.Drawing.Font> nesne. Bu örnekte, bir sayı tarafından döndürülen <xref:System.Drawing.Font.Height%2A> 19 olduğu. Bu satır aralığı ölçüm piksel dönüştürerek elde edilen (bir tamsayıya yuvarlanır) numarasıyla aynı olduğunu unutmayın.  
  
 (Boyut veya em boyutu olarak da bilinir) em yüksekliği ascent ve iniş olmadığını unutmayın. Hücre Yüksekliği ascent ve iniş çağrılır. Hücre Yüksekliği iç önde gelen eksi em boyuna eşit. Hücre Yüksekliği artı başlıca dış satır aralığını eşit.  
  
 [!code-csharp[System.Drawing.FontsAndText#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.FontsAndText#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Formlarında Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
- [Yazı Tipleri ve Metin Kullanma](using-fonts-and-text.md)
