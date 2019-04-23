---
title: 'Nasıl yapılır: Bir Şekli Resim Dokusuyla Doldurma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], using with brushes
- bitmaps [Windows Forms], using texture
- shapes [Windows Forms], filling with images
ms.assetid: 508da5a6-2433-4d2b-9680-eaeae4e96e3b
ms.openlocfilehash: 099bc9f5359f19439f308f28a6766d470956daea
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59177326"
---
# <a name="how-to-fill-a-shape-with-an-image-texture"></a>Nasıl yapılır: Bir Şekli Resim Dokusuyla Doldurma
Kullanarak kapalı şekil bir doku ile doldurabilirsiniz <xref:System.Drawing.Image> sınıfı ve <xref:System.Drawing.TextureBrush> sınıfı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir elips görüntü ile doldurur. Kod oluşturur bir <xref:System.Drawing.Image> nesnesi ve ardından, söz konusu adreslerinde <xref:System.Drawing.Image> nesne bağımsız değişkeni olarak bir <xref:System.Drawing.TextureBrush.%23ctor%2A> Oluşturucusu. Üçüncü deyim görüntüyü ölçeklendirir ve dördüncü deyimi yinelenen kopyaları Ölçeklendirilen görüntünün bir elips doldurur.  
  
 Aşağıdaki kodda, <xref:System.Drawing.TextureBrush.Transform%2A> çizildiğinde önce görüntüye uygulanan dönüşüm özelliği içerir. Özgün resmin 640 piksel genişliği ve yüksekliği 480 piksel sahip olduğunu varsayın. Dönüştürme, görüntü yatay ve dikey ölçekleme değerleri ayarlayarak 75 × 75 küçültür.  
  
> [!NOTE]
>  Aşağıdaki örnekte, 75 x 75 görüntü boyutu olduğundan ve 150 × 250 elips boyutudur. Görüntü doldurma elipsin daha küçük olduğu için üç nokta ile görüntü döşenir. Görüntüyü yatay ve dikey olarak şekli sınırına kadar yinelenir, anlamına gelir döşeme ulaşıldı. Döşeme hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir şekli bir görüntüyle döşeme](how-to-tile-a-shape-with-an-image.md).  
  
 [!code-csharp[System.Drawing.UsingABrush#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingABrush#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şekilleri Doldurmak için Fırça Kullanma](using-a-brush-to-fill-shapes.md)
