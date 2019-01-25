---
title: 'Nasıl yapılır: OvalShape ve RectangleShape denetimleriyle (Visual Studio) ile şekil çizme'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OvalShape control [Visual Basic]
- shapes, drawing
- RectangleShape control [Visual Basic]
ms.assetid: 0275b4c6-7a13-46c8-90f3-61db308c6b5d
ms.openlocfilehash: fe937236332591f6065e618c49ca5cf2c54b987c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701228"
---
# <a name="how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls-visual-studio"></a>Nasıl yapılır: OvalShape ve RectangleShape denetimleriyle (Visual Studio) ile şekil çizme
Kullanabileceğiniz <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> daireler veya Oval bir form veya kapsayıcı, hem tasarım zamanında hem de çalışma zamanında çizmek için denetimi. Kullanabileceğiniz <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> kareler, dikdörtgenler veya bir form veya kapsayıcı yuvarlak köşeli dikdörtgen çizmek için denetimi. Bu denetimi, hem tasarım zamanında hem de çalışma zamanında şekiller çizmek için de kullanabilirsiniz.  
  
 Genişlik, renk ve kenarlık stilini değiştirerek bir şekil görünümünü özelleştirebilirsiniz. Varsayılan olarak arka planda bir şeklin şeffaftır; düz renk, bir desen, bir Gradyan Dolgu (bir renk diğerine geçiş) veya bir görüntü görüntülenecek arka plan özelleştirebilirsiniz.  
  
### <a name="to-draw-a-simple-shape-at-design-time"></a>Basit bir şekil tasarım zamanında çizmek için  
  
1.  Sürükleme <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> veya <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> denetimi **Visual Basic PowerPacks** sekme (yüklemek için bkz [Visual Basic Power Packs denetimlerine](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)) içinde **araç kutusu** bir form veya kapsayıcı denetimi.  
  
2.  Boyutlandırma sürükleyin ve boyutu ve şekli yerleştirmek için tutamaçlarını taşıyın.  
  
     Ayrıca boyutu ve şekli değiştirerek yerleştirmek `Size` ve `Position` özelliklerinde **özellikleri** penceresi.  
  
     Yuvarlatılmış köşelere sahip bir dikdörtgen oluşturmak için seçin `CornerRadius` özelliğinde **özellikleri** penceresi ve 0'dan büyük bir değere ayarlayın.  
  
3.  İçinde **özellikleri** penceresinde şekli görünümünü değiştirmek için isteğe bağlı olarak ek özellikleri ayarlayın.  
  
### <a name="to-draw-a-simple-shape-at-run-time"></a>Basit bir şekil çalışma zamanında çizmek için  
  
1.  Üzerinde **proje** menüsünü tıklatın **Başvuru Ekle**.  
  
2.  İçinde **Başvuru Ekle** iletişim kutusunda **Microsoft.VisualBasic.PowerPacks.VS**ve ardından **Tamam**.  
  
3.  İçinde **Kod Düzenleyicisi**, ekleme bir `Imports` veya `using` üst modülünün deyimi:  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  Aşağıdaki kodu ekleyin bir `Event` yordam:  
  
     [!code-csharp[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.cs)]
     [!code-vb[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.vb)]  
  
## <a name="customizing-shapes"></a>Şekiller özelleştirme  
 Varsayılan ayarları kullandığınızda <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> ve <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> denetimleri bir piksel genişliğinde ve saydam bir arka plan olan düz bir siyah kenarlığa görüntülenir. Özelliklerini ayarlayarak, genişlik, stili ve kenarlık rengini değiştirebilirsiniz. Ek özellikler arka planını bir şekli düz renk, bir desen, bir gradyan dolgu veya görüntü değiştirmenize olanak tanır.  
  
 Bir şeklin arka değiştirmeden önce birkaç özelliklerini nasıl etkileşimde bulunduğunu bilmeniz gerekir.  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> Özellik ayarı hiçbir etkisi sürece <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> özelliği <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.  
  
-   Varsa <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> özelliği <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid>, <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A> geçersiz kılmalar <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>.  
  
-   Varsa <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> özelliği ayarlanmış bir desen değerine gibi <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Horizontal> veya <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Vertical>, deseni görüntülenmesi <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A>. Arka plan görüntülenir <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>, koşuluyla <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> özelliği <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.  
  
