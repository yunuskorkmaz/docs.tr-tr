---
title: Genel arabirimler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
ms.openlocfilehash: 09b8200d19b6f94cab423dbe4001fbeda83aa06f
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974243"
---
# <a name="generic-interfaces-c-programming-guide"></a>Genel Arabirimler (C# Programlama Kılavuzu)
Genellikle, genel amaçlı koleksiyon sınıfları, veya bir koleksiyondaki öğeleri temsil eden genel sınıfları arabirimler tanımlamak yararlıdır. Genel sınıflar için tercih genel arabirimler gibi kullanmaktır <xref:System.IComparable%601> yerine <xref:System.IComparable>, değer türleri kutulama ve kutudan çıkarma işlemleri önlemek için. .NET Framework sınıf kitaplığı ile koleksiyon sınıflarını kullanmak için çeşitli genel arabirimlerin tanımlar <xref:System.Collections.Generic> ad alanı.  
  
 Bir arabirim bir tür parametresi kısıtlaması olarak belirtildiğinde yalnızca arabirim türleri kullanılabilir. Aşağıdaki kod örnekte gösterildiği bir `SortedList<T>` türetilen sınıf `GenericList<T>` sınıfı. Daha fazla bilgi için [genel türlere giriş](../../../csharp/programming-guide/generics/introduction-to-generics.md). `SortedList<T>` kısıtlama ekler `where T : IComparable<T>`. Böylece `BubbleSort` yönteminde `SortedList<T>` genel kullanılacak <xref:System.IComparable%601.CompareTo%2A> liste öğelerini yöntemi. Bu örnekte, liste öğelerini basit bir sınıfı olan `Person`, uygulayan `IComparable<Person>`.  
  
 [!code-csharp[csProgGuideGenerics#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics2.cs#29)]  
  
 Birden çok arabirim olarak tek bir tür kısıtlamaları şu şekilde belirlenebilir:  
  
 [!code-csharp[csProgGuideGenerics#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#30)]  
  
 Bir arabirim gibi birden fazla tür parametresi tanımlayabilirsiniz:  
  
 [!code-csharp[csProgGuideGenerics#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#31)]  
  
 Sınıflar için geçerli olan kurallar devralma ayrıca arayüzlere uygulanır:  
  
 [!code-csharp[csProgGuideGenerics#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#32)]  
  
 Dönüş değeri olarak yalnızca kendi tür parametresi kullandığı anlamına gelir değişken karşıtı genel arabirim ise genel arabirimler genel olmayan Ara birimden devralınabilir. .NET Framework sınıf kitaplığındaki <xref:System.Collections.Generic.IEnumerable%601> devraldığı <xref:System.Collections.IEnumerable> çünkü <xref:System.Collections.Generic.IEnumerable%601> yalnızca kullanır `T` dönüş değerini <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> ve <xref:System.Collections.Generic.IEnumerator%601.Current%2A> özellik Alıcısı.  
  
 Somut sınıflar gibi kapalı oluşturulmuş arabirimler uygulayabilirsiniz:  
  
 [!code-csharp[csProgGuideGenerics#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#33)]  
  
 Arabirim tarafından şu şekilde gerekli tüm bağımsız değişkenler sınıfı parametre listesi sağlayan sürece genel sınıflar genel arabirimler veya kapalı bir oluşturulmuş arabirimler uygulayabilirsiniz:  
  
 [!code-csharp[csProgGuideGenerics#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#34)]  
  
 Yöntem aşırı yükü denetleyen kuralları Genel sınıflar, yapılar genel veya genel arabirimler içinde yöntemleri için aynıdır. Daha fazla bilgi için [genel yöntemler](../../../csharp/programming-guide/generics/generic-methods.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Genel Türlere Giriş](../../../csharp/programming-guide/generics/introduction-to-generics.md)
- [interface](../../../csharp/language-reference/keywords/interface.md)
- [Genel Türler](~/docs/standard/generics/index.md)
