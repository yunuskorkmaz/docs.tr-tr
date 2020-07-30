---
title: C++ şablonları ve C# genel türleri arasındaki farklar-C# Programlama Kılavuzu
description: C++ şablonları ve C# genel türleri arasındaki farklar hakkında bilgi edinin. Her ikisi de parametreli türler için destek sağlayan dil özelliklerdir.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], vs. C++ templates
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
ms.openlocfilehash: f405e2d4bef730317703b3b8470edef5b89f0bed
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301937"
---
# <a name="differences-between-c-templates-and-c-generics-c-programming-guide"></a>C++ Şablonları ve C# Genel Türleri Arasındaki Farklar (C# Programlama Kılavuzu)
C# Generics ve C++ şablonları, parametreli türler için destek sağlayan dil özellikleridir. Ancak, ikisi arasında birçok farklılık vardır. Sözdizimi düzeyinde C# genel türleri, C++ şablonlarının karmaşıklığı olmadan parametreli türlere daha basit bir yaklaşımdır. Ayrıca C#, C++ şablonlarının sağladığı tüm işlevleri sağlamaya çalışmaz. Uygulama düzeyinde, birincil fark, C# genel tür değişimlerin çalışma zamanında ve genel tür bilgilerinin bu nedenle oluşturulan nesneler için korunmasıdır. Daha fazla bilgi için bkz. [çalışma zamanındaki genel türler](./generics-in-the-run-time.md).  
  
 C# genel türleri ve C++ şablonları arasındaki temel farklılıklar aşağıda verilmiştir:  
  
- C# genel türleri, C++ şablonlarıyla aynı esneklik miktarını sağlamaz. Örneğin, Kullanıcı tanımlı işleçleri çağırmak mümkün olsa da, bir C# genel sınıfında aritmetik işleçleri çağırmak mümkün değildir.  
  
- C#, gibi tür olmayan şablon parametrelerine izin vermez `template C<int i> {}` .  
  
- C# açık özelleştirmeyi desteklemez; diğer bir deyişle, belirli bir tür için bir şablonun özel bir uygulamasıdır.  
  
- C# Kısmi özelleştirmeyi desteklemez: tür bağımsız değişkenlerinin bir alt kümesi için özel bir uygulama.  
  
- C#, tür parametresinin genel tür için temel sınıf olarak kullanılmasına izin vermez.  
  
- C#, tür parametrelerinin varsayılan türleri olmasını sağlar.  
  
- C# dilinde, bir genel tür parametresi genel olamaz, ancak oluşturulan türler genel türler olarak kullanılabilir. C++, şablon parametrelerine izin verir.  
  
- C++, şablondaki tüm tür parametreleri için geçerli olmayan koda izin verir, daha sonra tür parametresi olarak kullanılan belirli tür için denetlenir. C#, bir sınıftaki kodun, kısıtlamaları karşılayan herhangi bir türle çalışacak şekilde yazılmasına gerek duyar. Örneğin, C++ ' da aritmetik işleçleri ve tür parametresinin nesnelerini kullanan bir işlev yazmak mümkündür `+` `-` , bu da bu işleçleri desteklemeyen bir tür ile şablon örneği oluşturma sırasında bir hata oluşturur. C# buna izin vermez; izin verilen tek dil yapıları, kısıtlamalardan çıkarsanolabilecek olanlardır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Genel Türlere Giriş](./index.md)
- [Şablonlar](/cpp/cpp/templates-cpp)
