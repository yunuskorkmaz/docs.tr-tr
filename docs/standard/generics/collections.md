---
title: .NET’te Genel Koleksiyonlar
ms.date: 02/15/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generics [.NET], collections
- generic collections [.NET]
- generic types [.NET]
ms.assetid: 5b646751-6ab7-465c-916c-b1a76aefa9f5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fa6cd032ecf3a35c1dc32d9907218c9b6efd4bcc
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592272"
---
# <a name="generic-collections-in-net"></a>.NET’te Genel Koleksiyonlar

 .NET sınıf kitaplığı genel koleksiyon sınıflarını sunar <xref:System.Collections.Generic> ve <xref:System.Collections.ObjectModel> ad alanları. Bu sınıflar hakkında daha ayrıntılı bilgi için bkz: [yaygın olarak kullanılan koleksiyon türleri](../../../docs/standard/collections/commonly-used-collection-types.md).  
  
### <a name="systemcollectionsgeneric"></a>System.Collections.Generic  
 Birçok genel koleksiyon tür benzerlikler türlere var. <xref:System.Collections.Generic.Dictionary%602> Genel bir sürümü <xref:System.Collections.Hashtable>; genel yapısı kullanır <xref:System.Collections.Generic.KeyValuePair%602> yerine sabit listesi için <xref:System.Collections.DictionaryEntry>.  
  
 <xref:System.Collections.Generic.List%601> Genel bir sürümü <xref:System.Collections.ArrayList>. Vardır genel <xref:System.Collections.Generic.Queue%601> ve <xref:System.Collections.Generic.Stack%601> jenerik olmayan sürümlerle karşılık gelen sınıflar.  
  
 Jenerik ve jenerik olmayan sürümleri vardır <xref:System.Collections.Generic.SortedList%602>. Her iki sınıflarınızın bir sözlük ve bir listesinin bir karmasını sürümleridir. <xref:System.Collections.Generic.SortedDictionary%602> Genel sınıf saf bir sözlük ve jenerik olmayan hiçbir karşılığı yoktur.  
  
 <xref:System.Collections.Generic.LinkedList%601> Genel sınıftır true olarak bağlı bir liste. Bu, hiçbir jenerik olmayan karşılığı yoktur.  
  
### <a name="systemcollectionsobjectmodel"></a>System.Collections.ObjectModel  
 <xref:System.Collections.ObjectModel.Collection%601> Kendi genel koleksiyon türlerini türetmek için genel sınıf bir temel sınıf sağlar. <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> Sınıf uygulayan her tür salt okunur bir koleksiyon oluşturmak için kolay bir yol sağlar <xref:System.Collections.Generic.IList%601> genel arabirim. <xref:System.Collections.ObjectModel.KeyedCollection%602> Genel sınıf içeren, kendi anahtarlarına nesneleri depolamak için bir yol sağlar.  
  
## <a name="other-generic-types"></a>Diğer genel türler  
 <xref:System.Nullable%601> Genel yapısı alacağı bunlar atanabilir değer türlerinin kullanmanıza olanak verir `null`. Bu veritabanı sorgusu, burada, değer türleri içeren alanlar eksik olabilir çalışırken yararlı olabilir. Genel tür parametresi, herhangi bir değer türü olabilir.  
  
> [!NOTE]
>  C# ve Visual Basic kullanmak gerekli değildir <xref:System.Nullable%601> açıkça dili sözdizimi için boş değer atanabilir türleri olduğundan. Bkz: [boş değer atanabilir türler (C# programlama Kılavuzu)](../../csharp/programming-guide/nullable-types/index.md) ve [boş değer atanabilen değer türleri (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md). 
  
 <xref:System.ArraySegment%601> Genel yapısı, herhangi bir türde tek boyutlu, sıfır tabanlı bir dizi içinde öğe aralığını sınırlandırmak için bir yol sağlar. Genel tür parametresi, dizi öğelerinin türüdür.  
  
 <xref:System.EventHandler%601> Genel temsilci .NET Framework tarafından kullanılan olay işleme Düzen etkinliğiniz izliyorsa, olayları işlemek için bir temsilci türü bildirmek için gereken ortadan kaldırır. Örneğin, oluşturduğunuz düşünün bir `MyEventArgs` sınıfından türetilen <xref:System.EventArgs>, olay verilerini tutacak. Ardından, olay şu şekilde bildirebilirsiniz:  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Genel Türler](../../../docs/standard/generics/index.md)
- [Dizi ve Listeleri Düzenlemek için Genel Temsilciler](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)
- [Genel Arabirimler](../../../docs/standard/generics/interfaces.md)
