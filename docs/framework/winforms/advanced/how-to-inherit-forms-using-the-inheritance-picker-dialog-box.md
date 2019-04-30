---
title: 'Nasıl yapılır: Devralma Seçici İletişim Kutusunu Kullanarak Form Devralma'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], forms
- Inheritance Picker dialog box
- inherited forms [Windows Forms], creating
ms.assetid: 969b4c04-12aa-4297-93a2-0ae747447823
ms.openlocfilehash: 5ae1c236835141b10bc704cd39f55de6e3e974b0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723137"
---
# <a name="how-to-inherit-forms-using-the-inheritance-picker-dialog-box"></a>Nasıl yapılır: Devralma Seçici İletişim Kutusunu Kullanarak Form Devralma
Bir form veya diğer nesne devral en kolay yolu kullanmaktır **devralma Seçici** iletişim kutusu. Bununla, diğer çözümlere önceden oluşturduğunuz kodu veya kullanıcı arabirimi (UI) avantajlarından yararlanabilirsiniz.  
  
> [!NOTE]
>  Bir form devralma için **devralma Seçici** iletişim kutusunda, bu formu içeren proje gerekir oluşturulan bir yürütülebilir dosya veya DLL. Projeyi oluşturmak için Seç **Çözümü Derle** gelen **derleme** menüsü.  
>   
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-a-windows-form-inherited-from-an-existing-form-by-using-the-inheritance-picker"></a>Devralma Seçici'yi kullanarak varolan bir formdan devralınan bir Windows formu oluşturma  
  
1. Gelen **proje** menüsünde seçin **Windows formu eklemek**.  
  
     **Yeni Öğe Ekle** iletişim kutusu açılır.  
  
2. Arama **devralınan Form** searchbox ya tıklayarak şablonu **Windows Forms** kategorisini seçin ve içinde ad **adı** kutusu. Tıklayın **Ekle** devam etmek için düğmesine.  
  
     **Devralma Seçici** iletişim kutusu açılır. Geçerli proje forms içeriyorsa, bunlar görüntülenir **devralma Seçici** iletişim kutusu.  
  
3. Bir formdan başka bir derlemede devralmak için tıklatın **Gözat** düğmesi.  
  
4. İçinde **devralınacak bir bileşen içeren bir dosya seçin** iletişim kutusunda, istediğiniz modülü ve formu içeren projeye gidin.  
  
5. Onu seçin ve .exe veya .dll dosyası adına **açık** düğmesi.  
  
     Bu size döndürür **devralma Seçici** iletişim kutusu, burada bileşen artık listelenir, yanı sıra, bulunduğu proje.  
  
6. Bileşeni seçin.  
  
     İçinde **Çözüm Gezgini**, bileşen projenize eklenir. Bir kullanıcı Arabirimi varsa, devralınmış bir form parçası olan denetimler bir simge ile işaretlenir (![ekran görüntüsü Visual Basic kalıtımı sembol.](./media/how-to-inherit-forms-using-the-inheritance-picker-dialog-box/visual-basic-inheritance-glyph.gif)) ve seçili olduğunda, denetimin sahip güvenlik düzeyini gösteren bir kenarlığa sahip üst formu. Aşağıdaki tabloda farklı güvenlik düzeylerine karşılık gelen davranışlar listelenmektedir.  
  
    |Denetim için güvenlik düzeyi|Kullanılabilir etkileşiminin Tasarımcısı ve form devralınmış Kod Düzenleyicisi|  
    |-------------------------------|--------------------------------------------------------------------------------|  
    |Ortak|Boyutlandırma tutamaçları ile standart kenarlık: denetim boyutlandırıldığından ve taşındı. Denetim, dahili olarak onu bildiren sınıfın ve harici olarak diğer sınıflar tarafından erişilebilir.|  
    |Korumalı|Boyutlandırma tutamaçları ile standart kenarlık: denetim boyutlandırıldığından ve taşındı. Dahili olarak onu bildiren sınıfın ve üst sınıfından devralır, ancak dış sınıfları tarafından erişilemez herhangi bir sınıf tarafından erişilebilir.|  
    |İç (korumalı Visual Basic'te Friend) korumalı|Boyutlandırma tutamaçları ile standart kenarlık: denetim boyutlandırıldığından ve taşındı. Dahili olarak onu bildiren sınıfın, üst sınıfından devralan herhangi bir sınıf ve onu içeren derlemenin genel diğer üyeleri tarafından erişilebilir.|  
    |İç (Visual Basic'te Friend)|Standart Özellikler görünür formunda gösterilen hiçbir boyutlandırma tutamaçlarını kenarlıklı **özellikleri** penceresi. Ancak, tüm yönlerini denetimi salt okunur kabul edilir. Taşıyamaz veya denetimin boyutunu veya özelliklerini değiştirin. Denetim bir grup kutusu gibi diğer denetim kapsayıcısı ise yeni denetimler eklenemez ve bu denetimleri ortak bile mevcut denetimleri kaldırılamaz. Denetim, yalnızca derlemenin içerdiği diğer üyeleri tarafından erişilebilir.|  
    |Özel|Standart Özellikler görünür formunda gösterilen hiçbir boyutlandırma tutamaçlarını kenarlıklı **özellikleri** penceresi. Ancak, tüm yönlerini denetimi salt okunur kabul edilir. Taşıyamaz veya denetimin boyutunu veya özelliklerini değiştirin. Denetim bir grup kutusu gibi diğer denetim kapsayıcısı ise yeni denetimler eklenemez ve bu denetimleri ortak bile mevcut denetimleri kaldırılamaz. Denetim yalnızca bunu bildiren bir sınıf tarafından erişilebilir.|  
  
     Taban formun görünüşünü değiştirme hakkında daha fazla bilgi için bkz: [taban formun görünüşünü değiştirmenin etkileri](effects-of-modifying-base-form-appearance.md).  
  
    > [!NOTE]
    >  Standart denetimler ve Windows Forms bileşenleri ile devralınan denetimler ve bileşenler birleştirdiğinizde çakışmaları z-sıralamasıyla ile karşılaşabilirsiniz. Z-tıklayarak yapılır sırasını değiştirerek bunu düzeltebilirsiniz **biçimi** işaret menüsünde **sipariş**ve ardından **öne** veya  **Arkaya Gönder**. Denetimleri z düzeni hakkında daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms'da nesneleri katmanlara](../controls/how-to-layer-objects-on-windows-forms.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Inherits Deyimi](~/docs/visual-basic/language-reference/statements/inherits-statement.md)
- [using](~/docs/csharp/language-reference/keywords/using.md)
- [Taban Formun Görünüşünü Değiştirmenin Etkileri](effects-of-modifying-base-form-appearance.md)
- [Windows Forms Görsel Devralma](windows-forms-visual-inheritance.md)
