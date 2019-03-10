---
title: 'Nasıl yapılır: Küçük resimler oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thumbnail images [Windows Forms], creating
- images [Windows Forms], creating thumbnails
ms.assetid: e956242a-1e5b-4217-a3cf-5f3fb45d00ba
ms.openlocfilehash: 3ed1fb6a9a7fc8e7ded6ae0e124ca7dcbf0f3c98
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716965"
---
# <a name="how-to-create-thumbnail-images"></a>Nasıl yapılır: Küçük resimler oluşturma
Bir küçük resim, bir resmin küçük bir sürümüdür. Bir küçük resim çağırarak oluşturabileceğiniz <xref:System.Drawing.Image.GetThumbnailImage%2A> yöntemi bir <xref:System.Drawing.Image> nesne.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek oluşturan bir <xref:System.Drawing.Image> JPG dosyası nesne. Özgün resmin 640 piksel genişliği ve yüksekliği 479 piksel sahiptir. Kod 100 piksel genişliği ve yüksekliği 100 piksel olan bir küçük resim görüntüsü oluşturur.  
  
 Küçük resim görüntüsü aşağıda gösterilmiştir.  
  
 ![Küçük resim görüntüsü](./media/thumbnail1.png "Thumbnail1")  
  
> [!NOTE]
>  Bu örnekte, bir geri çağırma yöntemi bildirildi ancak hiç kullanılmadı. Bu, GDI +'in tüm sürümleri destekler.  
  
 [!code-csharp[System.Drawing.WorkingWithImages#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.WorkingWithImages#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi. Örneği çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yeni bir Windows Forms uygulaması oluşturun.  
  
2.  Örnek kod formuna ekleyin.  
  
3.  Form için bir işleyici oluşturma <xref:System.Windows.Forms.Control.Paint> olay  
  
4.  İçinde <xref:System.Windows.Forms.Control.Paint> işleyicisi, çağrı `GetThumbnail` yöntemi ve pass `e` için <xref:System.Windows.Forms.PaintEventArgs>.  
  
5.  Küçük resmini yapmak istediğiniz görüntü dosyasını bulun.  
  
6.  İçinde `GetThumbnail` yöntemi, bir yol belirtin ve dosya adı görüntünüze.  
  
7.  Örneği çalıştırmak için F5 tuşuna basın.  
  
     Form üzerinde bir 100 x 100 küçük resim görünür.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Görüntüler, Bit Eşlemler ve Meta Dosyaları](images-bitmaps-and-metafiles.md)
- [Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma](working-with-images-bitmaps-icons-and-metafiles.md)
