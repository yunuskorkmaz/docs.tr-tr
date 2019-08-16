---
title: 'Nasıl yapılır: Control Sınıfından Devralma'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
ms.openlocfilehash: 535827db660ab1113a25a01b7a0553a1c4414c74
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037782"
---
# <a name="how-to-inherit-from-the-control-class"></a>Nasıl yapılır: Control Sınıfından Devralma
Bir Windows formunda kullanmak üzere tamamen özel bir denetim oluşturmak isterseniz, <xref:System.Windows.Forms.Control> sınıfından ' ı devralması gerekir. <xref:System.Windows.Forms.Control> Sınıfından devralma işlemi daha fazla planlama ve uygulama gerçekleştirmenizi gerektirdiğinden, size en fazla seçenek aralığını da sağlar. ' Dan <xref:System.Windows.Forms.Control>devralırken, denetimlerin çalışmasını sağlayan temel işlevsellikleri devralırsınız. <xref:System.Windows.Forms.Control> Sınıfında devralınan işlevler, klavye ve fare aracılığıyla Kullanıcı girişini işler, denetimin sınırlarını ve boyutunu tanımlar, bir Windows tutamacı sağlar ve ileti işleme ve güvenlik sağlar. Bu, denetimin grafik arabiriminin gerçek işlemesi olan veya belirli kullanıcı etkileşimi işlevlerini dahil eden herhangi bir boyama içermez. Bu yönlerinin tümünü özel kod aracılığıyla sağlamanız gerekir.

## <a name="to-create-a-custom-control"></a>Özel bir denetim oluşturmak için

1. Yeni bir **Windows uygulaması** veya **Windows Denetim Kitaplığı** projesi oluşturun.

2. **Proje** menüsünden **Sınıf Ekle**' yi seçin.

3. **Yeni öğe Ekle** Iletişim kutusunda **özel denetim ' e**tıklayın.

     Projenize yeni bir özel denetim eklenir.

4. Özel denetiminizin **kod düzenleyicisini** açmak için F7 tuşuna basın.

5. Temel sınıf <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemine yapılan bir çağrı dışında boş olacak yöntemibulun.<xref:System.Windows.Forms.Control.OnPaint%2A>

6. Denetiminiz için istediğiniz özel boyamayı içerecek şekilde kodu değiştirin.

     Denetimler için grafik işlemek üzere kod yazma hakkında daha fazla bilgi için bkz. [özel denetim boyama ve işleme](custom-control-painting-and-rendering.md).

7. Denetiminizin dahil olacağı özel yöntemleri, özellikleri veya olayları uygulayın.

8. Denetiminizi kaydedin ve test edin.

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Denetim Çeşitleri](varieties-of-custom-controls.md)
- [Nasıl yapılır: UserControl sınıfından devralma](how-to-inherit-from-the-usercontrol-class.md)
- [Nasıl yapılır: Mevcut Windows Forms denetimlerinden devralma](how-to-inherit-from-existing-windows-forms-controls.md)
- [Nasıl yapılır: Windows Forms için yazar denetimleri](how-to-author-controls-for-windows-forms.md)
- [Visual Basic devralınan olay Işleyicileriyle ilgili sorunları giderme](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Tasarım Zamanında Windows Forms Denetimleri Geliştirme](developing-windows-forms-controls-at-design-time.md)
