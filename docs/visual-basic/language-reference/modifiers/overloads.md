---
title: "Aşırı Yüklemeler (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Overloads
- Overloads
helpviewer_keywords:
- Overloads keyword [Visual Basic]
- hiding by signature
- Shadows keyword [Visual Basic]
- signature, hiding by
ms.assetid: 0c6820b8-25b2-4664-bc59-5ca93c99c042
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a23a6b91681cbd814ac96464e1c340be99a0ecf0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="overloads-visual-basic"></a>Aşırı Yüklemeler (Visual Basic)
Bir özellik veya yordam bir veya daha fazla var olan özellikleri ya da aynı ada sahip yordamlar redeclares belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 *Aşırı yükleme* aynı kapsamda belirli bir özellik veya yordam adı için birden fazla tanım sağladığını uygulamadır. Bir özellik veya farklı bir imzaya sahip yordamı redeclaring bazen çağrılır *imzaya göre gizleme*.  
  
## <a name="rules"></a>Kurallar  
  
-   **Bildirim bağlamı.** Kullanabileceğiniz `Overloads` yalnızca bir özellik veya yordam bildirimi deyimi içinde.  
  
-   **Birleşik değiştirici.** Belirtemeyeceğiniz `Overloads` ile birlikte [gölgeleri](../../../visual-basic/language-reference/modifiers/shadows.md) aynı yordamı bildirimi.  
  
-   **Farkları gereklidir.** *İmza* bu bildirimi her bir özellik veya onu overloads yordamı imzadan farklı olması gerekir. İmza birlikte aşağıdaki özellik veya yordam adı oluşur:  
  
    -   parametre sayısı  
  
    -   Parametreler sırası  
  
    -   parametre veri türleri  
  
    -   Tür parametreleri (için genel bir yordam) sayısı  
  
    -   dönüş türü (yalnızca bir dönüşüm işleci yordam için)  
  
     Tüm aşırı aynı ada sahip olmalıdır, ancak her tüm başkalarından gelen bir veya daha önceki gizliliğinize farklı olmalıdır. Bu kod özellik veya yordam çağırdığında kullanmak için hangi sürümün ayırt etmek derleyici sağlar.  
  
-   **İzin verilmeyen farklılıkları.** Aşağıdakilerden birini veya birkaçını değiştirme, imza parçası olmadıklarından bir özellik veya yordam aşırı yüklemesi için geçerli değil:  
  
    -   desteklemediğini (için bir yordam) bir değer döndürür  
  
    -   Dönüş değeri (dışında bir dönüşüm işleci) veri türü  
  
    -   Tür parametreleri parametre adları  
  
    -   (için genel bir yordam) tür parametrelerindeki kısıtlamalar  
  
    -   parametresi değiştiricisi anahtar sözcükler (gibi `ByRef` veya `Optional`)  
  
    -   özellik veya yordam değiştiricisi anahtar sözcükler (gibi `Public` veya `Shared`)  
  
-   **İsteğe bağlı değiştiricisi.** Kullanmak zorunda değil `Overloads` aynı sınıfta birden fazla aşırı yüklenmiş özellikler ya da yordamlar tanımlarken değiştiricisi. Ancak, kullanırsanız `Overloads` bildirimleri her birinde, bunların tümünde kullanmanız gerekir.  
  
-   **Gölgeleme ve aşırı yüklemesi.** `Overloads`Ayrıca gölge var olan bir üye ya da bir taban sınıf içinde aşırı yüklenmiş üyeler kümesi kullanılabilir. Kullandığınızda `Overloads` bu şekilde, özellik veya yöntem aynı adı ve temel sınıf üyesi ile aynı parametre listesine bildirme ve sağladığınız değil `Shadows` anahtar sözcüğü.  
  
 Kullanırsanız `Overrides`, derleyici örtük olarak ekler `Overloads` kitaplığınızın API'leri iş böylece C# ile daha kolay.  
  
 `Overloads` Değiştiricisi bu bağlamlarında kullanılabilir:  
  
 [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Operator deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gölgeleri](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Yordam aşırı yüklemesi](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)  
 [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [İşleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [Nasıl yapılır: bir dönüşüm işleci tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
