---
title: Checked anahtar sözcüğü C# -başvurusu
ms.date: 07/20/2015
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
ms.openlocfilehash: 5963bb85ef4b61c1dc478667fb0e2e5438f3e4ad
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713703"
---
# <a name="checked-c-reference"></a>checked (C# Başvurusu)

`checked` anahtar sözcüğü, tam sayı türü aritmetik işlemler ve dönüştürmeler için taşma denetimini açık bir şekilde etkinleştirmek üzere kullanılır.

Varsayılan olarak, ifade hedef türü aralığının dışında bir değer üretirse yalnızca sabit değerler içeren bir ifade bir derleyici hatasına neden olur. İfade bir veya daha fazla sabit olmayan değer içeriyorsa, derleyici taşmayı algılamaz. Aşağıdaki örnekte `i2` atanan ifadenin değerlendirilmesi, bir derleyici hatasına neden olmaz.

[!code-csharp[csrefKeywordsChecked#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#3)]

Varsayılan olarak, bu sabit olmayan ifadeler çalışma zamanında taşma için denetlenmez ve taşma özel durumları oluşturmaz. Önceki örnekte iki pozitif tamsayının toplamı olarak-2.147.483.639 görüntülenir.

Taşma denetlemesi derleyici seçenekleri, ortam yapılandırması veya `checked` anahtar sözcüğünün kullanımı ile etkinleştirilebilir. Aşağıdaki örneklerde, çalışma zamanında önceki Sum tarafından üretilen taşmayı algılamak için `checked` ifadesinin veya `checked` bloğunun nasıl kullanılacağı gösterilmektedir. Her iki örnek de bir taşma özel durumu yükseltir.

[!code-csharp[csrefKeywordsChecked#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#4)]

[İşaretlenmemiş](./unchecked.md) anahtar sözcük, taşma denetimini engellemek için kullanılabilir.

## <a name="example"></a>Örnek

Bu örnek, çalışma zamanında taşma denetimini etkinleştirmek için `checked` nasıl kullanacağınızı gösterir.

[!code-csharp[csrefKeywordsChecked#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#1)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](./index.md)
- [İşaretli ve İşaretsiz](./checked-and-unchecked.md)
- [unchecked](./unchecked.md)
