---
title: Beğen (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8300e6d2-875b-481e-9ef4-e1e7c12d46fa
ms.openlocfilehash: fbe27f6e25c9d69f092a060fa2c3fbf0abc93318
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250508"
---
# <a name="like-entity-sql"></a>Beğen (Entity SQL)
Belirli bir karakterin `String` belirtilen bir Düzenle eşleşip eşleşmediğini belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
match [NOT] LIKE pattern [ESCAPE escape]  
```  
  
## <a name="arguments"></a>Arguments  
 `match`  
 Olarak değerlendirilen bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ifade. `String`  
  
 `pattern`  
 Belirtilen `String`ile eşleşecek bir model.  
  
 `escape`  
 Kaçış karakteri.  
  
 DEĞİL  
 Bunun sonucunu, ÖRNEĞIN, Değillenmiş olduğunu belirtir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true`, `string` düzeniyle eşleşiyorsa, `false`tersi durumda.  
  
## <a name="remarks"></a>Açıklamalar  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]LIKE işlecini kullanan ifadeler, filtre ölçütü olarak eşitlik kullanan ifadelerle aynı şekilde değerlendirilir. Ancak, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] LIKE işlecini kullanan ifadeler hem değişmez değerleri hem de joker karakterleri içerebilir.  
  
 Aşağıdaki tabloda, deseninin `string`sözdizimi açıklanmaktadır.  
  
|Joker Karakter|Açıklama|Örnek|  
|------------------------|-----------------|-------------|  
|%|`string` Sıfır veya daha fazla karakterden oluşabilir.|`title like '%computer%'`Başlığın herhangi bir yerindeki kelimeyle `"computer"` tüm başlıkları bulur.|  
|_ (alt çizgi)|Herhangi bir tek karakter.|`firstname like '_ean'`"DEA veya kemal gibi" ile `"ean`biten dört harfli ilk adı bulur.|  
|[ ]|Belirtilen aralıktaki ([a-f]) veya ayarlanan ([abcdef]) herhangi bir tek karakter.|`lastname like '[C-P]arsen'`"Arsen" ile biten son adları bulur ve, Carsen veya Larsen gibi C ile P arasında tek bir karakterle başlar.|  
|[^]|Belirtilen aralıkta ([^ a-f]) veya set ([^ abcdef]) içinde olmayan tek bir karakter.|`lastname like 'de[^l]%'`"de" ile başlayan ve aşağıdaki harfle "l" dahil olmayan tüm son adları bulur.|  
  
> [!NOTE]
> LIKE işleci ve kaçış yan tümcesi `System.DateTime` veya `System.Guid` değerlerine uygulanamaz. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]  
  
 Benzer şekilde, ASCII stili eşleştirmeyi ve Unicode düzeniyle eşleştirmeyi destekler. Tüm parametreler ASCII karakterleri olduğunda, ASCII stili eşleştirmesi gerçekleştirilir. Bir veya daha fazla bağımsız değişken Unicode ise, tüm bağımsız değişkenler Unicode 'a dönüştürülür ve Unicode deseninin eşleşmesi gerçekleştirilir. Benzer bir şekilde Unicode kullandığınızda, sondaki boşluklar önemlidir; Ancak Unicode olmayan, sondaki boşluklar önemli değildir. Öğesinin [!INCLUDE[esql](../../../../../../includes/esql-md.md)] model dize sözdizimi Transact-SQL ile aynıdır.  
  
 Bir desenler, düzenli karakter ve joker karakterler içerebilir. Model eşleştirme sırasında, normal karakterlerin karakter `string`içinde belirtilen karakterlerle tam olarak eşleşmesi gerekir. Ancak, joker karakterler karakter dizesinin rastgele parçaları ile eşleştirilebilir. Joker karakterlerle kullanıldığında, LIKE işleci = ve! = dize karşılaştırma işleçlerinden daha esnektir.  
  
> [!NOTE]
> Belirli bir sağlayıcıyı hedefliyorsanız sağlayıcıya özgü uzantıları kullanabilirsiniz. Ancak, bu tür yapılar diğer sağlayıcılar tarafından farklı şekilde değerlendirilemeyebilir. SqlServer, ilk ve son arasında tam olarak bir karakter eşleştiği ve ikinci tam olarak ilk ve son arasında olmayan bir karakterle eşleştiği [First-Last] ve [^ First-Last] desenlerini destekler.  
  
### <a name="escape"></a>Esc  
 KAÇıŞ yan tümcesini kullanarak, önceki bölümde yer alan tabloda açıklanan özel Joker karakterlerden birini veya birkaçını içeren karakter dizelerini arayabilirsiniz. Örneğin, başlıkta "% 100%" sabit değerini içeren ve bu belgelerin tümünü aramak istediğiniz birçok belge olduğunu varsayalım. Yüzde (%) nedeniyle karakter bir joker karakterdir, aramayı başarıyla yürütmek için [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kaçış yan tümcesini kullanarak bunu atlamanız gerekir. Aşağıda bu filtrenin bir örneği verilmiştir.  
  
```  
"title like '%100!%%' escape '!'"  
```  
  
 Bu arama ifadesinde, yüzde joker karakteri (%) ünlem işareti karakteri (!) hemen sonrasında, joker karakter yerine değişmez değer olarak değerlendirilir. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Joker karakterler ve köşeli ayraç (`[ ]`) karakterleri dışında herhangi bir karakteri çıkış karakteri olarak kullanabilirsiniz. Önceki örnekte, ünlem işareti (!) karakteri kaçış karakteridir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki iki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, belirli bir karakter dizesinin belirtilen bir Düzenle eşleşip eşleşmediğini anlamak için LIKE ve kaçış işleçlerini kullanır. İlk sorgu, karakterlerle `Name` `Down_`başlayan öğesini arar. Alt çizgi (`_`) bir joker karakter olduğundan bu sorgu kaçış seçeneğini kullanır. Kaçış seçeneğini belirtmeden, sorgu, ardından alt çizgi karakteri dışında bir `Name` tek karakter gelen kelimeyle `Down` başlayan tüm değerleri arar. Sorgular AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Aşağıdaki adımları uygulayın: PrimitiveType sonuçları](../how-to-execute-a-query-that-returns-primitivetype-results.md)döndüren bir sorgu yürütün.  
  
2. Aşağıdaki sorguyu `ExecutePrimitiveTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-csharp[DP EntityServices Concepts 2#LIKE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#like)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
