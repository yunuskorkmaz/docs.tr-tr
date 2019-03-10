---
title: 'Nasıl yapılır: Özel yazı tipi koleksiyonu oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- private font collections [Windows Forms], creating
- fonts [Windows Forms], creating private collections
ms.assetid: 6533d5e5-a8dc-4b76-9fc4-3bf75c8b9212
ms.openlocfilehash: 7cfd2a1fd29b58019d49c8cd5df9adb5b0873302
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723784"
---
# <a name="how-to-create-a-private-font-collection"></a>Nasıl yapılır: Özel yazı tipi koleksiyonu oluşturma
<xref:System.Drawing.Text.PrivateFontCollection> Sınıfının devraldığı <xref:System.Drawing.Text.FontCollection> soyut temel sınıf. Kullanabileceğiniz bir <xref:System.Drawing.Text.PrivateFontCollection> bir dizi uygulamanıza özel yazı nesnesine. Bir özel yazı tipi koleksiyonu yüklenen sistem yazı tiplerini ve bunun yanı sıra bilgisayarda yüklü değil yazı tipleri içerebilir. Bir özel yazı tipi koleksiyonu için bir yazı tipi dosyası eklemek için çağrı <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile%2A> yöntemi bir <xref:System.Drawing.Text.PrivateFontCollection> nesne.  
  
 <xref:System.Drawing.Text.FontCollection.Families%2A> Özelliği bir <xref:System.Drawing.Text.PrivateFontCollection> nesne içeren bir dizi <xref:System.Drawing.FontFamily> nesneleri.  
  
 Yazı tipi aileleri özel yazı tipi koleksiyondaki sayısını mutlaka koleksiyona eklenmiş olan yazı tipi dosyaları sayısı ile aynı değil. Örneğin, bir koleksiyona ArialBd.tff Times.tff ve TimesBd.tff dosyaları eklemek varsayalım. Olacaktır üç dosyayı ancak yalnızca iki ailesi koleksiyondaki Times.tff ve TimesBd.tff aynı ailesine ait olduğu için.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, aşağıdaki üç yazı tipi dosyaları ekler. bir <xref:System.Drawing.Text.PrivateFontCollection> nesnesi:  
  
-   C:\\*systemroot*\Fonts\Arial.tff (Arial, normal)  
  
-   C:\\*systemroot*\Fonts\CourBI.tff (Courier yeni, kalın italik)  
  
-   C:\\*systemroot*\Fonts\TimesBd.tff (kez yeni Roman Kalın)  
  
 Kod dizisi alır <xref:System.Drawing.FontFamily> nesnelerin <xref:System.Drawing.Text.FontCollection.Families%2A> özelliği <xref:System.Drawing.Text.PrivateFontCollection> nesne.  
  
 Her <xref:System.Drawing.FontFamily> nesne koleksiyonundaki kod çağrıları <xref:System.Drawing.FontFamily.IsStyleAvailable%2A> yöntemi (normal, kalın, italik, kalın italik, alt çizgi ve üstü çizili) çeşitli stilleri kullanılabilir olup olmadığını belirlemek için. Geçirilen bağımsız değişkenler <xref:System.Drawing.FontFamily.IsStyleAvailable%2A> yöntemi üyeleridir <xref:System.Drawing.FontStyle> sabit listesi.  
  
 Verilen ailesi/stil birleşimi varsa bir <xref:System.Drawing.Font> nesnesi, o ailesi ve stili kullanılarak oluşturulur. Geçirilen ilk bağımsız değişken <xref:System.Drawing.Font.%23ctor%2A> oluşturucudur yazı tipi ailesinin adı (değil bir <xref:System.Drawing.FontFamily> nesnesi diğer çeşitleri için olduğu gibi <xref:System.Drawing.Font.%23ctor%2A> Oluşturucu). Sonra <xref:System.Drawing.Font> nesnesi oluşturulduğunda, geçer <xref:System.Drawing.Graphics.DrawString%2A> yöntemi <xref:System.Drawing.Graphics> stil adı aile adını görüntülemek için sınıf.  
  
 Aşağıdaki kodun çıktısı aşağıdaki çizimde gösterilen çıktıya benzer.  
  
 ![Yazı tipleri metin](./media/csfontstext7.png "csfontstext7")  
  
 (Bu, aşağıdaki kod örneğinde özel yazı tipi koleksiyonu eklendi) Arial.tff Normal stili Arial yazı tipi dosyasıdır. Ancak, program çıktısı dışında normal Arial yazı tipi ailesi için birkaç kullanılabilir stiller gösterdiğine dikkat edin. Çünkü [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] kalın, italik ve kalın italik stillerden Normal stili benzetimini yapabilirsiniz. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Ayrıca alt çizgiler ve Normal stili'dan da üst çizgi üretebilir.  
  
 Benzer şekilde, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] kalın yazı stili veya italik stil kalın italik stil benzetimini yapabilirsiniz. Program çıktısı TimesBd.tff (kez yeni Roman Kalın) yalnızca olsa bile kalın italik stil kez ailesi için kullanılabilir olduğunu gösterir kez dosyasında koleksiyonu.  
  
 [!code-csharp[System.Drawing.FontsAndText#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.FontsAndText#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Drawing.Text.PrivateFontCollection>
- [Yazı Tipleri ve Metin Kullanma](using-fonts-and-text.md)
