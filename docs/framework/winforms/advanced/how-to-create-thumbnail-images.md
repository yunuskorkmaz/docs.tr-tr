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
ms.openlocfilehash: 786a92d99f5e7a0c27f502efa9a5fe617ac4d4d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923748"
---
# <a name="how-to-create-thumbnail-images"></a>Nasıl yapılır: Küçük Resimler Oluşturma
Küçük resim görüntüsü görüntünün küçük bir sürümüdür. <xref:System.Drawing.Image.GetThumbnailImage%2A> Bir<xref:System.Drawing.Image> nesnenin yöntemini çağırarak bir küçük resim görüntüsü oluşturabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir jpg <xref:System.Drawing.Image> dosyasından bir nesne oluşturur. Orijinal görüntüde 640 piksellik bir genişlik ve 479 piksellik yükseklik bulunur. Kod, 100 piksel genişlik ve 100 piksel yüksekliğinde bir küçük resim oluşturur.  
  
 Aşağıdaki çizim, küçük resim görüntüsünü göstermektedir:  
  
 ![Çıkış küçük resmini gösteren ekran görüntüsü.](./media/how-to-create-thumbnail-images/construct-thumbnail-image.png)  
  
> [!NOTE]
> Bu örnekte, bir geri çağırma yöntemi tanımlanmış, ancak hiç kullanılmadı. Bu, tüm GDI+ sürümlerini destekler.  
  
 [!code-csharp[System.Drawing.WorkingWithImages#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.WorkingWithImages#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnek, Windows Forms kullanımı için tasarlanmıştır ve <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.Control.Paint> olay işleyicisinin bir parametresi olan gerektirir `e`. Örneği çalıştırmak için aşağıdaki adımları izleyin:  
  
1. Yeni bir Windows Forms uygulaması oluşturun.  
  
2. Forma örnek kodu ekleyin.  
  
3. Formun <xref:System.Windows.Forms.Control.Paint> olayı için bir işleyici oluşturun  
  
4. İşleyicisinde metodunu çağırın ve `e` için<xref:System.Windows.Forms.PaintEventArgs>geçişyapın. <xref:System.Windows.Forms.Control.Paint> `GetThumbnail`  
  
5. Küçük resmini oluşturmak istediğiniz bir görüntü dosyası bulun.  
  
6. `GetThumbnail` Yönteminde, görüntünüzün yolunu ve dosya adını belirtin.  
  
7. Örneği çalıştırmak için F5 tuşuna basın.  
  
     Formda 100 ile 100 arasında bir küçük resim görüntülenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görüntüler, Bit Eşlemler ve Meta Dosyaları](images-bitmaps-and-metafiles.md)
- [Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma](working-with-images-bitmaps-icons-and-metafiles.md)
