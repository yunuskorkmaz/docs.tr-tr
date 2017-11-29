---
title: "Genel Arabirimler (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0326a7bc459c641cbfafe39fe36525a947051c16
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="generic-interfaces-c-programming-guide"></a>Genel Arabirimler (C# Programlama Kılavuzu)
Genellikle, arabirimleri genel koleksiyon sınıfları, veya koleksiyondaki öğelerin temsil eden genel sınıfları tanımlamak yararlıdır. Genel sınıflar için tercih genel arabirimler gibi kullanmaktır <xref:System.IComparable%601> yerine <xref:System.IComparable>, değer türleri kutulama ve kutudan çıkarma işlemlerini önlemek için. Koleksiyon sınıfları ile kullanılmak üzere birkaç genel arabirimler .NET Framework sınıf kitaplığı tanımlar <xref:System.Collections.Generic> ad alanı.  
  
 Arabirim tür parametresi bir kısıtlama olarak belirtildiğinde arabirimini uygulayan türleri kullanılabilir. Aşağıdaki örnekte gösterildiği kod bir `SortedList<T>` öğesinden türetilen sınıf `GenericList<T>` sınıfı. Daha fazla bilgi için bkz: [genel türlere giriş](../../../csharp/programming-guide/generics/introduction-to-generics.md). `SortedList<T>`kısıtlama ekler `where T : IComparable<T>`. Böylece `BubbleSort` yönteminde `SortedList<T>` genel kullanmak için <xref:System.IComparable%601.CompareTo%2A> liste öğelerini yöntemi. Bu örnekte, liste öğelerini basit bir sınıf olan `Person`, uygulayan `IComparable<Person>`.  
  
 [!code-csharp[csProgGuideGenerics#29](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_1.cs)]  
  
 Birden çok arabirim olarak tek bir türü kısıtlamaları gibi belirtilebilir:  
  
 [!code-csharp[csProgGuideGenerics#30](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_2.cs)]  
  
 Arabirim birden fazla tür parametresi, aşağıdaki gibi tanımlayabilirsiniz:  
  
 [!code-csharp[csProgGuideGenerics#31](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_3.cs)]  
  
 Sınıfları için geçerli bir kurallar devralma arabirimleri için de geçerlidir:  
  
 [!code-csharp[csProgGuideGenerics#32](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_4.cs)]  
  
 Genel arabirimi dönüş değeri olarak yalnızca kendi tür parametresi kullandığı anlamı karşıt-variant ise genel arabirimler genel olmayan arabirimlerinden devralabilirsiniz. .NET Framework Sınıf Kitaplığı'nda <xref:System.Collections.Generic.IEnumerable%601> devraldığı <xref:System.Collections.IEnumerable> çünkü <xref:System.Collections.Generic.IEnumerable%601> yalnızca kullanır `T` dönüş değeri olarak <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> ve <xref:System.Collections.Generic.IEnumerator%601.Current%2A> özellik Alıcısı.  
  
 Somut sınıflar kapalı oluşturulan arabirimleri, aşağıdaki gibi uygulayabilirsiniz:  
  
 [!code-csharp[csProgGuideGenerics#33](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_5.cs)]  
  
 Genel sınıflar arabirimi tarafından gibi gerekli tüm bağımsız değişkenler sınıfı parametre listesi sağlayan sürece genel arabirimler veya kapalı yapılandırılmış arabirimlerini uygulayabilirsiniz:  
  
 [!code-csharp[csProgGuideGenerics#34](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_6.cs)]  
  
 Genel sınıflar, yapılar genel veya genel arabirimler içinde yöntemlerini yöntemi aşırı yüklemesi denetleyen kurallar aynıdır. Daha fazla bilgi için bkz: [genel yöntemler](../../../csharp/programming-guide/generics/generic-methods.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Genel türlere giriş](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [arabirimi](../../../csharp/language-reference/keywords/interface.md)  
 [Genel türler](~/docs/standard/generics/index.md)
