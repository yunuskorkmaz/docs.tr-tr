---
title: Mevcut Denetimlerden Devralma
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
ms.openlocfilehash: b0e0053816efde349c7e4d13d03bef5f8801c667
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78849386"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a>Nasıl yapılır: Mevcut Windows Formları Denetimlerinden Devralma

Varolan bir denetimin işlevselliğini genişletmek istiyorsanız, devralma yoluyla varolan denetimden türetilen bir denetim oluşturabilirsiniz. Varolan bir denetimden devralırken, bu denetimin tüm işlevselliğini ve görsel özelliklerini devralırsınız. Örneğin, devralınan bir denetim <xref:System.Windows.Forms.Button>oluşturuyorsanız, yeni denetiminiz tam olarak standart <xref:System.Windows.Forms.Button> bir denetim gibi görünür ve hareket eder. Daha sonra özel yöntemler ve özellikler uygulanması yoluyla yeni denetimişlevselliğini genişletmek veya değiştirmek olabilir. Bazı denetimlerde, <xref:System.Windows.Forms.Control.OnPaint%2A> metodunu geçersiz kılarak devralınan denetiminizin görsel görünümünü de değiştirebilirsiniz.

## <a name="to-create-an-inherited-control"></a>Devralınan bir denetim oluşturmak için

1. Visual Studio'da yeni bir **Windows Forms Application** projesi oluşturun.

1. **Proje** menüsünden **Yeni Öğe Ekle'yi**seçin.

    **Yeni Öğe Ekle** iletişim kutusu görünür.

1. Yeni **Öğe Ekle** iletişim kutusunda, **Özel Denetim'i**çift tıklatın.

    Projenize yeni bir özel denetim eklenir.

1. Kullanıyorsanız:

    - Visual Basic, Çözüm **Gezgini'nin**en üstünde, **Tüm Dosyaları Göster'i**tıklatın. CustomControl1.vb'i genişletin ve ardından Code Editor'da CustomControl1.Designer.vb'yi açın.
    - C#, Kod Düzenleyicisi'nde CustomControl1.cs açın.

1. 'den <xref:System.Windows.Forms.Control>devralınan sınıf bildirimini bulun

1. Taban sınıfı devralmak istediğiniz denetimle değiştirin.

     Örneğin, devralmak <xref:System.Windows.Forms.Button>istiyorsanız, sınıf bildirimini aşağıdakiyle değiştirin:

    ```vb
    Partial Class CustomControl1
        Inherits System.Windows.Forms.Button
    ```

    ```csharp
    public partial class CustomControl1 : System.Windows.Forms.Button
    ```

1. Visual Basic kullanıyorsanız, CustomControl1.Designer.vb kaydedin ve kapatın. Code Editor'da CustomControl1.vb'i açın.

1. Denetiminizin dahil edeceği özel yöntemler veya özellikler uygulayın.

1. Denetiminizin grafik görünümünü değiştirmek istiyorsanız, <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi geçersiz kılın.

    > [!NOTE]
    > Geçersiz <xref:System.Windows.Forms.Control.OnPaint%2A> kılma, tüm denetimlerin görünümünü değiştirmenize izin vermez. Tüm resimlerini Windows tarafından yapılan bu denetimler <xref:System.Windows.Forms.TextBox>(örneğin,) asla kendi yöntemlerini <xref:System.Windows.Forms.Control.OnPaint%2A> aramaz ve bu nedenle özel kodu asla kullanmaz. <xref:System.Windows.Forms.Control.OnPaint%2A> Yöntemin kullanılabilir olup olmadığını görmek için değiştirmek istediğiniz özel denetim için Yardım belgelerine bakın. Tüm Windows Form Denetimlerinin listesi için [Windows Formlarında Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)bölümüne bakın. Denetim üye yöntemi <xref:System.Windows.Forms.Control.OnPaint%2A> olarak listelenmemişse, bu yöntemi geçersiz kılarak görünümünü değiştiremezsiniz. Özel boyama hakkında daha fazla bilgi için [Bkz. Özel Denetim Boyama ve Oluşturma.](custom-control-painting-and-rendering.md)

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

1. Kaydedin ve kontrol test edin.

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Denetim Çeşitleri](varieties-of-custom-controls.md)
- [Nasıl yapılır: Denetim Sınıfından Devralma](how-to-inherit-from-the-control-class.md)
- [Nasıl yapılır: UserControl Sınıfından Devralma](how-to-inherit-from-the-usercontrol-class.md)
- [Nasıl yapılır: Windows Forms için Denetimler Yazma](how-to-author-controls-for-windows-forms.md)
- [Visual Basic'de Devralınmış Olay İşleyicileri İle İlgili Sorun Giderme](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Walkthrough: Windows Forms Denetiminden Devralma](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
