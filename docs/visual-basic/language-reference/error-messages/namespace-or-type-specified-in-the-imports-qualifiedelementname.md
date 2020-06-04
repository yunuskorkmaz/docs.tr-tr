---
title: Imports '<qualifiedelementname>' içinde belirtilen ad alanı veya tür ortak üye içermiyor veya bulunamıyor
ms.date: 07/20/2015
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
ms.openlocfilehash: 8675d9c3b202200c89e12e7a5f51a19d9e3e0e64
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409471"
---
# <a name="namespace-or-type-specified-in-the-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a>Imports '\<qualifiedelementname>' içinde belirtilen ad alanı veya tür ortak üye içermiyor veya bulunamıyor

Imports ' ' içinde belirtilen ad alanı veya tür \<qualifiedelementname> ortak üye içermiyor veya bulunamıyor. Ad alanının veya türün tanımlandığından ve en az bir ortak üye içerdiğinden emin olun. Diğer ad adının başka diğer adlar içermediğinden emin olun.

Bir `Imports` ifade, bulunamayan veya hiçbir üye tanımlamayan bir kapsayan öğe belirtiyor `Public` .

*Kapsayan bir öğe* bir Namespace, Class, Structure, Module, Interface veya Enumeration olabilir. Kapsayan öğe, değişkenler, yordamlar veya içerilen diğer öğeler gibi Üyeler içerir.

İçeri aktarma amacı, kodunuzun ad alanına veya tür üyelerine, bunları nitelemek zorunda kalmadan erişmesine izin versağlamaktır. Projenizin ad alanına veya türe bir başvuru eklemesi de gerekebilir. Daha fazla bilgi için, bkz. "Içerilen öğeleri Içeri aktarma", [belirtilen öğelerin başvuruları](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).

Derleyici belirtilen içeren öğeyi bulamazsa, onu kullanan başvuruları çözemez. Öğe bulunursa ancak öğe hiçbir üye sunmadığında `Public` , hiçbir başvuru başarılı olmaz. Her iki durumda da, öğesini içeri aktarmak anlamlı değildir.

İçeren bir öğeyi içeri aktarıp buna bir içeri aktarma diğer adı atarsanız, başka bir öğeyi almak için bu içeri aktarma diğer adını kullanamazsınız. Aşağıdaki kod bir derleyici hatası oluşturur.

```vb
Imports winfrm = System.Windows.Forms

' The following statement is INVALID  because it reuses an import alias.

Imports behave = winfrm.Design.Behavior`
```

**Hata kimliği:** BC40056

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. İçeren öğenin projenizden erişilebilir olduğunu doğrulayın.

2. İçerilen öğe belirtiminin başka bir içeri aktarma ile herhangi bir içeri aktarma diğer adı içermediğinden emin olun.

3. Kapsayan öğenin en az bir üye gösterdiğinden emin olun `Public` .

## <a name="see-also"></a>Ayrıca bkz.

- [Imports Deyimi (.NET Ad Alanı ve Türü)](../statements/imports-statement-net-namespace-and-type.md)
- [Namespace Deyimi](../statements/namespace-statement.md)
- [Geneldir](../modifiers/public.md)
- [Visual Basic'de Ad Alanları](../../programming-guide/program-structure/namespaces.md)
- [Bildirilmiş Öğelere Başvurular](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
