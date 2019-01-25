---
title: 'Nasıl yapılır: Döndürme, yansıtma ve eğme görüntüleri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], reflecting
- images [Windows Forms], rotating
- images [Windows Forms], skewing
ms.assetid: a3bf97eb-63ed-425a-ba07-dcc65efb567c
ms.openlocfilehash: 2150e7797095b88227b499ec5481a3ce521270e9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667917"
---
# <a name="how-to-rotate-reflect-and-skew-images"></a>Nasıl yapılır: Döndürme, yansıtma ve eğme görüntüleri
Döndürme, yansıtma ve özgün resmin sol, sağ ve sol alt köşeler için hedef noktaları belirleyerek görüntü eğme. Üç hedef noktaları özgün dikdörtgen görüntü için bir eğdiğinizde Paralel Kenar eşleyen bir ilişkili dönüşümü belirler.  
  
## <a name="example"></a>Örnek  
 Örneğin, özgün resmin sol üst köşesinde bir dikdörtgen olduğunu varsayın (0, 0), sağ üst köşede (100, 0) ve sol alt köşede (0, 50). Bu harita varsayalım artık üç hedef noktalarına gibi işaret eder.  
  
|Özgün noktası|Hedef noktası|  
|--------------------|-----------------------|  
|Sol (0, 0)|(200, 20)|  
|Sağ üst köşede (100, 0)|(110, 100)|  
|Sol (0, 50)|(250, 30)|  
  
 Aşağıdaki çizimde, özgün resmin ve için eğdiğinizde Paralel Kenar eşlenen görüntüyü gösterir. Özgün resmin dengesiz, yansıtılan, döndürülen, çevrilmiş ve. X ekseni orijinal görüntünün üst kenarı boyunca çalıştırılma satıra eşlendi (200, 20) ve (110, 100). Y ekseni özgün resmin sol kenarda çalıştırılma satıra eşlendi (200, 20) ve (250, 30).  
  
 ![Şeritler](../../../../docs/framework/winforms/advanced/media/stripes1.gif "Stripes1")  
  
 Aşağıdaki çizimde, bir fotoğraf görüntüsüne uygulanacağı benzer bir dönüştürmeyi gösterir.  
  
 ![Dönüştürülen Tırmanıcı](../../../../docs/framework/winforms/advanced/media/transformedclimber.png "TransformedClimber")  
  
 Aşağıdaki çizim, meta dosyası için uygulanan benzer bir dönüştürmeyi gösterir.  
  
 ![Dönüştürülmüş meta](../../../../docs/framework/winforms/advanced/media/transformedmetafile.png "TransformedMetafile")  
  
 Aşağıdaki örnek ilk çizimde gösterilen görüntüleri oluşturur.  
  
 [!code-csharp[System.Drawing.WorkingWithImages#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.WorkingWithImages#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi. Değiştirdiğinizden emin olun `Stripes.bmp` yoluyla sisteminize göre geçerli bir görüntü.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
