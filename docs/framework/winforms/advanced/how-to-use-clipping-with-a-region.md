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
ms.openlocfilehash: bfc40d985ec12a30b73935ace7ef034aadbd5385
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-clipping-with-a-region"></a>Nasıl yapılır: Bir Bölgeyle Kırpma Kullanma
Özelliklerinden birini <xref:System.Drawing.Graphics> kırpma bölgesinin bir sınıftır. Gerçekleştirilen tüm çizim bir verilen <xref:System.Drawing.Graphics> nesnedir, kırpma bölgesi kısıtlı <xref:System.Drawing.Graphics> nesnesi. Kırpma bölgesinin çağırarak ayarlayabileceğiniz <xref:System.Drawing.Graphics.SetClip%2A> yöntemi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tek bir Çokgen oluşan bir yol oluşturur. Ardından bu yola göre bir bölge kodu oluşturur. Bölge geçirilir <xref:System.Drawing.Graphics.SetClip%2A> yöntemi bir <xref:System.Drawing.Graphics> nesnesi ve ardından iki dizeyi çizilir.  
  
 Aşağıdaki çizimde kırpılmış dizeleri gösterir.  
  
 ![Küçük](../../../../docs/framework/winforms/advanced/media/clip1.png "clip1")  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [GDI+'daki Bölgeler](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)  
 [Bölgeleri Kullanma](../../../../docs/framework/winforms/advanced/using-regions.md)
