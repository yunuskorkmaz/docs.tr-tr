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
ms.openlocfilehash: 51938dade8ebd1b84010533e04b26cf989ed5f24
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353948"
---
# <a name="generic-collections-in-net"></a>.NET’te Genel Koleksiyonlar

 .NET sınıf kitaplığı <xref:System.Collections.Generic> ve <xref:System.Collections.ObjectModel> ad alanlarında çok sayıda genel koleksiyon sınıfı sağlar. Bu sınıflar hakkında daha ayrıntılı bilgi için bkz. [yaygın olarak kullanılan koleksiyon türleri](../../../docs/standard/collections/commonly-used-collection-types.md).  
  
### <a name="systemcollectionsgeneric"></a>System. Collections. Generic  
 Genel koleksiyon türlerinin birçoğu genel olmayan türlerin doğrudan analoglarından. <xref:System.Collections.Generic.Dictionary%602>, <xref:System.Collections.Hashtable>; genel bir sürümüdür. <xref:System.Collections.DictionaryEntry> yerine numaralandırma için <xref:System.Collections.Generic.KeyValuePair%602> genel yapısını kullanır.  
  
 <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ArrayList> ' in genel bir sürümüdür. Genel olmayan sürümlere karşılık gelen genel <xref:System.Collections.Generic.Queue%601> ve <xref:System.Collections.Generic.Stack%601> sınıfları vardır.  
  
 @No__t-0 ' ın genel ve genel olmayan sürümleri vardır. Her iki sürüm de bir sözlüğün ve listenin hybrilar. @No__t-0 genel sınıfı saf bir sözlüktür ve genel olmayan bir karşılığı yok.  
  
 @No__t-0 genel sınıfı, doğru bağlantılı bir listesidir. Genel olmayan bir karşılığı yoktur.  
  
### <a name="systemcollectionsobjectmodel"></a>System. Collections. ObjectModel  
 @No__t-0 genel sınıfı, kendi genel koleksiyon türlerinizi türetmede bir temel sınıf sağlar. @No__t-0 sınıfı, <xref:System.Collections.Generic.IList%601> genel arabirimini uygulayan herhangi bir türden salt okunurdur bir koleksiyon oluşturmak için kolay bir yol sağlar. @No__t-0 genel sınıfı, kendi anahtarlarını içeren nesneleri depolamanın bir yolunu sağlar.  
  
## <a name="other-generic-types"></a>Diğer genel türler  
 @No__t-0 genel yapısı, değer türlerini, @no__t atandıklarından farklı şekilde kullanmanıza olanak sağlar. Bu, değer türlerini içeren alanların eksik olduğu veritabanı sorgularıyla çalışırken yararlı olabilir. Genel tür parametresi herhangi bir değer türü olabilir.  
  
> [!NOTE]
> C# Ve Visual Basic, dilin Nullable türler için sözdizimi olduğundan, <xref:System.Nullable%601> ' i kullanmak gerekmez. Bkz. [Nullable değer türleriC# (Programlama Kılavuzu)](../../csharp/programming-guide/nullable-types/index.md) ve [null yapılabilir değer türleri (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).
  
 @No__t-0 genel yapısı, herhangi bir türdeki bir öğe aralığını tek boyutlu, sıfır tabanlı bir dizi içinde sınırlandırmak için bir yol sağlar. Genel tür parametresi, dizinin öğelerinin türüdür.  
  
 @No__t-0 genel temsilcisi, olaylarınız .NET Framework tarafından kullanılan olay işleme modelini takip eden olayları işlemek için bir temsilci türü bildirme gereksinimini ortadan kaldırır. Örneğin, olayınıza ilişkin verileri tutmak için <xref:System.EventArgs> ' den türetilen `MyEventArgs` sınıfı oluşturduğunuzu varsayalım. Olayı daha sonra aşağıdaki gibi bildirebilirsiniz:  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Genel Türler](../../../docs/standard/generics/index.md)
- [Dizi ve Listeleri Düzenlemek için Genel Temsilciler](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)
- [Genel Arabirimler](../../../docs/standard/generics/interfaces.md)
