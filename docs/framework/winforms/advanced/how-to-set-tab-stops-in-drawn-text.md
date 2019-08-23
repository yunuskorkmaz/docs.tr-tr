---
title: 'Nasıl yapılır: Çizilmiş Metinde Sekme Durakları Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing with tab stops
- tabs [Windows Forms], drawn text
ms.assetid: 64878f98-39ba-4303-b63f-0859ab682eeb
ms.openlocfilehash: 8821f6170b8ba588e3197ef54eab14c2719a6cc3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947826"
---
# <a name="how-to-set-tab-stops-in-drawn-text"></a>Nasıl yapılır: Çizilmiş Metinde Sekme Durakları Ayarlama
Bir <xref:System.Drawing.StringFormat.SetTabStops%2A> <xref:System.Drawing.StringFormat> <xref:System.Drawing.Graphics.DrawString%2A> nesnenin yöntemini çağırarak ve sonra bu nesneyi <xref:System.Drawing.Graphics> sınıfının yöntemine geçirerek metin için sekme duraklarının ayarlanabilir olmasını sağlayabilirsiniz. <xref:System.Drawing.StringFormat>  
  
> [!NOTE]
> , <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType> Bayraklı metin için sekme duraklarının eklenmesini desteklemez, ancak <xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType> bayrağı kullanarak var olan sekme duraklarının genişleyebilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sekme duraklarının 150, 250 ve 350 olduğunu belirler. Daha sonra kod, ad ve test puanları sekmeli bir listesini görüntüler.  
  
 Aşağıdaki çizimde sekmeli metin gösterilmektedir:  
  
 ![Ad ve puanları sekmeli bir listesini gösteren ekran görüntüsü.](./media/how-to-set-tab-stops-in-drawn-text/tab-list-names-test-scores.png)  
  
 Aşağıdaki kod <xref:System.Drawing.StringFormat.SetTabStops%2A> yöntemine iki bağımsız değişken geçirir. İkinci bağımsız değişken sekme uzaklıklarını içeren bir dizidir. Geçirilen ilk bağımsız değişken 0 <xref:System.Drawing.StringFormat.SetTabStops%2A> ' dır ve dizideki ilk kaydırmanın, sınırlayıcı dikdörtgenin sol kenarı olan 0 konumundan ölçüldüğünü gösterir.  
  
 [!code-csharp[System.Drawing.FontsAndText#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.FontsAndText#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- Yukarıdaki örnek, Windows Forms kullanımı için tasarlanmıştır ve bir parametresi <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.PaintEventHandler>olan ' ı gerektirir `e`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yazı Tipleri ve Metin Kullanma](using-fonts-and-text.md)
- [Nasıl yapılır: GDI ile metin çizme](how-to-draw-text-with-gdi.md)
