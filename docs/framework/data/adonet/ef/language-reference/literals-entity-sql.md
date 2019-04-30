---
title: Değişmez değerler (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 092ef693-6e5f-41b4-b868-5b9e82928abf
ms.openlocfilehash: bff9b1907d3424dc2e3df80480b6ab12f5ab9261
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760668"
---
# <a name="literals-entity-sql"></a>Değişmez değerler (varlık SQL)
Bu konu başlığı altında açıklanır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] değişmez değerleri için destek.  
  
## <a name="null"></a>Null  
 Null değişmez değer, herhangi bir tür için null değeri temsil etmek için kullanılır. Bir null sabit değer herhangi bir türü ile uyumludur.  
  
 Türü belirlenmiş null değerlere bir dönüştürme işlemi tarafından null bir sabit değer oluşturulabilir. Daha fazla bilgi için [ATAMA](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md).  
  
 Null değişmez değerler kayan kuralları nereye hakkında ücretsiz için kullanılabilir, bkz: [Null değişmez değerler ve tür çıkarımı](../../../../../../docs/framework/data/adonet/ef/language-reference/null-literals-and-type-inference-entity-sql.md).  
  
## <a name="boolean"></a>Boole değeri  
 Anahtar sözcüklere göre Boole sabit değerleri temsil edilen `true` ve `false`.  
  
## <a name="integer"></a>Tamsayı  
 Tamsayı sabit değerleri türü olabilir <xref:System.Int32> veya <xref:System.Int64>. Bir <xref:System.Int32> bir sayısal karakter dizisi sabitidir. Bir <xref:System.Int64> sayısal karakter tarafından bir büyük harf l ardından dizi değişmez değeri  
  
## <a name="decimal"></a>Ondalık  
 Sabit noktalı bir sayı (ondalık), bir dizi sayısal karakterler, nokta (.) ve başka bir dizi bir büyük harf "M" harfinin sayısal karakter olabilir.  
  
## <a name="float-double"></a>Float, Double  
 Çift duyarlıklı kayan nokta sayısı, sayısal karakterler, nokta (.) ve başka bir seri büyük olasılıkla bir üs sayısal karakter dizisidir. Tek Precision bilgisayarlar bir kayan nokta numarası (veya float) olan bir çift duyarlıklı kayan noktası küçük f tarafından takip numarası söz dizimi.  
  
