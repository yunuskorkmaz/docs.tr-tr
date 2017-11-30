---
title: "Nasıl yapılır: Küçük Resimler Oluşturma"
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
- thumbnail images [Windows Forms], creating
- images [Windows Forms], creating thumbnails
ms.assetid: e956242a-1e5b-4217-a3cf-5f3fb45d00ba
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2a3866274340932819a419c622c10072dd67c439
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-thumbnail-images"></a>Nasıl yapılır: Küçük Resimler Oluşturma
Küçük resim, görüntünün küçük bir sürümüdür. Küçük resim çağırarak oluşturabileceğiniz <xref:System.Drawing.Image.GetThumbnailImage%2A> yöntemi bir <xref:System.Drawing.Image> nesnesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek oluşturan bir <xref:System.Drawing.Image> JPG dosyadan nesne. Özgün görüntüsüne 640 piksel genişliği ve yüksekliği 479 piksel sahiptir. Kod 100 piksel genişliği ve yüksekliği, 100 piksel olan bir küçük resim oluşturur.  
  
 Aşağıdaki çizim, küçük resim göstermektedir.  
  
 ![Küçük resim](../../../../docs/framework/winforms/advanced/media/thumbnail1.png "Thumbnail1")  
  
> [!NOTE]
>  Bu örnekte, bir geri çağırma yöntemi bildirildi, ancak hiç kullanılmadı. GDI +'in tüm sürümleri destekler.  
  
 [!code-csharp[System.Drawing.WorkingWithImages#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.WorkingWithImages#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi. Örneği çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yeni bir Windows Forms uygulaması oluşturma.  
  
2.  Örnek kod forma ekleyin.  
  
3.  Form için bir işleyici oluşturmak <xref:System.Windows.Forms.Control.Paint> olayı  
  
4.  İçinde <xref:System.Windows.Forms.Control.Paint> işleyici, çağrı `GetThumbnail` yöntemi ve geçişi `e` için <xref:System.Windows.Forms.PaintEventArgs>.  
  
5.  Küçük resmini yapmak istediğiniz bir görüntü dosyasını bulun.  
  
6.  İçinde `GetThumbnail` yöntemi yolunu belirtin ve dosya adı görüntünüze.  
  
7.  Örneği çalıştırmak için F5 tuşuna basın.  
  
     100'e 100 küçük resim formda görünür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Resimler, bit eşlemler ve meta dosyaları](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Resimler, bit eşlemler, simgeler ve meta dosyaları ile çalışma](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
