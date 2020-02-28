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
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159266"
---
# <a name="comparisons-and-sorts-within-collections"></a>Koleksiyonlardaki Karşılaştırmalar ve Sıralamalar
<xref:System.Collections> sınıfları, bir anahtar ve değer çiftinin değerini kaldırmak ya da döndürmek için arama yapılıp yapılmayacağını, koleksiyonları yönetmeye dahil olan tüm işlemlerde karşılaştırmalar gerçekleştirir.  
  
 Koleksiyonlar genellikle bir eşitlik karşılaştırıcısı ve/veya bir sıralama karşılaştırıcısı kullanır. Karşılaştırmalar için iki yapı kullanılır.  
  
<a name="BKMK_Checkingforequality"></a>
## <a name="checking-for-equality"></a>Eşitlik denetleniyor  
 `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A>ve `Remove` gibi yöntemler, koleksiyon öğeleri için eşitlik karşılaştırıcısı kullanır. Koleksiyon genel ise, öğeler aşağıdaki yönergelere göre eşitlik için karşılaştırılır:  
  
- Tür T <xref:System.IEquatable%601> genel arabirimini uyguluyorsa, eşitlik karşılaştırıcısı bu arabirimin <xref:System.IEquatable%601.Equals%2A> yöntemidir.  
  
- Tür T <xref:System.IEquatable%601>uygulamadığından, <xref:System.Object.Equals%2A?displayProperty=nameWithType> kullanılır.  
  
 Ayrıca, sözlük koleksiyonları için bazı Oluşturucu aşırı yüklemeleri, anahtarları eşitlik için karşılaştırmak üzere kullanılan bir <xref:System.Collections.Generic.IEqualityComparer%601> uygulamasını kabul eder. Bir örnek için <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=nameWithType> oluşturucusuna bakın.  
  
<a name="BKMK_Determiningsortorder"></a>
## <a name="determining-sort-order"></a>Sıralama düzenini belirleme  
 `BinarySearch` ve `Sort` gibi yöntemler, koleksiyon öğeleri için bir sıralama karşılaştırıcısı kullanır. Karşılaştırmalar koleksiyonun öğeleri arasında veya bir öğe ile belirtilen değer arasında olabilir. Nesneleri karşılaştırmak için, bir `default comparer` ve `explicit comparer`kavramı vardır.  
  
 Varsayılan karşılaştırıcı, **IComparable** arabirimini uygulamak için karşılaştırılan nesnelerden en az birini temel alır. Tüm sınıflarda **IComparable** uygulamak iyi bir uygulamadır, bir liste koleksiyonunda değer olarak veya bir sözlük koleksiyonundaki anahtarlar olarak kullanılır. Genel bir koleksiyon için eşitlik karşılaştırması aşağıdakilere göre belirlenir:  
  
- Tür T <xref:System.IComparable%601?displayProperty=nameWithType> genel arabirimini uyguluyorsa, varsayılan karşılaştırıcı bu arabirimin <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> yöntemidir  
  
- Tür T genel olmayan <xref:System.IComparable?displayProperty=nameWithType> arabirimini uyguluyorsa, varsayılan karşılaştırıcı, bu arabirimin <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> yöntemidir.  
  
- Tür T her iki arabirimi de uygulamadığından, varsayılan karşılaştırıcı yoktur ve açıkça bir karşılaştırıcı veya karşılaştırma temsilcisi sağlanmalıdır.  
  
 Açık karşılaştırmalar sağlamak için bazı yöntemler bir **IComparer** uygulamasını parametre olarak kabul eder. Örneğin, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> yöntemi bir <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> uygulamasını kabul eder.  
  
 Sistemin geçerli kültür ayarı karşılaştırmaları etkileyebilir ve bir koleksiyon içinde sıralama yapabilir. Varsayılan olarak, **koleksiyonlar** sınıflarında karşılaştırmalar ve sıralamalar kültüre duyarlıdır. Kültür ayarını yoksaymak ve bu nedenle tutarlı karşılaştırma ve sıralama sonuçları elde etmek için, <xref:System.Globalization.CultureInfo>kabul eden üye aşırı yüklemeleri olan <xref:System.Globalization.CultureInfo.InvariantCulture%2A> kullanın. Daha fazla bilgi için bkz. [koleksiyonlarda kültüre duyarsız dize Işlemleri gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) ve [dizilerde kültüre duyarsız dize işlemlerini gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).  
  
<a name="BKMK_Equalityandsortexample"></a>
## <a name="equality-and-sort-example"></a>Eşitlik ve sıralama örneği  
 Aşağıdaki kod, basit bir iş nesnesi üzerinde <xref:System.IEquatable%601> ve <xref:System.IComparable%601> bir uygulamasını gösterir. Ayrıca, nesnesi bir listede depolandığında ve sıralandığında, <xref:System.Collections.Generic.List%601.Sort> yöntemini çağırmanın `Part` türü için varsayılan karşılaştırıcının kullanılmasına ve anonim bir yöntem kullanılarak uygulanan <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> yöntemine neden olduğunu görürsünüz.  
  
 [!code-csharp[System.Collections.Generic.List.Sort#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.collections.generic.list.sort/cs/program.cs#1)]
 [!code-vb[System.Collections.Generic.List.Sort#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.collections.generic.list.sort/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.IComparer>
- <xref:System.IEquatable%601>
- <xref:System.Collections.Generic.IComparer%601>
- <xref:System.IComparable>
- <xref:System.IComparable%601>
