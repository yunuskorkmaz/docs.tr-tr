---
title: (C#) XML işlevsel dönüşümü
ms.date: 07/20/2015
ms.assetid: 0ccb9251-38d7-44e3-9b84-1b5fe25e4b59
ms.openlocfilehash: 75ad909994d75387648dbfa72f827cf63b85739e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643048"
---
# <a name="functional-transformation-of-xml-c"></a>(C#) XML işlevsel dönüşümü
Bu konu, XML belgelerinin sınırlandırması saf işlevsel dönüşüm yaklaşımını ele alır ve yordam yaklaşımından ile karşılaştırır.  
  
## <a name="modifying-an-xml-document"></a>Bir XML belgesi değiştirme  
 Bir XML programcı için en yaygın görevlerden biri XML bir şekilden diğerine dönüştürüyor. Bir XML belgesi şeklini aşağıdakileri içeren belge yapısı şöyledir:  
  
-   Belgeye göre ifade hiyerarşisi.  
  
-   Öğe ve öznitelik adları.  
  
-   Öznitelikleri ve öğeleri veri türleri.  
  
 Genel olarak, XML bir şekle dönüştürme en etkili, saf işlev dönüşümün yaklaşımdır. Bu yaklaşımda, birincil Programcı görev tüm XML belgesi (veya bir veya daha fazla kesinlikle tanımlanmış düğümleri) uygulanan bir dönüştürme oluşturmaktır. İşlevsel dönüşümü gerçekleşir tartışmaya kolay (programcı yaklaşım ile ilgili bilgi sahibi olduktan sonra) kodu için en Bakımı yapılabilir kodu üretir ve genellikle daha alternatif yaklaşımlar compact olur.  
  
### <a name="xml-functional-transformational-technologies"></a>XML işlevsel Dönüşümsel teknolojiler  
 Microsoft XML belgeleri kullanmak için iki işlevsel dönüşüm teknolojileri sunar: XSLT ve LINQ to XML. XSLT içerisinde desteklendiği <xref:System.Xml.Xsl> ad alanı yönetilen ve yerel MSXML COM uygulama. XSLT XML belgeleri yönetmek için güçlü bir teknoloji olsa da, bir özel etki alanı, XSLT dili ve destekleyici API'lerini uzmanlığı gerektirir.  
  
 LINQ to XML, C# veya Visual Basic kodu içinde bir ifadesel ve güçlü şekilde kod saf işlevsel dönüşümlere için gerekli araçları sağlar. Örneğin, birçok LINQ örnek XML belgeleri için saf işlevsel bir yaklaşım kullanın. Ayrıca, [Öğreticisi: WordprocessingML belgesindeki içeriği düzenleme (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) öğreticide kullanıyoruz LINQ to XML işlevsel bir yaklaşım bir Microsoft Word belgesi bilgilerini işlemek için.  
  
 Bir daha kapsamlı bir karşılaştırması LINQ to XML için diğer Microsoft XML teknolojileriyle bkz [LINQ to XML ile. Diğer XML teknolojileri](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md).  
  
 Kaynak belge düzensiz bir yapısı varsa XSLT belge odaklı dönüştürmeleri için önerilen araçtır. Ancak LINQ to XML belge odaklı dönüşümleri gerçekleştirebilirsiniz. Daha fazla bilgi için [nasıl yapılır: LINQ to XML ağaçlarını XSLT stilindeki dönüştürmek için ek açıklamalarını kullanma (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Giriş saf işlevsel dönüşümlere (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [Öğretici: WordprocessingML belgesindeki içeriği düzenleme (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
- [LINQ to XML ile Diğer XML Teknolojileri Karşılaştırması](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)
