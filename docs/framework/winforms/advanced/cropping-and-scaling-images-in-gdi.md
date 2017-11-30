---
title: "GDI+'da Görüntü Kırpma ve Ölçeklendirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 63e1e55e57d586cbbca87361b95c18f0f53b8c75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="cropping-and-scaling-images-in-gdi"></a>GDI+'da Görüntü Kırpma ve Ölçeklendirme
Kullanabileceğiniz <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi <xref:System.Drawing.Graphics> sınıf çizme ve vektör görüntüler ve ızgara görüntüleri getirin. <xref:System.Drawing.Graphics.DrawImage%2A>bağımsız değişkenlerle tedarik çeşitli yollardan şekilde bir aşırı yüklenmiş yöntemidir.  
  
## <a name="drawimage-variations"></a>DrawImage farklılıkları  
 Bir çeşitlemesi <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi alır bir <xref:System.Drawing.Bitmap> ve <xref:System.Drawing.Rectangle>. Dikdörtgen çizme işleminin hedefi belirtir; diğer bir deyişle, resim çizmek dikdörtgen belirtir. Hedef dikdörtgen boyutu özgün görüntüsüne boyutundan farklı ise, görüntüyü hedef dikdörtgen uyacak şekilde ölçeklendirilir. Aşağıdaki kod örneğinde, üç kez aynı resim çizmek gösterilmiştir: hiçbir ölçeklendirme ile bir kez, bir genişletme ile bir kez ve bir sıkıştırma ile bir kez:  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#31)]  
  
 Aşağıdaki çizim üç resim göstermektedir.  
  
 ![Ölçeklendirme](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art06.gif "AboutGdip03_Art06")  
  
 Bazı varyasyonları <xref:System.Drawing.Graphics.DrawImage%2A> yöntemine sahip bir hedef dikdörtgen parametre yanı sıra, bir kaynak dikdörtgen parametre. Kaynak dikdörtgen parametre çizmek için özgün görüntüsüne kısmını belirtir. Hedef dikdörtgen, söz konusu bölümü görüntünün çizmek dikdörtgen belirtir. Hedef dikdörtgen boyutu kaynak dikdörtgen boyutundan farklı ise, resmi hedef dikdörtgen uyacak şekilde ölçeklendirilir.  
  
 Aşağıdaki kod örneğinde nasıl oluşturulacağını gösteren bir <xref:System.Drawing.Bitmap> Runner.jpg dosyasından. Görüntünün tümünü hiçbir adresindeki ölçeklendirme ile çizilir (0, 0). Görüntünün küçük bir kısmı iki kez çizilir sonra: bir kez bir sıkıştırma ile bir kez bir genişletme.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#32)]  
  
 Aşağıdaki çizimde ölçeklendirilmemiş resim ve sıkıştırılmış ve genişletilmiş görüntü bölümünü gösterir.  
  
 ![Kırpma ve ölçeklendirme](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art07.gif "AboutGdip03_Art07")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Resimler, bit eşlemler ve meta dosyaları](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Resimler, bit eşlemler, simgeler ve meta dosyaları ile çalışma](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
