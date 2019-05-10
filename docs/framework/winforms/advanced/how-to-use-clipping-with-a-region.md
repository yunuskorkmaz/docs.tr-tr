---
title: 'Nasıl yapılır: Bir Bölgeyle Kırpma Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regions [Windows Forms], clipping
- regions [Windows Forms], restricting drawing surface
ms.assetid: 43d121b4-e14c-4901-b25c-2d6c25ba4e29
ms.openlocfilehash: e62be137b36a2f369c02151466154f6b3bab090b
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063846"
---
# <a name="how-to-use-clipping-with-a-region"></a>Nasıl yapılır: Bir Bölgeyle Kırpma Kullanma
Özelliklerinden birini <xref:System.Drawing.Graphics> kırpma bölgesini sınıftır. Tüm çizim tarafından bir verilen <xref:System.Drawing.Graphics> nesnedir, söz konusu küçük bölgesiyle sınırlı <xref:System.Drawing.Graphics> nesne. Kırpma bölgesini çağırarak ayarlayabileceğiniz <xref:System.Drawing.Graphics.SetClip%2A> yöntemi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek tek bir Çokgen oluşan bir yol oluşturur. Ardından bu yola göre bir bölge kodu oluşturur. Bölge geçirilir <xref:System.Drawing.Graphics.SetClip%2A> yöntemi bir <xref:System.Drawing.Graphics> nesnesi ve ardından iki dizeyi çizilmiştir.  
  
 Aşağıdaki çizim, kırpılmış dizelerden gösterir:  
  
 ![Sabitlenmiş dizeleri gösteren ekran görüntüsü.](./media/how-to-use-clipping-with-a-region/clipped-strings-polygon.png)  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.MiscLegacyTopics#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GDI+'daki Bölgeler](regions-in-gdi.md)
- [Bölgeleri Kullanma](using-regions.md)
