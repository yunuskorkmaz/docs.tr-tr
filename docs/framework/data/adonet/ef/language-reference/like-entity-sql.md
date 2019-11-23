---
title: Beğen (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8300e6d2-875b-481e-9ef4-e1e7c12d46fa
ms.openlocfilehash: f9e33c78235f637e0aa0622d9d8cc30255722beb
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319680"
---
# <a name="like-entity-sql"></a>Beğen (Entity SQL)
Belirli bir karakterin `String` belirtilen bir Düzenle eşleşip eşleşmediğini belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
match [NOT] LIKE pattern [ESCAPE escape]  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `match`  
 Bir `String`değerlendiren [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ifadesi.  
  
 `pattern`  
 Belirtilen `String`eşleşecek bir örüntü.  
  
 `escape`  
 Kaçış karakteri.  
  
 DEĞİL  
 Bunun sonucunu, ÖRNEĞIN, Değillenmiş olduğunu belirtir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `string` düzeniyle eşleşiyorsa `true`; Aksi takdirde, `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 LIKE işlecini kullanan [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ifadeleri, filtre ölçütü olarak eşitlik kullanan ifadelerle çok benzer şekilde değerlendirilir. Ancak, LIKE işlecini kullanan [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ifadeleri hem değişmez değerleri hem de joker karakterleri içerebilir.  
  
 Aşağıdaki tabloda `string`deseninin sözdizimi açıklanmaktadır.  
  
|Joker Karakter|Açıklama|Örnek|  
|------------------------|-----------------|-------------|  
|%|Sıfır veya daha fazla karakterin `string`.|`title like '%computer%'`, sözcüğü başlığın herhangi bir yerinden `"computer"` tüm başlıkları bulur.|  
|_ (alt çizgi)|Herhangi bir tek karakter.|`firstname like '_ean'`, "DEA veya kemal gibi" `"ean`ile biten dört harfli ilk adı bulur.|  
|[ ]|Belirtilen aralıktaki ([a-f]) veya ayarlanan ([abcdef]) herhangi bir tek karakter.|`lastname like '[C-P]arsen'`, "Arsen" ile biten son adları bulur ve, Carsen veya Larsen gibi C ile P arasında tek bir karakterle başlar.|  
|[^]|Belirtilen aralıkta ([^ a-f]) veya set ([^ abcdef]) içinde olmayan tek bir karakter.|`lastname like 'de[^l]%'`, "de" ile başlayan ve aşağıdaki harfle "l" dahil olmayan tüm son adları bulur.|  
  
> [!NOTE]
> İşleç ve KAÇıŞ yan tümcesi gıbı [!INCLUDE[esql](../../../../../../includes/esql-md.md)] `System.DateTime` veya `System.Guid` değerlerine uygulanamaz.  
  
 Benzer şekilde, ASCII stili eşleştirmeyi ve Unicode düzeniyle eşleştirmeyi destekler. Tüm parametreler ASCII karakterleri olduğunda, ASCII stili eşleştirmesi gerçekleştirilir. Bir veya daha fazla bağımsız değişken Unicode ise, tüm bağımsız değişkenler Unicode 'a dönüştürülür ve Unicode deseninin eşleşmesi gerçekleştirilir. Benzer bir şekilde Unicode kullandığınızda, sondaki boşluklar önemlidir; Ancak Unicode olmayan, sondaki boşluklar önemli değildir. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] model dize sözdizimi Transact-SQL ile aynıdır.  
  
 Bir desenler, düzenli karakter ve joker karakterler içerebilir. Model eşleştirme sırasında, normal karakterlerin `string`karakter olarak belirtilen karakterlerle tam olarak eşleşmesi gerekir. Ancak, joker karakterler karakter dizesinin rastgele parçaları ile eşleştirilebilir. Joker karakterlerle kullanıldığında, LIKE işleci = ve! = dize karşılaştırma işleçlerinden daha esnektir.  
  
> [!NOTE]
> Belirli bir sağlayıcıyı hedefliyorsanız sağlayıcıya özgü uzantıları kullanabilirsiniz. Ancak, bu tür yapılar diğer sağlayıcılar tarafından farklı şekilde değerlendirilemeyebilir. SqlServer, ilk ve son arasında tam olarak bir karakter eşleştiği ve ikinci tam olarak ilk ve son arasında olmayan bir karakterle eşleştiği [First-Last] ve [^ First-Last] desenlerini destekler.  
  
### <a name="escape"></a>Esc  
 KAÇıŞ yan tümcesini kullanarak, önceki bölümde yer alan tabloda açıklanan özel Joker karakterlerden birini veya birkaçını içeren karakter dizelerini arayabilirsiniz. Örneğin, başlıkta "%100%" sabit değerini içeren ve bu belgelerin tümünü aramak istediğiniz birçok belge olduğunu varsayalım. Yüzde (%) nedeniyle karakter bir joker karakterdir, aramayı başarıyla yürütmek için [!INCLUDE[esql](../../../../../../includes/esql-md.md)] KAÇıŞ yan tümcesini kullanarak bunu atlamanız gerekir. Aşağıda bu filtrenin bir örneği verilmiştir.  
  
```sql  
"title like '%100!%%' escape '!'"  
```  
  
 Bu arama ifadesinde, yüzde joker karakteri (%) ünlem işareti karakteri (!) hemen sonrasında, joker karakter yerine değişmez değer olarak değerlendirilir. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] joker karakter ve köşeli ayraç (`[ ]`) karakterleri dışında herhangi bir karakteri çıkış karakteri olarak kullanabilirsiniz. Önceki örnekte, ünlem işareti (!) karakteri kaçış karakteridir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki iki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgusu, belirli bir karakter dizesinin belirtilen bir Düzenle eşleşip eşleşmediğini anlamak için LIKE ve KAÇıŞ işleçlerini kullanır. İlk sorgu, `Down_`karakterlerle başlayan `Name` arar. Alt çizgi (`_`) bir joker karakter olduğundan bu sorgu KAÇıŞ seçeneğini kullanır. KAÇıŞ seçeneğini belirtmeden, sorgu, ardından alt çizgi karakteri dışında herhangi bir karakter `Down`, Word ile başlayan `Name` değerleri arar. Sorgular AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu `ExecutePrimitiveTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-sql[DP EntityServices Concepts#LIKE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#like)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