## <a name="string"></a>Dize  
 Bir dizeyi tırnak işaretleri içine alınmış karakter dizisidir. Tırnak işareti ya da hem tek tırnak olabilir (`'`) veya her iki çift tırnak ("). Unicode veya Unicode olmayan karakter dize sabit değerleri olabilir. Unicode değişmez bir karakter dizesi bildirmek için değişmez değerin büyük "N" ile önek. Unicode olmayan karakter dize sabit değerleri varsayılandır. Dize hazır değer yükü ile N arasındaki boşluk olabilir ve N büyük olmalıdır.  
  
```  
'hello' -- non-Unicode character string literal  
N'hello' -- Unicode character string literal  
"x"  
N"This is a string!"  
'so is THIS'  
```  
  
## <a name="datetime"></a>DateTime  
 Bir datetime hazır değerinde yerel bağımsızdır ve bir tarih bölümü ve bir saat bölümünü oluşur. Tarih ve saat bölümleri zorunludur ve varsayılan değerler yoktur.  
  
 Tarih bölümünü biçiminde olmalıdır: `YYYY` - `MM` - `DD`burada `YYYY` 0001 ve 9999 arasında dört basamaklı bir yıl değeri `MM` 1 ile 12 arasında bir ay ve `DD` olduğu belirli bir ay için geçerli olan gün değer `MM`.  
  
 Saat bölümünü biçiminde olmalıdır: `HH`:`MM`[:`SS`[.fffffff]] burada `HH` 0 ile 23 arasında saat değeri `MM` 0 ile 59 arasında dakika değeri `SS` ikinci değer 0 ile 59 arasında ve fffffff 0 ile 9999999 arasında kesirli ikinci değer. Tüm değer aralıklarına dahildir. Kesirli saniye isteğe bağlıdır. Kesirli saniye belirtilmediği sürece saniye isteğe bağlıdır; Bu durumda, saniye gereklidir. Sıfır varsayılan değeri, saniyeler veya kesirli saniye belirtilmedi, bunun yerine kullanılır.  
  
 Herhangi bir sayıda DATETIME sembol ve hazır değer yükü, ancak hiç yeni satır arasında boşluk olabilir.  
  
```  
DATETIME'2006-10-1 23:11'  
DATETIME'2006-12-25 01:01:00.0000000' -- same as DATETIME'2006-12-25 01:01'  
```  
  
## <a name="time"></a>Zaman  
 Bir değişmez değer yerel ayar bağımsızdır ve yalnızca saat bölümünü oluştuğu zamandır. Saat bölümünü zorunludur ve varsayılan değer yoktur. Ss: dd biçiminde olmalıdır [: SS [.fffffff]], değer olan 0 ile 23 arasında saat değeri MM 0 ile 59 arasında dakika değeri, SS ise ikinci değer 0 ile 59 arasında ve fffffff ikinci basamağını HH 0 ile 9999999 arasında burada. Tüm değer aralıklarına dahildir. Kesirli saniye isteğe bağlıdır. Kesirli saniye belirtilmediği sürece saniye isteğe bağlıdır; Bu durumda, saniye gereklidir. Varsayılan değer sıfır, saniye veya kesir belirtilmedi, bunun yerine kullanılır.  
  
 Herhangi bir sayıda zaman sembol ve hazır değer yükü, ancak hiç yeni satır arasında boşluk olabilir.  
  
```  
TIME‘23:11’  
TIME‘01:01:00.1234567’  
```  
  
## <a name="datetimeoffset"></a>DateTimeOffset  
 Yerel ayar bağımsızdır ve bir tarih bölümü, bir saat bölümünü ve uzaklık bir bölümü oluşan bir datetimeoffset hazır. Tüm tarih ve saat uzaklık bölümleri zorunludur ve varsayılan değerler yoktur. Tarih biçimi YYYY-AA-YYYY 0001 ve 9999 arasında dört basamaklı bir yıl değeri olduğu gg bölümü olmalıdır aa 1 ile 12 arasında bir ay ve DD belirli bir ay için geçerli olan gün değerdir. Saat bölümünü ss: dd biçiminde olmalıdır [: SS [.fffffff]], ss dd, 0 ve 23 arasında saat değeri 0 ile 59, SS arasında dakika değerdir olduğu ikinci değer 0 ile 59 arasında ve fffffff 0 ile 9999999 arasında kesirli ikinci değer. Tüm değer aralıklarına dahildir. Kesirli saniye isteğe bağlıdır. Kesirli saniye belirtilmediği sürece saniye isteğe bağlıdır; Bu durumda, saniye gereklidir. Varsayılan değer sıfır, saniye veya kesir belirtilmedi, bunun yerine kullanılır. Uzaklık bölümü biçiminde olmalıdır {+&#124;-} ss: dd HH ve MM sahip olduğu saat bölümünü olduğu gibi aynı anlama. Uzaklık, ancak dizi-14 arasında olmalıdır: 00 ve + 14:00  
  
 Herhangi bir sayıda DATETIMEOFFSET sembol ve hazır değer yükü, ancak hiç yeni satır arasında boşluk olabilir.  
  
```  
DATETIMEOFFSET‘2006-10-1 23:11 +02:00’  
DATETIMEOFFSET‘2006-12-25 01:01:00.0000000 -08:30’  
```  
  
> [!NOTE]
>  Geçerli bir varlık SQL değişmez değer dışında desteklenen aralıkları CLR veya veri kaynağı için gelebilir. Bu, bir özel durum neden olabilir  
  
## <a name="binary"></a>İkili  
 İkili anahtar sözcüğünü izleyen tek tırnak işareti veya kısayol sembol tarafından ayrılmış onaltılık basamak sırasının ve ikili dize değişmez değeri olan `X` veya `x`. Kısayol sembol `X` büyük/küçük harfe duyarlıdır. Sıfır veya daha fazla boşluk anahtar sözcüğü arasında izin `binary` ve ikili dize değeri.  
  
 Onaltılık karakter ayrıca büyük küçük harfe duyarlı değildir. Değişmez değer tek sayıda onaltılık basamak oluşuyorsa, değişmez değer için sonraki bile onaltılık basamak ile bir onaltılık değişmez değerin önüne sıfır basamak hizalanır. İkili dosya dizesine boyutuna biçimsel bir sınır yoktur.  
  
```  
Binary'00ffaabb'  
X'ABCabc'  
BINARY    '0f0f0f0F0F0F0F0F0F0F'  
X'' –- empty binary string  
```  
  
## <a name="guid"></a>Guid  
 A `GUID` değişmez değeri genel olarak benzersiz bir tanımlayıcı temsil eder. Anahtar sözcüğü tarafından oluşturulmuş bir dizisi olduğundan `GUID` onaltılık basamak olarak bilinen biçiminde ardından *kayıt defteri* biçimi: 8-4-4-4-tek tırnak içinde 12. Onaltılık basamak büyük/küçük harfe duyarsızdır.  
  
 Herhangi bir sayıda GUID sembol ve hazır değer yükü, ancak hiç yeni satır arasında boşluk olabilir.  
  
```  
Guid'1afc7f5c-ffa0-4741-81cf-f12eAAb822bf'  
GUID  '1AFC7F5C-FFA0-4741-81CF-F12EAAB822BF'  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
