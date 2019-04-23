---
title: GDI+'da Görüntü Kırpma ve Ölçeklendirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, scaling images
- GDI+, cropping images
- images [Windows Forms], cropping
- compressing data [Windows Forms], images
- images [Windows Forms], expansion
- images [Windows Forms], scaling
- rectangles [Windows Forms], source
- rectangles [Windows Forms], destination
- images [Windows Forms], compression
ms.assetid: ad5daf26-005f-45bc-a2af-e0e97777a21a
ms.openlocfilehash: c3cdb06e99770808461f9266fb5f07df9074149b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59183735"
---
# <a name="cropping-and-scaling-images-in-gdi"></a>GDI+'da Görüntü Kırpma ve Ölçeklendirme
Kullanabileceğiniz <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi <xref:System.Drawing.Graphics> çizmek ve vektör görüntüleri ve ızgara resimlerin konumlandırmak için sınıf. <xref:System.Drawing.Graphics.DrawImage%2A> bağımsız değişkenleriyle sağlayabilirsiniz birkaç yolu olduğundan aşırı yüklü bir yönteminiz var.  
  
## <a name="drawimage-variations"></a>DrawImage farklılıkları  
 Bir çeşitlemesi <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi alır bir <xref:System.Drawing.Bitmap> ve <xref:System.Drawing.Rectangle>. Dikdörtgen çizme işlemi için hedef belirtir. diğer bir deyişle, hangi görüntü çizme dikdörtgen belirtir. Hedef dikdörtgenin boyut orijinal görüntünün boyutundan farklıysa, hedef dikdörtgenin sığacak şekilde ölçeklendirilir. Aşağıdaki kod örneği, üç kez aynı görüntü çizmek gösterilmektedir: hiçbir ölçeklendirme ile bir kez, bir genişletme ile bir kez ve bir sıkıştırma ile bir kez:  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#31)]  
  
 Aşağıdaki çizim üç resimleri gösterir.  
  
 ![Ölçeklendirme](./media/aboutgdip03-art06.gif "AboutGdip03_Art06")  
  
 Bazı çeşitleri <xref:System.Drawing.Graphics.DrawImage%2A> yöntemine sahip bir hedef dikdörtgenin parametre yanı sıra kaynak dikdörtgenin parametresi. Kaynak dikdörtgenin parametresi çizmek için özgün görüntü kısmı belirtir. Hedef dikdörtgenin kaydedileceği görüntünün kısmı çizmek dikdörtgen belirtir. Hedef dikdörtgenin boyutu kaynak dikdörtgenin boyutundan farklı ise, resmi hedef dikdörtgenin sığacak şekilde ölçeklendirilir.  
  
 Aşağıdaki kod örneğinde nasıl oluşturulacağını gösterir. bir <xref:System.Drawing.Bitmap> Runner.jpg dosyasından. Ölçeklendirme yok, görüntünün çizilir (0, 0). Görüntünün küçük bir kısmını iki kez çizilir sonra: bir kez bir sıkıştırma ile bir kez bir genişletme.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#32)]  
  
 Ölçeklendirilmemiş resim ve görüntü sıkıştırılmış ve genişletilmiş bölümleri aşağıda gösterilmiştir.  
  
 ![Kırpma ve ölçeklendirme](./media/aboutgdip03-art07.gif "AboutGdip03_Art07")  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görüntüler, Bit Eşlemler ve Meta Dosyaları](images-bitmaps-and-metafiles.md)
- [Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma](working-with-images-bitmaps-icons-and-metafiles.md)
