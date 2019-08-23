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
ms.openlocfilehash: b0de14fd5d576774ed1605784f5f0c6b0fae2c8c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948922"
---
# <a name="generic-collections-in-net"></a>.NET’te Genel Koleksiyonlar

 .NET sınıf kitaplığı, <xref:System.Collections.Generic> ve <xref:System.Collections.ObjectModel> ad alanlarında çok sayıda genel koleksiyon sınıfı sağlar. Bu sınıflar hakkında daha ayrıntılı bilgi için bkz. [yaygın olarak kullanılan koleksiyon türleri](../../../docs/standard/collections/commonly-used-collection-types.md).  
  
### <a name="systemcollectionsgeneric"></a>System. Collections. Generic  
 Genel koleksiyon türlerinin birçoğu genel olmayan türlerin doğrudan analoglarından. <xref:System.Collections.Generic.Dictionary%602>, genel bir sürümüdür <xref:System.Collections.Hashtable>; yerine <xref:System.Collections.DictionaryEntry>numaralandırma için genel yapıyı <xref:System.Collections.Generic.KeyValuePair%602> kullanır.  
  
 <xref:System.Collections.Generic.List%601>, öğesinin <xref:System.Collections.ArrayList>genel bir sürümüdür. <xref:System.Collections.Generic.Queue%601> Genel ve <xref:System.Collections.Generic.Stack%601> olmayan sürümlere karşılık gelen sınıflar vardır.  
  
 Genel ve genel olmayan sürümleri <xref:System.Collections.Generic.SortedList%602>vardır. Her iki sürüm de bir sözlüğün ve listenin hybrilar. <xref:System.Collections.Generic.SortedDictionary%602> Genel sınıf saf bir sözlüktür ve genel olmayan bir karşılığı yoktur.  
  
 <xref:System.Collections.Generic.LinkedList%601> Genel sınıf, doğru bağlantılı bir listesidir. Genel olmayan bir karşılığı yoktur.  
  
### <a name="systemcollectionsobjectmodel"></a>System. Collections. ObjectModel  
 Genel <xref:System.Collections.ObjectModel.Collection%601> sınıf, kendi genel koleksiyon türlerinizi türetmede bir temel sınıf sağlar. Sınıfı <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> , <xref:System.Collections.Generic.IList%601> genel arabirimi uygulayan herhangi bir türden salt okunurdur bir koleksiyon oluşturmak için kolay bir yol sağlar. Genel <xref:System.Collections.ObjectModel.KeyedCollection%602> sınıfı, kendi anahtarlarını içeren nesneleri depolamanın bir yolunu sağlar.  
  
## <a name="other-generic-types"></a>Diğer genel türler  
 Genel yapı değer türlerini atandıklarından `null`farklı şekilde kullanmanıza olanak sağlar. <xref:System.Nullable%601> Bu, değer türlerini içeren alanların eksik olduğu veritabanı sorgularıyla çalışırken yararlı olabilir. Genel tür parametresi herhangi bir değer türü olabilir.  
  
> [!NOTE]
> C# Ve Visual Basic, dilin Nullable türler için sözdizimi olduğundan açıkça <xref:System.Nullable%601> kullanılması gerekli değildir. Bkz. [Nullable türlerC# (Programlama Kılavuzu)](../../csharp/programming-guide/nullable-types/index.md) ve [Nullable değer türleri (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md). 
  
 <xref:System.ArraySegment%601> Genel yapı, herhangi bir türdeki tek boyutlu, sıfır tabanlı dizi içindeki bir öğe aralığını sınırlandırmak için bir yol sağlar. Genel tür parametresi, dizinin öğelerinin türüdür.  
  
 <xref:System.EventHandler%601> Genel temsilci, olaylarınız .NET Framework tarafından kullanılan olay işleme modelini takip eden olayları işlemek için bir temsilci türü bildirme gereksinimini ortadan kaldırır. Örneğin, olayınıza ilişkin verileri tutmak için `MyEventArgs` , öğesinden <xref:System.EventArgs>türetilmiş bir sınıf oluşturduğunuzu varsayalım. Olayı daha sonra aşağıdaki gibi bildirebilirsiniz:  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Genel Türler](../../../docs/standard/generics/index.md)
- [Dizi ve Listeleri Düzenlemek için Genel Temsilciler](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)
- [Genel Arabirimler](../../../docs/standard/generics/interfaces.md)
