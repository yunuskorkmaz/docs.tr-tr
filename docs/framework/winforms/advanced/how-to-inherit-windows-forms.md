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
ms.openlocfilehash: 402386e16687162e25e16e5c30c787f7e721fbba
ms.sourcegitcommit: 1e72e2990220b3635cebc39586828af9deb72d8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2019
ms.locfileid: "71306370"
---
# <a name="how-to-inherit-windows-forms"></a>Nasıl yapılır: Windows Formlarını Devralma

Temel formlardan devralarak yeni Windows Forms oluşturmak, her ihtiyacınız olduğunda bir formu tamamen yeniden oluşturma işlemini gerçekleştirmeden en iyi çabalarınızı yinelemek için kullanışlı bir yoldur.

**Devralma Seçici** iletişim kutusunu kullanarak formları tasarım zamanında devralma ve devralınan denetimlerin güvenlik düzeyleri arasında görsel açıdan ayrım yapma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Devralma Seçici Iletişim kutusunu](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md)kullanarak formları devral.

> [!NOTE]
> Formdan devralması için, bu formu içeren dosya veya ad alanı yürütülebilir bir dosyaya veya DLL 'ye derlenmiş olmalıdır. Projeyi derlemek için **derleme** menüsünden **Oluştur** ' u seçin. Ayrıca, form devralan sınıfa ad alanı başvurusu eklenmelidir.

## <a name="inherit-a-form-programmatically"></a>Formu programlı bir şekilde devralma

1. Sınıfınıza, devralması istediğiniz formu içeren ad alanına bir başvuru ekleyin.

2. Sınıf tanımı ' nda, formunu devralacak bir başvuru ekleyin. Başvuru, formu içeren ad alanını, ardından bir nokta ve ardından temel formun adını içermelidir.

    ```vb
    Public Class Form2
        Inherits Namespace1.Form1
    ```

    ```csharp
    public class Form2 : Namespace1.Form1
    ```

 Formları devralırken, her olay hem temel sınıf hem de devralınan sınıf tarafından işlendiği için, iki kez çağrılan olay işleyicileriyle ilgili sorunların olabileceğini aklınızda bulundurun. Bu sorundan kaçınmak hakkında daha fazla bilgi için bkz. [Visual Basic devralınan olay Işleyicilerinin sorunlarını giderme](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Inherits Deyimi](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Imports Deyimi (.NET Ad Alanı ve Türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [using](../../../csharp/language-reference/keywords/using.md)
- [Taban Formun Görünüşünü Değiştirmenin Etkileri](effects-of-modifying-base-form-appearance.md)
- [Windows Forms Görsel Devralma](windows-forms-visual-inheritance.md)
