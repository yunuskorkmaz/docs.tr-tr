---
title: "Dize kurallı işlevleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e2cbebd-5df3-47c7-b0e2-49a17ab22bfb
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2eef6928098f762274ecd19272b34cce6ab41920
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="string-canonical-functions"></a>Dize kurallı işlevleri
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]dize kurallı işlevleri içerir.  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki tabloda, dize gösterilmektedir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevleri.  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|`Concat (` `string1`, `string2``)`|İçeren bir dize döndürür `string2` eklenen `string1`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `string1`: Dizeye `string2` eklenir.<br /><br /> `string2`: Eklenir dize `string1`.<br /><br /> **Dönüş değeri**<br /><br /> A `String`. Dönüş değeri dize uzunluğu izin verilen uzunluk üst sınırından daha büyük olması durumunda bir hata meydana gelir.<br /><br /> **Örnek**<br /><br /> `-- The following example returns abcxyz.`<br /><br /> `Concat('abc', 'xyz')`|  
|`Contains (` `string`, `target``)`|Döndürür `true` varsa `target` bulunan `string`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `string`: Aranır dize.<br /><br /> `target`: İçin arama hedef dize.<br /><br /> **Dönüş değeri**<br /><br /> `true`varsa `target` bulunan `string`; Aksi halde `false`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns true.`<br /><br /> `Contains('abc', 'bc')`|  
|`EndsWith (` `string`, `target``)`|Döndürür `true` varsa `target` ile biten `string`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `string`: Aranır dize.<br /><br /> `target`: Hedef dizesi sonunda için arama `string`.<br /><br /> **Dönüş değeri**<br /><br /> `True`varsa `string` ile biten `target`; Aksi halde `false`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns true.`<br /><br /> `EndsWith('abc', 'bc')`**Not:** kullanıyorsanız [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] veri sağlayıcı, bu işlevi döndürür `false` dize sabit uzunluk dize sütununda depolanıyorsa ve `target` bir sabit değer. Bu durumda, sonunda boşluk doldurma dahil olmak üzere tüm dizeyi aranır. Sabit uzunluk dizesinde aşağıdaki örnekteki gibi veriler kırpma için olası bir geçici çözüm şöyledir:`EndsWith(TRIM(string), target)`|  
|`IndexOf(` `target`, `string``)`|Konumunu döndürür `target` içinde `string`, ya da 0 ise bulunamadı. Başlangıcı belirtmek için 1 döndürür `string`. Dizin numaralandırmaya 1'den başlar.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `target`: İçin arama dize.<br /><br /> `string`: Aranır dize.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns 4.`<br /><br /> `IndexOf('xyz', 'abcxyz')`|  
|`Left (` `string`, `length``)`|İlk döndürür `length` sol tarafındaki karakterlerinden `string`. Varsa uzunluğunu `string` olan değerinden `length`, tüm dizesi döndürdü.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `string`: A `String`.<br /><br /> `length`: Bir `Int16`, `Int32`, `Int64`, veya `Byte`. `length`sıfırdan küçük olamaz.<br /><br /> **Dönüş değeri**<br /><br /> A `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns abc.`<br /><br /> `Left('abcxyz', 3)`|  
|`Length (` `string` `)`|Döndürür (`Int32`) dizenin karakter cinsinden uzunluğu.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `string`: A `String`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns 6.`<br /><br /> `Legth('abcxyz')`|  
|`LTrim(` `string` `)`|Döndürür `string` öndeki boşlukları olmadan.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `String`.<br /><br /> **Dönüş değeri**<br /><br /> A `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns abc.`<br /><br /> `LTrim('   abc')`|  
|`Replace (` `string1`, `string2`, `string3``)`|Döndürür `string1`, tüm oluşumlarını ile `string2` yerine `string3`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `String`.<br /><br /> **Dönüş değeri**<br /><br /> A `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns abcxyz.`<br /><br /> `Concat('abc', 'xyz')`|  
|`Reverse (` `string` `)`|Döndürür `string` karakter sırasını tersine.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `String`.<br /><br /> **Dönüş değeri**<br /><br /> A `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns dcba.`<br /><br /> `Reverse('abcd')`|  
|`Right (` `string`, `length``)`|Son döndürür `length` gelen karakter `string`. Varsa uzunluğunu `string` olan değerinden `length`, tüm dizesi döndürdü.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `string`: A `String`.<br /><br /> `length`: Bir `Int16`, `Int32`, `Int64`, veya `Byte`. `length`sıfırdan küçük olamaz.<br /><br /> **Dönüş değeri**<br /><br /> A `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns xyz.`<br /><br /> `Right('abcxyz', 3)`|  
|`RTrim(` `string` `)`|Döndürür `string` sonunda boşluk olmadan.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `String`.<br /><br /> **Dönüş değeri**<br /><br /> A `String`.|  
|`Substring (` `string`, `start`, `length``)`|Alt konumdan başlayarak dizesini döndürür `start`, uzunluğa sahip `length` karakter. Dizenin ilk karakteri 1 başlangıcını gösterir. Dizin numaralandırmaya 1'den başlar.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `string`: A `String`.<br /><br /> `start`: Bir `Int16`, `Int32`, `Int64` ve `Byte`. `start`birden az olamaz.<br /><br /> `length`: Bir `Int16`, `Int32`, `Int64` ve `Byte`. `length`sıfırdan küçük olamaz.<br /><br /> **Dönüş değeri**<br /><br /> A `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns xyz.`<br /><br /> `Substring('abcxyz', 4, 3)`|  
|`StartsWith (` `string`, `target``)`|Döndürür `true` varsa `string` ile başlayan `target`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `string`: Aranır dize.<br /><br /> `target`: Hedef dize başlangıcında için arama `string`.<br /><br /> **Dönüş değeri**<br /><br /> `True`varsa `string` ile başlayan `target`; Aksi halde `false`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns true.`<br /><br /> `StartsWith('abc', 'ab')`|  
|`ToLower(` `string` `)`|Döndürür `string` küçük harfe büyük harfler ile.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `String`.<br /><br /> **Dönüş değeri**<br /><br /> A `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns abc.`<br /><br /> `ToLower('ABC')`|  
|`ToUpper(` `string` `)`|Döndürür `string` küçük harfler büyük harfe dönüştürülmüş ile.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `String`.<br /><br /> **Dönüş değeri**<br /><br /> A `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns ABC.`<br /><br /> `ToUpper('abc')`|  
|`Trim(` `string` `)`|Döndürür `string` öndeki ve sondaki boşlukları olmadan.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `String`.<br /><br /> **Dönüş değeri**<br /><br /> A `String`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns abc.`<br /><br /> `Trim('      abc   ')`|  
  
 Bu işlevler döndürülecek `null` verildiyse `null` giriş.  
  
 Microsoft SQL istemci yönetilen sağlayıcısında eşdeğer işlevselliği kullanılabilir. Daha fazla bilgi için bkz: [SqlClient Entity Framework işlevleri için](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kurallı İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
