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
ms.openlocfilehash: c113dcf814a252808ae3232751028947c26821ba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012444"
---
# <a name="walkthrough-serializing-collections-of-standard-types-with-the-designerserializationvisibilityattribute"></a>İzlenecek yol: DesignerSerializationVisibilityAttribute ile Standart Türler Koleksiyonlarının Seri Hale Getirilmesi

Özel kontrollerinizi, bazen bir koleksiyon özelliği olarak açığa çıkarır. Bu izlenecek yolda nasıl kullanılacağını gösterir <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> koleksiyonu tasarım zamanında nasıl serileştirildiği denetlemek için sınıf. Uygulama <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> , koleksiyon özelliği için değer özelliği serileştirilecek sağlar.

 Bu konudaki tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: DesignerSerializationVisibilityAttribute ile standart türler koleksiyonlarının seri hale getirme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120)).

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için şunlar gerekir:

- Oluşturma ve Windows Forms application projesi Visual Studio'nun yüklü bilgisayarda çalıştırmak için yeterli izinleri yok.

## <a name="creating-a-control-that-has-a-serializable-collection"></a>Seri hale getirilebilir bir koleksiyon olan bir denetim oluşturma
 İlk adım, bir özellik olarak seri hale getirilebilir bir koleksiyon içeren bir denetim oluşturmaktır. Bu koleksiyonu kullanarak içeriği düzenleyebilir **Koleksiyonu Düzenleyicisi**, gelen erişebileceğiniz **özellikleri** penceresi.

### <a name="to-create-a-control-with-a-serializable-collection"></a>Bir denetim ile seri hale getirilebilir bir koleksiyon oluşturmak için

1. Adlı bir Windows Denetim Kitaplığı projesi oluşturun `SerializationDemoControlLib`. Daha fazla bilgi için [Windows Denetim Kitaplığı şablonu](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).

2. Yeniden adlandırma `UserControl1` için `SerializationDemoControl`. Daha fazla bilgi için [bir kod sembol yeniden düzenlemeyi yeniden adlandırma](/visualstudio/ide/reference/rename).

3. İçinde **özellikleri** penceresinde değerini ayarlayın <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> özelliğini `10`.

4. Bir yerde bir <xref:System.Windows.Forms.TextBox> denetim `SerializationDemoControl`.

5. Seçin <xref:System.Windows.Forms.TextBox> denetimi. İçinde **özellikleri** penceresinde, aşağıdaki özellikleri ayarlayın.

    |Özellik|Değiştirin|
    |--------------|---------------|
    |**Çok satırlı**|`true`|
    |**Dock**|<xref:System.Windows.Forms.DockStyle.Fill>|
    |**Kaydırma çubukları**|<xref:System.Windows.Forms.ScrollBars.Vertical>|
    |**ReadOnly**|`true`|

6. İçinde **Kod Düzenleyicisi**, adında bir dize dizisi alan bildirin `stringsValue` içinde `SerializationDemoControl`.

     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]

7. Tanımlama `Strings` özellikte `SerializationDemoControl`.

