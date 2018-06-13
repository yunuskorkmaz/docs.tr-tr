---
title: 'Nasıl yapılır: Bir Şekli Bir Görüntüyle Döşeme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- texture brushes [Windows Forms], tiling images with
- images [Windows Forms], filling shapes with
- shapes [Windows Forms], tiling with images
- bitmaps [Windows Forms], filling shapes with
ms.assetid: 6d407891-6e5c-4495-a546-3da5604e9fb8
ms.openlocfilehash: 0905f29b0f74c72979e252cf94e677d1c7e0525d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523129"
---
# <a name="how-to-tile-a-shape-with-an-image"></a>Nasıl yapılır: Bir Şekli Bir Görüntüyle Döşeme
Dikdörtgen görüntüleri yalnızca döşeme birbirinin yanına kat kapsayacak şekilde yerleştirilebilir gibi diğer yanındaki dolgu (döşeme) bir şekli yerleştirilebilir. Bir şekli iç döşeme için doku fırça kullanın. Oluşturduğunuzda bir <xref:System.Drawing.TextureBrush> nesne oluşturucuya geçirdiğiniz bağımsız değişkenlerden biri olan bir <xref:System.Drawing.Image> nesnesi. İç bir şekli kısmını boyamak için doku fırça kullandığınızda, şekil bu görüntüyü yinelenen kopyalarını dolu.  
  
 Kaydırma modu özelliğini <xref:System.Drawing.TextureBrush> nesne belirler dikdörtgen kılavuzda yinelenen nasıl görüntü yönlendirilmiş aynıdır. Tüm kutucukları ızgara aynı yönü yapabilir veya sonraki bir kılavuz konumundan Çevir görüntü yapabilirsiniz. Çevirme yatay olabilir dikey veya her ikisi de. Aşağıdaki örnekler çevirme farklı türleri ile döşeme gösterir.  
  
### <a name="to-tile-an-image"></a>Görüntü Döşeme  
  
-   Bu örnekte aşağıdaki 75 × 75 görüntü 200 × 200 dikdörtgen döşeme için kullanır.  
  
 ![Döşeme 1](../../../../docs/framework/winforms/advanced/media/tile1.gif "tile1")  
  
-   Aşağıdaki çizimde görüntüyle dikdörtgeni nasıl döşendiği gösterir. Tüm kutucukları aynı yönü gerektiğini unutmayın; hiçbir çevirme yoktur.  
  
 ![Döşeme 2](../../../../docs/framework/winforms/advanced/media/tile2.gif "tile2")  
  
 [!code-csharp[System.Drawing.UsingABrush#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingABrush#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#31)]  
  
### <a name="to-flip-an-image-horizontally-while-tiling"></a>Bir resmi yatay olarak döşeme sırasında döndürmek için  
  
-   Bu örnek aynı 75 × 75 görüntü 200 × 200 dikdörtgen doldurmak için kullanır. Kaydırma modu görüntü Yatayda ters çevirmek için ayarlanır. Aşağıdaki çizimde görüntüyle dikdörtgeni nasıl döşendiği gösterir. Belirli bir satırda sonraki bir kutucuğu taşıdığınızda, görüntünün yatay çevrilmiş unutmayın.  
  
 ![Döşeme 3](../../../../docs/framework/winforms/advanced/media/tile3.gif "tile3")  
  
 [!code-csharp[System.Drawing.UsingABrush#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.UsingABrush#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#32)]  
  
### <a name="to-flip-an-image-vertically-while-tiling"></a>Bir resmi dikey döşeme sırasında döndürmek için  
  
-   Bu örnek aynı 75 × 75 görüntü 200 × 200 dikdörtgen doldurmak için kullanır. Kaydırma modu görüntü Dikeyde ters çevirmek için ayarlanır.  
  
     [!code-csharp[System.Drawing.UsingABrush#33](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#33)]
     [!code-vb[System.Drawing.UsingABrush#33](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#33)]  
  
### <a name="to-flip-an-image-horizontally-and-vertically-while-tiling"></a>Bir resmi yatay ve dikey olarak çalışırken döşeme döndürmek için  
  
-   Bu örnek aynı 75 × 75 görüntü 200 × 200 dikdörtgen döşeme için kullanır. Kaydırma modu görüntü Yatayda ve Dikeyde ters çevirmek için ayarlanır. Aşağıdaki çizimde, görüntü tarafından dikdörtgeni nasıl döşendiği gösterir. Belirli bir satırda sonraki bir kutucuğu taşıdığınızda, görüntünün yatay çevrilmiş not alın ve belirli bir sütundaki sonraki bir kutucuğu taşıdığınızda, görüntünün dikey çevrilmiş.  
  
 ![Döşeme 5](../../../../docs/framework/winforms/advanced/media/tile5.gif "tile5")  
  
 [!code-csharp[System.Drawing.UsingABrush#34](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.UsingABrush#34](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Şekilleri Doldurmak için Fırça Kullanma](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
