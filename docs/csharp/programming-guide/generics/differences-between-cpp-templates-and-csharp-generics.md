---
title: C++ şablonları arasındaki farklar ve C# genel türler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], vs. C++ templates
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
ms.openlocfilehash: 1bf3eb97d633322f6bd04f8e975ae3fc8ec54329
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651818"
---
# <a name="differences-between-c-templates-and-c-generics-c-programming-guide"></a>C++ Şablonları ve C# Genel Türleri Arasındaki Farklar (C# Programlama Kılavuzu)
C# genel türleri ve C++ şablonları parametreli türler için destek sağlayan her iki dil özellikleridir. Ancak, ikisi arasındaki pek çok fark vardır. Sözdizimi, C# genel türleri için C++ şablonlarının karmaşıklığı olmadan parametreli türler basit bir yaklaşım düzeyindedir. Ayrıca, C# tüm C++ şablonları sağlayan işlevselliği sağlamak denemez. Uygulama düzeyinde birincil çalışma zamanında C# genel tür değişimler gerçekleştirilir ve genel tür bilgileri, böylece örneklenen nesneleri korunur farktır. Daha fazla bilgi için [çalışma zamanı'nda genel türler](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).  
  
 C++ şablonları ile C# genel türleri arasındaki temel farklılıklar şunlardır:  
  
-   C# genel türleri aynı miktarda C++ şablonları olarak esneklik sağlamaz. Kullanıcı tanımlı işleçler çağrılabilir olsa gibi bir C# genel sınıfta, aritmetik işleçler çağırmak mümkün değildir.  
  
-   C# izin vermiyor tür olmayan şablon parametreleri gibi `template C<int i> {}`.  
  
-   C# açık özelleştirme desteklemez; diğer bir deyişle, özel uygulanışı belirli bir tür için bir şablon.  
  
-   C# kısmi özelleştirmede desteklemiyor: özel bir uygulama için bir alt tür bağımsız değişkenleri.  
  
-   C# genel tür için temel sınıf olarak kullanılacak tür parametresi izin vermez.  
  
-   C# varsayılan türler tür parametreleri izin vermez.  
  
-   Genel türler oluşturulan türler kullanılabilir olsa da C# ' ta genel tür parametresi kendisi bir genel olamaz. C++ şablon parametreleri izin vermez.  
  
-   C++ tür parametresi kullanılan belirli bir tür için denetlenir şablondaki tüm tür parametreleri için geçerli olmayabilir kod sağlar. C# kısıtlamalar karşılayan herhangi bir türde çalışır şekilde yazılacak bir sınıftaki kod gerektirir. Örneğin, c++'ta aritmetik işleçler kullanan bir işlev yazmak mümkündür `+` ve `-` tür parametresinin nesneler üzerinde hangi ilişkilendiren bir hata şablonu bir örneğinin bu desteği olmayan bir tür ile anında işleçler. C# bu izin vermiyor; izin verilen tek dil yapıları kısıtlamalardan çıkarılabildiği olanlardır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Genel Türlere Giriş](../../../csharp/programming-guide/generics/introduction-to-generics.md)
- [Şablonlar](/cpp/cpp/templates-cpp)
