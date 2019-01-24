---
title: SQL komut ağaçlarından - en iyi uygulamalar oluşturma
ms.date: 03/30/2017
ms.assetid: 71ef6a24-4c4f-4254-af3a-ffc0d855b0a8
ms.openlocfilehash: 476a2b9d6d3a8efb6094afce0143abed765bdb48
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659101"
---
# <a name="generating-sql-from-command-trees---best-practices"></a>SQL komut ağaçlarından - en iyi uygulamalar oluşturma
Çıkış sorgu komut ağaçlarını yakından sorguları SQL ifade model. Ancak, SQL bir çıkış komut ağacından oluşturulurken bazı sık karşılaşılan zorluklar sağlayıcısı yazıcılar için vardır. Bu konuda, bu sorunları ele alınmıştır. Sonraki konu başlığında örnek sağlayıcısı bu sorunları gidermek üzere nasıl gösterir.  
  
## <a name="group-dbexpression-nodes-in-a-sql-select-statement"></a>Bir SQL SELECT deyimi içinde Dbexpression'dan düğümleri gruplandırma  
 Aşağıdaki şekil, iç içe bir yapı normal bir SQL deyimi vardır:  
  
```  
SELECT …  
FROM …  
WHERE …  
GROUP BY …  
ORDER BY …  
```  
  
 Bir veya daha fazla yan tümceleri boş olabilir.  İç içe geçmiş bir SELECT deyimi, tüm satırların oluşabilir.  
  
 Bir SQL SELECT deyimi sorgu komut ağacı, olası bir çevirisini her ilişkisel işleç için bir alt sorgu oluşturur. Ancak, okunması zor olabilecek gereksiz iç içe geçmiş alt sorgulara neden.  Bazı veri depoları sorgu sonlanmayacağından.  
  
 Örneğin, aşağıdaki sorgu komut ağacı göz önünde bulundurun.  
  
```  
Project (  
a.x,  
   a = Filter(  
      b.y = 5,   
      b = Scan("TableA")  
   )  
)  
```  
  
 Verimsiz bir çeviri oluşturur:  
  
```  
SELECT a.x  
FROM (   SELECT *  
         FROM TableA as b  
         WHERE b.y = 5) as a  
```  
  
 Her ilişkisel ifade düğüme yeni bir SQL SELECT deyimi olacağını unutmayın.  
  
 Bu nedenle, doğruluk korurken tek bir SQL SELECT deyimi içinde mümkün olduğunca çok ifade düğümleri toplamak önemlidir.  
  
 Yukarıda verilen örneği için bu tür bir toplama sonucu şöyle olacaktır:  
  
```  
SELECT b.x   
FROM TableA as b  
WHERE b.y = 5  
```  
  
## <a name="flatten-joins-in-a-sql-select-statement"></a>Bir SQL SELECT deyimi birleşimlerde düzleştirme  
 Tek bir SQL SELECT deyimi içinde birden çok düğüm toplayarak bir kullanım durumu, tek bir SQL SELECT deyimi birden fazla birleştirme ifadelere yeniden hesaplanır. İki girdi arasında tek bir birleştirme DbJoinExpression'temsil eder. Ancak, tek bir SQL SELECT deyimi bir parçası olarak, birden fazla birleştirme belirtilebilir. Bu durumda birleştirmeler belirtilen sıraya göre gerçekleştirilir.  
  
 Omurgası birleştirmeler sol, (başka bir birleşimin sol alt olarak görünen JOIN), daha kolay tek bir SQL SELECT deyimi içinde düzleştirilebilir. Örneğin, aşağıdaki sorgu komut ağacı göz önünde bulundurun:  
  
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
  
 Ancak, sol olmayan Sırt birleştirmeler kolayca düzleştirilmiş kullanılamaz ve bunları düzleştirilecek denememelisiniz. Örneğin, aşağıdaki sorguyu birleşimlerde ağaç komut:  
  
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
  
 Bir alt sorgusu ile SQL SELECT deyimi çevrilmesi.  
  
```  
SELECT *  
FROM TableA as a  
INNER JOIN (SELECT *   
   FROM TableB as c   
   LEFT OUTER JOIN TableC as d  
   ON c.y = d.x) as b  
ON b.y = d.z  
```  
  
