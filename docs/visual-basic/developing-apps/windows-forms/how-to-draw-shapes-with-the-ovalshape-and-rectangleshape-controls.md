---
title: 'Nasıl Yapılır: OvalShape ve RectangleShape Denetimleriyle Şekil Çizme (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OvalShape control [Visual Basic]
- shapes, drawing
- RectangleShape control [Visual Basic]
ms.assetid: 0275b4c6-7a13-46c8-90f3-61db308c6b5d
ms.openlocfilehash: f87865ba3aebe5739b87d6ae6bfeaa957af726d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls-visual-studio"></a>Nasıl Yapılır: OvalShape ve RectangleShape Denetimleriyle Şekil Çizme (Visual Studio)
Kullanabileceğiniz <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> daireler veya Oval bir form veya kapsayıcı, hem tasarım zamanında hem de çalışma zamanında çizmek için denetim. Kullanabileceğiniz <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> kareler, dikdörtgenler veya bir form veya kapsayıcı yuvarlak köşeli dikdörtgen çizmek için denetim. Bu denetim, hem tasarım zamanında hem de çalışma zamanında şekiller çizmek için de kullanabilirsiniz.  
  
 Genişlik, renk ve kenarlık stilini değiştirerek bir şekli görünümünü özelleştirebilirsiniz. Şeklin arka plan, varsayılan olarak saydamdır; düz renk, bir deseni, bir Gradyan Dolgu (bir renkten diğerine geçiş) veya bir görüntü görüntülemek için arka plan özelleştirebilirsiniz.  
  
### <a name="to-draw-a-simple-shape-at-design-time"></a>Tasarım zamanında basit bir şekil çizmek için  
  
1.  Sürükle <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> veya <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> gelen denetim **Visual Basic PowerPacks** sekmesini (yüklemek için bkz: [Visual Basic Power Packs denetimlerine](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)) içinde **araç kutusu** bir form veya kapsayıcı denetimi.  
  
2.  Boyutlandırma sürükleyin ve boyutu ve şekli konumlandırmak için tanıtıcıları taşıyın.  
  
     Ayrıca boyutu ve şekli değiştirerek Yerleştir `Size` ve `Position` özelliklerinde **özellikleri** penceresi.  
  
     Dikdörtgene yuvarlanmış köşeleri ile oluşturmak için seçin `CornerRadius` özelliğinde **özellikleri** penceresi ve 0'dan büyük bir değere ayarlayın.  
  
3.  İçinde **özellikleri** penceresinde, Şekil görünümünü değiştirmek için isteğe bağlı olarak ek özellikleri ayarlayın.  
  
### <a name="to-draw-a-simple-shape-at-run-time"></a>Çalışma zamanında basit bir şekil çizmek için  
  
1.  Üzerinde **proje** menüsünde tıklatın **Başvuru Ekle**.  
  
2.  İçinde **Başvuru Ekle** iletişim kutusunda **Microsoft.VisualBasic.PowerPacks.VS**ve ardından **Tamam**.  
  
3.  İçinde **Kod düzenleyicisinde**, ekleme bir `Imports` veya `using` deyimini dosyanın üst Modülü:  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  Aşağıdaki kodu ekleyin bir `Event` yordam:  
  
     [!code-csharp[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.cs)]
     [!code-vb[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.vb)]  
  
## <a name="customizing-shapes"></a>Şekilleri özelleştirme  
 Varsayılan ayarları kullandığınızda <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> ve <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> denetimleri bir piksel genişliğinde ve saydam arka plan düz bir siyah kenarlığa görüntülenir. Özellikleri ayarlayarak enini, tarzını ve kenarlık rengini değiştirebilirsiniz. Ek özellikler arka planını bir şekli düz renk, bir deseni, bir gradyan dolgu veya bir görüntü değiştirmenize olanak tanır.  
  
 Arka plan şeklin değiştirmeden önce birkaç özelliklerini nasıl etkileşim bilmeniz gerekir.  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> Özellik ayarı hiçbir etkisi sürece <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> özelliği ayarlanmış <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.  
  
-   Varsa <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> özelliği ayarlanmış <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid>, <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A> geçersiz kılmaları <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>.  
  
-   Varsa <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> özelliği ayarlanmış bir desen değeri gibi <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Horizontal> veya <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Vertical>, düzeni görüntülenir <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A>. Arka plan görüntülenir <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>, koşuluyla <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> özelliği ayarlanmış <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.  
  
