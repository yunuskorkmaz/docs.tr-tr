---
title: Genel arabirimler-C# Programlama Kılavuzu
description: C# dilinde genel arabirimleri kullanma hakkında bilgi edinin. Kod örneklerine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
ms.openlocfilehash: 6089e14bd2b13268a03d3600ef8bf78f9afa1c6d
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102206745"
---
# <a name="generic-interfaces-c-programming-guide"></a>Genel Arabirimler (C# Programlama Kılavuzu)

Genel koleksiyon sınıfları için ya da koleksiyondaki öğeleri temsil eden genel sınıflar için arabirim tanımlamak genellikle yararlıdır. Genel sınıfların tercihi, <xref:System.IComparable%601> <xref:System.IComparable> değer türlerinde kutulamayı ve kutudan çıkarma işlemlerini önlemek için yerine gibi genel arabirimleri kullanmaktır. .NET sınıf kitaplığı, ad alanındaki koleksiyon sınıflarıyla kullanılmak üzere çeşitli genel arabirimler tanımlar <xref:System.Collections.Generic> .  
  
 Bir arabirim bir tür parametresinde kısıtlama olarak belirtildiğinde, yalnızca arabirimini uygulayan türler kullanılabilir. Aşağıdaki kod örneğinde `SortedList<T>` sınıfından türetilen bir sınıf gösterilmektedir `GenericList<T>` . Daha fazla bilgi için bkz. [Genel türlere giriş](./index.md). `SortedList<T>` kısıtlamayı ekler `where T : IComparable<T>` . Bu, `BubbleSort` içindeki yönteminin `SortedList<T>` <xref:System.IComparable%601.CompareTo%2A> list öğelerinde genel yöntemini kullanmasına olanak sağlar. Bu örnekte, liste öğeleri, uygulayan basit bir sınıftır `Person` `IComparable<Person>` .  
  
 [!code-csharp[csProgGuideGenerics#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics2.cs#29)]  
  
 Birden çok arabirim, tek bir tür üzerinde kısıtlamalar olarak belirtilebilir ve aşağıdaki gibi:  
  
 [!code-csharp[csProgGuideGenerics#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#30)]  
  
 Bir arabirim, aşağıdaki gibi birden fazla tür parametresi tanımlayabilir:  
  
 [!code-csharp[csProgGuideGenerics#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#31)]  
  
 Sınıflar için uygulanan devralma kuralları arabirimler için de geçerlidir:  
  
 [!code-csharp[csProgGuideGenerics#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#32)]  
  
 Genel arabirimler ortak olmayan arabirimlerden devralınabilir ve bu, genel arabirim covaryant ise, bu, yalnızca kendi tür parametresini bir dönüş değeri olarak kullanacağı anlamına gelir. .NET sınıf kitaplığında <xref:System.Collections.Generic.IEnumerable%601> öğesinden devralır <xref:System.Collections.IEnumerable> çünkü <xref:System.Collections.Generic.IEnumerable%601> yalnızca `T` öğesinin dönüş değerinde <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> ve <xref:System.Collections.Generic.IEnumerator%601.Current%2A> özellik alıcısı içinde kullanılır.  
  
 Somut sınıflar, aşağıdaki gibi kapalı oluşturulmuş arabirimler uygulayabilir:  
  
 [!code-csharp[csProgGuideGenerics#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#33)]  
  
 Genel sınıflar, sınıf parametresi listesi arabirimin gerektirdiği tüm bağımsız değişkenleri aşağıdaki şekilde sağladığı sürece genel arabirimleri veya kapalı oluşturulmuş arabirimleri uygulayabilir:  
  
 [!code-csharp[csProgGuideGenerics#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#34)]  
  
 Yöntem aşırı yüklemesini denetleyen kurallar, genel sınıflar, genel yapılar veya genel arabirimler içindeki yöntemler için aynıdır. Daha fazla bilgi için bkz. [Genel yöntemler](./generic-methods.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Genel Türlere Giriş](./index.md)
- [arayüz](../../language-reference/keywords/interface.md)
- [Genel Türler](../../../standard/generics/index.md)