## <a name="input-alias-redirecting"></a>Giriş diğer adı yeniden yönlendirme  
 Giriş diğer adı yeniden yönlendirme açıklamak için DbFilterExpression, DbProjectExpression, DbCrossJoinExpression, DbJoinExpression, DbSortExpression, DbGroupByExpression, DbApplyExpression, ilişkisel ifadelerin yapısı göz önünde bulundurun ve DbSkipExpression.  
  
 Bu tür her bir giriş koleksiyonu tanımlayan bir veya daha fazla giriş özelliği vardır ve her bir girişe karşılık gelen bir bağlama değişken her giriş öğesinin bir koleksiyon geçişi sırasında temsil etmek için kullanılır. Bağlama değişkeni girişi öğesinde, örneğin bir DbFilterExpression koşul özelliğini ya da projeksiyon özelliği bir DbProjectExpression söz konusu olduğunda kullanılır.  
  
 Daha fazla ilişkisel ifade düğümleri tek bir SQL SELECT deyimi içinde toplama ve onu kullanan bağlama değişkeni bir ilişkisel ifade kullanıldı (örneğin bir DbProjectExpression yansıtma özelliğinin bir parçası) parçası olan bir ifade değerlendirme zaman olabilir birden fazla ifade bağlamaları tek bir ölçüde yönlendirilmesi yaptığınız gibi giriş diğer adı ile aynı olmaması.  Bu sorun, diğer adını yeniden adlandırma adı verilir.  
  
 Bu konudaki ilk örnek göz önünde bulundurun. Naïve çeviri yapılması ve projeksiyon a.x (DbPropertyExpression (bir, bir x)) çevirme, bunun içine çevirmek doğru olup olmadığını `a.x` çünkü diğer adlı giriş bağlama değişkeni eşleştirmek için "a" olarak sahip olabiliyoruz.  Ancak, her iki düğüm ile tek bir SQL SELECT deyimi toplanırken içine aynı DbPropertyExpression çevirmek ihtiyacınız `b.x`, "b" ile diğer adlı giriş süredir.  
  
## <a name="join-alias-flattening"></a>Diğer ad düzleştirme katılın  
 Diğer ilişkisel içindeki herhangi bir ifade bir çıktı komut ağacı, her biri girişleri birine karşılık gelen iki sütunlardan oluşan bir satır olduğundan bir sonuç türü DbJoinExpression çıkarır. Birleştirme sonucu kaynaklanan bir skaler özelliğe erişmek için yerleşik bir DbPropertyExpresssion başka bir DbPropertyExpresssion olur.  
  
 Örnek 2 ve 3. örnek "b.c.y" içinde "a.b.y" örnek olarak verilebilir. Ancak karşılık gelen SQL deyimlerinde bunlar "b.y" adlandırılır. Bu yeniden yumuşatma, diğer ad birleştirme düzleştirme çağrılır.  
  
## <a name="column-name-and-extent-alias-renaming"></a>Sütun adı ve uzantısı diğer adını yeniden adlandırma  
 Girişleri katılan tüm sütunları bir ad çakışması oluşabilir, listelenirken bir projeksiyon ile tamamlanması bir birleşimi olan bir SQL SELECT sorgu varsa, bir giriş olarak birden fazla aynı sütun adı sahip olabilir. Çakışma önlemek için sütun için farklı bir ad kullanın.  
  
 Ayrıca, birleşimler düzleştirme, tablo (veya alt sorgular) adlandırılması gerek bu durum çakışan diğer adlar, olabilir.  
  
## <a name="avoid-select-"></a>SELECT önlemek *  
 Kullanmayın `SELECT *` temel tabloları seçin. Depolama modelinde bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] uygulama yalnızca veritabanı tablodaki sütunların bir alt kümesini içerebilir. Bu durumda, `SELECT *` hatalı bir sonuç üretebilir. Bunun yerine, bir katılımcı ifadenin sonuç türü sütun adları kullanarak katılan tüm sütunları belirtmeniz gerekir.  
  
## <a name="reuse-of-expressions"></a>Yeniden ifade  
 İfadeleri yeniden geçirilen sorgu komut ağacı [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Her bir ifade yalnızca bir kez sorgu komutu ağaçta görünür varsaymayın.  
  
## <a name="mapping-primitive-types"></a>Eşleme ilkel türler  
 Tüm olası değerler uyacak şekilde, kavramsal (EDM) tür sağlayıcısı türleri eşlerken geniş türü (Int32) eşlenmesi gerekir. Ayrıca, BLOB türleri gibi birçok işlem için kullanılamaz türleriyle eşleme önlemek (örneğin, `ntext` SQL Server).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [SQL Üretimi](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
