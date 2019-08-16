---
title: 'Nasıl yapılır: Devralma Seçici İletişim Kutusunu Kullanarak Form Devralma'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], forms
- Inheritance Picker dialog box
- inherited forms [Windows Forms], creating
ms.assetid: 969b4c04-12aa-4297-93a2-0ae747447823
ms.openlocfilehash: 9382f1bf890fb5a886cf547d9b1e9b3031c12eb6
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040001"
---
# <a name="how-to-inherit-forms-using-the-inheritance-picker"></a>Nasıl yapılır: Devralma seçiciyi kullanarak formları devral

Bir formu veya diğer nesneyi devralmanın en kolay yolu **Devralma Seçici** iletişim kutusunu kullanmaktır. Bununla birlikte, diğer çözümlerde zaten oluşturduğunuz koddan veya kullanıcı arabiriminden (UI) yararlanabilirsiniz.

> [!NOTE]
> **Devralma Seçicisi** iletişim kutusuyla bir formdan devralmak için, bu formu içeren proje yürütülebilir bir dosyaya veya dll 'ye derlenmiş olmalıdır. Projeyi derlemek için **derleme** menüsünden **çözüm oluştur** ' u seçin.

## <a name="create-a-windows-form-by-using-the-inheritance-picker"></a>Devralma seçiciyi kullanarak bir Windows formu oluşturma

1. Visual Studio 'da, **Proje** menüsünden **Windows formu Ekle**' yi seçin.

   **Yeni Öğe Ekle** iletişim kutusu açılır.

2. **Devralınan form** şablonunda, searchbox ' dan veya **Windows Forms** kategorisine tıklayarak bu öğeyi seçip **ad** kutusunda adlandırın. Devam etmek için **Ekle** düğmesine tıklayın.

   **Devralma Seçicisi** iletişim kutusu açılır. Geçerli proje zaten formlar içeriyorsa **Devralma Seçicisi** iletişim kutusunda görüntülenir.

3. Başka bir derlemedeki formdan devralması için, **Gözden** geçirme düğmesine tıklayın.

4. İçinden **devralacak bir bileşen içeren bir dosya seçin** iletişim kutusunda, istediğiniz formu veya modülü içeren projeye gidin.

5. Seçmek için. exe veya. dll dosyasının adına tıklayın ve **Aç** düğmesine tıklayın.

   Bu, sizi, bileşenin bulunduğu projenin yanı da listede yer alan **Devralma Seçici** iletişim kutusuna geri döndürür.

6. Bileşeni seçin.

   **Çözüm Gezgini**, bileşen projenize eklenir. Bir kullanıcı arabirimi varsa, devralınan formun parçası olan denetimler bir karakter (![Visual Basic devralma sembolünün ekran görüntüsü) ile işaretlenir ve seçildiğinde, denetimin üzerinde bulunduğu güvenlik düzeyini belirten bir kenarlığı vardır.](./media/how-to-inherit-forms-using-the-inheritance-picker-dialog-box/visual-basic-inheritance-glyph.gif) üst sınıflı form. Farklı güvenlik düzeylerine karşılık gelen davranışlar aşağıdaki tabloda listelenmiştir.

    |Denetim güvenlik düzeyi|Devralınan formla tasarımcı ve kod Düzenleyicisi aracılığıyla kullanılabilir etkileşim|
    |-------------------------------|--------------------------------------------------------------------------------|
    |Ortak|Boyutlandırma tutamaçlarıyla standart kenarlık: denetim boyutlandırılabilir ve taşınabilir. Denetime onu bildiren ve diğer sınıflar tarafından harici olarak erişilebilir.|
    |Korumalı|Boyutlandırma tutamaçlarıyla standart kenarlık: denetim boyutlandırılabilir ve taşınabilir. Kendisini bildiren sınıf tarafından ve üst sınıftan devralan herhangi bir sınıf tarafından dahili olarak erişilebilir, ancak harici sınıflar tarafından erişilemez.|
    |Korumalı Iç (Visual Basic korunan arkadaş)|Boyutlandırma tutamaçlarıyla standart kenarlık: denetim boyutlandırılabilir ve taşınabilir. Kendisini bildiren sınıf tarafından, üst sınıftan devralan herhangi bir sınıf tarafından ve onu içeren derlemenin diğer üyeleri tarafından dahili olarak erişilebilir.|
    |İç (Visual Basic arkadaş)|Formda gösterilen, Özellikler penceresinde görünen özellikler, boyutlandırma tutamacı olmayan standart kenarlık. Ancak, denetimin tüm yönleri salt okunurdur. Denetimi taşıyamaz veya boyutlandıramaz ya da özelliklerini değiştiremezsiniz. Denetim, bir grup kutusu gibi diğer denetimlerin bir kapsayıcısıdır, yeni denetimler eklenemez ve bu denetimler ortak olsa bile var olan denetimler kaldırılamaz. Denetime yalnızca kendisini içeren derlemenin diğer üyeleri erişebilir.|
    |Özel|Formda gösterilen, Özellikler penceresinde görünen özellikler, boyutlandırma tutamacı olmayan standart kenarlık. Ancak, denetimin tüm yönleri salt okunurdur. Denetimi taşıyamaz veya boyutlandıramaz ya da özelliklerini değiştiremezsiniz. Denetim, bir grup kutusu gibi diğer denetimlerin bir kapsayıcısıdır, yeni denetimler eklenemez ve bu denetimler ortak olsa bile var olan denetimler kaldırılamaz. Denetime yalnızca onu bildiren sınıf erişebilir.|

     Temel formun görünümünü değiştirme hakkında daha fazla bilgi için, bkz. [temel formun görünümünü değiştirme etkileri](effects-of-modifying-base-form-appearance.md).

    > [!NOTE]
    > Devralınan denetimleri ve bileşenleri, Windows Forms üzerinde standart denetimlerle ve bileşenlerle birleştirdiğinizde, z Sıralamalı çakışmalardan karşılaşabilirsiniz. Bu işlemi, **Biçim** menüsüne tıklayıp **sırasıyla sıra**' ya ve ardından **öne getir** veya **geri gönder**' e tıklayarak yapılacak z düzeninde değişiklik yaparak düzeltebilirsiniz. Denetimlerin z sıralaması hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms](../controls/how-to-layer-objects-on-windows-forms.md)katman nesneleri.

## <a name="see-also"></a>Ayrıca bkz.

- [Inherits Deyimi](~/docs/visual-basic/language-reference/statements/inherits-statement.md)
- [using](~/docs/csharp/language-reference/keywords/using.md)
- [Taban Formun Görünüşünü Değiştirmenin Etkileri](effects-of-modifying-base-form-appearance.md)
- [Windows Forms Görsel Devralma](windows-forms-visual-inheritance.md)
