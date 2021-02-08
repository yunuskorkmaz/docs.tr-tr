---
description: 'Daha fazla bilgi edinin: dize kurallı Işlevleri'
title: Kurallı Dize İşlevleri
ms.date: 03/30/2017
ms.assetid: 5e2cbebd-5df3-47c7-b0e2-49a17ab22bfb
ms.openlocfilehash: aa356b094e900cca6bd9fdfe09b144d9a9424651
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767836"
---
# <a name="string-canonical-functions"></a>Kurallı Dize İşlevleri

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı dize işlevleri içerir.  
  
## <a name="remarks"></a>Açıklamalar  

 Aşağıdaki tabloda, dize [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevleri gösterilmektedir.  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|`Concat(string1, string2)`|Sonuna eklenen bir dize döndürür `string2` `string1` .<br /><br /> **Bağımsız değişkenler**<br /><br /> `string1`: Eklenecek dize `string2` .<br /><br /> `string2`: Öğesine eklenen dize `string1` .<br /><br /> **Dönüş Değeri**<br /><br /> Bir `String`. Dönüş değeri dizesinin uzunluğu izin verilen en fazla uzunluktan fazlaysa bir hata meydana gelir.<br /><br /> **Örnek**<br /><br /> `-- The following example returns abcxyz.`<br /><br /> `Concat('abc', 'xyz')`|  
|`Contains(string, target)`|`true` `target` İçinde içerilse döndürür `string` .<br /><br /> **Bağımsız değişkenler**<br /><br /> `string`: Aranan dize.<br /><br /> `target`: Aranan hedef dize.<br /><br /> **Dönüş Değeri**<br /><br /> `true` varsa `target` `string` ; Aksi takdirde `false` .<br /><br /> **Örnek**<br /><br /> `-- The following example returns true.`<br /><br /> `Contains('abc', 'bc')`|  
|`EndsWith(string, target)`|`true` `target` İle bitiyorsa döndürür `string` .<br /><br /> **Bağımsız değişkenler**<br /><br /> `string`: Aranan dize.<br /><br /> `target`: ' Nin sonunda için aranan hedef dize `string` .<br /><br /> **Dönüş Değeri**<br /><br /> `True``string`ile biter `target` ; Aksi takdirde `false` .<br /><br /> **Örnek**<br /><br /> `-- The following example returns true.`<br /><br /> `EndsWith('abc', 'bc')`**Note:**  SQL Server veri sağlayıcısını kullanıyorsanız, bu işlev, `false` dize sabit uzunluklu bir dize sütununda saklanırsa ve `target` sabit ise döndürür. Bu durumda tüm dize, sondaki boşlukları doldurarak aranır. Olası bir geçici çözüm, aşağıdaki örnekte olduğu gibi, sabit uzunluklu dizedeki verileri kırpmaya yönelik bir çözümdür: `EndsWith(TRIM(string), target)`|  
|`IndexOf(target, string)`|`target`İçinde konumunu `string` , veya bulunmazsa 0 değerini döndürür. Başlangıcını göstermek için 1 döndürür `string` . Dizin numaralandırması 1 ' den başlar.<br /><br /> **Bağımsız değişkenler**<br /><br /> `target`: Aranan dize.<br /><br /> `string`: Aranan dize.<br /><br /> **Dönüş Değeri**<br /><br /> Bir `Int32` .<br /><br /> **Örnek**<br /><br /> `-- The following example returns 4.`<br /><br /> `IndexOf('xyz', 'abcxyz')`|  
|`Left(string, length)`|`length`Öğesinin sol tarafındaki ilk karakterleri döndürür `string` . Uzunluğu `string` değerinden küçükse `length` , tüm dize döndürülür.<br /><br /> **Bağımsız değişkenler**<br /><br /> `string`: A `String` .<br /><br /> `length`: Bir `Int16` , `Int32` , `Int64` veya `Byte` . `length` sıfırdan küçük olamaz.<br /><br /> **Dönüş Değeri**<br /><br /> Bir `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns abc.`<br /><br /> `Left('abcxyz', 3)`|  
|`Length(string)`|`Int32`Dizenin karakter cinsinden () uzunluğunu döndürür.<br /><br /> **Bağımsız değişkenler**<br /><br /> `string`: A `String` .<br /><br /> **Dönüş Değeri**<br /><br /> Bir `Int32` .<br /><br /> **Örnek**<br /><br /> `-- The following example returns 6.`<br /><br /> `Legth('abcxyz')`|  
|`LTrim(string)`|`string`Baştaki boşluk olmadan döndürür.<br /><br /> **Bağımsız değişkenler**<br /><br /> Bir `String`.<br /><br /> **Dönüş Değeri**<br /><br /> Bir `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns abc.`<br /><br /> `LTrim('   abc')`|  
|`Replace(string1, string2, string3)`|`string1`' In tüm oluşumlarıyla birlikte döndürür `string2` `string3` .<br /><br /> **Bağımsız değişkenler**<br /><br /> Bir `String`.<br /><br /> **Dönüş Değeri**<br /><br /> Bir `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns abcxyz.`<br /><br /> `Concat('abc', 'xyz')`|  
|`Reverse(string)`|`string`Ters çevrilen karakterlerin sırası ile döndürür.<br /><br /> **Bağımsız değişkenler**<br /><br /> Bir `String`.<br /><br /> **Dönüş Değeri**<br /><br /> Bir `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns dcba.`<br /><br /> `Reverse('abcd')`|  
|`Right(string, length)`|`length`Öğesinden son karakterleri döndürür `string` . Uzunluğu `string` değerinden küçükse `length` , tüm dize döndürülür.<br /><br /> **Bağımsız değişkenler**<br /><br /> `string`: A `String` .<br /><br /> `length`: Bir `Int16` , `Int32` , `Int64` veya `Byte` . `length` sıfırdan küçük olamaz.<br /><br /> **Dönüş Değeri**<br /><br /> Bir `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns xyz.`<br /><br /> `Right('abcxyz', 3)`|  
|`RTrim(string)`|`string`Sondaki boşluk olmadan döndürür.<br /><br /> **Bağımsız değişkenler**<br /><br /> Bir `String`.<br /><br /> **Dönüş Değeri**<br /><br /> Bir `String`.|  
|`Substring(string, start, length)`|`start`Karakterden başlayarak, bir karakter uzunluğunda olan dizenin alt dizesini döndürür `length` . 1 başlangıcı dizenin ilk karakterini gösterir. Dizin numaralandırması 1 ' den başlar.<br /><br /> **Bağımsız değişkenler**<br /><br /> `string`: A `String` .<br /><br /> `start`: `Int16` , `Int32` , `Int64` Ve `Byte` . `start` birden az olamaz.<br /><br /> `length`: `Int16` , `Int32` , `Int64` Ve `Byte` . `length` sıfırdan küçük olamaz.<br /><br /> **Dönüş Değeri**<br /><br /> Bir `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns xyz.`<br /><br /> `Substring('abcxyz', 4, 3)`|  
|`StartsWith(string, target)`|`true` `string` İle başlıyorsa döndürür `target` .<br /><br /> **Bağımsız değişkenler**<br /><br /> `string`: Aranan dize.<br /><br /> `target`: Hedef dize, başlangıcında için arandı `string` .<br /><br /> **Dönüş Değeri**<br /><br /> `True``string`ile başlıyorsa `target` ; Aksi halde `false` .<br /><br /> **Örnek**<br /><br /> `-- The following example returns true.`<br /><br /> `StartsWith('abc', 'ab')`|  
|`ToLower(string)`|`string`Büyük harfli karakterlerle küçük harfe dönüştürülmüş döndürür.<br /><br /> **Bağımsız değişkenler**<br /><br /> Bir `String`.<br /><br /> **Dönüş Değeri**<br /><br /> Bir `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns abc.`<br /><br /> `ToLower('ABC')`|  
|`ToUpper(string)`|`string`Küçük harfli karakterlerle büyük harfe dönüştürülmüş döndürür.<br /><br /> **Bağımsız değişkenler**<br /><br /> Bir `String`.<br /><br /> **Dönüş Değeri**<br /><br /> Bir `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns ABC.`<br /><br /> `ToUpper('abc')`|  
|`Trim(string)`|`string`Baştaki ve sondaki boşluk olmadan döndürür.<br /><br /> **Bağımsız değişkenler**<br /><br /> Bir `String`.<br /><br /> **Dönüş Değeri**<br /><br /> Bir `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns abc.`<br /><br /> `Trim('      abc   ')`|  
  
 Bu işlevler, `null` verilen giriş durumunda döndürülür `null` .  
  
 Eşdeğer işlevsellik, Microsoft SQL Istemci tarafından yönetilen sağlayıcıda bulunur. Daha fazla bilgi için bkz. [Entity Framework işlevleri Için SqlClient](../sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kurallı İşlevler](canonical-functions.md)
