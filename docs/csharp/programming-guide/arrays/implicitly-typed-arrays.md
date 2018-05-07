---
title: Türü Örtük Olarak Belirlenmiş Diziler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], implicity-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
ms.openlocfilehash: 60d320b233986154c3c51c409bade24d0862dedd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a>Türü Örtük Olarak Belirlenmiş Diziler (C# Programlama Kılavuzu)
Dizi Başlatıcı belirtilen öğelerden array örneğine tür çıkarımı yapılan örtük olarak yazılan dizisi oluşturabilirsiniz. Örtük olarak yazılan değişken kuralları örtük olarak yazılan diziler için de geçerlidir. Daha fazla bilgi için bkz: [örtük olarak yazılan yerel değişkenler](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
 Örtük olarak yazılan diziler, genellikle anonim türler ve nesne ve koleksiyon başlatıcıları birlikte sorgu ifadelerinde kullanılır.  
  
 Aşağıdaki örnekler örtük olarak yazılan dizi oluşturulacağını gösterir:  
  
 [!code-csharp[csProgGuideLINQ#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_1.cs)]  
  
 Önceki örnekte, başlatma ifadesinin sol tarafta hiçbir köşeli örtük olarak yazılan diziler ile kullanılan dikkat edin. Basit diziler kullanarak başlatılır ayrıca unutmayın `new []` tek boyutlu diziler'olduğu gibi.  
  
## <a name="implicitly-typed-arrays-in-object-initializers"></a>Nesne başlatıcıları içindeki örtük olarak yazılan diziler  
 Bir dizi içeren bir anonim türü oluşturduğunuzda, dizi tür nesne Başlatıcı örtülü olarak yazılan gerekir. Aşağıdaki örnekte, `contacts` her biri içeren adlı bir dizi örtük olarak yazılan anonim türler dizisidir `PhoneNumbers`. Unutmayın `var` anahtar sözcüğü içinde nesne başlatıcıları kullanılmaz.  
  
 [!code-csharp[csProgGuideLINQ#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_2.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Örtülü Olarak Yazılan Yerel Değişkenler](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)  
 [Diziler](../../../csharp/programming-guide/arrays/index.md)  
 [Anonim Tipler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [Nesne ve Koleksiyon Başlatıcıları](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [var](../../../csharp/language-reference/keywords/var.md)  
 [LINQ Sorgu ifadeleri](../../../csharp/programming-guide/linq-query-expressions/index.md)
