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
ms.openlocfilehash: 8d0abbf0f71ac176d17261a0ae863938c575bdaf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59311670"
---
# <a name="how-to-layer-objects-on-windows-forms"></a>Nasıl yapılır: Windows Forms’da Nesneleri Katmanlara Ayırma
Karmaşık kullanıcı arabirimi oluşturmak veya birden çok belge arabirimi (MDI) formla çalışmak, genellikle denetimleri hem daha karmaşık kullanıcı arabirimleri (UI) oluşturmak için alt formları katman isteyeceksiniz. Taşıma ve denetimleri ve windows Grup bağlamında izlemek için z düzenini yönetmek. *Z düzenini* formun z ekseni (ayrıntılı) boyunca bir form üzerinde denetimleri visual katmanlarını olduğu. Pencerenin üst kısmında z düzenini, diğer tüm windows ile çakışıyor. Diğer tüm windows pencerenin alt kısmındaki z düzenini çakışıyor.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-layer-controls-at-design-time"></a>Tasarım zamanında katman denetimleri  
  
1. Katman istediğiniz denetimi seçin.  
  
2. Üzerinde **biçimi** menüsünde **sipariş**ve ardından **öne** veya **geri gönderme**.  
  
### <a name="to-layer-controls-programmatically"></a>Katman için programlı denetimler  
  
-   Kullanım <xref:System.Windows.Forms.Control.BringToFront%2A> ve <xref:System.Windows.Forms.Control.SendToBack%2A> denetimlerinin z düzenini yönetmek için yöntemleri.  
  
     Örneğin, bir <xref:System.Windows.Forms.TextBox> denetimi `txtFirstName`, olan altındaki başka bir denetim istiyorsanız üstte olması aşağıdaki kodu kullanın:  
  
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
>  Windows Forms destekler *denetim kapsama*. Denetim kapsamı içeren bir dizi gibi bir dizi içeren bir denetimi içindeki denetimler yerleştirme <xref:System.Windows.Forms.RadioButton> içinde denetleyen bir <xref:System.Windows.Forms.GroupBox> denetimi. Ardından, içeren denetimi içindeki denetimler katmanlayabilirsiniz. Grup kutusu taşıma, bunlar içinde yer aldığından, denetimleri de taşır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms Denetimleri](index.md)
- [Windows Forms’da Denetimleri Düzenleme](arranging-controls-on-windows-forms.md)
- [Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Windows Forms'da Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
- [İşleve Göre Windows Forms Denetimleri](windows-forms-controls-by-function.md)
