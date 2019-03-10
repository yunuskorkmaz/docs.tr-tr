---
title: Koordinat Sistemi Türleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], page
- unit of measure
- world coordinate system
- page coordinate system
- page transformation
- device coordinate system
- world transformation
- coordinate systems
- transformations [Windows Forms], world
ms.assetid: c61ff50a-eb1d-4e6c-83cd-f7e9764cfa9f
ms.openlocfilehash: 42e8b5626cf30010f154e7c978708042c4e3369a
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715869"
---
# <a name="types-of-coordinate-systems"></a>Koordinat Sistemi Türleri
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] üç koordinat kullanır: dünya, sayfa ve cihaz. Dünya koordinatlarını bir belirli grafik grubuna ilişkin model için kullanılan koordinatları ve .NET Framework yöntemleri için geçirdiğiniz koordinatları. Bir form veya denetim gibi çizim yüzeyi tarafından kullanılan koordinat sistemini sayfa koordinatlarına bakın. Cihaz, bir ekran veya kağıt gibi üzerine çizilmiş fiziksel cihaz tarafından kullanılan koordinat koordinatları. Çağrısı yaptığınızda `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, geçirdiğiniz noktaları <xref:System.Drawing.Graphics.DrawLine%2A> yöntemi —`(0, 0)` ve `(160, 80)`— dünyanın koordinat alanındadır. Önce [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ekranda çizgi çizmek, bir dizi dönüştürmeyi koordinatları geçirin. Gerçek koordinat dönüştürmesini adlı bir dönüştürme dünya koordinatlarını sayfa koordinatlarına dönüştüren ve sayfa dönüşümü adlı başka bir dönüştürme sayfa koordinatlarına cihaz koordinatlarına dönüştürür.  
  
## <a name="transforms-and-coordinate-systems"></a>Dönüşümler ve koordinat sistemi  
 Sol üst köşesinin yerine istemci alanını gövdesine, kaynağı olan bir koordinat sistemi çalışmak istediğinizi varsayalım. Örneğin, istemci alanın sol kenarından 100 piksel ve 50 piksel istemci alanının üst kaynağı istediğinizi varsayalım. Aşağıdaki çizimde, böyle bir koordinat sistemi gösterir.  
  
 ![Koordinat sistemi](./media/aboutgdip05-art01.gif "AboutGdip05_art01")  
  
 Çağrısı yaptığınızda `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, aşağıdaki çizimde gösterilen satır alın.  
  
 ![Koordinat sistemi](./media/aboutgdip05-art02.gif "AboutGdip05_art02")  
  
 Üç koordinat satırınızda bitiş noktası koordinatları aşağıdaki gibidir:  
  
|||  
|-|-|  
|Dünya|(0, 0) için (160, 80)|  
|Sayfa|(100, 50) için (260, 130)|  
|Cihaz|(100, 50) için (260, 130)|  
  
 Sayfa koordinat istemci alanını sol üst köşesinde kaynağına sahip olduğunu unutmayın; her zaman, bu durumda olacaktır. Ayrıca piksel ölçü olduğundan, cihaz koordinatlarını sayfa koordinatlarına aynı olduğunu unutmayın. Piksel (örneğin, inç) dışında bir ölçü ayarlarsanız, cihaz koordinatlarını sayfa koordinatlarına farklı olacaktır.  
  
 Dünya koordinatlarını sayfa koordinatlarına eşler, gerçek koordinat dönüştürmesini tutulur <xref:System.Drawing.Graphics.Transform%2A> özelliği <xref:System.Drawing.Graphics> sınıfı. Önceki örnekte gerçek koordinat dönüştürmesini çeviri 100 birim x yönünde ve y yönünde 50 Birim var. Aşağıdaki örnek, gerçek koordinat dönüştürmesini ayarlar bir <xref:System.Drawing.Graphics> nesnesi ve ardından kullanan <xref:System.Drawing.Graphics> önceki şekilde gösterildiği çizgi çizmek için nesne:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 Sayfa dönüşümü için cihaz koordinatlarını sayfa koordinatlarına eşler. <xref:System.Drawing.Graphics> Sağlar sınıfını <xref:System.Drawing.Graphics.PageUnit%2A> ve <xref:System.Drawing.Graphics.PageScale%2A> sayfa dönüşümü düzenlemek için özellikler. <xref:System.Drawing.Graphics> Sınıfı iki salt okunur özellikler sağlar <xref:System.Drawing.Graphics.DpiX%2A> ve <xref:System.Drawing.Graphics.DpiY%2A>, yatay ve dikey inç başına nokta görünen cihazın İnceleme için.  
  
 Kullanabileceğiniz <xref:System.Drawing.Graphics.PageUnit%2A> özelliği <xref:System.Drawing.Graphics> piksel dışındaki bir ölçü belirtmek için sınıf.  
  
> [!NOTE]
>  Ayarlayamazsınız <xref:System.Drawing.Graphics.PageUnit%2A> özelliğini <xref:System.Drawing.GraphicsUnit.World>, fiziksel bir birim değil ve bir özel durum neden olur.  
  
 Aşağıdaki örnek bir çizgi çizer (0, 0) için (2, 1), burada noktası (2, 1), 2 inç sağa ve aşağı 1 inç noktasından (0, 0):  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
>  Kalemi oluştururken bir kalem genişliği belirtmezseniz, önceki örnekte geniş bir inç bir çizgi çizer. Kalem genişliği ikinci bağımsız değişkeni belirtebilirsiniz <xref:System.Drawing.Pen> Oluşturucusu:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 Görüntü cihazı 96 inç başına nokta yatay yönde ve 96 inç başına nokta dikey yönde olduğunu varsayıyoruz önceki örnekte çizginin bitiş noktaları üç koordinat alanlarındaki aşağıdaki koordinatlar vardır:  
  
|||  
|-|-|  
|Dünya|(0, 0) için (2, 1)|  
|Sayfa|(0, 0) için (2, 1)|  
|Cihaz|(0, 0, için (192, 96)|  
  
 Dünya koordinat kaynağı istemci alanını sol üst köşesinde olduğundan, sayfa koordinatlarına dünya koordinatları ile aynı olduğunu unutmayın.  
  
 Çeşitli efektler elde etmek için world ve sayfa dönüştürmeleri birleştirebilirsiniz. Örneğin, ölçü birimi olarak inç kullanmak istediğiniz ve istemci alanını 1/2 inç istemci alanının üst ve sol kenarından 2 inç olacak şekilde, koordinat sistemi kaynağını istediğinizi varsayalım. Aşağıdaki örnek, dünya ve sayfa dönüşümleri ayarlar bir <xref:System.Drawing.Graphics> nesnesi ve ardından bir çizgi çizer (0, 0) için (2, 1):  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 Çizgi ve koordinat sistemini aşağıda gösterilmiştir.  
  
 ![Koordinat sistemi](./media/aboutgdip05-art03.gif "AboutGdip05_art03")  
  
 Görüntü cihazı 96 inç başına nokta yatay yönde ve 96 inç başına nokta dikey yönde olduğunu varsayıyoruz önceki örnekte çizginin bitiş noktaları üç koordinat alanlarındaki aşağıdaki koordinatlar vardır:  
  
|||  
|-|-|  
|Dünya|(0, 0) için (2, 1)|  
|Sayfa|(2, 0,5) için (4, 1.5)|  
|Cihaz|(192, 48) için (384, 144)|  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Koordinat Sistemleri ve Dönüştürmeler](coordinate-systems-and-transformations.md)
- [Dönüşümlerin Matrisle Temsili](matrix-representation-of-transformations.md)
