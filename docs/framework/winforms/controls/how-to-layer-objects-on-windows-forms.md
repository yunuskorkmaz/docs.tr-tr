---
title: 'Nasıl yapılır: Windows Forms’da Nesneleri Katmanlara Ayırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, layering
- controls [Windows Forms], layering
- z order
- controls [Windows Forms], positioning
- z-order
ms.assetid: 1acc4281-2976-4715-86f4-bda68134baaf
ms.openlocfilehash: 818f36633575b248d92da475c462cc0f211fe969
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966533"
---
# <a name="how-to-layer-objects-on-windows-forms"></a>Nasıl yapılır: Windows Forms’da Nesneleri Katmanlara Ayırma
Karmaşık bir kullanıcı arabirimi oluşturduğunuzda veya birden çok belge arabirimi (MDI) formuyla çalışıyorsanız, genellikle daha karmaşık kullanıcı arabirimleri (UI) oluşturmak için hem denetimleri hem de alt formları katman halinde katman yapmak isteyeceksiniz. Bir grup bağlamı içinde denetimleri ve pencereleri taşımak ve izlemek için z sırasını değiştirebilirsiniz. *Z düzeni* , formun Z ekseni (derinlik) üzerinde bir formdaki denetimlerin görsel katmandır. Z düzeninin en üstündeki pencere diğer tüm pencereler ile çakışıyor. Diğer tüm pencereler, z düzeninin alt kısmındaki pencereyle çakışıyor.

## <a name="to-layer-controls-at-design-time"></a>Tasarım zamanında katman denetimlerine

1. Katman yapmak istediğiniz bir denetim seçin.

2. **Biçim** menüsünde, **Düzen**' in üzerine gelin ve ardından **öne getir** veya **geri gönder**' e tıklayın.

## <a name="to-layer-controls-programmatically"></a>Denetimleri programlı olarak katman halinde

- Denetimlerin z düzenini <xref:System.Windows.Forms.Control.SendToBack%2A> değiştirmek için veyöntemlerinikullanın.<xref:System.Windows.Forms.Control.BringToFront%2A>

     Örneğin, bir <xref:System.Windows.Forms.TextBox> `txtFirstName`denetim başka bir denetimin altında ise ve en üstte olmasını istiyorsanız aşağıdaki kodu kullanın:

    ```vb
    txtFirstName.BringToFront()
    ```

    ```csharp
    txtFirstName.BringToFront();
    ```

    ```cpp
    txtFirstName->BringToFront();
    ```

> [!NOTE]
> Windows Forms *Denetim kapsamayı*destekler. Denetim kapsama, bir <xref:System.Windows.Forms.RadioButton> <xref:System.Windows.Forms.GroupBox> denetim içindeki denetim sayısı gibi, kapsayan bir denetim içinde çok sayıda denetim yerleştirmeyi içerir. Daha sonra, içeren denetim içindeki denetimleri katmandan yönetebilirsiniz. Grup kutusunun taşınması, içinde olduklarından, denetimleri de taşır.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms Denetimleri](index.md)
- [Windows Forms’da Denetimleri Düzenleme](arranging-controls-on-windows-forms.md)
- [Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Windows Forms'da Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
- [İşleve Göre Windows Forms Denetimleri](windows-forms-controls-by-function.md)
