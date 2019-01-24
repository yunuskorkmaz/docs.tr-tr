---
title: (SQL varlık gibi)
ms.date: 03/30/2017
ms.assetid: 8300e6d2-875b-481e-9ef4-e1e7c12d46fa
ms.openlocfilehash: 406e660efcc351df3fd2720a5d13d8398d1a8216
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536977"
---
# <a name="like-entity-sql"></a>(SQL varlık gibi)
Belirli bir karakter olup olmadığını belirleyen `String` belirtilen desenle eşleşir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
match [NOT] LIKE pattern [ESCAPE escape]  
```  
  
## <a name="arguments"></a>Arguments  
 `match`  
 Bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] için değerlendirilen bir ifade bir `String`.  
  
 `pattern`  
 Belirtilen eşleştirmek için bir desen `String`.  
  
 `escape`  
 Bir kaçış karakteri.  
  
 DEĞİL  
 BENZER sonucunu negatif olduğunu belirtir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true` varsa `string` desenle eşleşir; Aksi takdirde `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] LIKE işleci kullanan ifadeler çok eşitlik filtre ölçütü olarak kullanan ifadeler aynı şekilde değerlendirilir. Ancak, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] LIKE işleci kullanan ifadelerde hem sabit hem de joker karakterler içerebilir.  
  
 Sözdizimi deseni aşağıdaki tabloda açıklanmıştır `string`.  
  
|Joker Karakter|Açıklama|Örnek|  
|------------------------|-----------------|-------------|  
|%|Tüm `string` sıfır veya daha fazla karakter.|`title like '%computer%'` Word'ün sahip tüm başlıkları bulur `"computer"` başlığı herhangi bir yerindeki.|  
|_ (alt çizgi)|Herhangi bir tek karakter.|`firstname like '_ean'` tüm dört harfli ilk biten adlarını bulur `"ean`, "Deniz veya Sean gibi.|  
|[ ]|Tek belirtilen aralığında ([a-f]) karakter veya ayarlayın ([abcdef]).|`lastname like '[C-P]arsen'` bulur, P, Carsen veya Larsen gibi C arasındaki herhangi bir tek karakteri ile başlayan ve "arsen" ile biten son adları.|  
|[^]|Herhangi bir tek karakter belirtilen aralık içinde değil ([^ a-f]) veya ayarlayın ([^ abcdef]).|`lastname like 'de[^l]%'` "de" ile başlayan ve "m" şu harfini içermez tüm adların bulur.|  
  
> [!NOTE]
>  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] İşleci ve KAÇIŞ yan tümcesinde uygulanamaz gibi `System.DateTime` veya `System.Guid` değerleri.  
  
 Destekler ASCII desen eşleştirme ve Unicode desen eşleştirme gibi. Tüm parametreler ASCII karakterler olduğunda ASCII desen eşleştirme gerçekleştirilir. Bir veya daha fazla bağımsız değişken Unicode kullanıyorsanız, tüm bağımsız değişkenler, Unicode'a dönüştürülür ve Unicode desen eşleştirme gerçekleştirilir. Unicode gibi ile kullandığınızda, sondaki boşluk önemlidir; Ancak, Unicode olmayan için sondaki boşluklar önemli değildir. Desen dizesi söz dizimi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] , aynı [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].  
  
 Bir desen, normal bir karakter ve joker karakterler içerebilir. Desen eşleştirme sırasında normal karakter tam olarak belirtilen karakter karakterleri eşleşmelidir `string`. Ancak, joker karakter, karakter dizesi rastgele parçalarını eşleştirilebilir. = Joker karakterlerle kullanıldığında LIKE işleci daha esnektir ve! = dize karşılaştırma işleçleri.  
  
> [!NOTE]
>  Belirli bir sağlayıcı hedefliyorsanız, sağlayıcıya özgü uzantıları kullanabilirsiniz. Ancak, bu tür yapıları farklı diğer sağlayıcılar tarafından örneğin değerlendirilecek. SqlServer destekler [ilk son] ve [^ ilk son] arasında ilk ve son tam olarak bir karakter ve değerler arasında değildir: ikinci eşleşme tam olarak bir karakter önceki eşleştiği desenleri ilk ve son.  
  
### <a name="escape"></a>Esc  
 KAÇIŞ yan tümcesinde'ı kullanarak bir karakter dizeleri için arama yapabilirsiniz veya daha fazla özel joker karakter önceki bölümdeki tabloda açıklanan. Örneğin, birkaç belge değişmez değer "%100" başlığında içerir ve tüm bu belgeleri için arama yapmak istediğiniz varsayılır. Yüzde (%) karakterini bir joker karakter olduğundan kullanarak atlatmak gerekir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] KAÇIŞ yan tümcesinde arama başarıyla yürütülemedi. Bu filtre, bir örnek verilmiştir.  
  
```  
"title like '%100!%%' escape '!'"  
```  
  
 Bu arama ifadesinde ünlem işareti karakteri (!) takip yüzde joker karakter (%) bir değişmez değer olarak yerine bir joker karakter olarak kabul edilir. Herhangi bir karakterle dışında bir kaçış karakteri olarak kullanabileceğiniz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] joker karakterler ve köşeli ayraç (`[ ]`) karakter. Önceki örnekte, kaçış karakteri ünlem işareti (!) karakteridir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki iki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] belirli karakter dizesi olup olmadığını belirlemek için KAÇIŞ işleçleri, belirtilen desenle eşleşen ve sorgular gibi kullanın. İlk sorgu arar `Name` karakterlerle başlayan `Down_`. Bu sorgu çıkış seçeneği kullanır, çünkü alt çizgi (`_`) bir joker karakterdir. KAÇIŞ seçeneğini belirtmeden sorgu için arama `Name` kelimesiyle başlayan değerler `Down` alt çizgi karakteri dışındaki herhangi bir tek karakterle ardından. Sorgular, AdventureWorks satış modeline dayanır. Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:  
  
1.  Verilen yordamı izleyin [nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#LIKE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#like)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
