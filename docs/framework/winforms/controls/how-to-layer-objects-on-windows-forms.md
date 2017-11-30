---
title: "Nasıl yapılır: Windows Formlarında Nesneleri Katmanlara Ayırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bda4cb3641ff890646614af35d38ff13621cc16b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-layer-objects-on-windows-forms"></a>Nasıl yapılır: Windows Formlarında Nesneleri Katmanlara Ayırma
Karmaşık kullanıcı arabirimi oluşturma ya da birden çok belge arabirimi (MDI) formla çalışmak genellikle denetimleri ve daha karmaşık kullanıcı arabirimi (UI) oluşturmak için alt formları katman isteyeceksiniz. Taşıma ve denetimleri ve windows Grup bağlamında izlemek için bunların z düzenini yönetme. *Z düzeni* formun z ekseni (derinlik) boyunca bir form üzerinde denetimleri görsel katmanlarını değil. Pencerenin üst kısmındaki z düzenini diğer tüm windows çakışıyor. Diğer tüm windows pencerenin alt kısmındaki z düzenini çakışıyor.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-layer-controls-at-design-time"></a>Tasarım zamanında katman denetimleri için  
  
1.  Katman istediğiniz bir denetim seçin.  
  
2.  Üzerinde **biçimi** menüsündeki **sipariş**ve ardından **öne** veya **geri göndermek**.  
  
### <a name="to-layer-controls-programmatically"></a>Katman için program aracılığıyla denetler  
  
-   Kullanım <xref:System.Windows.Forms.Control.BringToFront%2A> ve <xref:System.Windows.Forms.Control.SendToBack%2A> denetimlerinin z sıralamasını değiştirmek için yöntemleri.  
  
     Örneğin, bir <xref:System.Windows.Forms.TextBox> denetimi `txtFirstName`, olan altındaki başka bir denetim ve istediğinizde üstte yoksa, aşağıdaki kodu kullanın:  
  
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
>  Windows Forms destekleyen *kontrol kapsama*. Denetimi kapsamasını içeren bir dizi bir dizi gibi içeren bir denetim içinde denetimleri yerleştirme <xref:System.Windows.Forms.RadioButton> içinde denetleyen bir <xref:System.Windows.Forms.GroupBox> denetim. Ardından içeren denetim içindeki denetimler katman. İçinde bulunan olduğundan grup kutusu taşıma denetimleri de taşır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms denetimleri](../../../../docs/framework/winforms/controls/index.md)  
 [Windows Forms'ta denetimleri düzenleme](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Ayrı Windows Forms denetimlerini etiketleme ve kısayollarını sunma](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Windows Forms'ta kullanılacak denetimler](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Windows Forms denetimleri işlevi](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
