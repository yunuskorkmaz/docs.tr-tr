---
title: Koleksiyonlardaki Karşılaştırmalar ve Sıralamalar
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting data, collections
- IComparable.CompareTo method
- Collections classes
- Equals method
- collections [.NET Framework], comparisons
ms.assetid: 5e4d3b45-97f0-423c-a65f-c492ed40e73b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11393f4013a1b5ed9dc90154f289466432102a38
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="comparisons-and-sorts-within-collections"></a>Koleksiyonlardaki Karşılaştırmalar ve Sıralamalar
<xref:System.Collections> Sınıfları öğesi kaldırmak arama olup olmadığını koleksiyonlar, yönetme veya bir anahtar-değer çiftinin değer döndürme söz konusu neredeyse tüm işlemlerde karşılaştırmaları gerçekleştirin.  
  
 Koleksiyonlar, genellikle bir eşitlik karşılaştırıcısını ve/veya bir sıralama karşılaştırıcı kullanın. İki yapıları karşılaştırmaları için kullanılır.  
  
<a name="BKMK_Checkingforequality"></a>   
## <a name="checking-for-equality"></a>Eşitlik için denetleniyor  
 Gibi yöntemler `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A>, ve `Remove` bir eşitlik karşılaştırıcısını koleksiyon öğeleri için kullanın. Koleksiyon genel ise, öğeleri aşağıdaki kılavuzlara göre eşitliği karşılaştırılır:  
  
-   Varsa T türü uygular <xref:System.IEquatable%601> genel arabirim eşitlik karşılaştırıcısını olduğundan <xref:System.IEquatable%601.Equals%2A> arabirimi yöntemi.  
  
-   T türü uygulamazsa <xref:System.IEquatable%601>, <xref:System.Object.Equals%2A?displayProperty=nameWithType> kullanılır.  
  
 Ayrıca, bazı Oluşturucusu aşırı sözlük koleksiyonlar için kabul bir <xref:System.Collections.Generic.IEqualityComparer%601> eşitlik tuşları karşılaştırmak için kullanılan uygulama. Bir örnek için bkz: <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=nameWithType> Oluşturucusu.  
  
<a name="BKMK_Determiningsortorder"></a>   
## <a name="determining-sort-order"></a>Sıralama düzenini belirleme  
 Gibi yöntemler `BinarySearch` ve `Sort` için koleksiyon öğeleri sıralama karşılaştırıcı kullanın. Karşılaştırmaları koleksiyon öğelerini bir öğe ile belirtilen değer arasında veya olabilir. Nesneleri karşılaştırma için kavramı yoktur bir `default comparer` ve bir `explicit comparer`.  
  
 En az bir uygulamak için karşılaştırılan nesnelerin varsayılan karşılaştırıcı dayanır **IComparable** arabirimi. Uygulamak için iyi bir uygulamadır **IComparable** tüm sınıflarında değerler liste koleksiyonu olarak veya bir sözlük koleksiyonu anahtar olarak kullanılır. Genel bir koleksiyon için eşitlik karşılaştırması aşağıdaki göre belirlenir:  
  
-   Varsa T türü uygular <xref:System.IComparable%601?displayProperty=nameWithType> genel arabirim olduğundan, varsayılan karşılaştırıcı <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> bu arabirimin yöntemi  
  
-   T türü genel olmayan uyguluyorsa <xref:System.IComparable?displayProperty=nameWithType> arabirim ise varsayılan karşılaştırıcı <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> arabirimi yöntemi.  
  
-   T türü ya da arabirimi uygulamaz, ardından varsayılan karşılaştırıcı yoktur ve karşılaştırıcı veya karşılaştırma temsilci açıkça sağlanmalıdır.  
  
 Açık karşılaştırmaları sağlamak için bazı yöntemler kabul bir **IComparer** bir parametre olarak uygulama. Örneğin, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> yöntemi kabul eden bir <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> uygulaması.  
  
 Geçerli kültür ayarı sisteminin karşılaştırmalar ve sıralamalar bir koleksiyon içinde etkileyebilir. Varsayılan, karşılaştırmaları ve sıralar **koleksiyonları** sınıfları kültüre duyarlı. Kültür ayarı yoksay ve bu nedenle tutarlı karşılaştırma ve sıralama sonuçları almak için kullanmak <xref:System.Globalization.CultureInfo.InvariantCulture%2A> kabul üye aşırı ile bir <xref:System.Globalization.CultureInfo>. Daha fazla bilgi için bkz: [koleksiyonlarda kültüre duyarsız dize işlemlerini gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) ve [dizilerde kültüre duyarsız dize işlemlerini gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).  
  
<a name="BKMK_Equalityandsortexample"></a>   
## <a name="equality-and-sort-example"></a>Eşitlik ve sıralama örneği  
 Aşağıdaki kod bir uygulama ortaya koyar <xref:System.IEquatable%601> ve <xref:System.IComparable%601> basit iş nesnesi üzerinde. Ayrıca, nesne bir listede depolanıp sıralanmış çağırmanın görürsünüz <xref:System.Collections.Generic.List%601.Sort> yöntemi için varsayılan karşılaştırıcı kullanımıyla sonuçlanıyor `Part` türü ve <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> anonim bir yöntemi kullanarak uygulanan yöntemi.  
  
 [!code-csharp[System.Collections.Generic.List.Sort#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.collections.generic.list.sort/cs/program.cs#1)]
 [!code-vb[System.Collections.Generic.List.Sort#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.collections.generic.list.sort/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.IComparer>  
 <xref:System.IEquatable%601>  
 <xref:System.Collections.Generic.IComparer%601>  
 <xref:System.IComparable>  
 <xref:System.IComparable%601>
