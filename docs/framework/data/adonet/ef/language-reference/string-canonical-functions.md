---
title: Kurallı dize işlevleri
ms.date: 03/30/2017
ms.assetid: 5e2cbebd-5df3-47c7-b0e2-49a17ab22bfb
ms.openlocfilehash: d4758f8325b99bc4bd91575dd774d2dabde1f925
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46696501"
---
# <a name="string-canonical-functions"></a>Kurallı dize işlevleri
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı dize işlevleri içerir.  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki tabloda dize gösterilmektedir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevler.  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|`Concat(string1, string2)`|İçeren bir dize döndürür `string2` eklenen `string1`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `string1`: Dizeye `string2` eklenir.<br /><br /> `string2`: Eklenen dize `string1`.<br /><br /> **Dönüş değeri**<br /><br /> A `String`. Dönüş değeri dize uzunluğu izin verilen uzunluk üst sınırından daha büyük ise, bir hata meydana gelir.<br /><br /> **Örnek**<br /><br /> `-- The following example returns abcxyz.`<br /><br /> `Concat('abc', 'xyz')`|  
|`Contains(string, target)`|Döndürür `true` varsa `target` bulunan `string`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `string`: Aranır dize.<br /><br /> `target`: İçin aranır hedef dizesi.<br /><br /> **Dönüş değeri**<br /><br /> `true` varsa `target` bulunan `string`; Aksi takdirde `false`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns true.`<br /><br /> `Contains('abc', 'bc')`|  
|`EndsWith(string, target)`|Döndürür `true` varsa `target` ile biten `string`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `string`: Aranır dize.<br /><br /> `target`: Hedef dizesi sonunda için Aranan `string`.<br /><br /> **Dönüş değeri**<br /><br /> `True` varsa `string` ile biten `target`; Aksi takdirde `false`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns true.`<br /><br /> `EndsWith('abc', 'bc')` **Not:** SQL Server veri sağlayıcısı kullanıyorsanız, bu işlevi döndürür `false` dize sabit uzunluk dize sütunu içinde depolanıyorsa ve `target` bir sabittir. Bu durumda, sondaki boşlukları herhangi doldurma dahil olmak üzere tüm dizeyi aranır. Aşağıdaki örnekte olduğu gibi sabit uzunluk dize verilerde kırpmak için olası bir geçici çözüm şöyledir: `EndsWith(TRIM(string), target)`|  
|`IndexOf(target, string)`|Konumunu döndürür `target` içinde `string`, veya 0 ise bulunamadı. Belirtmek için 1'i döndürür `string`. Numaralandırma dizini 1'den başlar.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `target`: İçin aranır dize.<br /><br /> `string`: Aranır dize.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns 4.`<br /><br /> `IndexOf('xyz', 'abcxyz')`|  
|`Left(string, length)`|İlk döndürür `length` sol tarafındaki karakterleri `string`. Varsa uzunluğunu `string` olduğu küçüktür `length`, tüm dize döndürülür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `string`: BİR `String`.<br /><br /> `length`: Bir `Int16`, `Int32`, `Int64`, veya `Byte`. `length` sıfırdan küçük olamaz.<br /><br /> **Dönüş değeri**<br /><br /> A `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns abc.`<br /><br /> `Left('abcxyz', 3)`|  
|`Length(string)`|Döndürür (`Int32`) dizenin karakter cinsinden uzunluğu.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `string`: BİR `String`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns 6.`<br /><br /> `Legth('abcxyz')`|  
|`LTrim(string)`|Döndürür `string` baştaki boşluk olmadan.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `String`.<br /><br /> **Dönüş değeri**<br /><br /> A `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns abc.`<br /><br /> `LTrim('   abc')`|  
|`Replace(string1, string2, string3)`|Döndürür `string1`, tüm oluşumlarını ile `string2` yerine `string3`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `String`.<br /><br /> **Dönüş değeri**<br /><br /> A `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns abcxyz.`<br /><br /> `Concat('abc', 'xyz')`|  
|`Reverse(string)`|Döndürür `string` karakterlerin sırasını tersine.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `String`.<br /><br /> **Dönüş değeri**<br /><br /> A `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns dcba.`<br /><br /> `Reverse('abcd')`|  
|`Right(string, length)`|Son döndürür `length` gelen karakter `string`. Varsa uzunluğunu `string` olduğu küçüktür `length`, tüm dize döndürülür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `string`: BİR `String`.<br /><br /> `length`: Bir `Int16`, `Int32`, `Int64`, veya `Byte`. `length` sıfırdan küçük olamaz.<br /><br /> **Dönüş değeri**<br /><br /> A `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns xyz.`<br /><br /> `Right('abcxyz', 3)`|  
|`RTrim(string)`|Döndürür `string` boşluk olmadan.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `String`.<br /><br /> **Dönüş değeri**<br /><br /> A `String`.|  
|`Substring(string, start, length)`|Konumunda başlayan dize alt döndürür `start`, uzunluğu `length` karakter. Dizenin ilk karakteri 1 başlangıcını gösterir. Numaralandırma dizini 1'den başlar.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `string`: BİR `String`.<br /><br /> `start`: Bir `Int16`, `Int32`, `Int64` ve `Byte`. `start` değerden daha az olamaz.<br /><br /> `length`: Bir `Int16`, `Int32`, `Int64` ve `Byte`. `length` sıfırdan küçük olamaz.<br /><br /> **Dönüş değeri**<br /><br /> A `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns xyz.`<br /><br /> `Substring('abcxyz', 4, 3)`|  
|`StartsWith(string, target)`|Döndürür `true` varsa `string` ile başlayan `target`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `string`: Aranır dize.<br /><br /> `target`: Hedef dizenin başlangıcında için Aranan `string`.<br /><br /> **Dönüş değeri**<br /><br /> `True` varsa `string` ile başlayan `target`; Aksi takdirde `false`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns true.`<br /><br /> `StartsWith('abc', 'ab')`|  
|`ToLower(string)`|Döndürür `string` büyük harf karakterler küçük harfe sahip.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `String`.<br /><br /> **Dönüş değeri**<br /><br /> A `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns abc.`<br /><br /> `ToLower('ABC')`|  
|`ToUpper(string)`|Döndürür `string` ile küçük harf karakterler büyük harfe dönüştürülür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `String`.<br /><br /> **Dönüş değeri**<br /><br /> A `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns ABC.`<br /><br /> `ToUpper('abc')`|  
|`Trim(string)`|Döndürür `string` baştaki ve sondaki boşluk olmadan.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `String`.<br /><br /> **Dönüş değeri**<br /><br /> A `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns abc.`<br /><br /> `Trim('      abc   ')`|  
  
 Bu işlevler döndüreceği `null` verildiyse `null` giriş.  
  
 Microsoft SQL istemci yönetilen sağlayıcısında eşdeğer bir işlevselliği kullanılabilir. Daha fazla bilgi için [Entity Framework işlevleri için SqlClient](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kurallı İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