-   Gradyan Dolgu görüntülemek için <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> özelliği ayarlanmalıdır <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid> ve <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillGradientStyle%2A> özelliği ayarlanmalıdır değerine dışında <xref:Microsoft.VisualBasic.PowerPacks.FillGradientStyle.None>.  
  
-   Ayar <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackgroundImage%2A> özelliği bir görüntü için diğer tüm arka plan ayarları geçersiz kılar.  
  
#### <a name="to-draw-a-circle-that-has-a-custom-border"></a>Özel kenarlık sahip bir daire çizmek için  
  
1.  Sürükleme `OvalShape` gelen denetim **Visual Basic PowerPacks** sekmesinde **araç** bir form veya kapsayıcı denetlemek için.  
  
2.  İçinde **özellikleri** penceresi, `Size` özelliği ayarlamak `Height` ve `Width` değerleri eşit olur.  
  
3.  Ayarlama `BorderColor` özelliğini istediğiniz rengi.  
  
4.  Ayarlama `BorderStyle` dışında herhangi bir değer özelliğine `Solid`.  
  
5.  Ayarlama `BorderWidth` piksel cinsinden istediğiniz boyutu.  
  
#### <a name="to-draw-a-circle-that-has-a-solid-fill"></a>Düz Dolgu sahip bir daire çizmek için  
  
1.  Sürükleme `OvalShape` gelen denetim **Visual Basic PowerPacks** sekmesinde **araç** bir form veya kapsayıcı denetlemek için.  
  
2.  İçinde **özellikleri** penceresi, `Size` özelliği ayarlamak `Height` ve `Width` değerleri eşit olur.  
  
3.  Ayarlama `BackColor` özelliğini istediğiniz rengi.  
  
4.  Ayarlama `BackStyle` özelliğine `Opaque`.  
  
#### <a name="to-draw-a-circle-that-has-a-patterned-fill"></a>Desenli dolgusu olan bir daire çizmek için  
  
1.  Sürükleme `OvalShape` gelen denetim **Visual Basic PowerPacks** sekmesinde **araç** bir form veya kapsayıcı denetlemek için.  
  
2.  İçinde **özellikleri** penceresi, `Size` özelliği ayarlamak `Height` ve `Width` değerleri eşit olur.  
  
3.  Ayarlama `BackColor` özelliğini istediğiniz için arka plan rengi.  
  
4.  Ayarlama `BackStyle` özelliğine `Opaque`.  
  
5.  Ayarlama `FillColor` desenini istediğiniz renk özelliğine.  
  
6.  Ayarlama `FillStyle` dışında herhangi bir değer özelliğine `Transparent` veya `Solid`.  
  
#### <a name="to-draw-a-circle-that-has-a-gradient-fill"></a>Gradyan dolgusu olan bir daire çizmek için  
  
1.  Sürükleme `OvalShape` gelen denetim **Visual Basic PowerPacks** sekmesinde **araç** bir form veya kapsayıcı denetlemek için.  
  
2.  İçinde **özellikleri** penceresi, `Size` özelliği ayarlamak `Height` ve `Width` değerleri eşit olur.  
  
3.  Ayarlama `FillColor` özelliğini başlangıç rengini istediğiniz rengi.  
  
4.  Ayarlama `FillGradientColor` özelliğini Bitiş rengini istediğiniz rengi.  
  
5.  Ayarlama `FillGradientStyle` dışında bir değere özelliğine `None`.  
  
#### <a name="to-draw-a-circle-that-is-filled-with-an-image"></a>Bir görüntü ile doldurulan bir daire çizmek için  
  
1.  Sürükleme `OvalShape` gelen denetim **Visual Basic PowerPacks** sekmesinde **araç** bir form veya kapsayıcı denetlemek için.  
  
2.  İçinde **özellikleri** penceresi, `Size` özelliği ayarlamak `Height` ve `Width` değerleri eşit olur.  
  
3.  Seçin `BackgroundImage` özelliği ve tıklatın **üç nokta** düğmesini (…).  
  
4.  İçinde **Select Resource** iletişim kutusunda, görüntülemek için görüntüyü bir seçin. Hiçbir görüntü kaynakları listelenmiyorsa, tıklatın **alma** bir görüntü dosyasının konumuna gidin.  
  
5.  Tıklatın **Tamam** resim eklemek için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>  
 <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>  
 [Çizgi ve Şekil Denetimlerine Giriş](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)  
 [Nasıl Yapılır: LineShape Denetimiyle Çizgi Çizme](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)
