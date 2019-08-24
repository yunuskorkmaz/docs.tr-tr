---
title: 'İzlenecek yol: DesignerSerializationVisibilityAttribute ile Standart Türler Koleksiyonlarının Seri Hale Getirilmesi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- serialization [Windows Forms], collections
- standard types [Windows Forms], collections
- collections [Windows Forms], serializing
- collections [Windows Forms], standard types
ms.assetid: 020c9df4-fdc5-4dae-815a-963ecae5668c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2fbb0715d148b443b1eca8f400e4ad43eb51fa43
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015730"
---
# <a name="walkthrough-serialize-collections-of-standard-types"></a>İzlenecek yol: Standart türlerin koleksiyonlarını serileştirme

Özel denetimleriniz bazen bir koleksiyonu özellik olarak kullanıma sunar. Bu izlenecek yol, <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> bir koleksiyonun tasarım zamanında nasıl serileştirildiği denetlemek için sınıfının nasıl kullanılacağını gösterir. <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> Değer koleksiyon özelliğine uygulandığında, özelliğin serileştirilmesi gerekir.

Bu konudaki kodu tek bir liste olarak kopyalamak için bkz [. nasıl yapılır: Standart türlerin koleksiyonlarını DesignerSerializationVisibilityAttribute](/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))ile serileştirme.

## <a name="prerequisites"></a>Önkoşullar

Bu yönergeyi tamamlamak için Visual Studio gerekir.

## <a name="create-a-control-with-a-serializable-collection"></a>Seri hale getirilebilir koleksiyonla bir denetim oluşturma

İlk adım, bir seri hale getirilebilir koleksiyonu özelliği olarak bir denetim oluşturmaktır. Bu koleksiyonun içeriğini, **Özellikler** penceresinden erişebileceğiniz **koleksiyon düzenleyicisini**kullanarak düzenleyebilirsiniz.

1. Visual Studio 'da bir Windows Denetim Kitaplığı projesi oluşturun ve **SerializationDemoControlLib**olarak adlandırın.

2. `UserControl1` Olarak`SerializationDemoControl`yeniden adlandırın. Daha fazla bilgi için bkz. [kod sembolünü yeniden düzenlemeyi yeniden adlandırma](/visualstudio/ide/reference/rename).

3. **Özellikler** penceresinde, <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> özelliğinin değerini **10**olarak ayarlayın.

4. İçine bir <xref:System.Windows.Forms.TextBox> denetim koyun. `SerializationDemoControl`

5. <xref:System.Windows.Forms.TextBox> Denetimi seçin. **Özellikler** penceresinde, aşağıdaki özellikleri ayarlayın.

    |Özellik|Değiştir|
    |--------------|---------------|
    |**Çok satırlı**|`true`|
    |**Dock**|<xref:System.Windows.Forms.DockStyle.Fill>|
    |**Çubuklarını**|<xref:System.Windows.Forms.ScrollBars.Vertical>|
    |**ReadOnly**|`true`|

6. **Kod düzenleyicisinde**, içinde `stringsValue` `SerializationDemoControl`adlı bir dize dizisi alanı bildirin.

     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]

