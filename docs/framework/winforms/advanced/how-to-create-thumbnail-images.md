---
title: 'Nasıl yapılır: Küçük Resimler Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thumbnail images [Windows Forms], creating
- images [Windows Forms], creating thumbnails
ms.assetid: e956242a-1e5b-4217-a3cf-5f3fb45d00ba
ms.openlocfilehash: 870ea223698e48438bd4dd08597d0a6ab79cec27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521491"
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
 [Görüntüler, Bit Eşlemler ve Meta Dosyaları](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
