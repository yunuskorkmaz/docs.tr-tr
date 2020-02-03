---
title: Denetimden Devralma
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: 09476da0-8d4c-4a4c-b969-649519dfb438
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 713ccf97a73ce9684b9124a121369f22751861d0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740143"
---
# <a name="walkthrough-inherit-from-a-windows-forms-control-with-c"></a>İzlenecek yol: C\# ile Windows Forms denetiminden devralma

İle C# *Devralma*yoluyla güçlü özel denetimler oluşturabilirsiniz. Devralma aracılığıyla standart Windows Forms denetimlerinin tüm devralınan işlevlerini koruyan ancak özel işlevleri de birleştiren denetimler oluşturabilirsiniz. Bu izlenecek yolda, `ValueButton`adlı basit bir devralınmış denetim oluşturacaksınız. Bu düğme standart Windows Forms <xref:System.Windows.Forms.Button> denetiminden işlevselliği devralacak ve `ButtonValue`adlı özel bir özelliği kullanıma sunacaktır.

## <a name="create-the-project"></a>Projeyi Oluşturma

Yeni bir proje oluşturduğunuzda, kök ad alanı, derleme adı ve proje adını ayarlamak ve varsayılan bileşenin doğru ad alanında yer aldığından emin olmak için adını belirtin.

### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a>ValueButtonLib denetim kitaplığını ve ValueButton denetimini oluşturmak için

1. Visual Studio 'da yeni bir **Windows Forms denetim kitaplığı** projesi oluşturun ve **ValueButtonLib**olarak adlandırın.

     `ValueButtonLib`proje adı, varsayılan olarak kök ad alanına da atanır. Kök ad alanı, derlemedeki bileşenlerin adlarını nitelemek için kullanılır. Örneğin, iki derleme `ValueButton`adlı bileşenler sağlamışsa, `ValueButtonLib.ValueButton`kullanarak `ValueButton` bileşenini belirtebilirsiniz. Daha fazla bilgi için bkz. [ad alanları](../../../csharp/programming-guide/namespaces/index.md).

2. **Çözüm Gezgini**' de, **UserControl1.cs**' a sağ tıklayıp kısayol menüsünden **Yeniden Adlandır** ' ı seçin. Dosya adını **ValueButton.cs**olarak değiştirin. '`UserControl1`' kod öğesiyle tüm başvuruları yeniden adlandırmak isteyip istemediğiniz sorulduğunda **Evet** düğmesine tıklayın.

3. **Çözüm Gezgini**' de, **ValueButton.cs** ' a sağ tıklayın ve **kodu görüntüle**' yi seçin.

4. `class` bildiri satırını bulun, `public partial class ValueButton`ve bu denetimin devraldığı türü <xref:System.Windows.Forms.UserControl> <xref:System.Windows.Forms.Button>olarak değiştirin. Bu, devralınan denetiminizin <xref:System.Windows.Forms.Button> denetiminin tüm işlevlerini devralmasına olanak tanır.

5. **Çözüm Gezgini**, tasarımcı tarafından oluşturulan kod dosyasını göstermek için **ValueButton.cs** düğümünü açın, **ValueButton.Designer.cs**. Bu dosyayı **kod düzenleyicisinde**açın.

6. `InitializeComponent` yöntemini bulun ve <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> özelliğini atayan çizgiyi kaldırın. Bu özellik <xref:System.Windows.Forms.Button> denetiminde yok.

7. Projeyi kaydetmek için **Dosya** menüsünden **Tümünü Kaydet** ' i seçin.

    > [!NOTE]
    > Görsel tasarımcı artık kullanılamıyor. <xref:System.Windows.Forms.Button> denetimi kendi boyadığı için, tasarımcıda görünümünü değiştiremedik. Görsel temsili, kodda değiştirilmediği sürece (yani, <xref:System.Windows.Forms.Button>) devraldığı sınıftan tam olarak aynı olacaktır. Tasarım yüzeyine, UI öğesi içermeyen bileşenler ekleyebilirsiniz.

## <a name="add-a-property-to-your-inherited-control"></a>Devralınan denetimi bir özellik ekleyin

Devralınan Windows Forms denetimlerinin olası bir kullanımı, standart Windows Forms denetimlerinin görünümü ve hisde aynı olan, ancak özel özellikler sunan denetimlerin oluşturulması. Bu bölümde, denetimi `ButtonValue` adlı bir özellik ekleyeceksiniz.

### <a name="to-add-the-value-property"></a>Değer özelliğini eklemek için

1. **Çözüm Gezgini**' de, **ValueButton.cs**' a sağ tıklayın ve ardından kısayol menüsünde **kodu görüntüle** ' ye tıklayın.