> [!NOTE]
> <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> Değer koleksiyonu etkinleştirmek için kullanılır.

 [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
 [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
 [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]

1. Projeyi oluşturmak ve denetim çalıştırmak için F5 tuşuna basın **UserControl Test kapsayıcısı**.

2. Bulma `Strings` özelliğinde <xref:System.Windows.Forms.PropertyGrid> , **UserControl Test kapsayıcısı**. Tıklayın `Strings` özelliği, sonra üç nokta simgesine tıklayın (![VisualStudioEllipsesButton ekran](../media/vbellipsesbutton.png "vbEllipsesButton")) açmak için düğmeyi **Dize Koleksiyonu Düzenleyicisi**.

3. Birkaç dizeleri girin **Dize Koleksiyonu Düzenleyicisi**. Bunları, her bir dizenin sonunda ENTER tuşuna basarak ayırın. Tıklayın **Tamam** dizeleri girmeyi tamamladığınızda.

> [!NOTE]
> Yazdığınız dizeleri görünür <xref:System.Windows.Forms.TextBox> , `SerializationDemoControl`.

## <a name="serializing-a-collection-property"></a>Bir koleksiyon özelliği seri hale getirme

Serileştirme davranışını test için bir form üzerinde yerleştirmek ve koleksiyonuyla içeriğini değiştirme **Koleksiyonu Düzenleyicisi**. Seri hale getirilmiş toplama durumu, bir özel Tasarımcı dosyasından bakarak gördüğünüz **Windows Form Tasarımcısı** kod yayar.

### <a name="to-serialize-a-collection"></a>Bir koleksiyonu sıralamak için

1. Bir Windows uygulaması projesi çözüme ekleyin. Projeyi adlandırın `SerializationDemoControlTest`.

2. İçinde **araç kutusu**, adlı sekmeyi bulun **SerializationDemoControlLib bileşenleri**. Bu sekmede bulursunuz `SerializationDemoControl`. Daha fazla bilgi için [izlenecek yol: Otomatik olarak araç kutusunu özel bileşenlerle doldurma](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).

3. Bir yerde bir `SerializationDemoControl` formunuzdaki.

4. Bulma `Strings` özelliğinde **özellikleri** penceresi. Tıklayın `Strings` özelliği, sonra üç nokta simgesine tıklayın (![VisualStudioEllipsesButton ekran](../media/vbellipsesbutton.png "vbEllipsesButton")) açmak için düğmeyi **Dize Koleksiyonu Düzenleyicisi**.

5. Birkaç dizelerde yazın **Dize Koleksiyonu Düzenleyicisi**. Bunları, her bir dizenin sonunda ENTER tuşuna basarak ayırın. Tıklayın **Tamam** dizeleri girmeyi tamamladığınızda.

> [!NOTE]
> Yazdığınız dizeleri görünür <xref:System.Windows.Forms.TextBox> , `SerializationDemoControl`.

1. İçinde **Çözüm Gezgini**, tıklayın **tüm dosyaları göster** düğmesi.

2. Açık **Form1** düğümü. Adlı bir dosya olduğu beneath **Form1.Designer.cs** veya **Form1.Designer.vb**. Bu dosyaya, **Windows Form Tasarımcısı** formunuza ve onun alt denetimleri tasarım zamanı durumunu temsil eden kod yayar. Bu dosyayı açmak **Kod Düzenleyicisi**.

3. Bölge adında açın **Windows Form Designer üretilen kod** ve etiketlenmiş bölümü bulun **serializationDemoControl1**. Bu etiketi altında denetiminizin serileştirilmiş durumu temsil eden kodudur. 5. adımda yazdığınız dizeleri atama görünen `Strings` özelliği. C# ve Visual Basic'te, aşağıdaki kod örnekleri Göster kod benzer şekilde, hangi dizeleri "red", "turuncu" ve "Sarı" yazılı görürsünüz.

    ```csharp
    this.serializationDemoControl1.Strings = new string[] {
            "red",
            "orange",
            "yellow"};
    ```

    ```vb
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}
    ```

4. İçinde **Kod Düzenleyicisi**, değiştirin <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> üzerinde `Strings` özelliğini <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.

    ```csharp
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]
    ```

    ```vb
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _
    ```

5. 3 ve 4 yineleme adımları ve çözümü yeniden oluşturun.

> [!NOTE]
> Bu durumda, **Windows Form Tasarımcısı** atama bulunamadı yayan `Strings` özelliği.

## <a name="next-steps"></a>Sonraki Adımlar

Standart türlerin koleksiyonunu serileştirmek nasıl öğrendikten sonra özel kontrollerinizi tasarım zamanı ortamına daha derin tümleştirme göz önünde bulundurun. Aşağıdaki konular, özel kontrollerinizi, tasarım zamanı tümleştirmeyi geliştirmek nasıl açıklar:

- [Tasarım zamanı mimarisi](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))

- [Windows Forms Denetimlerindeki Öznitelikler](attributes-in-windows-forms-controls.md)

- [Tasarımcı serileştirmeye genel bakış](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))

- [İzlenecek yol: Visual Studio tasarım zamanı özelliklerinden faydalanan Windows Forms denetimi oluşturma](creating-a-wf-control-design-time-features.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>
- [Tasarımcı serileştirmeye genel bakış](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))
- [Nasıl yapılır: DesignerSerializationVisibilityAttribute ile standart türler koleksiyonlarının seri hale getirme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))
- [İzlenecek yol: Otomatik olarak araç kutusunu özel bileşenlerle doldurma](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
