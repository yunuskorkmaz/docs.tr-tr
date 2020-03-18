---
title: C++ Şablonları ile C# Generics Arasındaki Farklar - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], vs. C++ templates
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
ms.openlocfilehash: e44f67353410c58c406620109270972df17f9f86
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75703539"
---
# <a name="differences-between-c-templates-and-c-generics-c-programming-guide"></a>C++ Şablonları ve C# Genel Türleri Arasındaki Farklar (C# Programlama Kılavuzu)
C# Generics ve C++ şablonları, parametreli türleri destekleyen her iki dil özelliğidir. Ancak, ikisi arasında birçok fark vardır. Sözdizimi düzeyinde, C# jeneronları C++ şablonlarının karmaşıklığı olmadan parametrelendirilmiş türlere daha basit bir yaklaşımdır. Ayrıca, C# C++ şablonlarının sağladığı tüm işlevleri sağlamaya çalışmaz. Uygulama düzeyinde, birincil fark C# genel tür değiştirmelerinin çalışma zamanında gerçekleştirilmesi ve genel tür bilgilerinin anlık nesneler için korunmasıdır. Daha fazla bilgi için [Çalışma Süresi'ndeki Genel Bilgiler'e](./generics-in-the-run-time.md)bakın.  
  
 C# Generics ve C++ şablonları arasındaki temel farklar şunlardır:  
  
- C# jenerikleri, C++ şablonları ile aynı düzeyde esneklik sağlamaz. Örneğin, kullanıcı tanımlı işleçleri çağırmak mümkün olsa da, C# genel sınıfında aritmetik işleçleri aramak mümkün değildir.  
  
- C# gibi `template C<int i> {}`tür olmayan şablon parametrelerine izin vermez.  
  
- C# açık uzmanlık desteklemez; diğer bir şekilde, belirli bir tür için şablonun özel bir uygulamasıdır.  
  
- C# kısmi uzmanlaşmayı desteklemez: tür bağımsız değişkenlerinin bir alt kümesi için özel bir uygulama.  
  
- C# türü parametresinin genel tür için taban sınıf olarak kullanılmasına izin vermez.  
  
- C# tür parametrelerinin varsayılan türlere sahip olmasını sağlamaz.  
  
- C#'da, genel bir tür parametresi genel olarak kullanılamaz, ancak yapılandırılan türler genel olarak kullanılabilir. C++ şablon parametrelerine izin verir.  
  
- C++, şablondaki tüm tür parametreleri için geçerli olmayan koda izin verir ve bu kod, daha sonra tür parametresi olarak kullanılan belirli bir tür için denetlenir. C# bir sınıftaki kodun kısıtlamaları karşılayan herhangi bir türle çalışacak şekilde yazılmasını gerektirir. Örneğin, C++'da aritmetik işleçleri `+` kullanan ve tür `-` parametresinin nesneleri üzerinde bu işleçleri desteklemeyen bir türle şablonun anında bir hata üretecek bir işlev yazmak mümkündür. C# bunu disallows; izin verilen tek dil yapıları kısıtlamalardan çıkarılabilenlerdir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Genel Türlere Giriş](./index.md)
- [Şablon](/cpp/cpp/templates-cpp)
