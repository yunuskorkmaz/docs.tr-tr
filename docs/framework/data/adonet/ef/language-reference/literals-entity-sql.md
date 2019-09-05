---
title: Değişmez değerler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 092ef693-6e5f-41b4-b868-5b9e82928abf
ms.openlocfilehash: 9aba737b522f75f1f81cc054fb87b414b06f9611
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250346"
---
# <a name="literals-entity-sql"></a>Değişmez değerler (Entity SQL)
Bu konuda, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] değişmez değer desteği açıklanmaktadır.  
  
## <a name="null"></a>Null  
 Null sabit değeri herhangi bir tür için null değerini temsil etmek için kullanılır. Null sabit değeri herhangi bir türle uyumludur.  
  
 Türü belirtilmiş null değerler, null değişmez değer üzerinden bir atama ile oluşturulabilir. Daha fazla bilgi için bkz. [cast](cast-entity-sql.md).  
  
 Boş kayan null sabit değerlerinin kullanılabileceği durumlar hakkında kurallar için bkz. [null sabit değerler ve tür çıkarımı](null-literals-and-type-inference-entity-sql.md).  
  
## <a name="boolean"></a>Boole değeri  
 Boole sabit değerleri, anahtar kelimeleri `true` ve `false`ile temsil edilir.  
  
## <a name="integer"></a>Integer  
 Tamsayı sabit değerleri veya <xref:System.Int32> <xref:System.Int64>türünde olabilir. <xref:System.Int32> Değişmez değer bir dizi sayısal karakterdir. <xref:System.Int64> Sabit değer, bir büyük harf ile izlenen sayısal karakterlerin serisidir.  
  
## <a name="decimal"></a>Ondalık  
 Sabit noktalı sayı (ondalık), bir dizi sayısal karakter, nokta (.) ve başka bir sayısal karakter serisi, büyük bir "ı" ile izlenir.  
  
## <a name="float-double"></a>Float, Double  
 Çift duyarlıklı kayan noktalı sayı, bir dizi sayısal karakter, nokta (.) ve başka bir sayısal karakter serisi olabilir. Tek duyarlıklı kayan noktalı sayı (veya float), bir çift duyarlıklı kayan noktalı sayı sözdizimidir ve ardından küçük harfli f.  
  
