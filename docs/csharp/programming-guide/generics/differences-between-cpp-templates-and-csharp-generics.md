---
title: C++ Şablonları ve C# Genel Türleri Arasındaki Farklar (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], vs. C++ templates
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
ms.openlocfilehash: db3311c7fa81d48137c542f320d0abef791e5116
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="differences-between-c-templates-and-c-generics-c-programming-guide"></a>C++ Şablonları ve C# Genel Türleri Arasındaki Farklar (C# Programlama Kılavuzu)
C# genel türleri ve C++ şablonları parametreli türleri için destek sağlayan iki dil özellikleridir. Bununla birlikte, ikisi arasındaki birçok farklılıklar vardır. Sözdizimi, C# genel türleri C++ şablonlarının KARMAŞASIZ parametreli türler için basit bir yaklaşım düzeyindedir. Ayrıca, C# tüm C++ şablonları sağlar işlevselliği sağlamak denemez. Uygulama düzeyinde birincil çalışma zamanında C# genel tür kısaltmaları gerçekleştirilir ve genel tür bilgileri için örnek nesneleri böylece korunur farktır. Daha fazla bilgi için bkz: [çalışma zamanı'nda genel türler](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).  
  
 C++ şablonları ile C# genel türleri arasındaki temel farklılıklar şunlardır:  
  
-   C# genel türleri esneklik C++ şablon olarak aynı miktarda sağlamaz. Kullanıcı tanımlı işleçler çağırmak mümkün olsa Örneğin, bunu bir C# genel sınıfta aritmetik işleçler çağırmak mümkün değil.  
  
-   C# izin vermiyor tür olmayan şablon parametreleri gibi `template C<int i> {}`.  
  
-   C# açık uzmanlık desteklemiyor; belirli bir tür için bir şablon başka bir deyişle, özel bir uygulaması.  
  
-   C# kısmi uzmanlığı desteklemiyor: tür bağımsız değişkenleri bir alt kümesi için özel bir uygulaması.  
  
-   C# genel tür için temel sınıf olarak kullanılacak tür parametresi izin vermiyor.  
  
-   C# varsayılan türleri tür parametreleri izin vermiyor.  
  
-   Genel türler oluşturulan türler kullanılabilse de C# ' ta bir genel tür parametresi kendisini bir genel olamaz. C++ şablon parametreleri izin vermez.  
  
-   C++ tür parametresi kullanılan belirli türünün sonra kullanıma şablondaki tüm tür parametreleri için geçerli olmayabilir kodu sağlar. C# kod kısıtlamaları karşılayan herhangi bir türü ile çalışacağını şekilde yazılması için bir sınıf gerektirir. Örneğin, c++'ta aritmetik işleçler kullanan bir işlev yazmak mümkündür `+` ve `-` tür parametresi nesnelerde hangi oluşturacak bir hata şablonu örneklemesi bu desteklemeyen türüne sahip zaman işleçler. C# bu izin vermez; izin verilen tek dil yapıları kısıtlamaları anlaşılan izinlerdir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Genel Türlere Giriş](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [Şablonlar](/cpp/cpp/templates-cpp)
