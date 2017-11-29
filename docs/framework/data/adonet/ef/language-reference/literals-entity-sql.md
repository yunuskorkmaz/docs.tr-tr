---
title: "Değişmez değerler (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 092ef693-6e5f-41b4-b868-5b9e82928abf
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 50edfb344177dbec8cff9609aeab56d1db762eb7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="literals-entity-sql"></a>Değişmez değerler (varlık SQL)
Bu konuda açıklanmaktadır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] desteklemek için hazır.  
  
## <a name="null"></a>Null  
 Null sabit değer herhangi bir tür için null değeri temsil etmek için kullanılır. Bir null hazır değeri herhangi bir türü ile uyumludur.  
  
 Tür null bir null hazır değeri bir cast tarafından oluşturulabilir. Daha fazla bilgi için bkz: [CAST](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md).  
  
 Kayan kuralları hakkında nereden serbest için null değişmez değerleri kullanılabilmesi için bkz: [Null değişmez değerler ve tür çıkarımı](../../../../../../docs/framework/data/adonet/ef/language-reference/null-literals-and-type-inference-entity-sql.md).  
  
## <a name="boolean"></a>Boole değeri  
 Anahtar sözcükleri Boolean değişmez değerleri temsil edilen `true` ve `false`.  
  
## <a name="integer"></a>Tamsayı  
 Tamsayı değişmez değerleri türü olabilir <xref:System.Int32> veya <xref:System.Int64>. Bir <xref:System.Int32> sayısal karakterler değişmez değer dizisidir. Bir <xref:System.Int64> sayısal karakterler bir Büyük Harf L. tarafından izlenen bir dizi değişmez değer  
  
## <a name="decimal"></a>Ondalık  
 Bir sabit noktalı (ondalık) bir dizi sayısal karakterler, nokta (.) ve bir büyük harf "M tarafından" sayısal karakterlik başka bir dizi sayıdır.  
  
## <a name="float-double"></a>Double float  
 Çift duyarlıklı kayan nokta sayısı, sayısal karakterler, nokta (.) ve sayısal karakter büyük olasılıkla bir üs tarafından ardından başka bir dizi dizisidir. Tek Precision bilgisayarlar bir sayı (veya float) olan bir çift duyarlıklı kayan nokta kayan nokta küçük f tarafından izlenen sayı sözdizimi.  
  
