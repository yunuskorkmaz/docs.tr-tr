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
ms.openlocfilehash: 0d8799359a12b9bb64331d83df2500bede8c0ff2
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59314550"
---
# <a name="how-to-inherit-windows-forms"></a>Nasıl yapılır: Windows Formlarını Devralma
Temel forms devralarak yeni Windows form oluşturmaya, ihtiyaç duyduğunuz her zaman bir form tamamen yeniden işlemine geçmeden çabalarınıza çoğaltmak için kullanışlı bir yoldur.  
  
 Formları kullanarak tasarım zaman devralma hakkında daha fazla bilgi için **devralma Seçici** iletişim kutusu ve görsel olarak güvenlik düzeyleri arasında ayrım yapmak nasıl devralınan denetimler için bkz: [nasıl yapılır: Devralma Seçici iletişim kutusunu kullanarak form devralma](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md).  
  
 **Not** bir formdan devralmak için dosya veya ad alanı, formu içeren bir yürütülebilir dosya veya DLL yerleştirilmiştir gerekir. Projeyi oluşturmak için Seç **derleme** gelen **derleme** menüsü. Ayrıca, formun devralan sınıf için bir ad alanına başvuru eklenmesi gerekir. Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-inherit-a-form-programmatically"></a>Bir form programlı olarak devralmak için  
  
1. Sınıfınızda, devralınan istediğiniz formu içeren ad alanı bir başvuru ekleyin.  
  
2. Sınıf tanımında devralmak için forma bir başvuru ekleyin. Başvuru formun taban form adını ardından bir nokta içeren ad alanı içermelidir.  
  
    ```vb  
    Public Class Form2  
        Inherits Namespace1.Form1  
    ```  
  
    ```csharp  
    public class Form2 : Namespace1.Form1  
    ```  
  
 Forms devralınırken her olay hem temel sınıfını hem de devralınan bir sınıf tarafından işlenmediğinden oluşabilecek sorunları iki kez çağrılan olay işleyicileri ile ilgili göz önünde bulundurun. Bu sorunu önlemek yapma hakkında daha fazla bilgi için bkz. [sorun giderme devralınmış olay işleyicileri Visual Basic'te](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Inherits Deyimi](~/docs/visual-basic/language-reference/statements/inherits-statement.md)
- [Imports Deyimi (.NET Ad Alanı ve Türü)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [kullanma](~/docs/csharp/language-reference/keywords/using.md)
- [Taban Formun Görünüşünü Değiştirmenin Etkileri](effects-of-modifying-base-form-appearance.md)
- [Windows Forms Görsel Devralma](windows-forms-visual-inheritance.md)
