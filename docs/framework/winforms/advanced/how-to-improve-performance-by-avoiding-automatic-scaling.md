---
title: 'Nasıl yapılır: Otomatik Ölçeklendirmeyi Önleyerek Performansı Artırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- automatic scaling
- images [Windows Forms], improving performance
- images [Windows Forms], using without automatic scaling
- performance [Windows Forms], improving image
ms.assetid: 5fe2c95d-8653-4d55-bf0d-e5afa28f223b
ms.openlocfilehash: dd1a1545dce33de1ce11938db8495ebf311dadda
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506210"
---
# <a name="how-to-improve-performance-by-avoiding-automatic-scaling"></a>Nasıl yapılır: Otomatik Ölçeklendirmeyi Önleyerek Performansı Artırma
Hangi performans azalır, çizin GDI +'da otomatik olarak bir görüntü ölçeklendirme. Alternatif olarak, hedef dikdörtgenin boyutlarına geçirerek görüntüsü ölçeklendirme denetleyebilirsiniz <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi.  
  
 Aşağıdaki örnek, çağrısı <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi bir sol üst köşesinde belirtir (50, 30) ancak hedef dikdörtgene belirtmiyor.  
  
 [!code-csharp[System.Drawing.WorkingWithImages#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.WorkingWithImages#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#31)]  
  
 Bu kolay sürümüdür ancak <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi gerekli bağımsız değişken sayısı bakımından, onu mutlaka en verimli değildir. GDI + (genellikle 96 inç başına nokta) tarafından kullanılan çözüm depolanan çözüm farklı olup olmadığını <xref:System.Drawing.Image> nesne, ardından <xref:System.Drawing.Graphics.DrawImage%2A> yönteminin resim ayarlayacaktır. Örneğin, bir <xref:System.Drawing.Image> nesne 216 piksel genişliğinde ve 72 dpi saklı yatay çözünürlük değeri vardır. 216/72 3, çünkü <xref:System.Drawing.Graphics.DrawImage%2A> görüntüyü 3 inç genişliğini 96 inç başına nokta çözünürlükte sahip olacak şekilde ölçeklendirir. Diğer bir deyişle, <xref:System.Drawing.Graphics.DrawImage%2A> 96 x 3 = 288 genişliğini içeren bir görüntüyü görüntüler piksel.  
  
 Ekran çözünürlüğünü 96 inç başına nokta farklı olsa bile 96 inç başına nokta ekran çözünürlüğü gibi GDI +'da büyük olasılıkla resmi ölçeklenir. Çünkü GDI + <xref:System.Drawing.Graphics> nesnesi bir cihaz bağlamı ile ilişkili olan ve sorgular GDI +'da ekran çözünürlüğünü için cihaz bağlamı, sonuç genellikle gerçek ekran çözünürlüğü ne olursa olsun, 96'dır. Hedef dikdörtgenin belirterek bir otomatik ölçeklendirme kaçınabilirsiniz <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki kez aynı resim çizer. İlk durumda, hedef dikdörtgenin yüksekliğini ve genişliğini belirtilmeyen ve otomatik olarak ölçeklendirilir. İkinci durumda, genişlik ve yükseklik (piksel cinsinden ölçülür) hedef dikdörtgenin genişliğini ve yüksekliğini orijinal görüntünün aynı olacak şekilde belirtilir. Aşağıdaki çizimde, iki kez çizilir görüntüde gösterilmektedir:  
  
 ![Ölçeklendirilmiş doku ile görüntüleri gösteren ekran görüntüsü.](./media/how-to-improve-performance-by-avoiding-automatic-scaling/two-scaled-texture-images.png)  
  
 [!code-csharp[System.Drawing.WorkingWithImages#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.WorkingWithImages#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#32)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi. Bir görüntü adı ve sisteminize göre geçerli yolu texture.jpg değiştirin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görüntüler, Bit Eşlemler ve Meta Dosyaları](images-bitmaps-and-metafiles.md)
- [Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma](working-with-images-bitmaps-icons-and-metafiles.md)
