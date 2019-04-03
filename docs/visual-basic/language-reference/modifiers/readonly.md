---
title: ReadOnly (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ReadOnly
helpviewer_keywords:
- ReadOnly keyword [Visual Basic]
- variables [Visual Basic], read-only
- ReadOnly property
- properties [Visual Basic], read-only
- read-only variables
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
ms.openlocfilehash: 6e361cbe89f4c51f28199b008de817c2d48ef326
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825397"
---
# <a name="readonly-visual-basic"></a>ReadOnly (Visual Basic)
Bir değişken veya özellik okunabildiğini ancak yazılmazsa olduğunu belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="rules"></a>Kurallar  
  
-   **Bildirim bağlamı.** Kullanabileceğiniz `ReadOnly` yalnızca Modül düzeyinde. Bildirim bağlamı başka bir deyişle bir `ReadOnly` öğesi bir sınıf, yapı veya modül olmalıdır ve bir kaynak dosyası, ad alanı ya da yordamın olamaz.  
  
-   **Birleşik değiştiriciler.** Belirtemezsiniz `ReadOnly` ile birlikte `Static` aynı bildirimde.  
  
-   **Bir değer atama.** Kod kullanan bir `ReadOnly` özellik değeri ayarlayamaz. Ancak, temel alınan depolama erişimi olan kod atama veya herhangi bir zamanda değeri değiştirin.  
  
     Bir değer atamak için bir `ReadOnly` yalnızca bildiriminden veya bir sınıf veya yapı içinde tanımlanmış olduğu oluşturucusunun değişken.  
  
## <a name="when-to-use-a-readonly-variable"></a>Salt okunur değişken kullanma zamanı  
 Bazı durumlarda, kullanamazsınız bir [Const deyimi](../../../visual-basic/language-reference/statements/const-statement.md) bildirmek ve sabit bir değer atamak için. Örneğin, `Const` deyimi atamak istediğiniz veri türü kabul ya da sabit bir ifade ile derleme zamanında değeri hesaplamak mümkün olmayabilir. Hatta derleme zamanında değeri etmeyebilirsiniz. Bu durumlarda, kullandığınız bir `ReadOnly` sabit değerini tutacak bir değişken.  
  
> [!IMPORTANT]
>  Değişkenin veri türü bir dizi veya bir sınıf örneği gibi bir başvuru türü ise değişken olsa bile üyelerini değiştirilebilir `ReadOnly`. Aşağıdaki örnek bunu göstermektedir.  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 Hazırlarken, dizi tarafından işaret edilen `characterArray()` ayrı tutma "x", "y" ve "z". Çünkü değişken `characterArray` olduğu `ReadOnly`; olan başlatıldıktan sonra değerini değiştiremezsiniz, yeni bir dizi atanamaz. Ancak, bir veya daha fazla dizi üyeleri değerlerini değiştirebilirsiniz. Bir yordam çağrısından `changeArrayElement`, dizi tarafından işaret edilen `characterArray()` ayrı tutma "x", "M" ve "z".  
  
 Bir yordam parametre bildirmek için benzer olduğuna dikkat edin [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), hangi yordamı çağırma bağımsız değiştirmesini engeller ancak üyelerini değiştirmek sağlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte tanımlayan bir `ReadOnly` özelliği üzerinde bir çalışan işe tarih. Bu özellik değerini dahili olarak sınıf deposu bir `Private` sınıf içinde değişken ve yalnızca kod, bu değeri değiştirebilirsiniz. Ancak, özelliğidir `Public`, ve sınıfı erişebilen herhangi bir kod özelliği okuyabilirsiniz.  
  
 [!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]  
  
 `ReadOnly` Bu bağlamda değiştirici kullanılabilir:  
  
 [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)
- [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)
