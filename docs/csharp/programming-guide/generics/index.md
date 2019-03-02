---
title: 'Genel türler - C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
  - 'C# language, generics'
  - 'generics [C#]'
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
---
# <a name="generics-c-programming-guide"></a>Genel Türler (C# Programlama Kılavuzu)
Genel türler, C# dili ve ortak dil çalışma zamanı (CLR) 2.0 sürümüne eklenmiştir. Genel türler için .NET Framework tasarım sınıfları ve sınıf ya da yöntem bildirildi ve istemci kodu sayesinde örneği kadar bir veya daha fazla tür belirtimi erteleme yöntemlere mümkün hale tür parametrelerinin kavramı tanıtır. Örneğin, bir genel tür parametre T kullanarak diğer istemci kodu çalışma zamanı atamaları veya kutulama işlemleri riskini ve maliyet olmaksızın burada gösterildiği gibi kullanabileceğiniz tek bir sınıf yazabilirsiniz:  
  
 [!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]  
  
## <a name="generics-overview"></a>Genel türlere genel bakış  
  
-   Genel türler, kod yeniden kullanımını, tür güvenliği ve performansı en üst düzeye çıkarmak için kullanın.  
  
-   Genel türlerin yararları en yaygın kullanımı, koleksiyon sınıfları oluşturmaktır.  
  
-   .NET Framework sınıf kitaplığı çeşitli yeni genel koleksiyon sınıflarını içeren <xref:System.Collections.Generic> ad alanı. Olası yerine gibi sınıfların her durumda bu kullanılmalıdır <xref:System.Collections.ArrayList> içinde <xref:System.Collections> ad alanı.  
  
-   Kendi genel arabirimler, sınıflar, yöntemler, olaylar ve temsilciler oluşturabilirsiniz.  
  
-   Genel sınıflar, yöntemler belirli veri türlerinde erişimi etkinleştirmek için kısıtlı olabilir.  
  
-   Genel veri türü kullanılan türleri hakkında bilgi çalışma zamanında yansıma kullanarak elde edilebilir.  
  
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
 Daha fazla bilgi edinmek için, bkz. [C# Dil Belirtimi](~/_csharplang/spec/types.md#constructed-types).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Türler](../../../csharp/programming-guide/types/index.md)
- [\<typeparam >](../../../csharp/programming-guide/xmldoc/typeparam.md)
- [\<typeparamref >](../../../csharp/programming-guide/xmldoc/typeparamref.md)
- [.NET içindeki genel türler](../../../standard/generics/index.md)
