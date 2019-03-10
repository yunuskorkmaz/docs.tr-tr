---
title: 'Nasıl yapılır: Denetim sınıfından devralma'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
ms.openlocfilehash: cf1b3c7d7d530710c4c7e0fbd137667c3598500a
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702977"
---
# <a name="how-to-inherit-from-the-control-class"></a>Nasıl yapılır: Denetim sınıfından devralma
Bir Windows formunda kullanmak için tamamen özel bir denetim oluşturmak istiyorsanız, gelen alması gerektiğini <xref:System.Windows.Forms.Control> sınıfı. Öğesinden devralan çalışırken <xref:System.Windows.Forms.Control> daha fazla planlama ve uygulama gerçekleştirmek, ayrıca, en büyük çeşitli seçenekleri sağlar sınıfını gerektirir. Gelen devralınırken <xref:System.Windows.Forms.Control>, iş denetimleri yapar çok temel işlevleri devralır. Doğal olarak işlevselliğini <xref:System.Windows.Forms.Control> sınıf klavye ve fare kullanıcı girişini işleme sınırları ve denetimin boyutunu tanımlar, windows tanıtıcı sağlar ve ileti işleme ve güvenlik sağlar. Grafik arabiriminin denetimin gerçek işleme Bu durumda olan tüm boyama birleşmez ya da herhangi bir belirli bir kullanıcı etkileşimi işlevi dahil etmez. Tüm özel kod aracılığıyla bu görünüşler sağlamanız gerekir.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-a-custom-control"></a>Özel bir denetim oluşturmak için  
  
1.  Yeni bir **Windows uygulama** veya **Windows Denetim Kitaplığı** proje.  
  
2.  Gelen **proje** menüsünde seçin **sınıfı Ekle**.  
  
3.  İçinde **Yeni Öğe Ekle** iletişim kutusu, tıklayın **özel denetim**.  
  
     Yeni özel denetim projenize eklenir.  
  
4.  Açmak için F7'ye basın **Kod Düzenleyicisi** özel denetiminizin.  
  
5.  Bulun <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi çağrısı dışında boş olur <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi temel sınıf.  
  
6.  Denetim için istediğiniz herhangi bir özel boyama birleştirmek için kodu değiştirin.  
  
     Grafik denetimleri için işlemek için kod yazma hakkında daha fazla bilgi için bkz: [özel denetim boyama ve işleme](custom-control-painting-and-rendering.md).  
  
7.  Tüm özel yöntemler, özellikler veya denetiminiz birleştirecektir olayların uygulayın.  
  
8.  Kaydet ve denetim test edin.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Özel Denetim Çeşitleri](varieties-of-custom-controls.md)
- [Nasıl yapılır: UserControl sınıfından devralma](how-to-inherit-from-the-usercontrol-class.md)
- [Nasıl yapılır: Mevcut Windows Formları denetimlerinden devralma](how-to-inherit-from-existing-windows-forms-controls.md)
- [Nasıl yapılır: Windows Forms için yazar denetimleri](how-to-author-controls-for-windows-forms.md)
- [Basic'de devralınmış olay işleyicileri Visual Basic sorunlarını giderme](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Tasarım Zamanında Windows Forms Denetimleri Geliştirme](developing-windows-forms-controls-at-design-time.md)
