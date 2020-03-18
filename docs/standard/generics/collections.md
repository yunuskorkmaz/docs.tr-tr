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
ms.openlocfilehash: dce0e38b0198396ec0dbc3ced7f2f59c2b112b56
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708416"
---
# <a name="generic-collections-in-net"></a>.NET'teki genel koleksiyonlar

 .NET sınıf kitaplığı, ad alanlarında bir <xref:System.Collections.Generic> <xref:System.Collections.ObjectModel> dizi genel koleksiyon sınıfı sağlar. Bu sınıflar hakkında daha ayrıntılı bilgi için, [Yaygın Kullanılan Koleksiyon Türleri'ne](../../../docs/standard/collections/commonly-used-collection-types.md)bakın.  
  
## <a name="systemcollectionsgeneric"></a>System.Collections.Generic

 Genel koleksiyon türlerinin çoğu, genel olmayan türlerin doğrudan analoglarıdır. <xref:System.Collections.Generic.Dictionary%602>genel bir <xref:System.Collections.Hashtable>versiyonudur; yerine numaralandırma <xref:System.Collections.Generic.KeyValuePair%602> için genel yapıyı <xref:System.Collections.DictionaryEntry>kullanır.  
  
 <xref:System.Collections.Generic.List%601>'nin <xref:System.Collections.ArrayList>genel bir versiyonudur. Genel olmayan <xref:System.Collections.Generic.Queue%601> <xref:System.Collections.Generic.Stack%601> sürümlere karşılık gelen genel ve sınıflar vardır.  
  
 Genel ve genel olmayan <xref:System.Collections.Generic.SortedList%602>sürümleri vardır. Her iki sürüm de sözlük ve bir listenin melezleridir. Genel <xref:System.Collections.Generic.SortedDictionary%602> sınıf saf bir sözlüktür ve genel olmayan bir benzerliği yoktur.  
  
 Genel <xref:System.Collections.Generic.LinkedList%601> sınıf gerçek bir bağlı listedir. Genel olmayan bir benzerliği yoktur.  
  
## <a name="systemcollectionsobjectmodel"></a>System.Collections.ObjectModel

 Genel <xref:System.Collections.ObjectModel.Collection%601> sınıf, kendi genel koleksiyon türlerinizi türemeniz için bir taban sınıf sağlar. Sınıf, <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> <xref:System.Collections.Generic.IList%601> genel arabirimi uygulayan herhangi bir türden salt okunur bir koleksiyon oluşturmak için kolay bir yol sağlar. Genel <xref:System.Collections.ObjectModel.KeyedCollection%602> sınıf, kendi anahtarlarını içeren nesneleri depolamak için bir yol sağlar.  
  
## <a name="other-generic-types"></a>Diğer genel türler

 Genel <xref:System.Nullable%601> yapı, değer türlerini atanmış `null`gibi kullanmanıza olanak tanır. Bu, değer türleri içeren alanların eksik olabileceği veritabanı sorgularıyla çalışırken yararlı olabilir. Genel tür parametresi herhangi bir değer türü olabilir.  
  
> [!NOTE]
> C# ve Visual Basic'te, dilin nullable türleri için sözdizimi olduğundan açıkça kullanılması <xref:System.Nullable%601> gerekmez. Bkz. [Nullable değer türleri (C# başvurusu)](../../csharp/language-reference/builtin-types/nullable-value-types.md) ve [Nullable değer türleri (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).
  
 Genel <xref:System.ArraySegment%601> yapı, herhangi bir türdeki tek boyutlu, sıfır tabanlı diziiçindeki bir öğe aralığını sınırlamanın bir yolunu sağlar. Genel tür parametresi, dizinin öğelerinin türüdür.  
  
 Genel <xref:System.EventHandler%601> temsilci, etkinliğiniz .NET Framework tarafından kullanılan olay işleme deseni izliyorsa, olayları işlemek için bir temsilci türü bildirme gereksinimini ortadan kaldırır. Örneğin, etkinliğiniz için `MyEventArgs` verileri tutmak <xref:System.EventArgs>için türetilen bir sınıf oluşturduğunuzu varsayalım. Daha sonra olayı aşağıdaki gibi bildirebilirsiniz:  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Genel Türler](../../../docs/standard/generics/index.md)
- [Dizi ve Listeleri Düzenlemek için Genel Temsilciler](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)
- [Genel Arabirimler](../../../docs/standard/generics/interfaces.md)
