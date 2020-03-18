---
title: İşaretçi Dönüşümleri - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 517166331d2bcf73132269ce2adcf68d5f60b4fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76745368"
---
# <a name="pointer-conversions-c-programming-guide"></a>İşaretçi Dönüşümleri (C# Programlama Kılavuzu)
Aşağıdaki tablo, önceden tanımlanmış örtük işaretçi dönüşümlerini gösterir. Örtülü dönüşümler, yöntem arama ve atama deyimleri de dahil olmak üzere birçok durumda oluşabilir.  
  
## <a name="implicit-pointer-conversions"></a>Örtük işaretçi dönüşümleri  
  
|Başlangıç|Alıcı|  
|----------|--------|  
|Herhangi bir işaretçi türü|geçersiz*|  
|null|Herhangi bir işaretçi türü|  
  
 Açık işaretçi dönüştürme, bir döküm ifadesi kullanılarak, örtülü dönüştürme bulunmayan dönüşümleri gerçekleştirmek için kullanılır. Aşağıdaki tabloda bu dönüşümler gösterilmektedir.  
  
## <a name="explicit-pointer-conversions"></a>Açık işaretçi dönüşümleri  
  
|Başlangıç|Alıcı|  
|----------|--------|  
|Herhangi bir işaretçi türü|Diğer işaretçi türü|  
|bayt, bayt, kısa, ushort, int, uint, uzun veya ulong|Herhangi bir işaretçi türü|  
|Herhangi bir işaretçi türü|bayt, bayt, kısa, ushort, int, uint, uzun veya ulong|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, işaretçi `int` için bir işaretçi `byte`için bir işaretçi dönüştürülür . İşaretçinin değişkenin en düşük adresli baytını işaret ettiğine dikkat edin. Sonucu art arda `int` ,(4 bayt) boyutuna kadar artımladiğinizde, değişkenin kalan baytlarını görüntüleyebilirsiniz.  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [İşaretçi türleri](pointer-types.md)
- [Başvuru türleri](../../language-reference/keywords/reference-types.md)
- [Değer türleri](../../language-reference/builtin-types/value-types.md)
- [Güvenli olmayan](../../language-reference/keywords/unsafe.md)
- [fixed Deyimi](../../language-reference/keywords/fixed-statement.md)
- [stackalloc](../../language-reference/operators/stackalloc.md)
