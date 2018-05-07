---
title: 'Nasıl yapılır: Windows Formlarını Devralma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inherited forms [Windows Forms], creating at run-time
- inheritance [Windows Forms], forms
- Windows Forms, inheritance
ms.assetid: cb3e1c0f-3d2a-4cdc-b0d1-c92eae567ffb
ms.openlocfilehash: ce938d922560c96b5ce3c76756d409af5858492d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-inherit-windows-forms"></a>Nasıl yapılır: Windows Formlarını Devralma
Temel formlardan devralarak yeni Windows Forms oluşturma en iyi çabalarınız bunu gerektiren her zaman bir form tamamen yeniden sürecinde geçmeden çoğaltmak için kullanışlı bir yoludur.  
  
 Tasarım zamanı kullanarak form devralma hakkında daha fazla bilgi için **devralma Seçici** iletişim kutusu ve görsel olarak güvenlik düzeyleri arasında ayrım yapma devralınan denetimleri için bkz: [nasıl yapılır: formları kullanarak devral Devralma Seçici iletişim kutusu](../../../../docs/framework/winforms/advanced/how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md).  
  
 **Not** bir formdan devralmak için dosya veya ad alanı, formu içeren bir yürütülebilir dosya veya DLL'e oluşturulmuş olmalıdır. Projeyi oluşturmak için tercih **yapı** gelen **yapı** menüsü. Ayrıca, ad alanı referansı formun devralma sınıfı eklenmesi gerekir. Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-inherit-a-form-programmatically"></a>Bir form program aracılığıyla devralmak için  
  
1.  Sınıfınızda, devralınan istediğiniz formu içeren ad alanı için bir başvuru ekleyin.  
  
2.  Sınıf tanımında form devralmak için bir başvuru ekleyin. Başvuru noktayla, ardından taban formun adını ve ardından formu içeren ad alanı içermesi gerekir.  
  
    ```vb  
    Public Class Form2  
        Inherits Namespace1.Form1  
    ```  
  
    ```csharp  
    public class Form2 : Namespace1.Form1  
    ```  
  
 Forms devralırken her olay hem temel sınıfını hem de devralınan sınıfı tarafından işlenmediğinden oluşabilecek sorunları, iki kez çağrılan olay işleyicileri açısından göz önünde bulundurun. Bu sorunu önlemek nasıl daha fazla bilgi için bkz: [sorun giderme devralınmış olay işleyicileri Visual Basic'te](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Inherits Deyimi](~/docs/visual-basic/language-reference/statements/inherits-statement.md)  
 [Imports Deyimi (.NET Ad Alanı ve Türü)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [using](~/docs/csharp/language-reference/keywords/using.md)  
 [Taban Formun Görünüşünü Değiştirmenin Etkileri](../../../../docs/framework/winforms/advanced/effects-of-modifying-base-form-appearance.md)  
 [Windows Forms Görsel Devralma](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)
