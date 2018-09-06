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
ms.openlocfilehash: 48838a90939899fc1e7e91cdb7bbe98019591416
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44036044"
---
# <a name="comparisons-and-sorts-within-collections"></a>Koleksiyonlardaki Karşılaştırmalar ve Sıralamalar
<xref:System.Collections> Sınıfları kaldırılacak öğe için arama olup olmadığını koleksiyonları, yönetme veya anahtar-değer çiftinin değer döndüren ilgili neredeyse tüm işlemler karşılaştırmalar gerçekleştirin.  
  
 Koleksiyonlar, genellikle bir eşitlik karşılaştırıcısının ve/veya bir sipariş karşılaştırıcı kullanır. İki yapıları karşılaştırmalar için kullanılır.  
  
<a name="BKMK_Checkingforequality"></a>   
## <a name="checking-for-equality"></a>Eşitlik için denetleniyor  
 Yöntemler gibi `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A>, ve `Remove` eşitlik karşılaştırıcısının koleksiyon öğeleri için kullanın. Koleksiyon genelse, öğe eşitlik aşağıdaki kılavuzlara göre karşılaştırılır:  
  
-   T türü uygulayan <xref:System.IEquatable%601> genel arabirim sonra eşitlik karşılaştırıcısının <xref:System.IEquatable%601.Equals%2A> o arabirimin yöntemi.  
  
-   T türü uygulamazsa <xref:System.IEquatable%601>, <xref:System.Object.Equals%2A?displayProperty=nameWithType> kullanılır.  
  
 Ayrıca, bazı oluşturucu aşırı yüklemeleri sözlük koleksiyonlar için kabul bir <xref:System.Collections.Generic.IEqualityComparer%601> eşitlik için anahtarları karşılaştırmak için kullanılan uygulama. Bir örnek için bkz <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=nameWithType> Oluşturucusu.  
  
<a name="BKMK_Determiningsortorder"></a>   
## <a name="determining-sort-order"></a>Sıralama düzenini belirleme  
 Yöntemler gibi `BinarySearch` ve `Sort` koleksiyon öğeleri için bir sıralama karşılaştırıcı kullanın. Karşılaştırmalar, koleksiyonun öğeleri arasında veya bir öğe ile belirtilen değer arasında olabilir. Nesneleri karşılaştırma için kavramı yoktur bir `default comparer` ve `explicit comparer`.  
  
 En az bir uygulama karşılaştırılan nesnelerin varsayılan karşılaştırıcı kullanır **IComparable** arabirimi. Uygulamak için iyi bir uygulamadır **IComparable** üzerinde tüm sınıflar, değerleri bir liste koleksiyon veya bir sözlük koleksiyondaki anahtarlar olarak kullanılır. Genel bir koleksiyon için eşitlik karşılaştırma aşağıdakilere göre belirlenir:  
  
-   T türü uygulayan <xref:System.IComparable%601?displayProperty=nameWithType> genel arabirim sonra varsayılan karşılaştırıcı <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> o arabirimin yöntemi  
  
-   T türü genel olmayan uyguluyorsa <xref:System.IComparable?displayProperty=nameWithType> arabirim ise varsayılan karşılaştırıcı <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> o arabirimin yöntemi.  
  
-   T türü ya da arabirimi uygulamaz, ardından hiçbir varsayılan karşılaştırıcı yoktur ve bir karşılaştırıcı veya karşılaştırma temsilciyi açıkça belirtilmelidir.  
  
 Açık karşılaştırma sağlamak için bazı yöntemler kabul bir **IComparer** bir parametre olarak bir uygulama. Örneğin, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> yöntemi kabul bir <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> uygulaması.  
  
 Koleksiyonlardaki karşılaştırmalar ve sıralamalar bir koleksiyon içinde sistemin geçerli kültür ayarı etkileyebilir. Varsayılan, karşılaştırma ve sıralar **koleksiyonları** kültüre duyarlı sınıflardır. Kültür ayarı yok sayılır ve bu nedenle tutarlı karşılaştırma ve sıralama sonuçları elde etmek için kullanın <xref:System.Globalization.CultureInfo.InvariantCulture%2A> kabul üye aşırı yüklemeleri ile bir <xref:System.Globalization.CultureInfo>. Daha fazla bilgi için [koleksiyonlarda kültüre duyarsız dize işlemlerini gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) ve [dizilerde kültüre duyarsız dize işlemlerini gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).  
  
<a name="BKMK_Equalityandsortexample"></a>   
## <a name="equality-and-sort-example"></a>Eşitlik ve sıralama örneği  
 Aşağıdaki kod bir uygulamasını gösterir <xref:System.IEquatable%601> ve <xref:System.IComparable%601> basit iş nesnesinde. Ayrıca, nesnenin bir listede depolanıp sıralanmış çağırmanın görürsünüz <xref:System.Collections.Generic.List%601.Sort> yöntemi için varsayılan karşılaştırıcı kullanımıyla sonuçlanıyor `Part` türü ve <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> anonim bir yöntem kullanılarak uygulanan yöntem.  
  
 [!code-csharp[System.Collections.Generic.List.Sort#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.collections.generic.list.sort/cs/program.cs#1)]
 [!code-vb[System.Collections.Generic.List.Sort#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.collections.generic.list.sort/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.IComparer>  
- <xref:System.IEquatable%601>  
- <xref:System.Collections.Generic.IComparer%601>  
- <xref:System.IComparable>  
- <xref:System.IComparable%601>
