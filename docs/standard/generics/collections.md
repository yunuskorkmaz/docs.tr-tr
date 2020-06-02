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
ms.openlocfilehash: 5767bac0bb1e3ae9e586e9a10d8452d421519447
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287577"
---
# <a name="generic-collections-in-net"></a>.NET’te genel koleksiyonlar

 .NET sınıf kitaplığı, <xref:System.Collections.Generic> ve ad alanlarında çok sayıda genel koleksiyon sınıfı sağlar <xref:System.Collections.ObjectModel> . Bu sınıflar hakkında daha ayrıntılı bilgi için bkz. [yaygın olarak kullanılan koleksiyon türleri](../collections/commonly-used-collection-types.md).  
  
## <a name="systemcollectionsgeneric"></a>System.Collections.Generic

 Genel koleksiyon türlerinin birçoğu genel olmayan türlerin doğrudan analoglarından. <xref:System.Collections.Generic.Dictionary%602>, genel bir sürümüdür <xref:System.Collections.Hashtable> ; <xref:System.Collections.Generic.KeyValuePair%602> yerine numaralandırma için genel yapıyı kullanır <xref:System.Collections.DictionaryEntry> .  
  
 <xref:System.Collections.Generic.List%601>, öğesinin genel bir sürümüdür <xref:System.Collections.ArrayList> . Genel <xref:System.Collections.Generic.Queue%601> ve <xref:System.Collections.Generic.Stack%601> olmayan sürümlere karşılık gelen sınıflar vardır.  
  
 Genel ve genel olmayan sürümleri vardır <xref:System.Collections.Generic.SortedList%602> . Her iki sürüm de bir sözlüğün ve listenin hybrilar. <xref:System.Collections.Generic.SortedDictionary%602>Genel sınıf saf bir sözlüktür ve genel olmayan bir karşılığı yoktur.  
  
 <xref:System.Collections.Generic.LinkedList%601>Genel sınıf, doğru bağlantılı bir listesidir. Genel olmayan bir karşılığı yoktur.  
  
## <a name="systemcollectionsobjectmodel"></a>System. Collections. ObjectModel

 <xref:System.Collections.ObjectModel.Collection%601>Genel sınıf, kendi genel koleksiyon türlerinizi türetmede bir temel sınıf sağlar. <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>Sınıfı, genel arabirimi uygulayan herhangi bir türden salt okunurdur bir koleksiyon oluşturmak için kolay bir yol sağlar <xref:System.Collections.Generic.IList%601> . <xref:System.Collections.ObjectModel.KeyedCollection%602>Genel sınıfı, kendi anahtarlarını içeren nesneleri depolamanın bir yolunu sağlar.  
  
## <a name="other-generic-types"></a>Diğer genel türler

 <xref:System.Nullable%601>Genel yapı değer türlerini atandıklarından farklı şekilde kullanmanıza olanak sağlar `null` . Bu, değer türlerini içeren alanların eksik olduğu veritabanı sorgularıyla çalışırken yararlı olabilir. Genel tür parametresi herhangi bir değer türü olabilir.  
  
> [!NOTE]
> C# ve Visual Basic içinde, <xref:System.Nullable%601> dilin Nullable türler için sözdizimi olduğundan açıkça kullanılması gerekli değildir. Bkz. [Nullable değer türleri (C# Başvurusu)](../../csharp/language-reference/builtin-types/nullable-value-types.md) ve [null yapılabilir değer türleri (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).
  
 <xref:System.ArraySegment%601>Genel yapı, herhangi bir türdeki tek boyutlu, sıfır tabanlı dizi içindeki bir öğe aralığını sınırlandırmak için bir yol sağlar. Genel tür parametresi, dizinin öğelerinin türüdür.  
  
 <xref:System.EventHandler%601>Genel temsilci, olaylarınız .NET Framework tarafından kullanılan olay işleme modelini takip eden olayları işlemek için bir temsilci türü bildirme gereksinimini ortadan kaldırır. Örneğin, `MyEventArgs` <xref:System.EventArgs> olayınıza ilişkin verileri tutmak için, öğesinden türetilmiş bir sınıf oluşturduğunuzu varsayalım. Olayı daha sonra aşağıdaki gibi bildirebilirsiniz:  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Genel Türler](index.md)
- [Dizileri ve listeleri Işlemek için genel Temsilciler](delegates-for-manipulating-arrays-and-lists.md)
- [Genel Arabirimler](interfaces.md)
