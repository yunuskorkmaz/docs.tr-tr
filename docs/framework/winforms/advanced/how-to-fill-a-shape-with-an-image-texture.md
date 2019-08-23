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
ms.openlocfilehash: 42c456137f84c6fa657ba5a09727eae052a45376
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911684"
---
# <a name="how-to-fill-a-shape-with-an-image-texture"></a>Nasıl yapılır: Bir Şekli Resim Dokusuyla Doldurma
Bir kapalı şekli, <xref:System.Drawing.Image> sınıfını <xref:System.Drawing.TextureBrush> ve sınıfını kullanarak bir dokuyla doldurabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir elipsi görüntüyle doldurur. Kod bir <xref:System.Drawing.Image> nesne oluşturur ve sonra bu <xref:System.Drawing.Image> nesnenin adresini bir <xref:System.Drawing.TextureBrush.%23ctor%2A> oluşturucuya bağımsız değişken olarak geçirir. Üçüncü ifade resmi ölçeklendirir ve dördüncü ifade, elipsi ölçeklenmiş görüntünün yinelenen kopyalarıyla doldurur.  
  
 Aşağıdaki kodda, <xref:System.Drawing.TextureBrush.Transform%2A> özelliği, çizilmeden önce görüntüye uygulanan dönüştürmeyi içerir. Orijinal görüntünün genişliği 640 piksel ve 480 piksel yüksekliğinde olduğunu varsayalım. Dönüştürme, yatay ve dikey ölçekleme değerlerini ayarlayarak görüntüyü 75 × 75 ' e küçültür.  
  
> [!NOTE]
> Aşağıdaki örnekte, görüntü boyutu 75 × 75 ve elips boyutu 150 × 250 ' dir. Görüntü, doldurdukları elipsin daha küçük olduğundan, elips görüntüyle döşenir. Döşeme, şeklin sınırına ulaşılana kadar görüntünün yatay ve dikey olarak yinelenme anlamına gelir. Döşeme hakkında daha fazla bilgi için bkz [. nasıl yapılır: Görüntüyle](how-to-tile-a-shape-with-an-image.md)bir şekil döşeme.  
  
 [!code-csharp[System.Drawing.UsingABrush#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingABrush#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnek, Windows Forms kullanımı için tasarlanmıştır ve <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.Control.Paint> olay işleyicisinin bir parametresi olan gerektirir `e`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şekilleri Doldurmak için Fırça Kullanma](using-a-brush-to-fill-shapes.md)
