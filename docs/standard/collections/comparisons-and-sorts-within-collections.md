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
ms.openlocfilehash: 3360652f22ed39ccfd99f9863052fe584b78562f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159266"
---
# <a name="comparisons-and-sorts-within-collections"></a>Koleksiyonlardaki Karşılaştırmalar ve Sıralamalar
Sınıflar, <xref:System.Collections> ister kaldırılacak öğeyi arıyor olsun, ister anahtar ve değer çiftinin değerini döndürün, koleksiyonları yönetmeyle ilgili hemen hemen tüm işlemlerde karşılaştırmalar gerçekleştirir.  
  
 Koleksiyonlar genellikle eşitlik karşılaştırıcısı ve/veya sipariş karşılayıcıkullanır. Karşılaştırmalar için iki yapı kullanılır.  
  
<a name="BKMK_Checkingforequality"></a>
## <a name="checking-for-equality"></a>Eşitliği kontrol etme  
 , , `Contains` <xref:System.Collections.IList.IndexOf%2A> <xref:System.Collections.Generic.List%601.LastIndexOf%2A>gibi yöntemler `Remove` ve toplama öğeleri için bir eşitlik karşılayıcısı kullanın. Koleksiyon genelse, öğeler aşağıdaki yönergelere göre eşitlik için karşılaştırılır:  
  
- T türü <xref:System.IEquatable%601> genel arabirimi uygularsa, eşitlik karşılayıcısı bu arabirimin <xref:System.IEquatable%601.Equals%2A> yöntemidir.  
  
- T türü <xref:System.IEquatable%601>uygulanmazsa, <xref:System.Object.Equals%2A?displayProperty=nameWithType> kullanılır.  
  
 Buna ek olarak, sözlük koleksiyonları için bazı <xref:System.Collections.Generic.IEqualityComparer%601> oluşturucu aşırı yükler eşitlik için anahtarları karşılaştırmak için kullanılan bir uygulama kabul eder. Örneğin, oluşturucuya <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=nameWithType> bakın.  
  
<a name="BKMK_Determiningsortorder"></a>
## <a name="determining-sort-order"></a>Sıralama sırasını belirleme  
 Toplama öğeleri `BinarySearch` `Sort` için bir sipariş karşılayıcısı gibi yöntemler ve kullanma yöntemleri. Karşılaştırmalar koleksiyonun öğeleri arasında veya bir öğe ve belirli bir değer arasında olabilir. Nesneleri karşılaştırmak için a `default comparer` ve bir `explicit comparer`kavramı vardır.  
  
 Varsayılan karşılayıcı, **IComparable** arabirimini uygulamak için karşılaştırılan nesnelerden en az birine dayanır. Tüm sınıflarda **IComparable** uygulamak için iyi bir uygulamadır bir liste koleksiyonunda değer olarak veya sözlük koleksiyonunda anahtar olarak kullanılır. Genel bir koleksiyon için eşitlik karşılaştırması aşağıdakilere göre belirlenir:  
  
- T türü <xref:System.IComparable%601?displayProperty=nameWithType> genel arabirimi uygularsa, varsayılan <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> karşılayıcı bu arabirimin yöntemidir  
  
- T türü genel <xref:System.IComparable?displayProperty=nameWithType> olmayan arabirimi uygularsa, varsayılan <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> karşılayıcı bu arabirimin yöntemidir.  
  
- T türü arabirimi uygulamıyorsa, varsayılan karşılayıcı yoktur ve bir karşılayıcı veya karşılaştırma temsilcisi açıkça sağlanmalıdır.  
  
 Açık karşılaştırmalar sağlamak için, bazı yöntemler bir parametre olarak **bir IComparer** uygulamasını kabul eder. Örneğin, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> yöntem bir <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> uygulamayı kabul eder.  
  
 Sistemin geçerli kültür ayarı, bir koleksiyondaki karşılaştırmaları ve sıralamaları etkileyebilir. Varsayılan olarak, Koleksiyonlar sınıflarında karşılaştırmalar ve **sıralamalar** kültüre duyarlıdır. Kültür ayarını yoksaymak ve bu nedenle tutarlı <xref:System.Globalization.CultureInfo.InvariantCulture%2A> karşılaştırma ve sıralama sonuçları <xref:System.Globalization.CultureInfo>elde etmek için, bir . Daha fazla bilgi için bkz: [Koleksiyonlarda Kültür-Duyarsız Yaylı İşlemler Gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) ve [Dizilerde Kültür-Duyarsız Yaylı İşlemler Gerçekleştirme.](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md)  
  
<a name="BKMK_Equalityandsortexample"></a>
## <a name="equality-and-sort-example"></a>Eşitlik ve sıralama örneği  
 Aşağıdaki kod, basit bir <xref:System.IEquatable%601> <xref:System.IComparable%601> iş nesnesinin uygulanmasını ve üzerinde olduğunu gösterir. Buna ek olarak, nesne bir listede depolandığında ve sıralandığında, <xref:System.Collections.Generic.List%601.Sort> yöntem çağırmanın `Part` tür için varsayılan karşılayıcının ve <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> anonim bir yöntem kullanılarak uygulanan yöntemin kullanılmasıyla sonuçlandığını görürsünüz.  
  
 [!code-csharp[System.Collections.Generic.List.Sort#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.collections.generic.list.sort/cs/program.cs#1)]
 [!code-vb[System.Collections.Generic.List.Sort#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.collections.generic.list.sort/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.IComparer>
- <xref:System.IEquatable%601>
- <xref:System.Collections.Generic.IComparer%601>
- <xref:System.IComparable>
- <xref:System.IComparable%601>
