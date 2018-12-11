---
title: typeof (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- typeof
- typeof_CSharpKeyword
helpviewer_keywords:
- typeof keyword [C#]
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
ms.openlocfilehash: 039294d17d25d1d8775e7f92f46f5f57f2ac3212
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53146686"
---
# <a name="typeof-c-reference"></a>typeof (C# Başvurusu)

Elde etmek için kullanılan `System.Type` nesne türü. A `typeof` ifade aşağıdaki biçimleri alır:

```csharp
System.Type type = typeof(int);
```

## <a name="remarks"></a>Açıklamalar

Bir ifadenin çalışma zamanı türü elde etmek için .NET Framework yöntemi kullanabilirsiniz <xref:System.Object.GetType%2A>, aşağıdaki örnekte olduğu gibi:

```csharp
int i = 0;
System.Type type = i.GetType();
```

`typeof` İşleci aşırı yüklenemez.

`typeof` İşleci açık genel türler üzerinde de kullanılabilir. Birden fazla tür parametresi ile türleri belirtiminde virgül uygun sayıda olmalıdır. Aşağıdaki örnek, bir yöntemin dönüş türü genel olup olmadığını belirlemek gösterilmektedir <xref:System.Collections.Generic.IEnumerable%601>. <xref:System.Type.GetInterface%2A?displayProperty=nameWithType> döndüreceği `null` dönüş türü değilse bir <xref:System.Collections.Generic.IEnumerable%601> genel tür.

[!code-csharp[typeof_3.cs](~/samples/snippets/csharp/keywords/typeof/typeof_3.cs)]

## <a name="example"></a>Örnek

[!code-csharp[csrefKeywordsOperator#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#12)] 

## <a name="example"></a>Örnek

Bu örnekte <xref:System.Object.GetType%2A> sayısal hesaplama sonucu kapsamak için kullanılmış türünü belirlemek için yöntemi. Bu, sonuçta elde edilen sayı depolama gereksinimlerine bağlıdır.

[!code-csharp[csrefKeywordsOperator#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#13)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [typeof işleci](~/_csharplang/spec/expressions.md#the-typeof-operator) içinde [ C# dil belirtimi](../language-specification/index.md). Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Type?displayProperty=nameWithType>
- [C# başvurusu](../../../csharp/language-reference/index.md)
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)
- [is](../../../csharp/language-reference/keywords/is.md)
- [İşleç Anahtar Sözcükleri](../../../csharp/language-reference/keywords/operator-keywords.md)