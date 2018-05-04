---
title: (Varlık gibi SQL)
ms.date: 03/30/2017
ms.assetid: 8300e6d2-875b-481e-9ef4-e1e7c12d46fa
ms.openlocfilehash: f2d06b364c577b581bb64af0436c133ca830bb2b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="like-entity-sql"></a>(Varlık gibi SQL)
Belirli bir karakteri olup olmadığını belirleyen `String` belirtilen desenle eşleşir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
match [NOT] LIKE pattern [ESCAPE escape]  
```  
  
## <a name="arguments"></a>Arguments  
 `match`  
 Bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] veren ifade bir `String`.  
  
 `pattern`  
 Belirtilen eşleştirmek için bir desen `String`.  
  
 `escape`  
 Bir kaçış karakteri.  
  
 DEĞİL  
 BENZER sonucunu tasarruflarını belirtir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true` varsa `string` desenle eşleşen; Aksi halde, `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] LIKE işleci kullanan ifadeler çok eşitlik filtre ölçütü olarak kullanan ifadeler aynı şekilde değerlendirilir. Ancak, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] LIKE işleci kullanan ifadeler değişmez değerleri ve joker karakterleri içerebilir.  
  
 Aşağıdaki tablo düzeni söz dizimi açıklanmıştır `string`.  
  
|Joker Karakter|Açıklama|Örnek|  
|------------------------|-----------------|-------------|  
|%|Tüm `string` sıfır veya daha fazla karakter.|`title like '%computer%'` word sahip tüm başlıkları bulur `"computer"` başlığı başka bir yerindeki.|  
|_ (alt çizgi)|Herhangi bir tek karakteri.|`firstname like '_ean'` tüm dört harfli ilk ile biten adlarını bulur `"ean`, "Deniz veya Gamze gibi.|  
|[ ]|Tüm tek belirtilen aralıkta ([a-f]) karakter veya ([abcdef]) ayarlayın.|`lastname like '[C-P]arsen'` bulur, "arsen" ile biten ve Carsen veya Etikan gibi P ile C arasındaki herhangi bir tek karakteri ile başlayan son adları.|  
|[^]|Tek bir karakter belirtilen aralık içinde değil ([^ a-f]) veya ayarlayın ([^ abcdef]).|`lastname like 'de[^l]%'` "de" ile başlamalı ve şu harfini olarak "m" dahil etmeyin, tüm son adlarını bulur.|  
  
> [!NOTE]
>  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] İşleci ve çıkış yan tümcesi uygulanamaz gibi `System.DateTime` veya `System.Guid` değerleri.  
  
 Destekler ASCII desen eşleştirme ve Unicode desen eşleştirme gibi. Tüm parametreleri ASCII karakterler olduğunda, ASCII desen eşleştirme gerçekleştirilir. Bir veya daha fazla bağımsız değişken Unicode varsa, tüm bağımsız değişkenler Unicode'a dönüştürülür ve Unicode desen eşleştirme gerçekleştirilir. Unicode gibi ile kullandığınızda, sondaki boşlukları önemli; Ancak, Unicode olmayan için sondaki boşlukları önemli değildir. Desen dizesi söz dizimi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] , aynı [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].  
  
 Bir desen normal karakter ve joker karakterler içerebilir. Desen eşleştirme sırasında normal karakter tam olarak karakteri belirtilen karakterleri eşleşmelidir `string`. Ancak, joker karakterler rasgele parçalarını karakter dizesiyle eşleşen. ' Den = joker karakterlerle kullanıldığında, LIKE işleci daha esnektir ve! = dize karşılaştırma işleçleri.  
  
> [!NOTE]
>  Belirli bir sağlayıcıyı hedefliyorsanız, sağlayıcıya özgü uzantılar kullanabilirsiniz. Ancak, böyle yapıları farklı şekilde, diğer sağlayıcıları tarafından örneğin kabul. SqlServer destekler [ilk-son] ve [^ ilk son] tam olarak bir karakter arasında ilk ve son ve arasında değil ikinci eşleşmeleri tam olarak bir karakter önceki eşleştiği desenleri ilk ve son.  
  
### <a name="escape"></a>Esc  
 KAÇIŞ yan tümcesini kullanarak, bir dahil karakter dizeleri için arama yapabilirsiniz veya daha fazla özel joker karakter önceki bölümdeki tabloda açıklanan. Örneğin, birkaç belge değişmez değer "% 100" başlığında içerir ve tüm bu belgeler için arama yapmak istediğiniz varsayın. Yüzde (%) karakter joker karakter olduğundan kullanarak kaçış gerekir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] KAÇIŞ başarıyla araması yürütmek için yan tümcesi. Bu filtre, bir örnek verilmiştir.  
  
```  
"title like '%100!%%' escape '!'"  
```  
  
 Bu arama ifadesinde ünlem işareti karakteri (!) hemen ardından yüzde joker karakter (%) bir hazır değer yerine bir joker karakter olarak kabul edilir. Bir kaçış karakteri dışındaki herhangi bir karakter kullanabilirsiniz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] joker karakterler ve köşeli ayraç (`[ ]`) karakter. Önceki örnekte kaçış karakteri ünlem işareti (!) karakterdir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki iki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorguları gibi kullanın ve bir özel karakter dizesi olup olmadığını belirlemek için KAÇIŞ işleçleri belirtilen desenle eşleşir. İlk sorguyu arar `Name` karakterlerle başlayıp `Down_`. Bu sorgu KAÇIŞ seçeneği kullanır, çünkü alt çizgi (`_`) bir joker karakterdir. KAÇIŞ seçeneğini belirtmeden sorgu aramanıza `Name` sözcüğüyle başlayan değerlerini `Down` alt çizgi karakteri dışındaki herhangi bir tek karakteri arkasından. Sorgular AdventureWorks satış modeline dayanır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür PrimitiveType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#LIKE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#like)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