7. Üzerinde özelliğini tanımlayın. `SerializationDemoControl` `Strings`

   > [!NOTE]
   > <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> Değer, koleksiyonun serileştirmesini etkinleştirmek için kullanılır.

   [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
   [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
   [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]

8. Projeyi derlemek için **F5** tuşuna basın ve denetimi **UserControl Test kapsayıcısında**çalıştırın.

9. **UserControl test kapsayıcısının**içinde <xref:System.Windows.Forms.PropertyGrid> **dizeler** özelliğini bulun. **Dizeler** özelliğini seçin, sonra **dize koleksiyonu düzenleyicisini**açmak için![üç nokta (Visual Studio](./media/visual-studio-ellipsis-button.png)'nun Özellikler penceresi) düğmesini seçin.

10. **Dize koleksiyonu düzenleyicisine**birkaç dize girin. Her bir dizenin sonundaki **ENTER** tuşuna basarak onları ayırın. Dizeleri girmeyi tamamladığınızda **Tamam** ' a tıklayın.

   > [!NOTE]
   > Yazdığınız dizeler içinde <xref:System.Windows.Forms.TextBox> `SerializationDemoControl`görüntülenir.

## <a name="serialize-a-collection-property"></a>Koleksiyon özelliğini serileştirme

Denetiminizin serileştirme davranışını test etmek için, bunu bir forma yerleştirip koleksiyonun içeriğini **koleksiyon Düzenleyicisi**ile değiştirirsiniz. Seri hale getirilmiş koleksiyon durumunu, **Windows Form Tasarımcısı** kod yaydığı özel bir tasarımcı dosyasına bakarak görebilirsiniz.

1. Çözüme bir Windows uygulama projesi ekleyin. Projeyi `SerializationDemoControlTest`adlandırın.

2. **Araç kutusunda** **SerializationDemoControlLib bileşenleri**adlı sekmeyi bulun. Bu sekmede, `SerializationDemoControl`' yi bulacaksınız. Daha fazla bilgi için bkz [. İzlenecek yol: Araç kutusunu özel bileşenlerle](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)otomatik olarak doldurma.

3. Formunuza bir `SerializationDemoControl` koyun.

4. `Strings` **Özellikler** penceresinde özelliği bulun. Özelliği tıklatın, ardından **dize koleksiyonu düzenleyicisini**açmak için![üç nokta (Visual Studio](./media/visual-studio-ellipsis-button.png)'nun Özellikler penceresi) düğmesine tıklayın. `Strings`

5. **Dize koleksiyonu düzenleyicisine**birkaç dize yazın. Her bir dizenin sonunda **ENTER** tuşuna basarak onları ayırın. Dizeleri girmeyi tamamladığınızda **Tamam** ' a tıklayın.

> [!NOTE]
> Yazdığınız dizeler içinde <xref:System.Windows.Forms.TextBox> `SerializationDemoControl`görüntülenir.

6. **Çözüm Gezgini**, **tüm dosyaları göster** düğmesine tıklayın.

7. **Form1** düğümünü açın. Bunun altında **Form1.Designer.cs** veya **Form1. Designer. vb**adlı bir dosyadır. Bu, **Windows Form Tasarımcısı** formunuzun tasarım zamanı durumunu ve onun alt denetimlerini temsil eden kodu yaydığı dosyadır. Bu dosyayı **kod düzenleyicisinde**açın.

8. **Windows Form Tasarımcısı tarafından oluşturulan kod** adlı bölgeyi açın ve **serializationDemoControl1**etiketli bölümü bulun. Bu etiketin altında, denetiminizin serileştirilmiş durumunu temsil eden kod bulunur. 5\. adımda yazdığınız dizeler, `Strings` özelliği için bir atamada görüntülenir. C# Ve Visual Basic aşağıdaki kod örnekleri, "Red", "turuncu" ve "sarı" dizelerini yazdığınız sırada göreceğiniz koda benzer kodu gösterir.

    ```csharp
    this.serializationDemoControl1.Strings = new string[] {
            "red",
            "orange",
            "yellow"};
    ```

    ```vb
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}
    ```

9. **Kod düzenleyicisinde**, <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> `Strings` özelliğindeki öğesinin değerini olarak <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>değiştirin.

    ```csharp
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]
    ```

    ```vb
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _
    ```

10. Çözümü yeniden derleyin ve 3. ve 4. adımları yineleyin.

> [!NOTE]
> Bu durumda **Windows Form Tasarımcısı** , `Strings` özelliğe atama yapılmaz.

## <a name="next-steps"></a>Sonraki adımlar

Standart türlerden oluşan bir koleksiyonun nasıl serileştirildiğini öğrendikten sonra, özel denetimlerinizi tasarım zamanı ortamına göre daha ayrıntılı bir şekilde tümleştirmeyi düşünün. Aşağıdaki konularda, özel denetimlerinizin tasarım zamanı tümleştirmesinin nasıl geliştirileceğini anlatmaktadır:

- [Tasarım zamanı mimarisi](/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))

- [Windows Forms Denetimlerindeki Öznitelikler](attributes-in-windows-forms-controls.md)

- [Tasarımcı serileştirmesine genel bakış](/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))

- [İzlenecek yol: Visual Studio tasarım zamanı özelliklerinden faydalanan bir Windows Forms denetimi oluşturma](creating-a-wf-control-design-time-features.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>
- [İzlenecek yol: Araç kutusunu özel bileşenlerle otomatik olarak doldurma](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
