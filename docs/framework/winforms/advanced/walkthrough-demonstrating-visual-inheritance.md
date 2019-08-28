---
title: 'İzlenecek yol: Görsel Devralmayı Gösterme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- form inheritance [Windows Forms], walkthroughs
- visual inheritance
- inheritance [Windows Forms], walkthroughs
- walkthroughs [Windows Forms], visual inheritance
- Windows Forms, inheritance
ms.assetid: 01966086-3142-450e-8210-3fd4cb33f591
ms.openlocfilehash: 32df98852b28963ffb748895156f7d9977c74b92
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046145"
---
# <a name="walkthrough-demonstrating-visual-inheritance"></a>İzlenecek yol: Görsel Devralmayı Gösterme

Görsel devralma, temel formdaki denetimleri görmenizi ve yeni denetimler eklemenizi sağlar. Bu kılavuzda, bir temel form oluşturacak ve onu bir sınıf kitaplığında derleyecaksınız. Bu sınıf kitaplığını başka bir projeye aktarır ve temel formdan devralan yeni bir form oluşturacaksınız. Bu izlenecek yol sırasında şunları yapmayı öğreneceksiniz:

- Temel form içeren bir sınıf kitaplığı projesi oluşturun.

- Temel formun türetilmiş sınıflarının değiştirebileceği özelliklere sahip bir düğme ekleyin.

- Temel formun ınherıtors tarafından değiştirilemeyen bir düğme ekleyin.

- Öğesinden `BaseForm`devralan bir form içeren bir proje oluşturun.

Sonuç olarak, Bu anlatım devralınan bir formdaki özel ve korunan denetimler arasındaki farkı gösterir.

> [!CAUTION]
> Tüm denetimler temel formdan Görsel devralmayı desteklemez. Aşağıdaki denetimler bu kılavuzda açıklanan senaryoyu desteklemez:
>
> - <xref:System.Windows.Forms.WebBrowser>
>
> - <xref:System.Windows.Forms.ToolStrip>
>
> - <xref:System.Windows.Forms.ToolStripPanel>
>
> - <xref:System.Windows.Forms.TableLayoutPanel>
>
> - <xref:System.Windows.Forms.FlowLayoutPanel>
>
> - <xref:System.Windows.Forms.DataGridView>
>
> Devralınan form içindeki bu denetimler her zaman, kullandığınız değiştiricilere (`private`, `protected`, veya `public`) bakılmaksızın salt okunurdur.

## <a name="create-a-class-library-project-containing-a-base-form"></a>Temel form içeren bir sınıf kitaplığı projesi oluşturma

1. Visual Studio 'da, **Dosya** menüsünden **Yeni** > **Proje** ' yi seçerek **Yeni proje** iletişim kutusunu açın.

2. Adlı `BaseFormLibrary`bir Windows Forms uygulaması oluşturun.

3. Standart bir Windows Forms uygulaması yerine bir sınıf kitaplığı oluşturmak için, **Çözüm Gezgini**, **BaseFormLibrary** proje düğümüne sağ tıklayın ve ardından **Özellikler**' i seçin.

4. Projenin özelliklerinde, **çıkış türünü** **Windows uygulamasından** **sınıf kitaplığı**olarak değiştirin.

5. **Dosya** menüsünde **Tümünü Kaydet** ' i seçerek projeyi ve dosyaları varsayılan konuma kaydedin.

Sonraki iki yordam, temel forma düğme ekler. Görsel devralmayı göstermek için, `Modifiers` özelliklerini ayarlayarak düğmelere farklı erişim düzeyleri verirsiniz.

## <a name="add-a-button-that-inheritors-of-the-base-form-can-modify"></a>Temel formun devralanıların değiştirebileceği bir düğme Ekle

1. Tasarımcıda **Form1** ' i açın.

2. Forma düğme eklemek için **araç kutusunun** **tüm Windows Forms** sekmesinde **düğme** ' ye çift tıklayın. Düğmeyi konumlandırmak ve yeniden boyutlandırmak için fareyi kullanın.

3. Özellikler penceresi, düğmenin aşağıdaki özelliklerini ayarlayın:

    - **Text** özelliğini **Hello**olarak ayarlayın.

    - **(Name)** özelliğini **btnProtected**olarak ayarlayın.

    - **Değiştiriciler** özelliğini **korumalı**olarak ayarlayın. Bu, **Form1** 'ten kalıtımla alan formların **btnProtected**'nin özelliklerini değiştirmesine olanak tanır.

4. Tıklama olayına bir olay işleyicisi eklemek için, **Merhaba** **'** a çift tıklayın.

5. Aşağıdaki kod satırını olay işleyicisine ekleyin:

    ```vb
    MessageBox.Show("Hello, World!")
    ```

    ```csharp
    MessageBox.Show("Hello, World!");
    ```

## <a name="add-a-button-that-cannot-be-modified-by-inheritors-of-the-base-form"></a>Temel formun ınherıtors tarafından değiştirilemeyen bir düğme ekleyin

1. Kod düzenleyicisinin üzerindeki **Form1. vb [Design], Form1.cs [Design] veya Form1. jsl [Design** ] sekmesine tıklayarak ya da F7 tuşuna basarak Tasarım görünümüne geçiş yapın.

