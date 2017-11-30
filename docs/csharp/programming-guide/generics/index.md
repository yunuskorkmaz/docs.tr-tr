---
title: "Genel Türler (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0804ca0fcefcc53e06352accf9a2db19edb31037
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
  
-   [Genel türlere giriş](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
  
-   [Genel türlerin yararları](../../../csharp/programming-guide/generics/benefits-of-generics.md)  
  
-   [Genel tür parametreleri](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
-   [Tür parametrelerindeki kısıtlamalar](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
-   [Genel sınıflar](../../../csharp/programming-guide/generics/generic-classes.md)  
  
-   [Genel arabirimler](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
-   [Genel yöntemler](../../../csharp/programming-guide/generics/generic-methods.md)  
  
-   [Genel temsilciler](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
-   [C++ şablonları ve C# genel türleri arasındaki farklar](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
-   [Genel türler ve yansıma](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
-   [Çalışma zamanındaki genel türler](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
-   [.NET Framework Sınıf Kitaplığı'nda genel türler](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 Daha fazla bilgi edinmek için, bkz. [C# Dil Belirtimi](../../../csharp/language-reference/language-specification/index.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.Generic>  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Türler](../../../csharp/programming-guide/types/index.md)  
 [\<typeparam >](../../../csharp/programming-guide/xmldoc/typeparam.md)  
 [\<typeparamref >](../../../csharp/programming-guide/xmldoc/typeparamref.md)
