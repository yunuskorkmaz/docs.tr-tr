---
title: 'Nasıl yapılır: Bileşik Denetimler Yazma'
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], creating composite controls
- user controls [Windows Forms], creating
- user controls [Windows Forms], inheriting from
- composite controls [Windows Forms], creating
ms.assetid: 79c9cf05-5ab6-4a18-886d-88a64748b098
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 08cb07ceebf08b3096415f9b7370e2d955152cb6
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015928"
---
# <a name="how-to-author-composite-controls"></a>Nasıl yapılır: Bileşik denetimleri yaz

Bileşik denetimler birçok şekilde çalıştırılabilir. Bunları bir Windows masaüstü uygulaması projesinin parçası olarak yazabilir ve yalnızca projedeki formlarda kullanabilirsiniz. Ya da bunları bir Windows denetim kitaplığı projesinde yazabilir, projeyi bir derlemede derleyebilir ve diğer projelerdeki denetimleri kullanabilirsiniz. Hatta onlardan devralabilir ve Görsel devralmayı kullanarak özel amaçlar için bunları hızlıca özelleştirebilirsiniz.

## <a name="to-author-a-composite-control"></a>Bileşik denetim yazmak için

1. Visual Studio 'da yeni bir **Windows uygulaması** projesi oluşturun ve bunu **DemoControlHost**olarak adlandırın.

2. **Proje** menüsünde **Kullanıcı denetimi Ekle**' ye tıklayın.

3. **Yeni öğe Ekle** iletişim kutusunda, bileşik denetimin sahip olmasını istediğiniz adı sınıf dosyasına (. vb veya. cs dosyası) verin.

4. Bileşik denetimin sınıf dosyasını oluşturmak için **Ekle** düğmesini seçin.

5. **Araç kutusundan** bileşik denetim yüzeyine denetimler ekleyin.

6. Bileşik denetim veya bileşen denetimleri tarafından oluşturulan olayları işlemek için olay yordamlarına kod koyun.

7. Bileşik denetim için tasarımcıyı kapatın ve istendiğinde dosyayı kaydedin.

8. Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.

     Özel denetimlerin **araç kutusunda**görünmesi için projenin oluşturulması gerekir.

9. Denetiminizin örneklerini öğesine `Form1`eklemek Için **araç kutusunun** **DemoControlHost** sekmesini kullanın.

## <a name="to-author-a-control-class-library"></a>Bir denetim sınıfı kitaplığı yazmak için

1. Yeni bir **Windows Denetim Kitaplığı** projesi açın.

     Varsayılan olarak, proje bir bileşik denetim içerir.

2. Yukarıdaki yordamda açıklandığı gibi denetimleri ve kodu ekleyin.

3. Sınıfların değiştirilmesini istemediğiniz bir denetim seçin ve bu denetimin **değiştiriciler** özelliğini **özel**olarak ayarlayın.

4. DLL 'yi oluşturun.

## <a name="to-inherit-from-a-composite-control-in-a-control-class-library"></a>Bir denetim sınıfı kitaplığındaki bileşik denetimden devralması için

1. Çözüme yeni bir **Windows uygulaması** projesi eklemek için **Dosya** menüsünde, **Ekle** ' ye gelin ve **Yeni proje** ' yi seçin.

2. **Çözüm Gezgini**' de, yeni proje için **Başvurular** klasörüne sağ tıklayın ve başvuru Ekle Iletişim kutusunu açmak için **Başvuru Ekle** ' yi seçin.

3. **Projeler** sekmesini seçin ve denetim kitaplığı projenize çift tıklayın.

4. Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.

5. **Çözüm Gezgini**, denetim kitaplığı projenize sağ tıklayıp kısayol menüsünden **Yeni öğe Ekle** ' yi seçin.

6. **Yeni öğe Ekle** Iletişim kutusundan **devralınan Kullanıcı denetimi** şablonunu seçin.

7. **Devralma Seçicisi** iletişim kutusunda, devralmak istediğiniz denetime çift tıklayın.

     Projenize yeni bir denetim eklenir.

8. Yeni denetim için görsel tasarımcıyı açın ve ek bileşen denetimleri ekleyin.

     DLL 'inizdeki bileşik denetimden devralınan yapısal denetimleri görebilir ve **değiştiriciler** özelliği **ortak**olan denetimlerin özelliklerini değiştirebilirsiniz. **Değiştiriciler** özelliği **özel**olan denetimin özelliklerini değiştiremezsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: Bileşik denetim yazma](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [İzlenecek yol: Windows Forms denetiminden devralma](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
- [Denetim Türü Önerileri](control-type-recommendations.md)
- [Nasıl yapılır: Windows Forms için yazar denetimleri](how-to-author-controls-for-windows-forms.md)
- [Özel Denetim Çeşitleri](varieties-of-custom-controls.md)