2. İkinci bir düğme ekleyin ve özelliklerini aşağıdaki gibi ayarlayın:

    - **Metin** özelliğini, **güle söylemek**için ayarlayın.

    - **(Ad)** özelliğini **btnPrivate**olarak ayarlayın.

    - **Değiştiriciler** özelliğini **özel**olarak ayarlayın. Bu, **Form1** 'ten kalıtımla alan formların **btnPrivate**özelliklerinin değiştirilmesini olanaksız hale getirir.

3. **Tıklama** olayına bir olay işleyicisi eklemek için **söyleyin** düğmesine çift tıklayın. Aşağıdaki kod satırını olay yordamına yerleştirin:

    ```vb
    MessageBox.Show("Goodbye!")
    ```

    ```csharp
    MessageBox.Show("Goodbye!");
    ```

4. Sınıf kitaplığını derlemek için **Build (oluştur** ) menüsünde **BaseForm kitaplığı** ' nı seçin.

     Kitaplık derlendikten sonra, yeni oluşturduğunuz formdan devralan yeni bir proje oluşturabilirsiniz.

## <a name="create-a-project-containing-a-form-that-inherits-from-the-base-form"></a>Temel formdan devralan form içeren bir proje oluşturma

1. **Yeni Proje Ekle** iletişim kutusunu açmak için **Dosya** menüsünden **Ekle** ve **Yeni proje** ' yi seçin.

2. Adlı `InheritanceTest`bir Windows Forms uygulaması oluşturun.

## <a name="add-an-inherited-form"></a>Devralınan form ekleme

1. **Çözüm Gezgini**, **InheritanceTest** projesine sağ tıklayın, **Ekle**' yi seçin ve ardından **Yeni öğe**' yi seçin.

2. **Yeni öğe Ekle** iletişim kutusunda **Windows Forms** kategorisini seçin (kategori listeniz varsa) ve ardından **devralınan form** şablonunu seçin.

3. Varsayılan adını `Form2` bırakın ve **Ekle**' ye tıklayın.

4. **Devralma Seçicisi** iletişim kutusunda, **BaseFormLibrary** projesinden öğesinden devralınacak form olarak **Form1** ' i seçin ve **Tamam**' a tıklayın.

     Bu, **BaseFormLibrary**biçimindeki formdan türetilen **InheritanceTest** projesinde bir form oluşturur.

5. Zaten açık değilse, tasarımcıda devralınan formu (**Form2**) çift tıklayarak açın.

    Tasarımcıda, devralınan düğmelerin bir sembolü vardır (![Visual Basic devralma sembolünün ekran görüntüsü.](./media/walkthrough-demonstrating-visual-inheritance/visual-basic-inheritance-glyph.gif)) üst köşede devralındığını gösterir.

6. **Merhaba deyin** düğmesini seçin ve yeniden boyutlandırma tutamaçlarını gözlemleyin. Bu düğme korunduğundan, devracılar onu taşıyabilir, yeniden boyutlandırabilir, resim yazısını değiştirebilir ve başka değişiklikler yapabilir.

7. Özel **söyleyin** düğmesini seçin ve yeniden boyutlandırma tutamaçları olmadığına dikkat edin. Ayrıca, **Özellikler** penceresinde bu düğmenin özellikleri, değiştirilmeyeceğini belirtmek için gridir.

8. Görsel C#kullanıyorsanız:

    1. **Çözüm Gezgini**, **InheritanceTest** projesinde **Form1** öğesine sağ tıklayın ve ardından **Sil**' i seçin. Görüntülenen ileti kutusunda, silme işlemini onaylamak için **Tamam** ' ı tıklatın.

    2. Program.cs dosyasını açın ve satırı `Application.Run(new Form1());` olarak `Application.Run(new Form2());`değiştirin.

9. **Çözüm Gezgini**, **InheritanceTest** projesine sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.

10. **Çözüm Gezgini**, **InheritanceTest** projesine sağ tıklayın ve **Özellikler**' i seçin.

11. **InheritanceTest** özelliği sayfalarında, **Başlangıç nesnesini** devralınan form (**Form2**) olarak ayarlayın.

12. **F5** tuşuna basarak uygulamayı çalıştırın ve devralınan formun davranışını gözlemleyin.

## <a name="next-steps"></a>Sonraki adımlar

Kullanıcı denetimleri için devralma de aynı şekilde çalışmaktadır. Yeni bir sınıf kitaplığı projesi açın ve bir kullanıcı denetimi ekleyin. Bileşen denetimlerini üzerine yerleştirin ve projeyi derleyin. Başka bir yeni sınıf kitaplığı projesi açın ve derlenen sınıf kitaplığına bir başvuru ekleyin. Ayrıca, projeye devralınan bir denetim eklemeyi ( **yeni öğeler Ekle** iletişim kutusu aracılığıyla) ve **Devralma seçicisini**kullanmayı deneyin. Bir kullanıcı denetimi ekleyin ve `Inherits` (`:` görsel C#olarak) ekstresini değiştirin. Daha fazla bilgi için [nasıl yapılır: Windows Forms](how-to-inherit-windows-forms.md)devralma.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Windows Forms devralma](how-to-inherit-windows-forms.md)
- [Windows Forms Görsel Devralma](windows-forms-visual-inheritance.md)
- [Windows Forms](../index.md)
