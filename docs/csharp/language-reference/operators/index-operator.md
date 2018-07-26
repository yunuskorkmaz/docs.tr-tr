---
title: '[] İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '[]_CSharpKeyword'
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
ms.openlocfilehash: 65908bb3bcd8912ef81fc094e5958ae8dc4ae1f1
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37961451"
---
# <a name="-operator-c-reference"></a>[] İşleci (C# Başvurusu)
Köşeli ayraçlar (`[]`) diziler, dizin oluşturucular ve öznitelikleri için kullanılır. İşaretçiler ile de kullanılabilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir dizi türü arkasından bir türdür `[]`:  
  
 [!code-csharp[csRefOperators#43](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_1.cs)]  
  
 Bir dizinin bir öğesine erişmek için istenen öğenin dizini ayraç içine alınır:  
  
 [!code-csharp[csRefOperators#44](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_2.cs)]  
  
 Bir dizi dizini aralık dışında ise bir özel durum oluşturulur.  
  
 Dizin oluşturma işleci dizi aşırı yüklenemez; Ancak, türleri, dizin oluşturucular ve bir veya daha fazla parametre özellikleri tanımlayabilirsiniz. Dizin Oluşturucu parametresi dizi dizinleri gibi köşeli ayraçlar içine alınan ancak dizin oluşturucu parametresi tamsayı dizisi dizinler, aksine herhangi bir türde olması için bildirilebilir.  
  
 Örneğin, .NET Framework tanımlayan bir `Hashtable` anahtarları ve değerleri rastgele tür ilişkilendirir türü:  
  
 [!code-csharp[csRefOperators#45](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_3.cs)]  
  
 Köşeli ayraçlar belirtmek için de kullanılır [öznitelikleri](../../../csharp/programming-guide/concepts/attributes/index.md):  
  
 [!code-csharp[csRefOperators#46](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_4.cs)]  
  
 Bir işaretçi dizinlemek için köşeli ayraçlar kullanabilirsiniz:  
  
 [!code-csharp[csRefOperators#47](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_5.cs)]  
  
 Sınır denetimi gerçekleştirilir.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# İşleçleri](../../../csharp/language-reference/operators/index.md)  
 [Diziler](../../../csharp/programming-guide/arrays/index.md)  
 [Dizin Oluşturucular](../../../csharp/programming-guide/indexers/index.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed Deyimi](../../../csharp/language-reference/keywords/fixed-statement.md)