-   Bir Gradyan Dolgu görüntülemek için <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> özelliği ayarlanmalıdır <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid> ve <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillGradientStyle%2A> özelliği ayarlanmalıdır değerine dışında <xref:Microsoft.VisualBasic.PowerPacks.FillGradientStyle.None>.  
  
-   Ayar <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackgroundImage%2A> görüntü özelliğini, diğer tüm arka plan ayarları geçersiz kılar.  
  
#### <a name="to-draw-a-circle-that-has-a-custom-border"></a>Özel bir kenarlığa sahip bir daire çizin  
  
1.  Sürükleme `OvalShape` denetimi **Visual Basic PowerPacks** sekmesinde **araç kutusu** bir form veya kapsayıcı denetlemek için.  
  
2.  İçinde **özellikleri** penceresi, `Size` özelliği ayarlamak `Height` ve `Width` değerleri eşit olur.  
  
3.  Ayarlama `BorderColor` özelliğini istediğiniz rengi.  
  
4.  Ayarlama `BorderStyle` dışında herhangi bir değer özelliğini `Solid`.  
  
5.  Ayarlama `BorderWidth` piksel cinsinden istediğiniz boyuta.  
  
#### <a name="to-draw-a-circle-that-has-a-solid-fill"></a>Bir tek renk dolgu olan bir daire çizme  
  
1.  Sürükleme `OvalShape` denetimi **Visual Basic PowerPacks** sekmesinde **araç kutusu** bir form veya kapsayıcı denetlemek için.  
  
2.  İçinde **özellikleri** penceresi, `Size` özelliği ayarlamak `Height` ve `Width` değerleri eşit olur.  
  
3.  Ayarlama `BackColor` özelliğini istediğiniz rengi.  
  
4.  Ayarlama `BackStyle` özelliğini `Opaque`.  
  
#### <a name="to-draw-a-circle-that-has-a-patterned-fill"></a>Desenli dolgu olan bir daire çizme  
  
1.  Sürükleme `OvalShape` denetimi **Visual Basic PowerPacks** sekmesinde **araç kutusu** bir form veya kapsayıcı denetlemek için.  
  
2.  İçinde **özellikleri** penceresi, `Size` özelliği ayarlamak `Height` ve `Width` değerleri eşit olur.  
  
3.  Ayarlama `BackColor` özelliğini istediğiniz için arka plan rengi.  
  
4.  Ayarlama `BackStyle` özelliğini `Opaque`.  
  
5.  Ayarlama `FillColor` özelliğini desenini istediğiniz rengi.  
  
6.  Ayarlama `FillStyle` dışında herhangi bir değer özelliğini `Transparent` veya `Solid`.  
  
#### <a name="to-draw-a-circle-that-has-a-gradient-fill"></a>Gradyan Dolgu olan bir daire çizme  
  
1.  Sürükleme `OvalShape` denetimi **Visual Basic PowerPacks** sekmesinde **araç kutusu** bir form veya kapsayıcı denetlemek için.  
  
2.  İçinde **özellikleri** penceresi, `Size` özelliği ayarlamak `Height` ve `Width` değerleri eşit olur.  
  
3.  Ayarlama `FillColor` başlangıç rengini istediğiniz renkle özelliği.  
  
4.  Ayarlama `FillGradientColor` Bitiş rengini istediğiniz renkle özelliği.  
  
5.  Ayarlama `FillGradientStyle` dışında bir değere `None`.  
  
#### <a name="to-draw-a-circle-that-is-filled-with-an-image"></a>Bir görüntü ile dolu bir daire çizin  
  
1.  Sürükleme `OvalShape` denetimi **Visual Basic PowerPacks** sekmesinde **araç kutusu** bir form veya kapsayıcı denetlemek için.  
  
2.  İçinde **özellikleri** penceresi, `Size` özelliği ayarlamak `Height` ve `Width` değerleri eşit olur.  
  
3.  Seçin `BackgroundImage` özelliği ve tıklatın **üç nokta** düğmesini (…).  
  
4.  İçinde **seçin kaynak** iletişim kutusunda görüntülenecek resmin seçin. Hiçbir resim kaynakları listelenirse, tıklayın **alma** bir görüntü dosyasının konumuna gidin.  
  
5.  Tıklayın **Tamam** resim eklemek için.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>
- <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>
- [Çizgi ve Şekil Denetimlerine Giriş](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)
- [Nasıl yapılır: LineShape denetimiyle çizgi çizme](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)
