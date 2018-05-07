---
title: 'Nasıl yapılır: Bir Şekli Görüntü Dokusuyla Doldurma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], using with brushes
- bitmaps [Windows Forms], using texture
- shapes [Windows Forms], filling with images
ms.assetid: 508da5a6-2433-4d2b-9680-eaeae4e96e3b
ms.openlocfilehash: c1eb090bebcced125193c1db16087b6165d27ff3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-fill-a-shape-with-an-image-texture"></a>Nasıl yapılır: Bir Şekli Görüntü Dokusuyla Doldurma
Kullanarak bir dokuyla kapalı bir şekil doldurabilirsiniz <xref:System.Drawing.Image> sınıfı ve <xref:System.Drawing.TextureBrush> sınıfı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek elips bir görüntü ile doldurur. Kod oluşturur bir <xref:System.Drawing.Image> nesne ve daha sonra adresini geçirir <xref:System.Drawing.Image> nesne bağımsız değişkeni olarak bir <xref:System.Drawing.TextureBrush.%23ctor%2A> Oluşturucusu. Üçüncü ifade görüntüyü ölçeklendirir ve dördüncü ifade Ölçeklendirilen görüntünün yinelenen kopyalarla elips doldurur.  
  
 Aşağıdaki kodda, <xref:System.Drawing.TextureBrush.Transform%2A> özelliği çizildiğinde önce görüntüye uygulanan dönüştürme içerir. Özgün görüntüsüne 640 piksel genişliği ve yüksekliği 480 piksel sahip olduğunu varsayın. Dönüştürme resmi yatay ve dikey ölçekleme değerlerini ayarlayarak 75 × 75 küçültür.  
  
> [!NOTE]
>  Aşağıdaki örnekte, görüntü boyutu 75 × 75'tir ve üç nokta boyutu 150 × 250'dir. Görüntü, doldurma elips küçük olduğu için üç nokta görüntüyle döşenir. Döşeme görüntü yatay ve dikey olarak şekli sınır kadar yinelenir, anlamına gelir erişilmiştir. Döşeme hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir şekli bir görüntüyle döşeme](../../../../docs/framework/winforms/advanced/how-to-tile-a-shape-with-an-image.md).  
  
 [!code-csharp[System.Drawing.UsingABrush#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingABrush#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Şekilleri Doldurmak için Fırça Kullanma](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