## <a name="string"></a>Dize  
 Dize, tırnak işaretleri içine alınmış bir karakter dizisidir. Tırnak işaretleri hem tek tırnak (`'`) hem de çift tırnak (") olabilir. Karakter dizesi sabit değerleri Unicode veya Unicode olmayan bir değer olabilir. Unicode olarak bir karakter dizesi hazır değeri bildirmek için, sabit değeri büyük harfle ("N") önek olarak ekleyin. Varsayılan değer Unicode olmayan karakter dizesi değişmez değerleri. N ile dize değişmez değeri arasında boşluk olamaz ve N büyük harf olmalıdır.  
  
```  
'hello' -- non-Unicode character string literal  
N'hello' -- Unicode character string literal  
"x"  
N"This is a string!"  
'so is THIS'  
```  
  
## <a name="datetime"></a>DateTime  
 DateTime sabit değeri yerel ayardan bağımsızdır ve bir tarih bölümünden ve saat bölümünden oluşur. Hem tarih hem de saat bölümlerinin ikisi de zorunludur ve varsayılan değer yoktur.  
  
 `YYYY`Tarih kısmı şu biçimde olmalıdır: - `DD` `MM` , burada 0001`YYYY` ve 9999 arasında dört basamaklı bir yıl değeri, 1 ile `MM`12arasındaki ay-ve `DD` belirtilen ay `MM`için geçerli olan gün değeri.  
  
 Zaman `HH`kısmı`MM` 0ile`SS` 23 arasında bir saat değeri olan 0 ile 23 `MM` arasında bir Hour değeri olan 0 ile 59 arasında bir dakika değeri, 0 ile 59 arasındaki ikinci değerdir.`SS` `HH` ve fffffff 0 ile 9999999 arasında kesirli ikinci değerdir. Tüm değer aralıkları dahil değildir. Kesirli saniyeler isteğe bağlıdır. Kesirli saniyeler belirtilmediği takdirde saniyeler isteğe bağlıdır; Bu durumda, saniyeler gereklidir. Saniye veya Kesirli saniyeler belirtilmediğinde bunun yerine varsayılan sıfır değeri kullanılır.  
  
 DATETIME simgesiyle sabit değer yükü arasında herhangi bir sayıda boşluk olabilir, ancak yeni satır yoktur.  
  
```  
DATETIME'2006-10-1 23:11'  
DATETIME'2006-12-25 01:01:00.0000000' -- same as DATETIME'2006-12-25 01:01'  
```  
  
## <a name="time"></a>Zaman  
 Bir zaman sabiti, yerel ayardan bağımsızdır ve yalnızca bir zaman kısmından oluşur. Saat bölümü zorunludur ve varsayılan değer yoktur. HH: MM [: SS [. fffffff]] biçiminde olmalıdır; burada ss, 0 ile 23 arasında bir Hour değeridir, 59 MM 0 ile 59 arasındaki ikinci değerdir ve fffffff 0 ile 9999999 arasında ikinci kesir değeridir. Tüm değer aralıkları dahil değildir. Kesirli saniyeler isteğe bağlıdır. Kesirli saniyeler belirtilmediği takdirde saniyeler isteğe bağlıdır; Bu durumda, saniyeler gereklidir. Saniyeler veya kesirler belirtilmediğinde bunun yerine varsayılan sıfır değeri kullanılır.  
  
 ZAMAN simgesi ve değişmez değer yükü arasında herhangi bir sayıda boşluk olabilir, ancak yeni satır olamaz.  
  
```  
TIME‘23:11’  
TIME‘01:01:00.1234567’  
```  
  
## <a name="datetimeoffset"></a>DateTimeOffset  
 DateTimeOffset sabit değeri yerel ayardan bağımsızdır ve bir tarih bölümünden, bir saat bölümünden ve bir konum bölümünden oluşur. Tüm tarih, saat ve konum bölümleri zorunludur ve varsayılan değer yoktur. Tarih kısmı YYYY-AA-GG biçiminde olmalıdır. burada YYYY, 0001 ile 9999 arasında dört basamaklı bir yıl değeri, aa ise 1 ile 12 arasında bir, gg ise verilen ay için geçerli olan gün değeridir. Zaman bölümü HH: MM [: SS [. fffffff]] biçiminde olmalıdır; burada ss, 0 ile 23 arasında bir Hour değeri, 59 MM 0 ile 59 arasındaki ikinci değerdir ve fffffff 0 ile 9999999 arasındaki kesirli ikinci değerdir. Tüm değer aralıkları dahil değildir. Kesirli saniyeler isteğe bağlıdır. Kesirli saniyeler belirtilmediği takdirde saniyeler isteğe bağlıdır; Bu durumda, saniyeler gereklidir. Saniyeler veya kesirler belirtilmediğinde bunun yerine varsayılan sıfır değeri kullanılır. Konum bölümü {+&#124;-} hh: mm biçiminde olmalıdır; burada SS ve dd, saat bölümünde olduğu gibi anlamdadır. Ancak, kaydırın aralığı-14:00 ile + 14:00 arasında olmalıdır  
  
 DATETIMEOFFSET sembolü ve değişmez değer yükü arasında herhangi bir sayıda boşluk olabilir, ancak yeni satır olamaz.  
  
```  
DATETIMEOFFSET‘2006-10-1 23:11 +02:00’  
DATETIMEOFFSET‘2006-12-25 01:01:00.0000000 -08:30’  
```  
  
> [!NOTE]
> Geçerli bir Entity SQL sabit değeri CLR veya veri kaynağı için desteklenen aralıkların dışında olabilir. Bu durum bir özel durumla sonuçlanabilir  
  
## <a name="binary"></a>İkili  
 İkili dize sabit değeri, ikili anahtar veya kısayol simgesi `X` ya da ya da ya da ya da ya da ya da ya da ya da ya `x`da ' Kısayol sembolü `X` büyük/küçük harfe duyarlıdır. Anahtar sözcüğü `binary` ve ikili dize değeri arasında sıfır veya daha fazla boşluk kullanılabilir.  
  
 Onaltılık karakterler de büyük/küçük harfe duyarlıdır. Sabit değer tek sayıda onaltılı basamaktan oluşuyorsa, değişmez değer, onaltılı sıfır basamağı ile değişmez değer eklenerek, sonraki çift onaltılık basamağa hizalanır. İkili dizenin boyutunda bir biçimsel sınır yoktur.  
  
```  
Binary'00ffaabb'  
X'ABCabc'  
BINARY    '0f0f0f0F0F0F0F0F0F0F'  
X'' –- empty binary string  
```  
  
## <a name="guid"></a>Guid  
 `GUID` Değişmez değer, genel olarak benzersiz tanımlayıcıyı temsil eder. Bu, anahtar sözcüğü `GUID` tarafından oluşturulan ve ardından form, *kayıt defteri* biçimi olarak bilinen onaltılık basamaklardan oluşan bir dizidir: 8-4-4-4-12 tek tırnak içine alınmıştır. Onaltılık basamaklar büyük/küçük harfe duyarlıdır.  
  
 GUID sembolü ve değişmez değer yükü arasında herhangi bir sayıda boşluk olabilir, ancak yeni satır olamaz.  
  
```  
Guid'1afc7f5c-ffa0-4741-81cf-f12eAAb822bf'  
GUID  '1AFC7F5C-FFA0-4741-81CF-F12EAAB822BF'  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
