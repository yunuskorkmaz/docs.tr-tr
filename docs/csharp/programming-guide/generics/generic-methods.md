---
title: Genel yöntemler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
ms.openlocfilehash: 083fc6ff3dd15252fb6cf2beb27b5be0a6e489f5
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423448"
---
# <a name="generic-methods-c-programming-guide"></a>Genel Yöntemler (C# Programlama Kılavuzu)
Genel bir yöntem tür parametreleri ile aşağıdaki gibi belirtilen bir yöntemdir:  
  
 [!code-csharp[csProgGuideGenerics#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#22)]  
  
 Aşağıdaki kod örneği kullanarak yöntemini çağırma yollarından biri gösterilmektedir `int` tür bağımsız değişkeni için:  
  
 [!code-csharp[csProgGuideGenerics#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#23)]  
  
 Tür bağımsız değişkeni de atlayabilirsiniz ve derleyici bunu çıkarımlar. Aşağıdaki çağrı `Swap` önceki çağrısına eşdeğerdir:  
  
 [!code-csharp[csProgGuideGenerics#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#24)]  
  
 Tür çıkarımı için aynı kurallara statik ve örnek yöntemleri için geçerlidir. Derleyici, geçirdiğiniz yöntem bağımsız değişkenleri temel tür parametreleri çıkarımını; Kısıtlama türü Parametreler yalnızca tanım Çıkarsama veya dönüş değeri. Bu nedenle tür çıkarımı, parametresi olmayan yöntemleri ile çalışmaz. Tür çıkarımı, derleyici aşırı yüklenmiş yöntem imzaları çözmeye çalışmadan önce derleme zamanında gerçekleşir. Derleyicinin tür çıkarımı mantıksal aynı adı paylaşan tüm genel yöntemleri için geçerlidir. Aşırı yükleme çözünürlüğü adımda yalnızca üzerinde tür çıkarımı başarılı genel yöntemler derleyicisini içerir.  
  
 Genel bir sınıf içinde genel olmayan yöntemler sınıf düzeyinde tür parametreleri gibi erişebilirsiniz:  
  
 [!code-csharp[csProgGuideGenerics#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#25)]  
  
 Kapsayan sınıfı aynı tür parametreleri alan genel yöntem tanımlama, yöntemi kapsam içinde iç için bağımsız değişken sağladığından derleyici uyarı CS0693 oluşturur `T` dış içinsağlananbağımsızdeğişkengizliyor`T`. Tür bağımsız değişkenleri sınıfı oluşturulduğunda sağlanan olanlar dışındaki bir genel sınıfı yöntemini çağırma esneklik gerekiyorsa, başka bir tanımlayıcı yöntem türü parametresi sağlamayı gösterildiği gibi düşünün `GenericList2<T>` aşağıdaki örnek.  
  
 [!code-csharp[csProgGuideGenerics#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#26)]  
  
 Kısıtlama yöntemlerini tür parametrelerindeki daha özel işlemlerini etkinleştirmek için kullanın. Bu sürümü `Swap<T>`, artık adlandırılmış `SwapIfGreater<T>`, uygulama tür bağımsız değişkenleri ile yalnızca kullanılabilir <xref:System.IComparable%601>.  
  
 [!code-csharp[csProgGuideGenerics#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#27)]  
  
 Birden çok tür parametrelerinde genel yöntemler aşırı yüklenebilir. Örneğin, aşağıdaki yöntemlerden tümü aynı sınıf içinde yer alabilir:  
  
 [!code-csharp[csProgGuideGenerics#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#28)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 Daha fazla bilgi edinmek için, bkz. [C# Dil Belirtimi](~/_csharplang/spec/classes.md#methods).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Genel Türlere Giriş](../../../csharp/programming-guide/generics/index.md)
- [Yöntemler](../../../csharp/programming-guide/classes-and-structs/methods.md)