## <a name="string"></a>Dize  
 Bir dizi tırnak işaretleri içine karakter dizesidir. Tırnak işareti ya da hem tek tırnak olabilir (`'`) veya her iki çift tırnak ("). Karakter dizelerini Unicode veya Unicode olmayan olabilir. Bir karakter dizesi Unicode olarak değişmez değer bildirmek için sabit bir büyük harf "N" ile önek. Unicode olmayan karakter dizelerini varsayılandır. N dize sabit değeri yükü arasındaki boşluk olamaz ve N büyük olması gerekir.  
  
```  
'hello' -- non-Unicode character string literal  
N'hello' -- Unicode character string literal  
"x"  
N"This is a string!"  
'so is THIS'  
```  
  
## <a name="datetime"></a>DateTime  
 Datetime hazır değerinde yerel bağımsızdır ve bir tarih bölümü ve bir saat bölümünü oluşur. Tarih ve saat bölümleri zorunludur ve varsayılan değer yok.  
  
 Tarih bölümünü biçiminde olmalıdır: `YYYY` - `MM` - `DD`, burada `YYYY` 0001-9999 arasında bir dört basamaklı yıl değer olan `MM` 1 ile 12 arasında ay ve `DD` olduğu verilen ayı için geçerli olduğu gün değeri `MM`.  
  
 Saat bölümünü biçiminde olmalıdır: `HH`:`MM`[:`SS`[.fffffff]] burada `HH` 0 ile 23 arasında saat değeridir `MM` minute değeri 0 ile 59 arasında `SS` ikinci değer 0 ile 59 arasında ve fffffff 0 ile 9999999 arasında kesirli ikinci değer. Tüm değer aralıklar dahildir. Kesirli saniye isteğe bağlıdır. Kesirli saniye belirtilmedikçe saniye isteğe bağlıdır; Bu durumda, saniye gereklidir. Saniye veya kesirli saniye belirtilmezse, varsayılan değerin sıfır yerine kullanılır.  
  
 DATETIME simgesi ve hazır değer yükü, ancak hiç yeni satır arasında boşluk herhangi bir sayıda olabilir.  
  
```  
DATETIME'2006-10-1 23:11'  
DATETIME'2006-12-25 01:01:00.0000000' -- same as DATETIME'2006-12-25 01:01'  
```  
  
## <a name="time"></a>Zaman  
 Bir değişmez değer yerel bağımsızdır ve yalnızca zaman bölümünün oluşan zamandır. Saat bölümünü zorunludur ve varsayılan değer yoktur. Ss: dd biçiminde olmalıdır [: SS [.fffffff]], değer olan 0 ile 23 arasında saat değeri MM 0 ile 59 arasında dakika değeri, SS 0 ile 59 arasında ikinci değerdir ve fffffff ikinci kesir HH burada 0 ile 9999999 arasında. Tüm değer aralıklar dahildir. Kesirli saniye isteğe bağlıdır. Kesirli saniye belirtilmedikçe saniye isteğe bağlıdır; Bu durumda, saniye gereklidir. Saniye veya kesir belirtilmezse, varsayılan değerin sıfır yerine kullanılır.  
  
 Herhangi bir sayıda saati sembolü ve hazır değer yükü, ancak hiç yeni satır arasında boşluk olabilir.  
  
```  
TIME‘23:11’  
TIME‘01:01:00.1234567’  
```  
  
## <a name="datetimeoffset"></a>DateTimeOffset  
 Datetimeoffset sabit değeri yerel bağımsızdır ve oluşan bir tarih bölümü, bir saat bölümünü ve uzaklık bir parçası olur. Tüm tarih, saat ve uzaklık bölümleri zorunludur ve varsayılan değer yok. Bölümü YYYY-AA-YYYY 0001 ile 9999 arasında dört rakamlı yıl değeri olduğu, gg biçiminde olmalıdır tarih dd 1 ile 12 arasında ayı ve GG verilen ayı için geçerli olduğu gün değerdir. Saat bölümünü ss: dd biçiminde olmalıdır [: SS [.fffffff]] HH MM 0 ve 23 arasında saat değeri 0 ile 59, SS arasındaki dakika değerdir ikinci değer 0 ile 59 arasında olduğu ve fffffff olan 0 ile 9999999 arasında kesirli ikinci değer. Tüm değer aralıklar dahildir. Kesirli saniye isteğe bağlıdır. Kesirli saniye belirtilmedikçe saniye isteğe bağlıdır; Bu durumda, saniye gereklidir. Saniye veya kesir belirtilmezse, varsayılan değerin sıfır yerine kullanılır. Uzaklık bölümü biçiminde olmalıdır {+ &#124;-} ss: dd ss ve MM sahip olduğu saat bölümünü olduğu gibi aynı anlama. Uzaklık, ancak dizi-14 arasında olması gerekir: 00 ve + 14:00  
  
 DATETIMEOFFSET simgesi ve hazır değer yükü, ancak hiç yeni satır arasında boşluk herhangi bir sayıda olabilir.  
  
```  
DATETIMEOFFSET‘2006-10-1 23:11 +02:00’  
DATETIMEOFFSET‘2006-12-25 01:01:00.0000000 -08:30’  
```  
  
> [!NOTE]
>  Geçerli bir varlık SQL değişmez değer CLR veya veri kaynağı için desteklenen aralık dışında dönebilir. Bu, bir özel durum neden  
  
## <a name="binary"></a>İkili  
 Bir ikili dize sabit değeri bir ikili anahtar sözcüğünü izleyen tek tırnak veya kısayol simgesini tarafından ayrılmış onaltılık rakam dizisini olan `X` veya `x`. Kısayol simgesi `X` büyük/küçük harfe duyarlıdır. Sıfır veya daha fazla alanları arasında anahtar sözcüğü izin `binary` ve ikili dize değeri.  
  
 Onaltılık karakterler ayrıca büyük küçük harfe duyarlı değildir. Değişmez değeri bir onaltılık basamak tek sayıda oluşuyorsa, sabit sonraki bile onaltılık basamak değişmez değeri bir onaltılık ile ekleyerek sıfır basamaklı hizalanır. İkili dosya dizesine boyutuna resmi bir sınır yoktur.  
  
```  
Binary'00ffaabb'  
X'ABCabc'  
BINARY    '0f0f0f0F0F0F0F0F0F0F'  
X'' –- empty binary string  
```  
  
## <a name="guid"></a>Guid  
 A `GUID` değişmez değeri bir genel benzersiz tanımlayıcısını temsil eder. Anahtar sözcüğe göre biçimlendirilmiş bir dizisi olduğundan `GUID` olarak bilinen formunda onaltılık basamak arkasından *kayıt defteri* biçimi: 8-4-4-4-tek tırnak içine alınmış 12. Onaltılık basamak büyük/küçük harfe duyarsızdır.  
  
 Herhangi bir sayıda GUID simgesi ve hazır değer yükü, ancak hiç yeni satır arasında boşluk olabilir.  
  
```  
Guid'1afc7f5c-ffa0-4741-81cf-f12eAAb822bf'  
GUID  '1AFC7F5C-FFA0-4741-81CF-F12EAAB822BF'  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık SQL genel bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
