---
title: 'Nasıl yapılır: Mevcut Windows Forms Denetimlerinden Devralma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- custom controls [Windows Forms], inheritance
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
ms.openlocfilehash: 9ac18fae126425126712dafeb80f05663dfc2ebc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966595"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a>Nasıl yapılır: Mevcut Windows Forms Denetimlerinden Devralma
Varolan bir denetimin işlevselliğini genişletmek istiyorsanız, devralma yoluyla var olan bir denetimden türetilmiş bir denetim oluşturabilirsiniz. Var olan bir denetimden devralınırken, bu denetimin tüm işlevselliğini ve görsel özelliklerini devralırsınız. Örneğin, öğesinden <xref:System.Windows.Forms.Button>devralınan bir denetim oluşturuyorsanız, yeni denetiminiz bir standart <xref:System.Windows.Forms.Button> denetim gibi görünür ve çalışır. Daha sonra özel yöntemlerin ve özelliklerin uygulanmasıyla yeni denetiminizin işlevselliğini genişletebilir veya değiştirebilirsiniz. Bazı denetimlerde, kendi <xref:System.Windows.Forms.Control.OnPaint%2A> metodunu geçersiz kılarak devralınmış denetiminizin görsel görünümünü de değiştirebilirsiniz.

## <a name="to-create-an-inherited-control"></a>Devralınan bir denetim oluşturmak için

1. Yeni bir **Windows Forms uygulama** projesi oluşturun.

2. **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.

     **Yeni Öğe Ekle** iletişim kutusu görünür.

3. **Yeni öğe Ekle** Iletişim kutusunda **özel denetim ' e**çift tıklayın.

     Projenize yeni bir özel denetim eklenir.

4. Visual Basic kullanıyorsanız, **Çözüm Gezgini**üst kısmında **tüm dosyaları göster**' e tıklayın. CustomControl1. vb öğesini genişletin ve ardından kod düzenleyicisinde CustomControl1. Designer. vb dosyasını açın.

5. Kullanıyorsanız C#, kod düzenleyicisi 'nde CustomControl1.cs öğesini açın.

6. Öğesinden <xref:System.Windows.Forms.Control>devralan sınıf bildirimini bulun.

7. Taban sınıfını, devralması istediğiniz denetim olarak değiştirin.

     Örneğin, öğesinden <xref:System.Windows.Forms.Button>devralma yapmak istiyorsanız, sınıf bildirimini aşağıdaki şekilde değiştirin:

    ```vb
    Partial Class CustomControl1
        Inherits System.Windows.Forms.Button
    ```

    ```csharp
    public partial class CustomControl1 : System.Windows.Forms.Button
    ```

8. Visual Basic kullanıyorsanız, CustomControl1. Designer. vb dosyasını kaydedin ve kapatın. Kod Düzenleyicisi 'nde CustomControl1. vb dosyasını açın.

9. Denetiminizin dahil olacağı özel yöntemleri veya özellikleri uygulayın.

10. Denetiminizin grafik görünümünü değiştirmek istiyorsanız, <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemini geçersiz kılın.

    > [!NOTE]
    > Geçersiz <xref:System.Windows.Forms.Control.OnPaint%2A> kılma, tüm denetimlerin görünümünü değiştirmenize izin vermez. Tüm boyama pencerelerinin Windows tarafından (örneğin, <xref:System.Windows.Forms.TextBox>) yaptığı denetimler hiçbir şekilde <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemini çağırmaz ve bu nedenle özel kodu hiçbir şey kullanmaz. <xref:System.Windows.Forms.Control.OnPaint%2A> Yöntemin kullanılabilir olup olmadığını görmek için değiştirmek istediğiniz belirli denetim için yardım belgelerine başvurun. Tüm Windows form denetimlerinin listesi için bkz. [Windows Forms Için kullanılacak denetimler](controls-to-use-on-windows-forms.md). Bir denetim <xref:System.Windows.Forms.Control.OnPaint%2A> üye yöntemi olarak listelenmiyorsa, bu yöntemi geçersiz kılarak görünümünü değiştiremezsiniz. Özel boyama hakkında daha fazla bilgi için bkz. [özel denetim boyama ve işleme](custom-control-painting-and-rendering.md).

    ```vb
    Protected Overrides Sub OnPaint(ByVal e As _
       System.Windows.Forms.PaintEventArgs)
       MyBase.OnPaint(e)
       ' Insert code to do custom painting.
       ' If you want to completely change the appearance of your control,
       ' do not call MyBase.OnPaint(e).
    End Sub
    ```

    ```csharp
    protected override void OnPaint(PaintEventArgs pe)
    {
       base.OnPaint(pe);
       // Insert code to do custom painting.
       // If you want to completely change the appearance of your control,
       // do not call base.OnPaint(pe).
    }
    ```

11. Denetiminizi kaydedin ve test edin.

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Denetim Çeşitleri](varieties-of-custom-controls.md)
- [Nasıl yapılır: Denetim sınıfından devralma](how-to-inherit-from-the-control-class.md)
- [Nasıl yapılır: UserControl sınıfından devralma](how-to-inherit-from-the-usercontrol-class.md)
- [Nasıl yapılır: Windows Forms için yazar denetimleri](how-to-author-controls-for-windows-forms.md)
- [Visual Basic devralınan olay Işleyicileriyle ilgili sorunları giderme](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [İzlenecek yol: Visual Basic ile Windows Forms denetiminden devralma](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)
- [İzlenecek yol: Görsel ile Windows Forms denetiminden devralmaC#](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
