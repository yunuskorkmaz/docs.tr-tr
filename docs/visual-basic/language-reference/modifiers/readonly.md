---
title: ReadOnly (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.ReadOnly
helpviewer_keywords:
- ReadOnly keyword [Visual Basic]
- variables [Visual Basic], read-only
- ReadOnly property
- properties [Visual Basic], read-only
- read-only variables
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9ca1d2e4eddb3b88073d6fcd46b0de5c627ba809
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="readonly-visual-basic"></a>ReadOnly (Visual Basic)
Bir değişkenin veya özelliğin okuma ancak yazılmadı belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="rules"></a>Kurallar  
  
-   **Bildirim bağlamı.** Kullanabileceğiniz `ReadOnly` yalnızca modülü düzeyinde. Bu bildirimi bağlamının anlamına gelir bir `ReadOnly` öğesi bir sınıf, yapı veya modülü olması ve kaynak dosyasını, ad alanı veya yordam olamaz.  
  
-   **Birleşik değiştirici.** Belirtemeyeceğiniz `ReadOnly` ile birlikte `Static` aynı bildirimi.  
  
-   **Bir değer atama.** Kod kullanan bir `ReadOnly` özellik değeri ayarlanamaz. Ancak temel alınan depolama erişimi kod atayabilir veya herhangi bir zamanda değeri değiştirin.  
  
     Bir değere atayabileceğiniz bir `ReadOnly` yalnızca bildiriminden veya bir sınıf veya yapı tanımlanmış oluşturucusunun değişken.  
  
## <a name="when-to-use-a-readonly-variable"></a>Bir salt okunur değişken kullanmak ne zaman  
 İçinde kullanamazsınız durumlar vardır bir [Const deyimi](../../../visual-basic/language-reference/statements/const-statement.md) bildirme ve sabit bir değer atayabilirsiniz. Örneğin, `Const` deyimi atamak istediğiniz veri türü kabul veya sabit bir ifade ile derleme zamanında değeri işlem mümkün olmayabilir. Hatta derleme zamanında değeri anlamayabilirsiniz. Bu durumlarda, kullanabileceğiniz bir `ReadOnly` değişkeni sabit bir değer tutun.  
  
> [!IMPORTANT]
>  Değişken olsa bile değişkenin veri türü bir dizi ya da bir sınıf örneği gibi bir başvuru türü ise üyeleri değiştirilebilir `ReadOnly`. Aşağıdaki örnek bunu göstermektedir.  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 Hazırlarken, dizi işaret için tarafından `characterArray()` ayrı tutma "x", "y" ve "z". Çünkü değişkeni `characterArray` olan `ReadOnly`; olan başlatıldıktan sonra değeri değiştirilemiyor, yeni bir dizi atayamazsınız. Ancak, bir veya daha fazla dizi üyeleri değerlerini değiştirebilirsiniz. Aşağıdaki yordam çağrısına `changeArrayElement`, tarafından diziyi işaret için `characterArray()` ayrı tutma "x", "M" ve "z".  
  
 Bunun bir yordam parametresini olacak şekilde bildirmek için benzer olduğunu unutmayın [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), yordamı çağıran bağımsız değişkenin kendisine değiştirmelerini ancak üyelerini değiştirmek izin verir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek tanımlayan bir `ReadOnly` özelliği bir çalışan üzerinde işe tarihi için. Bu özellik değerini dahili olarak sınıf deposu bir `Private` sınıfı içinde değişken ve yalnızca kod, bu değeri değiştirebilirsiniz. Ancak, özelliktir `Public`, ve sınıf erişebilmeniz için herhangi bir kod özelliği okuyabilirsiniz.  
  
 [!code-vb[VbVbalrKeywords#4](../../../visual-basic/language-reference/codesnippet/VisualBasic/readonly_1.vb)]  
  
 `ReadOnly` Değiştiricisi bu bağlamlarında kullanılabilir:  
  
 [Dim deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)  
 [Anahtar sözcükler](../../../visual-basic/language-reference/keywords/index.md)
