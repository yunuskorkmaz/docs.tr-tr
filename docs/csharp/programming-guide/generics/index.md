---
title: Genel Türler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: 8f412366072c81b8aaca94829e0aa214f356200d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="generics-c-programming-guide"></a>Genel Türler (C# Programlama Kılavuzu)
Genel türler 2.0 C# dili ve ortak dil çalışma zamanı (CLR) sürümüne eklenmiştir. Genel türler için .NET Framework tasarım sınıflar ve sınıf veya yöntemin bildirilen ve istemci kodu tarafından örneği kadar bir veya daha fazla türü belirtimini erteleneceği yöntemler için olası kolaylaştırır tür parametreleri kavramı tanıtır. Örneğin, bir genel tür parametresi T kullanarak kullanabileceğiniz diğer istemci kodu maliyet ya da çalışma zamanı atamaları veya kutulama işlemleri riskini yansıtılmasını olmadan aşağıda gösterildiği gibi tek bir sınıf yazabilirsiniz:  
  
 [!code-csharp[csProgGuideGenerics#1](../../../csharp/programming-guide/generics/codesnippet/CSharp/index_1.cs)]  
  
## <a name="generics-overview"></a>Genel türler genel bakış  
  
-   Kodu yeniden kullanma, tür güvenliği ve performansı en üst düzeye çıkarmak için genel türler kullanın.  
  
-   En yaygın genel türler koleksiyon sınıfları oluşturmak için kullanılır.  
  
-   .NET Framework sınıf kitaplığı birkaç yeni genel koleksiyon sınıflarda içeren <xref:System.Collections.Generic> ad alanı. Olası yerine gibi sınıflar her durumda bunları kullanılmalıdır <xref:System.Collections.ArrayList> içinde <xref:System.Collections> ad alanı.  
  
-   Sınıfları, yöntemleri, olaylar ve temsilciler kendi genel arabirimler oluşturabilirsiniz.  
  
-   Genel sınıflar, belirli veri türlerini yöntemlere erişimi etkinleştirmek için kısıtlanmış.  
  
-   Yansıma kullanarak çalışma zamanında bir genel veri türünde kullanılan türleri hakkında bilgi alınabilir.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Daha fazla bilgi için:  
  
-   [Genel Türlere Giriş](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
  
-   [Genel Türlerin Yararları](../../../csharp/programming-guide/generics/benefits-of-generics.md)  
  
-   [Genel Tür Parametreleri](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
-   [Tür Parametrelerindeki Kısıtlamalar](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
-   [Genel Sınıflar](../../../csharp/programming-guide/generics/generic-classes.md)  
  
-   [Genel Arabirimler](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
-   [Genel Yöntemler](../../../csharp/programming-guide/generics/generic-methods.md)  
  
-   [Genel Temsilciler](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
-   [C++ Şablonları ve C# Genel Türleri Arasındaki Farklar](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
-   [Genel Türler ve Yansıma](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
-   [Çalışma Zamanındaki Genel Türler](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 Daha fazla bilgi edinmek için, bkz. [C# Dil Belirtimi](../../../csharp/language-reference/language-specification/index.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.Generic>  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Türler](../../../csharp/programming-guide/types/index.md)  
 [\<typeparam >](../../../csharp/programming-guide/xmldoc/typeparam.md)  
 [\<typeparamref >](../../../csharp/programming-guide/xmldoc/typeparamref.md)  
 [.NET'nda genel türler](../../../standard/generics/index.md)  