2. `class` ifadesini bulun. `{`hemen sonra aşağıdaki kodu yazın:

    ```csharp
    // Creates the private variable that will store the value of your
    // property.
    private int varValue;
    // Declares the property.
    public int ButtonValue
    {
       // Sets the method for retrieving the value of your property.
       get
       {
          return varValue;
       }
       // Sets the method for setting the value of your property.
       set
       {
          varValue = value;
       }
    }
    ```

     Bu kod, `ButtonValue` özelliğinin depolandığı ve alındığı yöntemleri belirler. `get` ifade, özel değişken `varValue`depolanan değere döndürülen değeri ayarlar ve `set` ifade, `value` anahtar sözcüğünün kullanımıyla özel değişkenin değerini ayarlar.

3. Projeyi kaydetmek için **Dosya** menüsünden **Tümünü Kaydet** ' i seçin.

## <a name="test-the-control"></a>Denetimi test etme

Denetimler tek başına projeler değildir; Bunlar bir kapsayıcıda barındırılmalıdır. Denetiminizi test etmek için, içinde çalışması için bir test projesi sağlamanız gerekir. Ayrıca, denetimi (derleyerek) oluşturarak denetiminizi test projesi için de erişilebilir yapmanız gerekir. Bu bölümde, denetiminizi oluşturacak ve bir Windows formunda test edersiniz.

### <a name="to-build-your-control"></a>Denetiminizi oluşturmak için

**Yapı** menüsünde **Yapı Çözümü**’ne tıklayın. Derleme, derleyici hataları veya uyarıları olmadan başarılı olmalıdır.

### <a name="to-create-a-test-project"></a>Bir test projesi oluşturmak için

1. **Dosya** menüsünde, **Ekle** ' nin üzerine gelin **ve yeni proje ' ye** tıklayarak yeni proje **Ekle** iletişim kutusunu açın.

2. **Görsel C#**  düğümün altında **Windows** düğümünü seçin ve **Windows Forms uygulama**' ya tıklayın.

3. **Ad** kutusuna **Test**girin.

4. **Çözüm Gezgini**, test projeniz için **Başvurular** düğümüne sağ tıklayın ve ardından kısayol menüsünden **Başvuru Ekle** ' yi seçerek **Başvuru Ekle** iletişim kutusunu görüntüleyin.

5. Etiketli **Projeler**sekmesine tıklayın. ValueButtonLib projeniz **Proje adı**altında listelenecektir. Başvuruyu test projesine eklemek için projeye çift tıklayın.

6. **Çözüm Gezgini** ' de **Test** ' e sağ tıklayın ve **Oluştur**' u seçin.

### <a name="to-add-your-control-to-the-form"></a>Formunuza denetim eklemek için

1. **Çözüm Gezgini**' de, **Form1.cs** ' ye sağ tıklayıp kısayol menüsünden **tasarımcıyı görüntüle** ' yi seçin.

2. **Araç kutusunda** **ValueButtonLib bileşenleri**' ni seçin. **ValueButton**öğesine çift tıklayın.

     Formda bir **ValueButton** görünür.

3. **ValueButton** öğesine sağ tıklayın ve kısayol menüsünden **Özellikler** ' i seçin.

4. **Özellikler** penceresinde, bu denetimin özelliklerini inceleyin. Bunlar, bir standart düğme tarafından sunulan özelliklerle aynıdır, ancak ek bir özellik, ButtonValue olur.

5. **ButtonValue** özelliğini **5**olarak ayarlayın.

6. Formunuza bir <xref:System.Windows.Forms.Label> denetimi eklemek için **araç kutusunun** **tüm Windows Forms** sekmesinde **etiket** ' e çift tıklayın.

7. Etiketi formun merkezine yeniden yerleştir.

8. `valueButton1`çift tıklayın.

     **Kod düzenleyicisi** `valueButton1_Click` olayına açılır.

9. Aşağıdaki kod satırını ekleyin.

    ```csharp
    label1.Text = valueButton1.ButtonValue.ToString();
    ```

10. **Çözüm Gezgini**' de **Test**' e sağ tıklayın ve kısayol menüsünde **Başlangıç projesi olarak ayarla** ' yı seçin.

11. **Hata Ayıkla** menüsünden **hata ayıklamayı Başlat**' ı seçin.

     `Form1` görüntülenir.

12. `valueButton1` öğesine tıklayın.

     ' 5 ' rakamı, devralınan denetiminizin `ButtonValue` özelliğinin `valueButton1_Click` yöntemi aracılığıyla `label1` geçtiğini gösteren `label1`görüntülenir. Bu nedenle `ValueButton` denetiminiz standart Windows Forms düğmesinin tüm işlevlerini devralır, ancak ek, özel bir özellik sunar.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Araç Kutusu Öğelerini Seç İletişim Kutusunda bir Denetimi Görüntüleme](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [İzlenecek yol: Visual C# İle Bileşik Denetim Yazma](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
