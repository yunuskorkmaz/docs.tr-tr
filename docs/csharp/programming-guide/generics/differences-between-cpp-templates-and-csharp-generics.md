---
title: C++ şablonları arasındaki farklar ve C# genel türler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], vs. C++ templates
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
ms.openlocfilehash: 8151d426d1f0d3da5a5ce5fe795635348efd9696
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423529"
---
# <a name="differences-between-c-templates-and-c-generics-c-programming-guide"></a>C++ Şablonları ve C# Genel Türleri Arasındaki Farklar (C# Programlama Kılavuzu)
C# genel türleri ve C++ şablonları parametreli türler için destek sağlayan her iki dil özellikleridir. Ancak, ikisi arasındaki pek çok fark vardır. Sözdizimi, C# genel türleri için C++ şablonlarının karmaşıklığı olmadan parametreli türler basit bir yaklaşım düzeyindedir. Ayrıca, C# tüm C++ şablonları sağlayan işlevselliği sağlamak denemez. Uygulama düzeyinde birincil çalışma zamanında C# genel tür değişimler gerçekleştirilir ve genel tür bilgileri, böylece örneklenen nesneleri korunur farktır. Daha fazla bilgi için [çalışma zamanı'nda genel türler](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).  
  
 C++ şablonları ile C# genel türleri arasındaki temel farklılıklar şunlardır:  
  
- C# genel türleri aynı miktarda C++ şablonları olarak esneklik sağlamaz. Kullanıcı tanımlı işleçler çağrılabilir olsa gibi bir C# genel sınıfta, aritmetik işleçler çağırmak mümkün değildir.  
  
- C# izin vermiyor tür olmayan şablon parametreleri gibi `template C<int i> {}`.  
  
- C# açık özelleştirme desteklemez; diğer bir deyişle, özel uygulanışı belirli bir tür için bir şablon.  
  
- C# kısmi özelleştirmede desteklemiyor: özel bir uygulama için bir alt tür bağımsız değişkenleri.  
  
- C# genel tür için temel sınıf olarak kullanılacak tür parametresi izin vermez.  
  
- C# varsayılan türler tür parametreleri izin vermez.  
  
- Genel türler oluşturulan türler kullanılabilir olsa da C# ' ta genel tür parametresi kendisi bir genel olamaz. C++ şablon parametreleri izin vermez.  
  
- C++ tür parametresi kullanılan belirli bir tür için denetlenir şablondaki tüm tür parametreleri için geçerli olmayabilir kod sağlar. C# kısıtlamalar karşılayan herhangi bir türde çalışır şekilde yazılacak bir sınıftaki kod gerektirir. Örneğin, c++'ta aritmetik işleçler kullanan bir işlev yazmak mümkündür `+` ve `-` tür parametresinin nesneler üzerinde hangi ilişkilendiren bir hata şablonu bir örneğinin bu desteği olmayan bir tür ile anında işleçler. C# bu izin vermiyor; izin verilen tek dil yapıları kısıtlamalardan çıkarılabildiği olanlardır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Genel Türlere Giriş](../../../csharp/programming-guide/generics/index.md)
- [Şablonlar](/cpp/cpp/templates-cpp)
