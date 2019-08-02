---
title: 'Nasıl yapılır: Değerde değişmez bir değişken Oluştur (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
ms.openlocfilehash: d201e95463dd0431825fee03ebfd340ac80cc552
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630889"
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a>Nasıl yapılır: Değerde değişmez bir değişken Oluştur (Visual Basic)

Değerini değiştirolmayan bir değişken kavramı, çelişkili gibi görünebilir. Ancak, bir sabit değer mümkün olmadığında ve sabit bir değere sahip bir değişken olması faydalı olduğunda durumlar vardır. Böyle bir durumda, [salt okunur](../../../../visual-basic/language-reference/modifiers/readonly.md) anahtar sözcüğüyle bir üye değişkeni tanımlayabilirsiniz.

[Const ifadesini](../../../../visual-basic/language-reference/statements/const-statement.md) aşağıdaki koşullarda bir sabit değer bildirmek ve atamak için kullanamazsınız:

- `Const` İfade, kullanmak istediğiniz veri türünü kabul etmiyor

- Derleme zamanında değeri bilemezsiniz

- Derleme zamanında sabit değeri hesaplayamıyor

### <a name="to-create-a-variable-that-does-not-change-in-value"></a>Değerde değişiklik olmayan bir değişken oluşturmak için

1. Modül düzeyinde, [Dim ifadesiyle](../../../../visual-basic/language-reference/statements/dim-statement.md)bir üye değişkeni bildirin ve [salt okunur](../../../../visual-basic/language-reference/modifiers/readonly.md) anahtar sözcüğünü ekleyin.

    ```vb
    Dim ReadOnly timeStarted
    ```

    Yalnızca bir üye `ReadOnly` değişkeninde belirtebilirsiniz. Bu, herhangi bir yordamın dışında değişkeni modül düzeyinde tanımlamanız gereken anlamına gelir.

2. Derleme zamanında değeri tek bir ifadede hesapladıysanız, `Dim` deyimindeki bir başlatma yan tümcesini kullanın. Eşittir işareti [](../../../../visual-basic/language-reference/statements/as-clause.md) (`=`) ve ardından bir ifade gelen as yan tümcesini izleyin. Derleyicinin bu ifadeyi sabit bir değere değerlendirebilmesi için emin olun.

    ```vb
    Dim ReadOnly timeStarted As Date = Now
    ```

    Bir `ReadOnly` değişkene yalnızca bir kez değer atayabilirsiniz. Bunu yaptığınızda, herhangi bir kod hiçbir zaman değerini değiştiremez.

    Derleme zamanında değeri bilemezsiniz veya tek bir ifadede derleme zamanında hesapladıysanız, yine de bir oluşturucuda çalışma zamanında atayabilirsiniz. Bunu yapmak için `ReadOnly` değişkeni sınıf veya yapı düzeyinde bildirmeniz gerekir. Bu sınıf veya yapı için oluşturucuda, değişkenin sabit değerini hesaplayın ve oluşturucuyu döndürmeden önce değişkenine atayın.

## <a name="see-also"></a>Ayrıca bkz.

- [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [Const Deyimi](../../../../visual-basic/language-reference/statements/const-statement.md)
