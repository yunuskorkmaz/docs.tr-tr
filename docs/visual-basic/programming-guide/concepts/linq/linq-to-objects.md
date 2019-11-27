---
title: Nesnelere LINQ
ms.date: 07/20/2015
ms.assetid: dd4c30bc-1c9b-4781-a482-b5eada38deb2
ms.openlocfilehash: ef7d6fe232a788ab77661e9c5f313a80df4779b5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354312"
---
# <a name="linq-to-objects-visual-basic"></a>LINQ to Objects (Visual Basic)
"LINQ to Objects" terimi, bir ara LINQ sağlayıcısının veya [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) veya [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)gibi API kullanılmadan doğrudan herhangi bir <xref:System.Collections.IEnumerable> veya <xref:System.Collections.Generic.IEnumerable%601> koleksiyonuyla LINQ sorgularının kullanımını ifade eder. <xref:System.Collections.Generic.List%601>, <xref:System.Array>veya <xref:System.Collections.Generic.Dictionary%602>gibi herhangi bir sıralanabilir koleksiyonu sorgulamak için LINQ 'i kullanabilirsiniz. Koleksiyon Kullanıcı tanımlı olabilir veya bir .NET Framework API 'SI tarafından döndürülen olabilir.  
  
 Temel anlamda, LINQ to Objects koleksiyonlara yönelik yeni bir yaklaşımı temsil eder. Eski şekilde, bir koleksiyondan verilerin nasıl alınacağını belirtilen karmaşık `For Each` döngüleri yazmanız gerekiyordu. LINQ yaklaşımında, almak istediklerinizi açıklayan bildirim kodu yazarsınız.  
  
 Ayrıca, LINQ sorguları geleneksel `For Each` döngülerine göre üç temel avantaj sunar:  
  
1. Özellikle birden fazla koşula filtre uygulanırken bunlar daha kısa ve okunabilir.  
  
2. En az uygulama kodu ile güçlü filtreleme, sıralama ve gruplama özellikleri sağlar.  
  
3. Bunlar, çok az değişiklik yapmadan diğer veri kaynaklarına da eklenebilir.  
  
 Genel olarak, veriler üzerinde gerçekleştirmek istediğiniz işlem daha karmaşıktır, geleneksel yineleme teknikleri yerine LINQ kullanarak bunu daha fazla avantaj elde edersiniz.  
  
 Bu bölümün amacı, bazı Select örnekleri ile LINQ yaklaşımını göstermektir. Bu, kapsamlı olmak üzere tasarlanmamıştır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [LINQ ve dizeler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 LINQ 'in dizeleri ve dize koleksiyonlarını sorgulamak ve dönüştürmek için nasıl kullanılabileceğini açıklar. Ayrıca, bu ilkeleri gösteren konuların bağlantılarını içerir.  
  
 [LINQ ve yansıma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-reflection.md)  
 LINQ 'in yansıma kullanımını gösteren bir örneğe bağlantılar.  
  
 [LINQ ve dosya dizinleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)  
 LINQ 'in dosya sistemleriyle etkileşime geçmek için nasıl kullanılabileceğini açıklar. Ayrıca, bu kavramları gösteren konuların bağlantılarını içerir.  
  
 [Nasıl yapılır: LINQ ile ArrayList 'i sorgulama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)  
 İçinde C#ArrayList 'in nasıl sorgulanacağını gösterir.  
  
 [Nasıl yapılır: LINQ sorguları için özel yöntemler ekleme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)  
 <xref:System.Collections.Generic.IEnumerable%601> arabirimine uzantı yöntemleri ekleyerek, LINQ sorguları için kullanabileceğiniz yöntemlerin kümesinin nasıl genişletileceğini açıklar.  
  
 [Dil ile tümleşik sorgu (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 LINQ ' i açıklayan ve sorguları gerçekleştiren koda örnek sağlayan konulara bağlantılar sağlar.
