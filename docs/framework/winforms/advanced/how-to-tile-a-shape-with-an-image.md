---
title: 'Nasıl yapılır: Bir Şekli Bir Resimle Döşeme'
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
ms.openlocfilehash: ad7b8737a63028e533cadfa6db56b063eb943f22
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61954940"
---
# <a name="how-to-tile-a-shape-with-an-image"></a>Nasıl yapılır: Bir Şekli Bir Resimle Döşeme
Dikdörtgen görüntüleri yalnızca kutucukları birbirinin yanına bir katı kapsayacak şekilde yerleştirilebilir gibi diğer yanındaki (döşeme) bir şekil doldurmak için yerleştirilebilir. Bir şeklin içinin döşeme için bir doku fırça kullanın. Oluşturduğunuzda bir <xref:System.Drawing.TextureBrush> nesnesi oluşturucusuna geçirmeniz bağımsız değişkenlerden biri olan bir <xref:System.Drawing.Image> nesne. Bir şeklin içinin boyamak için doku fırça kullandığınızda, bu görüntüyü yinelenen kopyalarını şekli doldurulur.  
  
 Kaydırma modu özelliğini <xref:System.Drawing.TextureBrush> nesneyi belirleyen dikdörtgen bir kılavuzda yinelenen olarak nasıl yönlendirilmiş görüntüsüdür. Tüm kutucukları kılavuzunda aynı yönü hale getirebilir veya sonraki bir kılavuz konumundan Çevir görüntü yapabilirsiniz. Çevirme yatay olabilir dikey ya da her ikisini de. Aşağıdaki örnekler, farklı türde çevirme ile döşeme göstermektedir.  
  
### <a name="to-tile-an-image"></a>Resim kutucuğunda için  
  
- Bu örnek, bir 200 × 200 dikdörtgen kutucuğa 75 × 75 aşağıda kullanır.  
  
 ![Döşeme 1](./media/tile1.gif "tile1")  
  
- Aşağıdaki çizim dikdörtgeni görüntünün ile nasıl döşenir gösterir. Tüm kutucuklar aynı yönü gerektiğini unutmayın; hiçbir çevirme yoktur.  
  
 ![Döşeme 2](./media/tile2.gif "tile2")  
  
 [!code-csharp[System.Drawing.UsingABrush#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingABrush#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#31)]  
  
### <a name="to-flip-an-image-horizontally-while-tiling"></a>Görüntüyü döşeme sırasında yatay olarak çevrilip çevrilmediği  
  
- Bu örnek, bir 200 × 200 dikdörtgen doldurmak için 75 × 75 görüntünün aynısını kullanır. Görüntüyü yatay olarak çevrilip çevrilmediği gerçekleştirilmeye ayarlayın. Aşağıdaki çizim dikdörtgeni görüntünün ile nasıl döşenir gösterir. Belirli bir satırda sonraki bir kutucuğunuz taşırken, görüntüyü yatay olarak çevrilmiş unutmayın.  
  
 ![Döşeme 3](./media/tile3.gif "tile3")  
  
 [!code-csharp[System.Drawing.UsingABrush#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.UsingABrush#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#32)]  
  
### <a name="to-flip-an-image-vertically-while-tiling"></a>Görüntüyü dikey olarak döşeme sırasında ters çevirmek için  
  
- Bu örnek, bir 200 × 200 dikdörtgen doldurmak için 75 × 75 görüntünün aynısını kullanır. Görüntüyü dikey olarak çevrilip çevrilmediği gerçekleştirilmeye ayarlayın.  
  
     [!code-csharp[System.Drawing.UsingABrush#33](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#33)]
     [!code-vb[System.Drawing.UsingABrush#33](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#33)]  
  
### <a name="to-flip-an-image-horizontally-and-vertically-while-tiling"></a>Görüntü çalışırken döşeme Yatayda ve Dikeyde ters çevirmek için  
  
- Bu örnek, bir 200 × 200 dikdörtgen kutucuğa 75 × 75 görüntünün aynısını kullanır. Görüntüyü yatay ve dikey olarak çevrilip çevrilmediği gerçekleştirilmeye ayarlayın. Aşağıdaki çizim dikdörtgeni görüntünün tarafından nasıl döşenir gösterir. Belirli bir satıra gelecek bir kutucuğunuz gitme, görüntüyü yatay olarak çevrilmiş ve sonraki belirli bir sütundaki bir kutucuğunuz taşırken, görüntüyü dikey olarak çevrilmiş unutmayın.  
  
 ![Döşeme 5](./media/tile5.gif "tile5")  
  
 [!code-csharp[System.Drawing.UsingABrush#34](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.UsingABrush#34](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şekilleri Doldurmak için Fırça Kullanma](using-a-brush-to-fill-shapes.md)
