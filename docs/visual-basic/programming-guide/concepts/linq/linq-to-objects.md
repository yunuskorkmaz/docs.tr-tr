---
title: Nesnelere LINQ
ms.date: 07/20/2015
ms.assetid: dd4c30bc-1c9b-4781-a482-b5eada38deb2
ms.openlocfilehash: cb277a255151bf7db9d0fb0a50605ee07ba1423f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075297"
---
# <a name="linq-to-objects-visual-basic"></a>LINQ to Objects (Visual Basic)

"LINQ to Objects" terimi, <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> bır ara LINQ sağlayıcısı veya [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) veya [LINQ to XML](../../../../standard/linq/linq-xml-overview.md)gibi API KULLANıLMADAN doğrudan herhangi bir veya koleksiyonuyla LINQ sorgularının kullanımını ifade eder. , Veya gibi tüm sıralanabilir koleksiyonları sorgulamak için LINQ kullanabilirsiniz <xref:System.Collections.Generic.List%601> <xref:System.Array> <xref:System.Collections.Generic.Dictionary%602> . Koleksiyon Kullanıcı tanımlı olabilir veya bir .NET Framework API 'SI tarafından döndürülen olabilir.  
  
 Temel anlamda, LINQ to Objects koleksiyonlara yönelik yeni bir yaklaşımı temsil eder. Eski şekilde, `For Each` bir koleksiyondan verilerin nasıl alınacağını belirtilen karmaşık döngüler yazmanız gerekiyordu. LINQ yaklaşımında, almak istediklerinizi açıklayan bildirim kodu yazarsınız.  
  
 Ayrıca, LINQ sorguları geleneksel Döngülerde üç temel avantaj sunar `For Each` :  
  
1. Özellikle birden fazla koşula filtre uygulanırken bunlar daha kısa ve okunabilir.  
  
2. En az uygulama kodu ile güçlü filtreleme, sıralama ve gruplama özellikleri sağlar.  
  
3. Bunlar, çok az değişiklik yapmadan diğer veri kaynaklarına da eklenebilir.  
  
 Genel olarak, veriler üzerinde gerçekleştirmek istediğiniz işlem daha karmaşıktır, geleneksel yineleme teknikleri yerine LINQ kullanarak bunu daha fazla avantaj elde edersiniz.  
  
 Bu bölümün amacı, bazı Select örnekleri ile LINQ yaklaşımını göstermektir. Bu, kapsamlı olmak üzere tasarlanmamıştır.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [LINQ ve dizeler (Visual Basic)](linq-and-strings.md)  
 LINQ 'in dizeleri ve dize koleksiyonlarını sorgulamak ve dönüştürmek için nasıl kullanılabileceğini açıklar. Ayrıca, bu ilkeleri gösteren konuların bağlantılarını içerir.  
  
 [LINQ ve yansıma (Visual Basic)](linq-and-reflection.md)  
 LINQ 'in yansıma kullanımını gösteren bir örneğe bağlantılar.  
  
 [LINQ ve dosya dizinleri (Visual Basic)](linq-and-file-directories.md)  
 LINQ 'in dosya sistemleriyle etkileşime geçmek için nasıl kullanılabileceğini açıklar. Ayrıca, bu kavramları gösteren konuların bağlantılarını içerir.  
  
 [Nasıl yapılır: LINQ ile ArrayList 'i sorgulama (Visual Basic)](how-to-query-an-arraylist-with-linq.md)  
 C# içinde ArrayList 'in nasıl sorgulanacağını gösterir.  
  
 [Nasıl yapılır: LINQ sorguları için özel yöntemler ekleme (Visual Basic)](how-to-add-custom-methods-for-linq-queries.md)  
 Arabirime uzantı yöntemleri ekleyerek, LINQ sorguları için kullanabileceğiniz yöntemlerin kümesinin nasıl genişletileceğini açıklar <xref:System.Collections.Generic.IEnumerable%601> .  
  
 [Dil ile tümleşik sorgu (LINQ) (Visual Basic)](index.md)  
 LINQ ' i açıklayan ve sorguları gerçekleştiren koda örnek sağlayan konulara bağlantılar sağlar.
