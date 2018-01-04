---
title: "Null semantiği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 6786c7ea4441b1a753d6f0b4213f40fa64dcb4ef
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="null-semantics"></a>Null semantiği
Aşağıdaki tabloda, çeşitli bölümlerine bağlantılar sağlanmaktadır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] belgeleri nerede `null` (`Nothing` içinde [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) sorunları ele alınmıştır.  
  
|Konu|Açıklama|  
|-----------|-----------------|  
|[SQL-CLR Tür Uyumsuzlukları](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mismatches.md)|Üç durumlu SQL Boolean iki durumlu ortak dil çalışma zamanı (CLR) karşı tartışması bu konuda "Null semantiği" kısmında bulunur <xref:System.Boolean>, sabit `Nothing` ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) ve `null` (C#) ve benzer diğer sorunları.|  
|[Standart Sorgu İşleci Çevirisi](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)|Bu konunun "Null semantiği" bölümüne null karşılaştırma semantiği açıklar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].|  
|[System.String Yöntemleri](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md)|Bu konunun "Farklar gelen .NET" bölümüne 0'dan döndürmek nasıl açıklar <xref:System.String.LastIndexOf%2A> dizesi null veya bulunan konumu 0 olduğu anlamına gelebilir.|  
|[Sayısal Dizideki Değerlerin Toplamını Hesaplama](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)|Açıklar nasıl <xref:System.Linq.Enumerable.Sum%2A> işleci hesaplar için `null` (`Nothing` içinde [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) yerine boş bir dizi veya yalnızca null içeren bir dizi için 0.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Türleri ve İşlevleri](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
