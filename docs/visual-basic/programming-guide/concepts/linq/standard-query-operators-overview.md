---
title: "Standart sorgu işleçlerine genel bakış (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 302bd39e-2ec1-495b-94bf-37d370d6f05f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3f9ad39b4890455f7d03f0b9bbfc51264d98d56b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="standard-query-operators-overview-visual-basic"></a>Standart sorgu işleçlerine genel bakış (Visual Basic)
*Standart sorgu işleçleri* LINQ düzeni form yöntemleridir. Bu yöntemlerin çoğu bir dizi türü uygulayan bir nesne olduğu sıraları üzerinde çalışması <xref:System.Collections.Generic.IEnumerable%601> arabirimi veya <xref:System.Linq.IQueryable%601> arabirimi. Standart sorgu işleçleri filtreleme, yansıtma, toplama, sıralama ve daha fazlası dahil olmak üzere sorgu özellikleri sağlar.  
  
 LINQ standart sorgu işleçleri, bir tür nesneler üzerinde çalışan iki kümesi vardır <xref:System.Collections.Generic.IEnumerable%601> ve tür nesneler üzerinde çalışan diğer <xref:System.Linq.IQueryable%601>. Her ayarlama yapmak yöntemleri statik üyeleri olan <xref:System.Linq.Enumerable> ve <xref:System.Linq.Queryable> sınıfları, sırasıyla. Olarak tanımlanan *genişletme yöntemleri* üzerinde çalışacağı türü. Başka bir deyişle, bunlar statik yöntem sözdizimi veya örnek yöntemi sözdizimini kullanarak çağrılabilir.  
  
 Ayrıca, çeşitli standart sorgu işleci yöntemler türleri üzerinde tabanlı olanlar dışındaki çalışmayabilir <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Linq.IQueryable%601>. <xref:System.Linq.Enumerable> Türünü tanımlayan iki tür yöntem her ikisi de türündeki nesneler üzerinde çalışan <xref:System.Collections.IEnumerable>. Bu yöntemler <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> ve <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let LINQ desende Sorgulanacak parametreli olmayan veya genel olmayan, bir toplama etkinleştir. Kesin türü belirtilmiş bir nesneler koleksiyonunu oluşturarak bunu. <xref:System.Linq.Queryable> Sınıfı tanımlayan iki benzer yöntemler <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> ve <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, türündeki nesneler üzerinde çalışan <xref:System.Linq.Queryable>.  
  
 Standart sorgu işleçleri, bunlar bir singleton değeri veya değerler dizisini döndürür bağlı olarak, yürütme, zamanlama içinde farklılık gösterir. Tek değer döndürme bu yöntemleri (örneğin, <xref:System.Linq.Enumerable.Average%2A> ve <xref:System.Linq.Enumerable.Sum%2A>) hemen yürütün. Bir dizi döndüren yöntemler sorgu yürütme erteleneceği ve bir numaralandırma nesnesi döndürür.  
  
 Bellek içi koleksiyonlarında, diğer bir deyişle, genişletme bu yöntemleri çalışması yöntemleri durumunda <xref:System.Collections.Generic.IEnumerable%601>, yönteme geçirilen bağımsız değişken döndürülen numaralandırılabilir nesne yakalar. Bu nesne numaralandırılan sorgu işleci mantığı işe ve sorgusu sonuç döndürmedi.  
  
 Buna karşılık, yöntemleri, genişletme <xref:System.Linq.IQueryable%601> herhangi sorgulanırken davranışı kullanılmaz, ancak gerçekleştirilmesi için sorguyu temsil eden bir ifade ağacına derleme. Sorgu işleme kaynak tarafından işlenen <xref:System.Linq.IQueryable%601> nesnesi.  
  
 Sorgu yöntemleri çağrıları rasgele karmaşık hale gelmesine sorgularını sağlayan, tek bir sorguda birbirine zincirlenebilir.  
  
 Aşağıdaki kod örneği, bir dizi hakkında bilgi edinmek için standart sorgu işleçleri'nın nasıl kullanılabileceğini gösterir.  
  
```vb  
Dim sentence = "the quick brown fox jumps over the lazy dog"  
' Split the string into individual words to create a collection.  
Dim words = sentence.Split(" "c)  
  
Dim query = From word In words   
            Group word.ToUpper() By word.Length Into gr = Group   
            Order By Length _  
            Select Length, GroupedWords = gr  
  
Dim output As New System.Text.StringBuilder  
For Each obj In query  
    output.AppendLine(String.Format("Words of length {0}:", obj.Length))  
    For Each word As String In obj.GroupedWords  
        output.AppendLine(word)  
    Next  
Next  
  
'Display the output  
MsgBox(output.ToString())  
  
' This code example produces the following output:  
'  
' Words of length 3:  
' THE  
' FOX  
' THE  
' DOG  
' Words of length 4:  
' OVER  
' LAZY  
' Words of length 5:  
' QUICK  
' BROWN  
' JUMPS   
```  
  
## <a name="query-expression-syntax"></a>Sorgu ifade sözdizimi  
 Bazı daha sık kullanılan standart sorgu işleçleri bunları parçası olarak çağrılacak etkinleştiren C# ve Visual Basic dil anahtar sözcüğü sözdizimini adanmış bir *sorgu* *ifade*. Anahtar sözcükler ve bunların karşılık gelen sözdizimleri ayrılmış standart sorgu işleçleri hakkında daha fazla bilgi için bkz: [standart sorgu işleçleri (Visual Basic) için sorgu ifade sözdizimi](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).  
  
## <a name="extending-the-standard-query-operators"></a>Standart sorgu işleçleri genişletme  
 Standart sorgu işleçleri kümesi hedef etki alanına veya teknoloji için uygun olan oluşturma etki alanına özgü yöntemlerle genişletebilirsiniz. Standart sorgu işleçleri, uzak değerlendirme, sorgu çeviri ve en iyi duruma getirme gibi ek hizmetleri sağlayan kendi uygulamaları ile de değiştirebilirsiniz. Bkz: <xref:System.Linq.Enumerable.AsEnumerable%2A> bir örnek.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Aşağıdaki bağlantılar işlevselliğine bağlı çeşitli standart sorgu işleçleri hakkında ek bilgiler sağlayan konulara götürür.  
  
 [Verileri sıralama](../../../../visual-basic/programming-guide/concepts/linq/sorting-data.md)  
  
 [Ayarlama işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/set-operations.md)  
  
 [Filtre veri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/filtering-data.md)  
  
 [Niceleyici işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)  
  
 [Projeksiyon işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)  
  
 [Bölümleme veri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/partitioning-data.md)  
  
 [Birleştirme işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md)  
  
 [Gruplandırma veri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/grouping-data.md)  
  
 [Oluşturma işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/generation-operations.md)  
  
 [Eşitlik işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/equality-operations.md)  
  
 [Öğe işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/element-operations.md)  
  
 [Dönüştürme veri türleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)  
  
 [Birleştirme işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/concatenation-operations.md)  
  
 [Toplama işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Linq.Enumerable>  
 <xref:System.Linq.Queryable>  
 [Lınq'ye giriş (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)  
 [Standart sorgu işleçleri (Visual Basic) için sorgu ifade sözdizimi](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)  
 [Standart sorgu işleçleri (Visual Basic) yürütme yöntemine göre sınıflandırılması](../../../../visual-basic/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)  
 [Genişletme yöntemleri](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
