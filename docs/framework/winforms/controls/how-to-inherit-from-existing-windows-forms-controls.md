---
title: 'Nasıl yapılır: Mevcut Windows Formları Denetimlerinden Devralma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- custom controls [Windows Forms], inheritance
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 063f5bb87b6348ee83573cf1506c9fabdaf651ee
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460571"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a>Nasıl yapılır: Mevcut Windows Formları Denetimlerinden Devralma

Varolan bir denetimin işlevselliğini genişletmek istiyorsanız, devralma yoluyla var olan bir denetimden türetilmiş bir denetim oluşturabilirsiniz. Var olan bir denetimden devralınırken, bu denetimin tüm işlevselliğini ve görsel özelliklerini devralırsınız. Örneğin, <xref:System.Windows.Forms.Button>devralınan bir denetim oluşturuyorsanız, yeni denetiminiz standart bir <xref:System.Windows.Forms.Button> denetimi gibi görünür ve aynı şekilde davranır. Daha sonra özel yöntemlerin ve özelliklerin uygulanmasıyla yeni denetiminizin işlevselliğini genişletebilir veya değiştirebilirsiniz. Bazı denetimlerde, <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemini geçersiz kılarak devralınmış denetiminizin görsel görünümünü de değiştirebilirsiniz.

## <a name="to-create-an-inherited-control"></a>Devralınan bir denetim oluşturmak için

1. Visual Studio 'da yeni bir **Windows Forms uygulama** projesi oluşturun.

1. **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.

    **Yeni öğe Ekle** iletişim kutusu görüntülenir.

1. **Yeni öğe Ekle** Iletişim kutusunda **özel denetim ' e**çift tıklayın.

    Projenize yeni bir özel denetim eklenir.

1. Şunu kullanıyorsanız:

    - Visual Basic, **Çözüm Gezgini**üst kısmında **tüm dosyaları göster**' e tıklayın. CustomControl1. vb öğesini genişletin ve ardından kod düzenleyicisinde CustomControl1. Designer. vb dosyasını açın.
    - C#, kod düzenleyicisinde CustomControl1.cs öğesini açın.

1. <xref:System.Windows.Forms.Control>devralan sınıf bildirimini bulun.

1. Taban sınıfını, devralması istediğiniz denetim olarak değiştirin.

     Örneğin, <xref:System.Windows.Forms.Button>devralma yapmak istiyorsanız, sınıf bildirimini aşağıdaki şekilde değiştirin:

    ```vb
    Partial Class CustomControl1
        Inherits System.Windows.Forms.Button
    ```

    ```csharp
    public partial class CustomControl1 : System.Windows.Forms.Button
    ```

1. Visual Basic kullanıyorsanız, CustomControl1. Designer. vb dosyasını kaydedin ve kapatın. Kod Düzenleyicisi 'nde CustomControl1. vb dosyasını açın.

1. Denetiminizin dahil olacağı özel yöntemleri veya özellikleri uygulayın.

1. Denetiminizin grafik görünümünü değiştirmek istiyorsanız <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemini geçersiz kılın.

    > [!NOTE]
    > <xref:System.Windows.Forms.Control.OnPaint%2A> geçersiz kılmak tüm denetimlerin görünümünü değiştirmenize izin vermez. Tüm boyalarını Windows tarafından gerçekleştirilen (örneğin, <xref:System.Windows.Forms.TextBox>) denetimler hiçbir şekilde <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemini çağırmaz ve bu nedenle özel kodu hiçbir şekilde kullanmaz. <xref:System.Windows.Forms.Control.OnPaint%2A> yönteminin kullanılabilir olup olmadığını görmek için değiştirmek istediğiniz belirli denetim için yardım belgelerine başvurun. Tüm Windows form denetimlerinin listesi için bkz. [Windows Forms Için kullanılacak denetimler](controls-to-use-on-windows-forms.md). Bir denetimin üye yöntemi olarak listelenen <xref:System.Windows.Forms.Control.OnPaint%2A> yoksa, bu yöntemi geçersiz kılarak görünümünü değiştiremezsiniz. Özel boyama hakkında daha fazla bilgi için bkz. [özel denetim boyama ve işleme](custom-control-painting-and-rendering.md).

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

1. Denetiminizi kaydedin ve test edin.

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Denetim Çeşitleri](varieties-of-custom-controls.md)
- [Nasıl yapılır: Denetim Sınıfından Devralma](how-to-inherit-from-the-control-class.md)
- [Nasıl yapılır: UserControl Sınıfından Devralma](how-to-inherit-from-the-usercontrol-class.md)
- [Nasıl yapılır: Windows Forms için Denetimler Yazma](how-to-author-controls-for-windows-forms.md)
- [Visual Basic devralınan olay Işleyicileriyle ilgili sorunları giderme](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [İzlenecek yol: Windows Forms denetiminden devralma](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
