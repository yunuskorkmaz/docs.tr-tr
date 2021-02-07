---
description: 'Hakkında daha fazla bilgi edinin: (Entity SQL)'
title: Beğen (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8300e6d2-875b-481e-9ef4-e1e7c12d46fa
ms.openlocfilehash: 932ddfcf8a8ab8b32f6a097f92ff2979e32239da
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748277"
---
# <a name="like-entity-sql"></a>Beğen (Entity SQL)

Belirli bir karakterin `String` belirtilen bir Düzenle eşleşip eşleşmediğini belirler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
match [NOT] LIKE pattern [ESCAPE escape]  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `match`  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Olarak değerlendirilen bir ifade `String` .  
  
 `pattern`  
 Belirtilen ile eşleşecek bir model `String` .  
  
 `escape`  
 Kaçış karakteri.  
  
 NOT  
 Bunun sonucunu, ÖRNEĞIN, Değillenmiş olduğunu belirtir.  
  
## <a name="return-value"></a>Dönüş Değeri  

 `true` , `string` düzeniyle eşleşiyorsa, tersi durumda `false` .  
  
## <a name="remarks"></a>Açıklamalar  

 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] LIKE işlecini kullanan ifadeler, filtre ölçütü olarak eşitlik kullanan ifadelerle aynı şekilde değerlendirilir. Ancak, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] LIKE işlecini kullanan ifadeler hem değişmez değerleri hem de joker karakterleri içerebilir.  
  
 Aşağıdaki tabloda, deseninin sözdizimi açıklanmaktadır `string` .  
  
|Joker Karakter|Açıklama|Örnek|  
|------------------------|-----------------|-------------|  
|%|`string`Sıfır veya daha fazla karakterden oluşabilir.|`title like '%computer%'` Başlığın herhangi bir yerindeki kelimeyle tüm başlıkları bulur `"computer"` .|  
|_ (alt çizgi)|Herhangi bir tek karakter.|`firstname like '_ean'` "DEA veya kemal gibi" ile biten dört harfli ilk adı bulur `"ean` .|  
|[ ]|Belirtilen aralıktaki ([a-f]) veya ayarlanan ([abcdef]) herhangi bir tek karakter.|`lastname like '[C-P]arsen'` "Arsen" ile biten son adları bulur ve, Carsen veya Larsen gibi C ile P arasında tek bir karakterle başlar.|  
|[^]|Belirtilen aralıkta ([^ a-f]) veya set ([^ abcdef]) içinde olmayan tek bir karakter.|`lastname like 'de[^l]%'` "de" ile başlayan ve aşağıdaki harfle "l" dahil olmayan tüm son adları bulur.|  
  
> [!NOTE]
> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]LIKE işleci ve kaçış yan tümcesi `System.DateTime` veya `System.Guid` değerlerine uygulanamaz.  
  
 Benzer şekilde, ASCII stili eşleştirmeyi ve Unicode düzeniyle eşleştirmeyi destekler. Tüm parametreler ASCII karakterleri olduğunda, ASCII stili eşleştirmesi gerçekleştirilir. Bir veya daha fazla bağımsız değişken Unicode ise, tüm bağımsız değişkenler Unicode 'a dönüştürülür ve Unicode deseninin eşleşmesi gerçekleştirilir. Benzer bir şekilde Unicode kullandığınızda, sondaki boşluklar önemlidir; Ancak Unicode olmayan, sondaki boşluklar önemli değildir. Öğesinin model dize sözdizimi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Transact-SQL ile aynıdır.  
  
 Bir desenler, düzenli karakter ve joker karakterler içerebilir. Model eşleştirme sırasında, normal karakterlerin karakter içinde belirtilen karakterlerle tam olarak eşleşmesi gerekir `string` . Ancak, joker karakterler karakter dizesinin rastgele parçaları ile eşleştirilebilir. Joker karakterlerle kullanıldığında, LIKE işleci = ve! = dize karşılaştırma işleçlerinden daha esnektir.  
  
> [!NOTE]
> Belirli bir sağlayıcıyı hedefliyorsanız sağlayıcıya özgü uzantıları kullanabilirsiniz. Ancak, bu tür yapılar diğer sağlayıcılar tarafından farklı şekilde değerlendirilemeyebilir. SqlServer, ilk ve son arasında tam olarak bir karakter eşleştiği ve ikinci tam olarak ilk ve son arasında olmayan bir karakterle eşleştiği [First-Last] ve [^ First-Last] desenlerini destekler.  
  
### <a name="escape"></a>Esc  

 KAÇıŞ yan tümcesini kullanarak, önceki bölümde yer alan tabloda açıklanan özel Joker karakterlerden birini veya birkaçını içeren karakter dizelerini arayabilirsiniz. Örneğin, başlıkta "%100%" sabit değerini içeren ve bu belgelerin tümünü aramak istediğiniz birçok belge olduğunu varsayalım. Yüzde (%) nedeniyle karakter bir joker karakterdir, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] aramayı başarıyla yürütmek için kaçış yan tümcesini kullanarak bunu atlamanız gerekir. Aşağıda bu filtrenin bir örneği verilmiştir.  
  
```sql  
"title like '%100!%%' escape '!'"  
```  
  
 Bu arama ifadesinde, yüzde joker karakteri (%) ünlem işareti karakteri (!) hemen sonrasında, joker karakter yerine değişmez değer olarak değerlendirilir. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Joker karakterler ve köşeli ayraç () karakterleri dışında herhangi bir karakteri çıkış karakteri olarak kullanabilirsiniz `[ ]` . Önceki örnekte, ünlem işareti (!) karakteri kaçış karakteridir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki iki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, belirli bir karakter dizesinin belirtilen bir Düzenle eşleşip eşleşmediğini anlamak IÇIN LIKE ve kaçış işleçlerini kullanır. İlk sorgu, `Name` karakterlerle başlayan öğesini arar `Down_` . Alt çizgi ( `_` ) bir joker karakter olduğundan bu sorgu kaçış seçeneğini kullanır. KAÇıŞ seçeneğini belirtmeden, sorgu, `Name` `Down` ardından alt çizgi karakteri dışında bir tek karakter gelen kelimeyle başlayan tüm değerleri arar. Sorgular AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecutePrimitiveTypeQuery` :  
  
 [!code-sql[DP EntityServices Concepts#LIKE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#like)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
