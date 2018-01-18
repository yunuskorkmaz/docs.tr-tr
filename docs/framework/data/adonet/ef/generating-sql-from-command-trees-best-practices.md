---
title: "SQL komut ağaçlarını - en iyi uygulamaları oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71ef6a24-4c4f-4254-af3a-ffc0d855b0a8
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d68194ab83a6606337a33668470411ed8b1c6957
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="generating-sql-from-command-trees---best-practices"></a>SQL komut ağaçlarını - en iyi uygulamaları oluşturma
Çıktı sorgu komut ağaçlarını yakından sorguları SQL'de ifade model. Ancak, SQL bir çıkış komut ağacından oluştururken sağlayıcısı yazıcılarına ilişkin ortak bazı zorluklar mevcuttur. Bu konuda bu zorluklar anlatılmaktadır. Sonraki konusundaki örnek sağlayıcısı bu güçlükleri gösterilmektedir.  
  
## <a name="group-dbexpression-nodes-in-a-sql-select-statement"></a>Grup DbExpression düğümlerini SQL SELECT deyimi  
 Tipik bir SQL deyimi aşağıdaki şeklin iç içe geçmiş bir yapı vardır:  
  
```  
SELECT …  
FROM …  
WHERE …  
GROUP BY …  
ORDER BY …  
```  
  
 Bir veya daha fazla yan tümceleri boş olabilir.  İç içe geçmiş bir SELECT deyimi satırları hiçbirinde meydana gelebilir.  
  
 Olası bir sorgu komut ağacı çeviri SQL SELECT deyimi içinde her ilişkisel işleci için bir alt sorgu üretir. Ancak, okunması zor olacaktır gereksiz iç içe alt sorgulara yol açar.  Bazı veri depoları sorgu kötü gerçekleştirebilir.  
  
 Örnek olarak, aşağıdaki sorgu komut ağacı göz önünde bulundurun.  
  
```  
Project (  
a.x,  
   a = Filter(  
      b.y = 5,   
      b = Scan("TableA")  
   )  
)  
```  
  
 Bir verimsiz çevirisini oluşturur:  
  
```  
SELECT a.x  
FROM (   SELECT *  
         FROM TableA as b  
         WHERE b.y = 5) as a  
```  
  
 Her ilişkisel ifadesi düğüm yeni bir SQL SELECT deyimi olacağını unutmayın.  
  
 Bu nedenle, doğruluk korurken tek bir SQL SELECT deyimi içinde mümkün olduğu kadar ifade düğümleri toplamak önemlidir.  
  
 Yukarıda gösterilen örnek için bu tür bir toplama sonucu olacaktır:  
  
```  
SELECT b.x   
FROM TableA as b  
WHERE b.y = 5  
```  
  
## <a name="flatten-joins-in-a-sql-select-statement"></a>Bir SQL SELECT deyimi içinde birleştirmeler düzleştirme  
 Tek bir SQL SELECT deyimine birden çok düğüm toplayarak, bir durumda, tek bir SQL SELECT deyimine birden fazla birleşim ifadelere toplama. DbJoinExpression iki girdi arasında tek bir birleşim temsil eder. Ancak, tek bir SQL SELECT deyimi bir parçası olarak, birden fazla birleşim belirtilebilir. Bu durumda birleştirmeler belirtilen sırayla gerçekleştirilir.  
  
 Sırt birleştirmeler sol, (başka bir birleştirme sol alt olarak görünür birleştirmeler) daha kolay tek bir SQL SELECT deyimine düzleştirilmiş. Örneğin, aşağıdaki sorgu komut ağacı göz önünde bulundurun:  
  
```  
InnerJoin(  
   a = LeftOuterJoin(  
   b = Extent("TableA")  
   c = Extent("TableB")  
   ON b.y = c.x ),  
   d = Extent("TableC")   
   ON a.b.y = d.z  
)  
```  
  
 Bu doğru içine çevrilebilir:  
  
```  
SELECT *  
FROM TableA as b  
LEFT OUTER JOIN TableB as c ON b.y = c.x  
INNER JOIN TableC as d ON b.y = d.z  
```  
  
 Ancak, sol olmayan Sırt birleştirmeler kolayca düzleştirilmiş olamaz ve değil bunları düzleştirmek denemelisiniz. Örneğin, aşağıdaki sorguyu birleşimlerde ağaç komut:  
  
```  
InnerJoin(  
   a = Extent("TableA")   
   b = LeftOuterJoin(  
   c = Extent("TableB")  
   d = Extent("TableC")  
   ON c.y = d.x),  
   ON a.z = b.c.y  
)  
```  
  
 Bir alt sorgu ile SQL SELECT deyimi çevrilmesi.  
  
