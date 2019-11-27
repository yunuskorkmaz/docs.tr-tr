---
title: 'Nasıl yapılır: Değeri Değişmeyen Bir Değişken Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
ms.openlocfilehash: d5d8a6b066ae7e8795afd2f788b60823d8efdafa
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348640"
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a>Nasıl yapılır: Değeri Değişmeyen Bir Değişken Oluşturma (Visual Basic)

Değerini değiştirolmayan bir değişken kavramı, çelişkili gibi görünebilir. Ancak, bir sabit değer mümkün olmadığında ve sabit bir değere sahip bir değişken olması faydalı olduğunda durumlar vardır. Böyle bir durumda, [salt okunur](../../../../visual-basic/language-reference/modifiers/readonly.md) anahtar sözcüğüyle bir üye değişkeni tanımlayabilirsiniz.

[Const ifadesini](../../../../visual-basic/language-reference/statements/const-statement.md) aşağıdaki koşullarda bir sabit değer bildirmek ve atamak için kullanamazsınız:

- `Const` deyimin kullanmak istediğiniz veri türü kabul etmez

- Derleme zamanında değeri bilemezsiniz

- Derleme zamanında sabit değeri hesaplayamıyor

### <a name="to-create-a-variable-that-does-not-change-in-value"></a>Değerde değişiklik olmayan bir değişken oluşturmak için

1. Modül düzeyinde, [Dim ifadesiyle](../../../../visual-basic/language-reference/statements/dim-statement.md)bir üye değişkeni bildirin ve [salt okunur](../../../../visual-basic/language-reference/modifiers/readonly.md) anahtar sözcüğünü ekleyin.

    ```vb
    Dim ReadOnly timeStarted
    ```

    Yalnızca üye değişkeninde `ReadOnly` belirtebilirsiniz. Bu, herhangi bir yordamın dışında değişkeni modül düzeyinde tanımlamanız gereken anlamına gelir.

2. Derleme zamanında değeri tek bir ifadede hesapladıysanız, `Dim` deyimindeki bir başlatma yan tümcesi kullanın. [As](../../../../visual-basic/language-reference/statements/as-clause.md) yan tümcesini, eşittir işareti (`=`) ve ardından bir ifade ile izleyin. Derleyicinin bu ifadeyi sabit bir değere değerlendirebilmesi için emin olun.

    ```vb
    Dim ReadOnly timeStarted As Date = Now
    ```

    Bir `ReadOnly` değişkenine yalnızca bir kez değer atayabilirsiniz. Bunu yaptığınızda, herhangi bir kod hiçbir zaman değerini değiştiremez.

    Derleme zamanında değeri bilemezsiniz veya tek bir ifadede derleme zamanında hesapladıysanız, yine de bir oluşturucuda çalışma zamanında atayabilirsiniz. Bunu yapmak için, sınıf veya yapı düzeyinde `ReadOnly` değişkenini bildirmeniz gerekir. Bu sınıf veya yapı için oluşturucuda, değişkenin sabit değerini hesaplayın ve oluşturucuyu döndürmeden önce değişkenine atayın.

## <a name="see-also"></a>Ayrıca bkz.

- [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [Const Deyimi](../../../../visual-basic/language-reference/statements/const-statement.md)
