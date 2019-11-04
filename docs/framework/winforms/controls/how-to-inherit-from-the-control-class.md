---
title: 'Nasıl yapılır: Denetim Sınıfından Devralma'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7af7d1fe8f14c71dfc90836d84023b98feb44961
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458375"
---
# <a name="how-to-inherit-from-the-control-class"></a>Nasıl yapılır: Denetim Sınıfından Devralma

Bir Windows formunda kullanmak üzere tamamen özel bir denetim oluşturmak istiyorsanız <xref:System.Windows.Forms.Control> sınıfından ' ı devralması gerekir. <xref:System.Windows.Forms.Control> sınıfından devralırken daha fazla planlama ve uygulama gerçekleştirmeniz gerekir, Ayrıca size en fazla seçenek aralığını da sağlar. <xref:System.Windows.Forms.Control>devralırken, denetimlerin çalışmasını sağlayan temel işlevsellikleri devralırsınız. <xref:System.Windows.Forms.Control> sınıfında devralınan işlevler, klavye ve fare aracılığıyla Kullanıcı girişini işler, denetimin sınırlarını ve boyutunu tanımlar, bir Windows tutamacı sağlar ve ileti işleme ve güvenlik sağlar. Bu, denetimin grafik arabiriminin gerçek işlemesi olan veya belirli kullanıcı etkileşimi işlevlerini dahil eden herhangi bir boyama içermez. Bu yönlerinin tümünü özel kod aracılığıyla sağlamanız gerekir.

## <a name="to-create-a-custom-control"></a>Özel bir denetim oluşturmak için

1. Visual Studio 'da yeni bir **Windows uygulaması** veya **Windows Denetim Kitaplığı** projesi oluşturun.

2. **Proje** menüsünden **Sınıf Ekle**' yi seçin.

3. **Yeni öğe Ekle** Iletişim kutusunda **özel denetim ' e**tıklayın.

   Projenize yeni bir özel denetim eklenir.

4. Özel denetiminizin **kod düzenleyicisini** açmak için **F7** tuşuna basın.

5. Temel sınıfın <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemine yönelik bir çağrı haricinde boş olacak <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemini bulun.

6. Denetiminiz için istediğiniz özel boyamayı içerecek şekilde kodu değiştirin.

   Denetimler için grafik işlemek üzere kod yazma hakkında daha fazla bilgi için bkz. [özel denetim boyama ve işleme](custom-control-painting-and-rendering.md).

7. Denetiminizin dahil olacağı özel yöntemleri, özellikleri veya olayları uygulayın.

8. Denetiminizi kaydedin ve test edin.

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Denetim Çeşitleri](varieties-of-custom-controls.md)
- [Nasıl yapılır: UserControl Sınıfından Devralma](how-to-inherit-from-the-usercontrol-class.md)
- [Nasıl yapılır: Mevcut Windows Forms Denetimlerinden Devralma](how-to-inherit-from-existing-windows-forms-controls.md)
- [Nasıl yapılır: Windows Forms için Denetimler Yazma](how-to-author-controls-for-windows-forms.md)
- [Visual Basic devralınan olay Işleyicileriyle ilgili sorunları giderme](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Tasarım Zamanında Windows Forms Denetimleri Geliştirme](developing-windows-forms-controls-at-design-time.md)
