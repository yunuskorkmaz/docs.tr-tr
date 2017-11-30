---
title: .NET Framework'teki Genel Koleksiyonlar
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generics [.NET Framework], collections
- generic collections [.NET Framework]
ms.assetid: 5b646751-6ab7-465c-916c-b1a76aefa9f5
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 94da20072f793e137b0b7545c1a658ed20537a7f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="generic-collections-in-the-net-framework"></a>.NET Framework'teki Genel Koleksiyonlar
Bu konu genel koleksiyon sınıfları ve diğer genel türleri .NET Framework'teki genel bakış sağlar.  
  
## <a name="generic-collections-in-the-net-framework"></a>.NET Framework'teki Genel Koleksiyonlar  
 .NET Framework sınıf kitaplığı bir genel koleksiyon sınıfları sağlar <xref:System.Collections.Generic> ve <xref:System.Collections.ObjectModel> ad alanları. Bu sınıfları hakkında daha fazla bilgi için bkz: [yaygın olarak kullanılan koleksiyon türleri](../../../docs/standard/collections/commonly-used-collection-types.md).  
  
### <a name="systemcollectionsgeneric"></a>System.Collections.Generic  
 Çoğu genel koleksiyon türleri benzerlikler türlere bulunur. <xref:System.Collections.Generic.Dictionary%602>Genel bir sürümü <xref:System.Collections.Hashtable>; genel yapısı kullanır <xref:System.Collections.Generic.KeyValuePair%602> yerine numaralandırması için <xref:System.Collections.DictionaryEntry>.  
  
 <xref:System.Collections.Generic.List%601>Genel bir sürümü <xref:System.Collections.ArrayList>. Vardır genel <xref:System.Collections.Generic.Queue%601> ve <xref:System.Collections.Generic.Stack%601> nongeneric sürümüne karşılık gelen sınıfları.  
  
 Genel ve nongeneric sürümü vardır <xref:System.Collections.Generic.SortedList%602>. Her iki sürümleridir sınıflarınızın bir karmasını bir sözlük ve bir listesi. <xref:System.Collections.Generic.SortedDictionary%602> Genel sınıfı saf bir sözlük ve hiçbir nongeneric karşılığı vardır.  
  
 <xref:System.Collections.Generic.LinkedList%601> Genel sınıftır true bağlantılı liste. Hiçbir nongeneric karşılığı vardır.  
  
### <a name="systemcollectionsobjectmodel"></a>System.Collections.ObjectModel  
 <xref:System.Collections.ObjectModel.Collection%601> Genel bir sınıf kendi genel koleksiyon türleri türetme için temel sınıf sağlar. <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> Sınıfı uygulayan herhangi bir türü salt okunur bir koleksiyondan üretmek için kolay bir yol sağlar <xref:System.Collections.Generic.IList%601> genel arabirim. <xref:System.Collections.ObjectModel.KeyedCollection%602> Genel bir sınıf kendi anahtarlarını içeren nesneleri depolamak için bir yol sağlar.  
  
## <a name="other-generic-types"></a>Diğer genel türler  
 <xref:System.Nullable%601> Genel yapısı sanki bunlar atanabilir değer türlerinin kullanmanıza olanak verir `null`. Burada, değer türleri içeren alanlar eksik olabilir veritabanı sorguları ile çalışırken, bu yararlı olabilir. Genel tür parametresi herhangi bir değer türü olabilir.  
  
> [!NOTE]
>  C# ile kullanmak ise gerekli değildir <xref:System.Nullable%601> açıkça dili sözdizimi boş değer atanabilir türler için sahip olduğu.  
  
 <xref:System.ArraySegment%601> Genel yapısı içinde herhangi bir türde tek boyutlu, sıfır tabanlı bir dizi öğelerin bir dizi sınırlandırmak için bir yol sağlar. Genel tür parametresi dizi öğeleri türüdür.  
  
 <xref:System.EventHandler%601> Genel temsilcisi ortadan kaldırır, olay tarafından kullanılan olay işleme düzeni izliyorsa olayları işlemek için bir temsilci bildirmek için gereken [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Örneğin, oluşturduğunuz varsayalım bir `MyEventArgs` türetilmiş sınıf <xref:System.EventArgs>, olay verilerini tutacak. Ardından, olay gibi bildirebilirsiniz:  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.ObjectModel?displayProperty=nameWithType>  
 [Genel türler](../../../docs/standard/generics/index.md)  
 [Dizi ve listeleri düzenlemek için genel temsilciler](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)  
 [Genel arabirimler](../../../docs/standard/generics/interfaces.md)
