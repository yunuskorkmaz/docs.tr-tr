---
title: Nesnelere LINQ (C#)
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: ae4389aa1ce049edc71bff42c38f66fb328ba034
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344777"
---
# <a name="linq-to-objects-c"></a>Nesnelere LINQ (C#)
"LinQ to Objects" terimi, linq sorgularının doğrudan <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> herhangi bir veya koleksiyona sahip, bir ara LINQ sağlayıcısı veya [LINQ'dan SQL'e](../../../../framework/data/adonet/sql/linq/index.md) veya [LINQ'dan XML'e](./linq-to-xml-overview.md)API kullanmadan kullanılması anlamına gelir. Linq'i kullanarak <xref:System.Collections.Generic.List%601>, <xref:System.Array>, veya <xref:System.Collections.Generic.Dictionary%602>. Koleksiyon kullanıcı tarafından tanımlanabilir veya .NET Framework API tarafından döndürülebilir.  
  
 Temel anlamda LINQ to Objects koleksiyonlara yeni bir yaklaşımı temsil eder. Eski şekilde, bir koleksiyondan `foreach` veri alma nın nasıl olduğunu belirten karmaşık döngüler yazmanız gerekiyordu. LINQ yaklaşımında, ne almak istediğinizi açıklayan bildirim kodu yazarsınız.  
  
 Buna ek olarak, LINQ sorguları `foreach` geleneksel döngülere göre üç ana avantaj sunar:  
  
1. Özellikle birden çok koşulu filtrelerken daha kısa ve okunabilirdirler.  
  
2. En az uygulama koduyla güçlü filtreleme, sıralama ve gruplandırma özellikleri sağlarlar.  
  
3. Çok az değişiklik olmadan veya hiç değişiklik olmadan diğer veri kaynaklarına taşınabilirler.  
  
 Genel olarak, veriler üzerinde gerçekleştirmek istediğiniz işlem ne kadar karmaşıksa, geleneksel yineleme teknikleri yerine LINQ'u kullanarak o kadar çok fayda elde elabilirsiniz.  
  
 Bu bölümün amacı, LINQ yaklaşımını bazı belirli örneklerle göstermektir. Bu ayrıntılı olması amaçlanmamıştır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [LINQ ve Dizeleri (C#)](./linq-and-strings.md)  
 LINQ dizeleri ve dizeleri koleksiyonları sorgulamak ve dönüştürmek için nasıl kullanılabileceğini açıklar. Ayrıca bu ilkeleri gösteren konulara bağlantılar içerir.  
  
 [LINQ ve Yansıma (C#)](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 LINQ'un yansımayı nasıl kullandığını gösteren bir örneğe bağlantılar.  
  
 [LINQ ve Dosya Dizinleri (C#)](./linq-and-file-directories.md)  
 LINQ'nin dosya sistemleriyle etkileşimde bulunmak için nasıl kullanılabileceğini açıklar. Ayrıca bu kavramları gösteren konulara bağlantılar içerir.  
  
 [LINQ (C#) ile ArrayList nasıl sorgulanır?](./how-to-query-an-arraylist-with-linq.md)  
 C#'da bir ArrayList'in nasıl sorgulanır olduğunu gösterir.  
  
 [LINQ sorguları için özel yöntemler ekleme (C#)](./how-to-add-custom-methods-for-linq-queries.md)  
 Arabirime uzantı yöntemleri ekleyerek LINQ sorguları için kullanabileceğiniz yöntem <xref:System.Collections.Generic.IEnumerable%601> kümesini nasıl genişletebileceğinizi açıklar.  
  
 [Dil-Tümleşik Sorgu (LINQ) (C#)](./index.md)  
 LINQ açıklayan ve sorguları gerçekleştiren kod örnekleri sağlayan konulara bağlantılar sağlar.
