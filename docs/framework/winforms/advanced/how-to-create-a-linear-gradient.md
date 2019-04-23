---
title: 'Nasıl yapılır: Doğrusal Gradyan Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- linear gradients [Windows Forms], creating
- gradients [Windows Forms], creating linear
- colors [Windows Forms], creating linear gradients
- gradients
ms.assetid: 6c88e1cc-1217-4399-ac12-cb37592b9f01
ms.openlocfilehash: b836659821b54698b675d48acd4e46466001d654
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59977281"
---
# <a name="how-to-create-a-linear-gradient"></a>Nasıl yapılır: Doğrusal Gradyan Oluşturma
GDI +'da yatay, dikey ve Çapraz doğrusal gradyanlar sağlar. Varsayılan olarak, aynı şekilde doğrusal gradyan rengi değişir. Ancak, Tekdüzen olmayan biçimde rengini değiştirir, böylece doğrusal gradyan özelleştirebilirsiniz.  

> [!NOTE]
> Bu makaledeki örneklerde bir denetimin çağrılan yöntemlerdir <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  

Aşağıdaki örnek, bir satır, bir elips ve dikdörtgen Yatay doğrusal gradyan fırçası ile doldurur.  
  
<xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> Oluşturucusu dört bağımsız değişken alır: iki nokta ve iki rengi. İlk noktası (0, 10) ilk rengi (kırmızı) ile ilişkilendirilir ve ikinci bir nokta (200, 10) ikinci rengi (mavi) ile ilişkilendirilir. Gelen çizgi beklediğiniz gibi (0, 10) için (200, 10) değişiklikleri aşamalı olarak mavi ve kırmızı.  
  
 10'luk bloklar noktaları (0, 10) ve (200, 10) önemli değildir. Önemli olan, iki nokta aynı ikinci koordinat sahip olabilir; bunları bağlayan bir çizgi yataydır. Elips ve dikdörtgen de aşamalı olarak kırmızı, mavi ve yatay koordinatı 0 ile 200'e gider gibi değiştirin.  
  
 Aşağıdaki çizimde, çizgi, elips ve dikdörtgen gösterilir. Yatay koordinat 200 arttıkça renk gradyanı kendisini tekrarlar olduğunu unutmayın.  
  
 ![Doğrusal gradyan](./media/cslineargradient1.png "cslineargradient1")  
  
### <a name="to-use-horizontal-linear-gradients"></a>Yatay doğrusal gradyanlar kullanmak için  
  
-   Donuk kırmızı ve donuk mavi renkle üçüncü ve dördüncü bağımsız değişken olarak, sırasıyla geçirin.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#21)]
     [!code-vb[System.Drawing.UsingaGradientBrush#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#21)]  
  
 Önceki örnekte, 200 yatay koordinat için 0 yatay bir Koordinattan geçerken renk bileşenlerine doğrusal olarak değiştirin. Örneğin, bir nokta olan ilk koordinatı 0 ile 200 arasında olan sürenin yarısına ulaşıldığında, 0 ile 255 arasında ortasında ise mavi bir bileşen olacaktır.  
  
 GDI +'da, bir renk gradyan kenarından değişir şekilde ayarlamanıza olanak sağlar. Siyahtan kırmızı aşağıdaki tabloya göre değiştiren bir gradyan fırçası oluşturmak istediğinizi varsayalım.  
  
|Yatay koordinatı|RGB bileşenleri|  
|---------------------------|--------------------|  
|0|(0, 0, 0)|  
|40|(128, 0, 0)|  
|200|(255, 0, 0)|  
  
 Yatay koordinatı 0 ile 200 biçimini yüzde 20'sinden yalnızca olduğunda kırmızı bileşeni yarım yoğunlukta olduğunu unutmayın.  
  
 Aşağıdaki örnek kümeleri <xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A?displayProperty=nameWithType> üç göreli yoğunluklarını üç göreli konum ile ilişkilendirilecek özellik. Yukarıdaki tabloda olduğu gibi bir göreli 0,5 yoğunluğunu 0.2 göreli bir konum ilişkilidir. Kod, bir elips ve dikdörtgen gradyan fırçası ile doldurur.  
  
 Aşağıdaki çizimde, sonuçta elde edilen elips ve dikdörtgen gösterilir.  
  
 ![Doğrusal gradyan](./media/cslineargradient2.png "cslineargradient2")  

### <a name="to-customize-linear-gradients"></a>Doğrusal gradyanlar özelleştirmek için  
  
-   Donuk siyah ve donuk kırmızı renkte üçüncü ve dördüncü bağımsız değişken olarak, sırasıyla geçirin.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#22)]
     [!code-vb[System.Drawing.UsingaGradientBrush#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#22)]  
  
 Önceki örneklerde gradyanlar yatay; yatay bir çizgi boyunca taşımak gibi diğer bir deyişle, kademeli olarak rengi değiştirir. Dikey Gradyan ve çapraz gradyanlar de tanımlayabilirsiniz.  
  
 Aşağıdaki örnek noktaları (0, 0) ve (200, 100) geçirir bir <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> Oluşturucusu. Mavi ilişkili olduğu (0, 0) ve yeşil ilişkili olduğu (200, 100). Doğrusal gradyan fırçası ile bir satır (Kalem genişliği 10 ile) bir elips doldurulur.  
  
 Aşağıdaki çizim, satır ve üç nokta gösterir. Not geçerken elips değişiklikleri rengi kademeli olarak satırında aracılığıyla geçirme satırına paralel (0, 0) ve (200, 100).  
  
 ![Doğrusal gradyan](./media/cslineargradient3.png "cslineargradient3")  
  
### <a name="to-create-diagonal-linear-gradients"></a>Çapraz doğrusal gradyanlar oluşturma  
  
-   Donuk mavi ve donuk yeşil renkte üçüncü ve dördüncü bağımsız değişken olarak, sırasıyla geçirin.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#23)]
     [!code-vb[System.Drawing.UsingaGradientBrush#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#23)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şekilleri Doldurmak için Gradyan Fırçası Kullanma](using-a-gradient-brush-to-fill-shapes.md)
- [Windows Forms’da Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
