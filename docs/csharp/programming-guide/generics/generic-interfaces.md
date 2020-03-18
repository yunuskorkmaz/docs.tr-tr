---
title: Genel Arayüzler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
ms.openlocfilehash: 4cce23da7579e30ecff80b3afb92a5a58795c1bd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712214"
---
# <a name="generic-interfaces-c-programming-guide"></a>Genel Arabirimler (C# Programlama Kılavuzu)
Genel koleksiyon sınıfları veya koleksiyondaki öğeleri temsil eden genel sınıflar için arabirimleri tanımlamak genellikle yararlıdır. Genel sınıflar için tercih, değer türlerinde <xref:System.IComparable%601> kutulama <xref:System.IComparable>ve kutulamayı önleme işlemlerini önlemek için, "kutulama ve kutulamayı önleme" yerine genel arabirimler kullanmaktır. .NET Framework sınıf <xref:System.Collections.Generic> kitaplığı, ad alanındaki koleksiyon sınıflarıyla kullanılmak üzere birkaç genel arabirimi tanımlar.  
  
 Bir arabirim, bir tür parametresi üzerinde bir kısıtlama olarak belirtildiğinde, yalnızca arabirimi uygulayan türler kullanılabilir. Aşağıdaki kod `SortedList<T>` `GenericList<T>` örneği, sınıftan türeyen bir sınıfı gösterir. Daha fazla bilgi için [jeneriklere giriş](./index.md)ebakına bakın. `SortedList<T>`kısıtlama `where T : IComparable<T>`ekler. Bu, liste `BubbleSort` öğelerinde genel `SortedList<T>` <xref:System.IComparable%601.CompareTo%2A> yöntemi kullanmak için yöntem sağlar. Bu örnekte, liste öğeleri basit `Person`bir sınıf, bu `IComparable<Person>`uygular.  
  
 [!code-csharp[csProgGuideGenerics#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics2.cs#29)]  
  
 Birden çok arabirim, aşağıdaki gibi, tek bir tür üzerinde kısıtlamalar olarak belirtilebilir:  
  
 [!code-csharp[csProgGuideGenerics#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#30)]  
  
 Arabirim, aşağıdaki gibi birden fazla tür parametresi tanımlayabilir:  
  
 [!code-csharp[csProgGuideGenerics#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#31)]  
  
 Sınıflar için geçerli olan devralma kuralları arabirimler için de geçerlidir:  
  
 [!code-csharp[csProgGuideGenerics#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#32)]  
  
 Genel arabirim, genel arabirim karşıtsa genel olmayan arabirimlerden devralınabilir, bu da yalnızca tür parametresini iade değeri olarak kullandığı anlamına gelir. .NET <xref:System.Collections.Generic.IEnumerable%601> Framework sınıf kitaplığında, <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> yalnızca `T` <xref:System.Collections.Generic.IEnumerator%601.Current%2A> mülk sahibinin <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> ve mülk sahibinin iade değerinde kullandığı için devralır.  
  
 Beton sınıfları aşağıdaki gibi kapalı inşa arayüzleri uygulayabilirsiniz:  
  
 [!code-csharp[csProgGuideGenerics#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#33)]  
  
 Genel sınıflar, sınıf parametre listesi arabirim tarafından gerekli olan tüm bağımsız değişkenleri sağladığı sürece genel arabirimleri veya kapalı oluşturulmuş arabirimleri aşağıdaki gibi uygulayabilir:  
  
 [!code-csharp[csProgGuideGenerics#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#34)]  
  
 Yöntemaşırı yüklemeyi denetleyen kurallar, genel sınıflar, genel yapı veya genel arabirimlerdeki yöntemler için aynıdır. Daha fazla bilgi için [Genel Yöntemler'e](./generic-methods.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Genel Türlere Giriş](./index.md)
- [Arabirim](../../language-reference/keywords/interface.md)
- [Genel Türler](../../../standard/generics/index.md)
