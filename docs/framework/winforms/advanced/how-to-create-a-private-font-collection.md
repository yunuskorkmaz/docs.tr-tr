---
title: 'Nasıl yapılır: Özel Yazı Tipi Koleksiyonu Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- private font collections [Windows Forms], creating
- fonts [Windows Forms], creating private collections
ms.assetid: 6533d5e5-a8dc-4b76-9fc4-3bf75c8b9212
ms.openlocfilehash: 824d42c40b07e8662395e7a1286b9a5a6112c415
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-private-font-collection"></a>Nasıl yapılır: Özel Yazı Tipi Koleksiyonu Oluşturma
<xref:System.Drawing.Text.PrivateFontCollection> Sınıfının devraldığı <xref:System.Drawing.Text.FontCollection> soyut taban sınıfı. Kullanabileceğiniz bir <xref:System.Drawing.Text.PrivateFontCollection> uygulamanız için özellikle yazı tipleri kümesini korumak için nesne. Özel yazı tipi koleksiyonu yüklü yazı tipleri ve bunun yanı sıra bilgisayarda yüklü değil yazı tipleri içerebilir. Özel yazı tipi koleksiyonu için bir yazı tipi dosyası eklemek için arama <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile%2A> yöntemi bir <xref:System.Drawing.Text.PrivateFontCollection> nesnesi.  
  
 <xref:System.Drawing.Text.FontCollection.Families%2A> Özelliği bir <xref:System.Drawing.Text.PrivateFontCollection> nesnesini içeren bir dizi <xref:System.Drawing.FontFamily> nesneleri.  
  
 Özel yazı tipi koleksiyonundaki yazı tipi aileleri sayısı mutlaka koleksiyonuna eklenen yazı tipi dosya sayısı ile aynı değil. Örneğin, bir koleksiyona ArialBd.tff, Times.tff ve TimesBd.tff dosyaları eklemek varsayalım. Olacaktır üç dosyaları ancak koleksiyonda yalnızca iki aileleri Times.tff ve TimesBd.tff aynı aileye ait olduğundan.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki üç yazı tipi dosyaları aşağıdaki örnek, bir <xref:System.Drawing.Text.PrivateFontCollection> nesnesi:  
  
-   C:\\*systemroot*\Fonts\Arial.tff (Arial, normal)  
  
-   C:\\*systemroot*\Fonts\CourBI.tff (Courier New, kalın italik)  
  
-   C:\\*systemroot*\Fonts\TimesBd.tff (kez yeni Roma, kalın)  
  
 Bir dizi kodu alır <xref:System.Drawing.FontFamily> nesnelerin <xref:System.Drawing.Text.FontCollection.Families%2A> özelliği <xref:System.Drawing.Text.PrivateFontCollection> nesnesi.  
  
 Her <xref:System.Drawing.FontFamily> nesne kodu çağrıları koleksiyonunun <xref:System.Drawing.FontFamily.IsStyleAvailable%2A> yöntemi (normal, kalın, italik ve kalın italik, alt çizgi ve üstü çizili) çeşitli stiller kullanılabilir olup olmadığını belirlemek için. Bağımsız değişkenler geçirilen <xref:System.Drawing.FontFamily.IsStyleAvailable%2A> yöntemi üyeleri olan <xref:System.Drawing.FontStyle> numaralandırması.  
  
 Verilen ailesi/stil birleşimi varsa bir <xref:System.Drawing.Font> nesnesi, bu ailesi ve stili kullanılarak oluşturulur. Geçirilen ilk bağımsız değişken <xref:System.Drawing.Font.%23ctor%2A> Oluşturucusu yazı tipi ailesinin adı olduğu (olmayan bir <xref:System.Drawing.FontFamily> nesne diğer varyasyonları için olduğu gibi <xref:System.Drawing.Font.%23ctor%2A> Oluşturucusu). Sonra <xref:System.Drawing.Font> nesne yapılandırılmıştır, için geçirilen <xref:System.Drawing.Graphics.DrawString%2A> yöntemi <xref:System.Drawing.Graphics> stil adı ile birlikte aile adı görüntülenecek sınıf.  
  
 Aşağıdaki kod çıkışı, aşağıdaki çizimde gösterilen çıkış benzerdir.  
  
 ![Yazı tipleri metin](../../../../docs/framework/winforms/advanced/media/csfontstext7.png "csfontstext7")  
  
 (Bu, aşağıdaki kod örneğinde özel yazı tipi koleksiyonu eklendi) Arial.tff Arial Normal stili için yazı tipi dosyasıdır. Ancak, program çıktısı Arial yazı tipi ailesi için normal dışında birkaç kullanılabilir stiller gösterdiğine dikkat edin. Çünkü [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] kalın, italik ve kalın italik stilleri Normal stili benzetimini yapabilirsiniz. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Ayrıca alt çizgiler ve Normal stili gelen da üst çizgi üretebilir.  
  
 Benzer şekilde, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] kalın stil veya italik stilini kalın italik stili benzetimini yapabilirsiniz. Program çıktısı TimesBd.tff (kez yeni Roma, kalın) yalnızca olsa bile kalın italik stili kez ailesi için kullanılabilir olduğunu gösterir kez dosyasında koleksiyonu.  
  
 [!code-csharp[System.Drawing.FontsAndText#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.FontsAndText#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 [Yazı Tipleri ve Metin Kullanma](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
