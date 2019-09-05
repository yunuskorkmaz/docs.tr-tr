---
title: Kurallı Dize İşlevleri
ms.date: 03/30/2017
ms.assetid: 5e2cbebd-5df3-47c7-b0e2-49a17ab22bfb
ms.openlocfilehash: 9013b8bd8505442666dd0688eaf2586959a61b70
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249097"
---
# <a name="string-canonical-functions"></a>Kurallı Dize İşlevleri
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]kurallı dize işlevleri içerir.  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki tabloda, dize [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevleri gösterilmektedir.  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|`Concat(string1, string2)`|`string2` Sonunaeklenen`string1`bir dize döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `string1`: Eklenecek dize `string2` .<br /><br /> `string2`: Öğesine `string1`eklenen dize.<br /><br /> **Dönüş değeri**<br /><br /> A `String`. Dönüş değeri dizesinin uzunluğu izin verilen en fazla uzunluktan fazlaysa bir hata meydana gelir.<br /><br /> **Örnek**<br /><br /> `-- The following example returns abcxyz.`<br /><br /> `Concat('abc', 'xyz')`|  
|`Contains(string, target)`|İçinde içerilse döndürür `true`. `target` `string`<br /><br /> **Bağımsız Değişkenler**<br /><br /> `string`: Aranan dize.<br /><br /> `target`: Aranan hedef dize.<br /><br /> **Dönüş değeri**<br /><br /> `true`varsa `target` ; aksi takdirde`false`. `string`<br /><br /> **Örnek**<br /><br /> `-- The following example returns true.`<br /><br /> `Contains('abc', 'bc')`|  
|`EndsWith(string, target)`|İle `true` `target` bitiyorsa döndürür. `string`<br /><br /> **Bağımsız Değişkenler**<br /><br /> `string`: Aranan dize.<br /><br /> `target`: Sonunda için aranan hedef dize `string`.<br /><br /> **Dönüş değeri**<br /><br /> `True``false`ile `string` biter`target`; Aksi takdirde.<br /><br /> **Örnek**<br /><br /> `-- The following example returns true.`<br /><br /> `EndsWith('abc', 'bc')`**Note:**  SQL Server veri sağlayıcısını kullanıyorsanız, bu işlev, dize sabit uzunluklu bir `false` dize sütununda saklanırsa ve `target` sabit ise döndürür. Bu durumda tüm dize, sondaki boşlukları doldurarak aranır. Olası bir geçici çözüm, aşağıdaki örnekte olduğu gibi, sabit uzunluklu dizedeki verileri kırpmaya yönelik bir çözümdür:`EndsWith(TRIM(string), target)`|  
|`IndexOf(target, string)`|`target` İçinde`string`konumunu, veya bulunmazsa 0 değerini döndürür. Başlangıcını göstermek için 1 döndürür `string`. Dizin numaralandırması 1 ' den başlar.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `target`: Aranan dize.<br /><br /> `string`: Aranan dize.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns 4.`<br /><br /> `IndexOf('xyz', 'abcxyz')`|  
|`Left(string, length)`|`length` Öğesinin`string`sol tarafındaki ilk karakterleri döndürür. Uzunluğu `string` değerinden`length`küçükse, tüm dize döndürülür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `string`: A `String`.<br /><br /> `length`: `Int16` ,`Int32`, Veya .`Byte` `Int64` `length`sıfırdan küçük olamaz.<br /><br /> **Dönüş değeri**<br /><br /> A `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns abc.`<br /><br /> `Left('abcxyz', 3)`|  
|`Length(string)`|Dizenin karakter cinsinden`Int32`() uzunluğunu döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `string`: A `String`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns 6.`<br /><br /> `Legth('abcxyz')`|  
|`LTrim(string)`|Baştaki `string` boşluk olmadan döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `String`.<br /><br /> **Dönüş değeri**<br /><br /> A `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns abc.`<br /><br /> `LTrim('   abc')`|  
|`Replace(string1, string2, string3)`|' `string1`In `string2` Tümoluşumlarıyla`string3`birlikte döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `String`.<br /><br /> **Dönüş değeri**<br /><br /> A `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns abcxyz.`<br /><br /> `Concat('abc', 'xyz')`|  
|`Reverse(string)`|Ters `string` çevrilen karakterlerin sırası ile döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `String`.<br /><br /> **Dönüş değeri**<br /><br /> A `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns dcba.`<br /><br /> `Reverse('abcd')`|  
|`Right(string, length)`|Öğesinden son `length` karakterleri döndürür. `string` Uzunluğu `string` değerinden`length`küçükse, tüm dize döndürülür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `string`: A `String`.<br /><br /> `length`: `Int16` ,`Int32`, Veya .`Byte` `Int64` `length`sıfırdan küçük olamaz.<br /><br /> **Dönüş değeri**<br /><br /> A `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns xyz.`<br /><br /> `Right('abcxyz', 3)`|  
|`RTrim(string)`|Sondaki `string` boşluk olmadan döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `String`.<br /><br /> **Dönüş değeri**<br /><br /> A `String`.|  
|`Substring(string, start, length)`|`length` Karakterden başlayarak `start`, bir karakter uzunluğunda olan dizenin alt dizesini döndürür. 1 başlangıcı dizenin ilk karakterini gösterir. Dizin numaralandırması 1 ' den başlar.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `string`: A `String`.<br /><br /> `start`: `Int16` ,`Int32`Ve .`Byte` `Int64` `start`birden az olamaz.<br /><br /> `length`: `Int16` ,`Int32`Ve .`Byte` `Int64` `length`sıfırdan küçük olamaz.<br /><br /> **Dönüş değeri**<br /><br /> A `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns xyz.`<br /><br /> `Substring('abcxyz', 4, 3)`|  
|`StartsWith(string, target)`|`true` İle`string` başlıyorsa döndürür`target`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `string`: Aranan dize.<br /><br /> `target`: ' Nin `string`başlangıcında aranan hedef dize.<br /><br /> **Dönüş değeri**<br /><br /> `True``false`ile `string` başlıyorsa`target`; Aksi halde.<br /><br /> **Örnek**<br /><br /> `-- The following example returns true.`<br /><br /> `StartsWith('abc', 'ab')`|  
|`ToLower(string)`|Büyük `string` harfli karakterlerle küçük harfe dönüştürülmüş döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `String`.<br /><br /> **Dönüş değeri**<br /><br /> A `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns abc.`<br /><br /> `ToLower('ABC')`|  
|`ToUpper(string)`|Küçük `string` harfli karakterlerle büyük harfe dönüştürülmüş döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `String`.<br /><br /> **Dönüş değeri**<br /><br /> A `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns ABC.`<br /><br /> `ToUpper('abc')`|  
|`Trim(string)`|Baştaki `string` ve sondaki boşluk olmadan döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `String`.<br /><br /> **Dönüş değeri**<br /><br /> A `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns abc.`<br /><br /> `Trim('      abc   ')`|  
  
 Bu işlevler, verilen `null` `null` giriş durumunda döndürülür.  
  
 Eşdeğer işlevsellik, Microsoft SQL Istemci tarafından yönetilen sağlayıcıda bulunur. Daha fazla bilgi için bkz. [Entity Framework işlevleri Için SqlClient](../sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kurallı İşlevler](canonical-functions.md)
