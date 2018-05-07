---
title: LINQ to nesneler (Visual Basic)
ms.date: 07/20/2015
ms.assetid: dd4c30bc-1c9b-4781-a482-b5eada38deb2
ms.openlocfilehash: f04ccc3d8541c1d4327ff9356fe7c4105681bd0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="linq-to-objects-visual-basic"></a>LINQ to nesneler (Visual Basic)
"Nesnelere LINQ" başvuruyor LINQ kullanımını terim tüm sorgular <xref:System.Collections.IEnumerable> veya <xref:System.Collections.Generic.IEnumerable%601> koleksiyonu veya bir ara LINQ sağlayıcısı gibi API kullanmadan, doğrudan [LINQ-SQL](../../../../framework/data/adonet/sql/linq/index.md) veya [LINQ-XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13). LINQ numaralandırılabilir tüm koleksiyonlar gibi sorgulamak için kullanabileceğiniz <xref:System.Collections.Generic.List%601>, <xref:System.Array>, veya <xref:System.Collections.Generic.Dictionary%602>. Koleksiyon, kullanıcı tanımlı olabilir veya bir .NET Framework API tarafından döndürülen.  
  
 Bir temel anlamda nesnelere LINQ koleksiyonlar için yeni bir yaklaşım temsil eder. Karmaşık yazma gerekiyordu eski biçimde `For Each` koleksiyondan verileri almak üzere nasıl belirtilen döngüler. LINQ yaklaşımda, almak istediğiniz açıklar bildirim temelli bir kod yazın.  
  
 Ayrıca, üç ana avantajları geleneksel LINQ sorgularını teklif `For Each` döngüler:  
  
1.  Bunlar özellikle birden çok koşul filtre uygularken daha kısa ve okunabilir,.  
  
2.  Güçlü filtreleme, sıralama ve uygulama kodu en az özellikleriyle gruplandırma sağlarlar.  
  
3.  Bunlar çok az kayıpla veya hiç değişiklik ile diğer veri kaynakları için bağlantı noktası kurulmuş.  
  
 Genel olarak, daha karmaşık hayata geçirmek yerine geleneksel yineleme teknikleri LINQ kullanarak daha fazla avantajı, veriler üzerinde gerçekleştirmek istediğiniz işlem.  
  
 Bu bölümün amacı select bazı örnekler LINQ yaklaşımda göstermektir. Kapsamlı olması amaçlanmamıştır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [LINQ ve dizeler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 LINQ Sorgu ve dizeler ve koleksiyonları dizeleri dönüştürmek için nasıl kullanılabileceği açıklanır. Ayrıca bu ilkeler göstermek konulara bağlantılar içerir.  
  
 [LINQ ve yansıma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-reflection.md)  
 LINQ yansıma nasıl kullandığını gösteren bir örnek bağlantılar.  
  
 [LINQ ve dosya dizinleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)  
 LINQ dosya sistemleri ile etkileşim kurmak için nasıl kullanılabileceği açıklanır. Ayrıca bu kavramları göstermeye konulara bağlantılar içerir.  
  
 [Nasıl yapılır: LINQ (Visual Basic) ile ArrayList sorgulama](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)  
 C# ArrayList sorgulama gösterir.  
  
 [Nasıl yapılır: özel yöntemler ekleme LINQ sorgularını (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)  
 İçin genişletme yöntemleri ekleyerek LINQ sorguları için kullanabileceğiniz yöntemler kümesi genişletmek açıklanmaktadır <xref:System.Collections.Generic.IEnumerable%601> arabirimi.  
  
 [Dil ile tümleşik sorgu (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 LINQ açıklayan ve sorgular gerçekleştirebilir kod örnekleri sağlayın konulara bağlantılar sağlar.
