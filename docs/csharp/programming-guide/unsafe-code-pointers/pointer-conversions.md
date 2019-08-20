---
title: İşaretçi dönüştürmeleri- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 81b2110e6a571e174693fd272d1c6b4bf44dbae3
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588223"
---
# <a name="pointer-conversions-c-programming-guide"></a>İşaretçi Dönüşümleri (C# Programlama Kılavuzu)
Aşağıdaki tabloda önceden tanımlanmış örtük işaretçi dönüşümleri gösterilmektedir. Örtük dönüştürmeler, yöntem çağırma ve atama deyimleri dahil olmak üzere birçok durumda gerçekleşebilir.  
  
## <a name="implicit-pointer-conversions"></a>Örtük işaretçi dönüşümleri  
  
|Başlangıç|Bitiş|  
|----------|--------|  
|Herhangi bir işaretçi türü|Kağıt|  
|null|Herhangi bir işaretçi türü|  
  
 Açık işaretçi dönüştürmesi, bir atama ifadesi kullanarak örtük dönüştürme olmayan dönüştürmeler gerçekleştirmek için kullanılır. Aşağıdaki tabloda bu dönüşümler gösterilmektedir.  
  
## <a name="explicit-pointer-conversions"></a>Açık işaretçi dönüşümleri  
  
|Başlangıç|Bitiş|  
|----------|--------|  
|Herhangi bir işaretçi türü|Diğer herhangi bir işaretçi türü|  
|SByte, Byte, Short, ushort, int, uint, Long veya ulong|Herhangi bir işaretçi türü|  
|Herhangi bir işaretçi türü|SByte, Byte, Short, ushort, int, uint, Long veya ulong|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, için bir işaretçisi `int` `byte`işaretçisine dönüştürülür. İşaretçinin, değişkenin en düşük adresli baytını işaret ettiğini unutmayın. Sonucu büyük ölçüde arttırdığınızda `int` (4 bayt), değişkenin kalan baytlarını görüntüleyebilirsiniz.  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [İşaretçi türleri](./pointer-types.md)
- [Türler](../../language-reference/keywords/types.md)
- [unsafe](../../language-reference/keywords/unsafe.md)
- [fixed Deyimi](../../language-reference/keywords/fixed-statement.md)
- [stackalloc](../../language-reference/operators/stackalloc.md)
