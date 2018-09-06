---
title: LINQ to Objects'in (C#)
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: 19dd15fdd7e818e0619647205f2369a55f3bc2b0
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44039244"
---
# <a name="linq-to-objects-c"></a>LINQ to Objects'in (C#)
Tüm sorgular "LINQ için nesneler" LINQ kullanımı ifade eder <xref:System.Collections.IEnumerable> veya <xref:System.Collections.Generic.IEnumerable%601> koleksiyon Ara LINQ sağlayıcısı veya API gibi kullanmadan, doğrudan [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md) veya [LINQ to XML](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md). LINQ gibi herhangi bir sıralanabilir koleksiyonu sorgulamak için kullanabileceğiniz <xref:System.Collections.Generic.List%601>, <xref:System.Array>, veya <xref:System.Collections.Generic.Dictionary%602>. Koleksiyon veya bir .NET Framework API tarafından döndürülen kullanıcı tanımlı olabilir.  
  
 Temel bir anlamda, LINQ to Objects'in koleksiyonları yeni bir yaklaşımı temsil eder. Karmaşık yazmanız gerekirdi eski biçimde `foreach` belirtilen bir koleksiyondaki verileri alma döngüleri. LINQ yaklaşımda almak istediğiniz açıklayan bildirim temelli bir kod yazın.  
  
 Ayrıca, LINQ sorguları üç ana avantajları geleneksel teklif `foreach` döngüleri:  
  
1.  Özellikle birden çok koşulu filtrelerken daha kısa süren ve okunabilir, değildirler.  
  
2.  Güçlü filtreleme, sıralama ve Gruplama yetenekler uygulama kodu en az sağlarlar.  
  
3.  Bunlar çok az kayıpla veya hiç değişiklik diğer veri kaynaklarıyla için unity'nin.  
  
 Genel olarak, daha karmaşık fark geleneksel yineleme teknikleri yerine LINQ kullanarak daha fazla avantaj, verilerle ilgili gerçekleştirmek istediğiniz işlem.  
  
 Bu bölümün amacı, select bazı örnekler LINQ yaklaşımıyla göstermektir. Testin daha kapsamlı olmasını sağlamak için tasarlanmamıştır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [LINQ ve dizeler (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
 LINQ Sorgu dizeleri ve dizelerden oluşan koleksiyonları dönüştürmek için nasıl kullanılabileceğini açıklar. Ayrıca, bu ilkeyi gösteren konulara bağlantılar içerir.  
  
 [LINQ ve yansıma (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-reflection.md)  
 LINQ yansıma nasıl kullandığını gösteren bir örnek bağlar.  
  
 [LINQ ve dosya dizinleri (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)  
 Dosya sistemleri ile etkileşimde bulunmak için LINQ'ın nasıl kullanılabileceğini açıklar. Ayrıca bu kavramları göstermeye konulara bağlantılar içerir.  
  
 [Nasıl yapılır: LINQ (C#) ile ArrayList sorgulama](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)  
 C# ArrayList sorgulama işlemi gösterilmektedir.  
  
 [Nasıl yapılır: özel yöntemler LINQ sorguları için (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)  
 İçin genişletme yöntemleri ekleyerek LINQ sorguları için kullanabileceğiniz yöntemler kümesi genişletmek açıklanmaktadır <xref:System.Collections.Generic.IEnumerable%601> arabirimi.  
  
 [Dil ile tümleşik sorgu (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)  
 LINQ açıklamak ve sorguları gerçekleştirme kod örnekleri sağlayan konulara bağlantılar sağlar.
