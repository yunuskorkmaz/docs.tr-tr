---
title: Genel Arabirimler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
ms.openlocfilehash: 4c7449568ff250c8de521e7afb71178536f52657
ms.sourcegitcommit: 4bca8f7e172fd019ef437a4803bf5895c6bc4781
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2018
ms.locfileid: "50980781"
---
# <a name="generic-interfaces-c-programming-guide"></a>Genel Arabirimler (C# Programlama Kılavuzu)
Genellikle, genel amaçlı koleksiyon sınıfları, veya bir koleksiyondaki öğeleri temsil eden genel sınıfları arabirimler tanımlamak yararlıdır. Genel sınıflar için tercih genel arabirimler gibi kullanmaktır <xref:System.IComparable%601> yerine <xref:System.IComparable>, değer türleri kutulama ve kutudan çıkarma işlemleri önlemek için. .NET Framework sınıf kitaplığı ile koleksiyon sınıflarını kullanmak için çeşitli genel arabirimlerin tanımlar <xref:System.Collections.Generic> ad alanı.  
  
 Bir arabirim bir tür parametresi kısıtlaması olarak belirtildiğinde yalnızca arabirim türleri kullanılabilir. Aşağıdaki kod örnekte gösterildiği bir `SortedList<T>` türetilen sınıf `GenericList<T>` sınıfı. Daha fazla bilgi için [genel türlere giriş](../../../csharp/programming-guide/generics/introduction-to-generics.md). `SortedList<T>` kısıtlama ekler `where T : IComparable<T>`. Böylece `BubbleSort` yönteminde `SortedList<T>` genel kullanılacak <xref:System.IComparable%601.CompareTo%2A> liste öğelerini yöntemi. Bu örnekte, liste öğelerini basit bir sınıfı olan `Person`, uygulayan `IComparable<Person>`.  
  
 [!code-csharp[csProgGuideGenerics#29](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_1.cs)]  
  
 Birden çok arabirim olarak tek bir tür kısıtlamaları şu şekilde belirlenebilir:  
  
 [!code-csharp[csProgGuideGenerics#30](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_2.cs)]  
  
 Bir arabirim gibi birden fazla tür parametresi tanımlayabilirsiniz:  
  
 [!code-csharp[csProgGuideGenerics#31](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_3.cs)]  
  
 Sınıflar için geçerli olan kurallar devralma ayrıca arayüzlere uygulanır:  
  
 [!code-csharp[csProgGuideGenerics#32](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_4.cs)]  
  
 Dönüş değeri olarak yalnızca kendi tür parametresi kullandığı anlamına gelir değişken karşıtı genel arabirim ise genel arabirimler genel olmayan Ara birimden devralınabilir. .NET Framework sınıf kitaplığındaki <xref:System.Collections.Generic.IEnumerable%601> devraldığı <xref:System.Collections.IEnumerable> çünkü <xref:System.Collections.Generic.IEnumerable%601> yalnızca kullanır `T` dönüş değerini <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> ve <xref:System.Collections.Generic.IEnumerator%601.Current%2A> özellik Alıcısı.  
  
 Somut sınıflar gibi kapalı oluşturulmuş arabirimler uygulayabilirsiniz:  
  
 [!code-csharp[csProgGuideGenerics#33](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_5.cs)]  
  
 Arabirim tarafından şu şekilde gerekli tüm bağımsız değişkenler sınıfı parametre listesi sağlayan sürece genel sınıflar genel arabirimler veya kapalı bir oluşturulmuş arabirimler uygulayabilirsiniz:  
  
 [!code-csharp[csProgGuideGenerics#34](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_6.cs)]  
  
 Yöntem aşırı yükü denetleyen kuralları Genel sınıflar, yapılar genel veya genel arabirimler içinde yöntemleri için aynıdır. Daha fazla bilgi için [genel yöntemler](../../../csharp/programming-guide/generics/generic-methods.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Genel Türlere Giriş](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
- [interface](../../../csharp/language-reference/keywords/interface.md)  
- [Genel Türler](~/docs/standard/generics/index.md)