```  
SELECT *  
FROM TableA as a  
INNER JOIN (SELECT *   
   FROM TableB as c   
   LEFT OUTER JOIN TableC as d  
   ON c.y = d.x) as b  
ON b.y = d.z  
```  
  
## <a name="input-alias-redirecting"></a>Diğer ad yönlendirme giriş  
 Giriş diğer adı yeniden yönlendirme açıklamak için DbFilterExpression, DbProjectExpression, DbCrossJoinExpression, DbJoinExpression, DbSortExpression, toplama, DbApplyExpression, gibi ilişkisel ifadeleri yapısını göz önünde bulundurun ve DbSkipExpression.  
  
 Bu türlerinin her biri bir giriş koleksiyonu açıklayan bir veya daha fazla giriş özellikleri vardır ve her giriş için karşılık gelen bir bağlama değişken her öğe bu giriş, koleksiyon geçişi sırasında temsil etmek için kullanılır. Bağlama değişkeni girişi öğesinde, örneğin bir DbFilterExpression koşulu özelliğinin ya da bir DbProjectExpression projeksiyon özelliği için söz konusu olduğunda kullanılır.  
  
 Daha fazla ilişkisel ifade düğümleri tek bir SQL SELECT deyimine toplayarak ve kullandığı bağlama değişkeni ilişkisel ifade (örneğin bir DbProjectExpression projeksiyon özelliğinin bir parçası) parçası olan bir ifade değerlendirme zaman olabilir birden çok ifade bağlamaları tek bir kapsam için yeniden yönlendirilmesi yaptığınız gibi giriş diğer adı ile aynı olması.  Bu sorun, diğer yeniden adlandırma adlandırılır.  
  
 Bu konudaki ilk örneği göz önünde bulundurun. Naïve çeviri yapılması ve projeksiyon a.x (DbPropertyExpression (x)) çevirme, onu içine çevirmek doğru olup olmadığını `a.x` biz diğer giriş bağlama değişkeni eşleştirmek için "a" olarak olduğundan.  Bununla birlikte, her iki düğüm tek bir SQL SELECT deyimine toplanırken içine aynı DbPropertyExpression çevirmek ihtiyacınız `b.x`giriş diğer adı "b" bırakıldı gibi.  
  
## <a name="join-alias-flattening"></a>Diğer ad düzleştirme katılma  
 Diğer ilişkisel içindeki herhangi bir ifade farklı olarak bir çıkış komut ağacı, her biri girişleri birine karşılık gelen iki sütunlarının oluşan bir satır, bir sonuç türü DbJoinExpression çıkarır. Bir birleştirme sonucu kaynaklanan skaler bir özelliğe erişmek için bir DbPropertyExpresssion yerleşik başka bir DbPropertyExpresssion olur.  
  
 Örnek 2 ve 3 örnekte "b.c.y" "a.b.y" örnek verilebilir. Ancak karşılık gelen SQL deyimlerinde bunlar "b.y" adlandırılır. Bu yeniden yumuşatma diğer birleştirme düzleştirme adı verilir.  
  
## <a name="column-name-and-extent-alias-renaming"></a>Sütun adı ve uzantı Alias yeniden adlandırma  
 Birden fazla olarak girişleri katılan tüm sütunları bir ad çakışması ortaya çıkabilir, numaralandırılırken bir yansıtma ile tamamlanacak bir birleşimi olan bir SQL SELECT sorgu varsa, bir giriş aynı sütun adı olabilir. Çakışma önlemek için sütun için farklı bir ad kullanın.  
  
 Ayrıca, birleştirmeler düzleştirme, katılımcı tabloları (veya alt sorgular) yeniden adlandırılması gerek bu durumda yazılımlarla çakışma diğer adlar, olabilir.  
  
## <a name="avoid-select-"></a>SELECT kaçının *  
 Kullanmayın `SELECT *` temel tablolardan seçin. Depolama modelinde bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] uygulama veritabanı tabloda yer alan bir sütun alt kümesini yalnızca içerebilir. Bu durumda, `SELECT *` hatalı bir sonuç üretebilir. Bunun yerine, katılımcı ifadeler sonuç türü sütun adlarından kullanarak tüm katılımcı sütunları belirtmeniz gerekir.  
  
## <a name="reuse-of-expressions"></a>İfadeler kullanılmasını  
 İfadeler yeniden kullanılabilir geçirilen sorgu komut ağacındaki [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Her bir ifadenin yalnızca bir kez sorgu komutu ağacında görünür varsayalım değil.  
  
## <a name="mapping-primitive-types"></a>İlkel türler eşleme  
 Tüm olası değerler uyacak şekilde, kavramsal (EDM) türleri sağlayıcısı türlerinin eşlerken, geniş türü (Int32) eşlenmesi gerekir. Ayrıca, BLOB türleri gibi birçok işlem için kullanılamaz türler için eşleme kaçının (örneğin, `ntext` içinde [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Üretimi](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
