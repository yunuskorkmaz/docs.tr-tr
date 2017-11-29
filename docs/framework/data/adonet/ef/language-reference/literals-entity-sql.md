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
# <a name="literals-entity-sql"></a><span data-ttu-id="99214-102">Değişmez değerler (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="99214-102">Literals (Entity SQL)</span></span>
<span data-ttu-id="99214-103">Bu konuda açıklanmaktadır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] desteklemek için hazır.</span><span class="sxs-lookup"><span data-stu-id="99214-103">This topic describes [!INCLUDE[esql](../../../../../../includes/esql-md.md)] support for literals.</span></span>  
  
## <a name="null"></a><span data-ttu-id="99214-104">Null</span><span class="sxs-lookup"><span data-stu-id="99214-104">Null</span></span>  
 <span data-ttu-id="99214-105">Null sabit değer herhangi bir tür için null değeri temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="99214-105">The null literal is used to represent the value null for any type.</span></span> <span data-ttu-id="99214-106">Bir null hazır değeri herhangi bir türü ile uyumludur.</span><span class="sxs-lookup"><span data-stu-id="99214-106">A null literal is compatible with any type.</span></span>  
  
 <span data-ttu-id="99214-107">Tür null bir null hazır değeri bir cast tarafından oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="99214-107">Typed nulls can be created by a cast over a null literal.</span></span> <span data-ttu-id="99214-108">Daha fazla bilgi için bkz: [CAST](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="99214-108">For more information, see [CAST](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md).</span></span>  
  
 <span data-ttu-id="99214-109">Kayan kuralları hakkında nereden serbest için null değişmez değerleri kullanılabilmesi için bkz: [Null değişmez değerler ve tür çıkarımı](../../../../../../docs/framework/data/adonet/ef/language-reference/null-literals-and-type-inference-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="99214-109">For rules about where free floating null literals can be used, see [Null Literals and Type Inference](../../../../../../docs/framework/data/adonet/ef/language-reference/null-literals-and-type-inference-entity-sql.md).</span></span>  
  
## <a name="boolean"></a><span data-ttu-id="99214-110">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="99214-110">Boolean</span></span>  
 <span data-ttu-id="99214-111">Anahtar sözcükleri Boolean değişmez değerleri temsil edilen `true` ve `false`.</span><span class="sxs-lookup"><span data-stu-id="99214-111">Boolean literals are represented by the keywords `true` and `false`.</span></span>  
  
## <a name="integer"></a><span data-ttu-id="99214-112">Tamsayı</span><span class="sxs-lookup"><span data-stu-id="99214-112">Integer</span></span>  
 <span data-ttu-id="99214-113">Tamsayı değişmez değerleri türü olabilir <xref:System.Int32> veya <xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="99214-113">Integer literals can be of type <xref:System.Int32> or <xref:System.Int64>.</span></span> <span data-ttu-id="99214-114">Bir <xref:System.Int32> sayısal karakterler değişmez değer dizisidir.</span><span class="sxs-lookup"><span data-stu-id="99214-114">An <xref:System.Int32> literal is a series of numeric characters.</span></span> <span data-ttu-id="99214-115">Bir <xref:System.Int64> sayısal karakterler bir Büyük Harf L. tarafından izlenen bir dizi değişmez değer</span><span class="sxs-lookup"><span data-stu-id="99214-115">An <xref:System.Int64> literal is series of numeric characters followed by an uppercase L.</span></span>  
  
## <a name="decimal"></a><span data-ttu-id="99214-116">Ondalık</span><span class="sxs-lookup"><span data-stu-id="99214-116">Decimal</span></span>  
 <span data-ttu-id="99214-117">Bir sabit noktalı (ondalık) bir dizi sayısal karakterler, nokta (.) ve bir büyük harf "M tarafından" sayısal karakterlik başka bir dizi sayıdır.</span><span class="sxs-lookup"><span data-stu-id="99214-117">A fixed-point number (decimal) is a series of numeric characters, a dot (.) and another series of numeric characters followed by an uppercase "M".</span></span>  
  
## <a name="float-double"></a><span data-ttu-id="99214-118">Double float</span><span class="sxs-lookup"><span data-stu-id="99214-118">Float, Double</span></span>  
 <span data-ttu-id="99214-119">Çift duyarlıklı kayan nokta sayısı, sayısal karakterler, nokta (.) ve sayısal karakter büyük olasılıkla bir üs tarafından ardından başka bir dizi dizisidir.</span><span class="sxs-lookup"><span data-stu-id="99214-119">A double-precision floating point number is a series of numeric characters, a dot (.) and another series of numeric characters possibly followed by an exponent.</span></span> <span data-ttu-id="99214-120">Tek Precision bilgisayarlar bir sayı (veya float) olan bir çift duyarlıklı kayan nokta kayan nokta küçük f tarafından izlenen sayı sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="99214-120">A single-precisions floating point number (or float) is a double-precision floating point number syntax followed by the lowercase f.</span></span>  
  
## <a name="string"></a><span data-ttu-id="99214-121">Dize</span><span class="sxs-lookup"><span data-stu-id="99214-121">String</span></span>  
 <span data-ttu-id="99214-122">Bir dizi tırnak işaretleri içine karakter dizesidir.</span><span class="sxs-lookup"><span data-stu-id="99214-122">A string is a series of characters enclosed in quote marks.</span></span> <span data-ttu-id="99214-123">Tırnak işareti ya da hem tek tırnak olabilir (`'`) veya her iki çift tırnak (").</span><span class="sxs-lookup"><span data-stu-id="99214-123">Quotes can be either both single-quotes (`'`) or both double-quotes (").</span></span> <span data-ttu-id="99214-124">Karakter dizelerini Unicode veya Unicode olmayan olabilir.</span><span class="sxs-lookup"><span data-stu-id="99214-124">Character string literals can be either Unicode or non-Unicode.</span></span> <span data-ttu-id="99214-125">Bir karakter dizesi Unicode olarak değişmez değer bildirmek için sabit bir büyük harf "N" ile önek.</span><span class="sxs-lookup"><span data-stu-id="99214-125">To declare a character string literal as Unicode, prefix the literal with an uppercase "N".</span></span> <span data-ttu-id="99214-126">Unicode olmayan karakter dizelerini varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="99214-126">The default is non-Unicode character string literals.</span></span> <span data-ttu-id="99214-127">N dize sabit değeri yükü arasındaki boşluk olamaz ve N büyük olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="99214-127">There can be no spaces between the N and the string literal payload, and the N must be uppercase.</span></span>  
  
```  
'hello' -- non-Unicode character string literal  
N'hello' -- Unicode character string literal  
"x"  
N"This is a string!"  
'so is THIS'  
```  
  
## <a name="datetime"></a><span data-ttu-id="99214-128">DateTime</span><span class="sxs-lookup"><span data-stu-id="99214-128">DateTime</span></span>  
 <span data-ttu-id="99214-129">Datetime hazır değerinde yerel bağımsızdır ve bir tarih bölümü ve bir saat bölümünü oluşur.</span><span class="sxs-lookup"><span data-stu-id="99214-129">A datetime literal is independent of locale and is composed of a date part and a time part.</span></span> <span data-ttu-id="99214-130">Tarih ve saat bölümleri zorunludur ve varsayılan değer yok.</span><span class="sxs-lookup"><span data-stu-id="99214-130">Both date and time parts are mandatory and there are no default values.</span></span>  
  
 <span data-ttu-id="99214-131">Tarih bölümünü biçiminde olmalıdır: `YYYY` - `MM` - `DD`, burada `YYYY` 0001-9999 arasında bir dört basamaklı yıl değer olan `MM` 1 ile 12 arasında ay ve `DD` olduğu verilen ayı için geçerli olduğu gün değeri `MM`.</span><span class="sxs-lookup"><span data-stu-id="99214-131">The date part must have the format: `YYYY`-`MM`-`DD`, where `YYYY` is a four digit year value between 0001 and 9999, `MM` is the month between 1 and 12 and `DD` is the day value that is valid for the given month `MM`.</span></span>  
  
 <span data-ttu-id="99214-132">Saat bölümünü biçiminde olmalıdır: `HH`:`MM`[:`SS`[.fffffff]] burada `HH` 0 ile 23 arasında saat değeridir `MM` minute değeri 0 ile 59 arasında `SS` ikinci değer 0 ile 59 arasında ve fffffff 0 ile 9999999 arasında kesirli ikinci değer.</span><span class="sxs-lookup"><span data-stu-id="99214-132">The time part must have the format: `HH`:`MM`[:`SS`[.fffffff]], where `HH` is the hour value between 0 and 23, `MM` is the minute value between 0 and 59, `SS` is the second value between 0 and 59 and fffffff is the fractional second value between 0 and 9999999.</span></span> <span data-ttu-id="99214-133">Tüm değer aralıklar dahildir.</span><span class="sxs-lookup"><span data-stu-id="99214-133">All value ranges are inclusive.</span></span> <span data-ttu-id="99214-134">Kesirli saniye isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="99214-134">Fractional seconds are optional.</span></span> <span data-ttu-id="99214-135">Kesirli saniye belirtilmedikçe saniye isteğe bağlıdır; Bu durumda, saniye gereklidir.</span><span class="sxs-lookup"><span data-stu-id="99214-135">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="99214-136">Saniye veya kesirli saniye belirtilmezse, varsayılan değerin sıfır yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="99214-136">When seconds or fractional seconds are not specified, the default value of zero will be used instead.</span></span>  
  
 <span data-ttu-id="99214-137">DATETIME simgesi ve hazır değer yükü, ancak hiç yeni satır arasında boşluk herhangi bir sayıda olabilir.</span><span class="sxs-lookup"><span data-stu-id="99214-137">There can be any number of spaces between the DATETIME symbol and the literal payload, but no new lines.</span></span>  
  
```  
DATETIME'2006-10-1 23:11'  
DATETIME'2006-12-25 01:01:00.0000000' -- same as DATETIME'2006-12-25 01:01'  
```  
  
## <a name="time"></a><span data-ttu-id="99214-138">Zaman</span><span class="sxs-lookup"><span data-stu-id="99214-138">Time</span></span>  
 <span data-ttu-id="99214-139">Bir değişmez değer yerel bağımsızdır ve yalnızca zaman bölümünün oluşan zamandır.</span><span class="sxs-lookup"><span data-stu-id="99214-139">A time literal is independent of locale and composed of a time part only.</span></span> <span data-ttu-id="99214-140">Saat bölümünü zorunludur ve varsayılan değer yoktur.</span><span class="sxs-lookup"><span data-stu-id="99214-140">The time part is mandatory and there is no default value.</span></span> <span data-ttu-id="99214-141">Ss: dd biçiminde olmalıdır [: SS [.fffffff]], değer olan 0 ile 23 arasında saat değeri MM 0 ile 59 arasında dakika değeri, SS 0 ile 59 arasında ikinci değerdir ve fffffff ikinci kesir HH burada 0 ile 9999999 arasında.</span><span class="sxs-lookup"><span data-stu-id="99214-141">It must have the format HH:MM[:SS[.fffffff]], where HH is the hour value between 0 and 23, MM is the minute value between 0 and 59, SS is the second value between 0 and 59, and fffffff is the second fraction value between 0 and 9999999.</span></span> <span data-ttu-id="99214-142">Tüm değer aralıklar dahildir.</span><span class="sxs-lookup"><span data-stu-id="99214-142">All value ranges are inclusive.</span></span> <span data-ttu-id="99214-143">Kesirli saniye isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="99214-143">Fractional seconds are optional.</span></span> <span data-ttu-id="99214-144">Kesirli saniye belirtilmedikçe saniye isteğe bağlıdır; Bu durumda, saniye gereklidir.</span><span class="sxs-lookup"><span data-stu-id="99214-144">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="99214-145">Saniye veya kesir belirtilmezse, varsayılan değerin sıfır yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="99214-145">When seconds or fractions are not specified, the default value of zero will be used instead.</span></span>  
  
 <span data-ttu-id="99214-146">Herhangi bir sayıda saati sembolü ve hazır değer yükü, ancak hiç yeni satır arasında boşluk olabilir.</span><span class="sxs-lookup"><span data-stu-id="99214-146">There can be any number of spaces between the TIME symbol and the literal payload, but no new lines.</span></span>  
  
```  
TIME‘23:11’  
TIME‘01:01:00.1234567’  
```  
  
## <a name="datetimeoffset"></a><span data-ttu-id="99214-147">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="99214-147">DateTimeOffset</span></span>  
 <span data-ttu-id="99214-148">Datetimeoffset sabit değeri yerel bağımsızdır ve oluşan bir tarih bölümü, bir saat bölümünü ve uzaklık bir parçası olur.</span><span class="sxs-lookup"><span data-stu-id="99214-148">A datetimeoffset literal is independent of locale and composed of a date part, a time part, and an offset part.</span></span> <span data-ttu-id="99214-149">Tüm tarih, saat ve uzaklık bölümleri zorunludur ve varsayılan değer yok.</span><span class="sxs-lookup"><span data-stu-id="99214-149">All date, time, and offset parts are mandatory and there are no default values.</span></span> <span data-ttu-id="99214-150">Bölümü YYYY-AA-YYYY 0001 ile 9999 arasında dört rakamlı yıl değeri olduğu, gg biçiminde olmalıdır tarih dd 1 ile 12 arasında ayı ve GG verilen ayı için geçerli olduğu gün değerdir.</span><span class="sxs-lookup"><span data-stu-id="99214-150">The date part must have the format YYYY-MM-DD, where YYYY is a four digit year value between 0001 and 9999, MM is the month between 1 and 12, and DD is the day value that is valid for the given month.</span></span> <span data-ttu-id="99214-151">Saat bölümünü ss: dd biçiminde olmalıdır [: SS [.fffffff]] HH MM 0 ve 23 arasında saat değeri 0 ile 59, SS arasındaki dakika değerdir ikinci değer 0 ile 59 arasında olduğu ve fffffff olan 0 ile 9999999 arasında kesirli ikinci değer.</span><span class="sxs-lookup"><span data-stu-id="99214-151">The time part must have the format HH:MM[:SS[.fffffff]], where HH is the hour value between 0 and 23, MM is the minute value between 0 and 59, SS is the second value between 0 and 59, and fffffff is the fractional second value between 0 and 9999999.</span></span> <span data-ttu-id="99214-152">Tüm değer aralıklar dahildir.</span><span class="sxs-lookup"><span data-stu-id="99214-152">All value ranges are inclusive.</span></span> <span data-ttu-id="99214-153">Kesirli saniye isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="99214-153">Fractional seconds are optional.</span></span> <span data-ttu-id="99214-154">Kesirli saniye belirtilmedikçe saniye isteğe bağlıdır; Bu durumda, saniye gereklidir.</span><span class="sxs-lookup"><span data-stu-id="99214-154">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="99214-155">Saniye veya kesir belirtilmezse, varsayılan değerin sıfır yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="99214-155">When seconds or fractions are not specified, the default value of zero will be used instead.</span></span> <span data-ttu-id="99214-156">Uzaklık bölümü biçiminde olmalıdır {+ &#124;-} ss: dd ss ve MM sahip olduğu saat bölümünü olduğu gibi aynı anlama.</span><span class="sxs-lookup"><span data-stu-id="99214-156">The offset part must have the format {+&#124;-}HH:MM, where HH and MM have the same meaning as in the time part.</span></span> <span data-ttu-id="99214-157">Uzaklık, ancak dizi-14 arasında olması gerekir: 00 ve + 14:00</span><span class="sxs-lookup"><span data-stu-id="99214-157">The range of the offset, however, must be between -14:00 and + 14:00</span></span>  
  
 <span data-ttu-id="99214-158">DATETIMEOFFSET simgesi ve hazır değer yükü, ancak hiç yeni satır arasında boşluk herhangi bir sayıda olabilir.</span><span class="sxs-lookup"><span data-stu-id="99214-158">There can be any number of spaces between the DATETIMEOFFSET symbol and the literal payload, but no new lines.</span></span>  
  
```  
DATETIMEOFFSET‘2006-10-1 23:11 +02:00’  
DATETIMEOFFSET‘2006-12-25 01:01:00.0000000 -08:30’  
```  
  
> [!NOTE]
>  <span data-ttu-id="99214-159">Geçerli bir varlık SQL değişmez değer CLR veya veri kaynağı için desteklenen aralık dışında dönebilir.</span><span class="sxs-lookup"><span data-stu-id="99214-159">A valid Entity SQL literal value can fall outside the supported ranges for CLR or the data source.</span></span> <span data-ttu-id="99214-160">Bu, bir özel durum neden</span><span class="sxs-lookup"><span data-stu-id="99214-160">This might result in an exception</span></span>  
  
## <a name="binary"></a><span data-ttu-id="99214-161">İkili</span><span class="sxs-lookup"><span data-stu-id="99214-161">Binary</span></span>  
 <span data-ttu-id="99214-162">Bir ikili dize sabit değeri bir ikili anahtar sözcüğünü izleyen tek tırnak veya kısayol simgesini tarafından ayrılmış onaltılık rakam dizisini olan `X` veya `x`.</span><span class="sxs-lookup"><span data-stu-id="99214-162">A binary string literal is a sequence of hexadecimal digits delimited by single quotes following the keyword binary or the shortcut symbol `X` or `x`.</span></span> <span data-ttu-id="99214-163">Kısayol simgesi `X` büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="99214-163">The shortcut symbol `X` is case insensitive.</span></span> <span data-ttu-id="99214-164">Sıfır veya daha fazla alanları arasında anahtar sözcüğü izin `binary` ve ikili dize değeri.</span><span class="sxs-lookup"><span data-stu-id="99214-164">A zero or more spaces are allowed between the keyword `binary` and the binary string value.</span></span>  
  
 <span data-ttu-id="99214-165">Onaltılık karakterler ayrıca büyük küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="99214-165">Hexadecimal characters are also case insensitive.</span></span> <span data-ttu-id="99214-166">Değişmez değeri bir onaltılık basamak tek sayıda oluşuyorsa, sabit sonraki bile onaltılık basamak değişmez değeri bir onaltılık ile ekleyerek sıfır basamaklı hizalanır.</span><span class="sxs-lookup"><span data-stu-id="99214-166">If the literal is composed of an odd number of hexadecimal digits, the literal will be aligned to the next even hexadecimal digit by prefixing the literal with a hexadecimal zero digit.</span></span> <span data-ttu-id="99214-167">İkili dosya dizesine boyutuna resmi bir sınır yoktur.</span><span class="sxs-lookup"><span data-stu-id="99214-167">There is no formal limit on the size of the binary string.</span></span>  
  
```  
Binary'00ffaabb'  
X'ABCabc'  
BINARY    '0f0f0f0F0F0F0F0F0F0F'  
X'' –- empty binary string  
```  
  
## <a name="guid"></a><span data-ttu-id="99214-168">Guid</span><span class="sxs-lookup"><span data-stu-id="99214-168">Guid</span></span>  
 <span data-ttu-id="99214-169">A `GUID` değişmez değeri bir genel benzersiz tanımlayıcısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="99214-169">A `GUID` literal represents a globally unique identifier.</span></span> <span data-ttu-id="99214-170">Anahtar sözcüğe göre biçimlendirilmiş bir dizisi olduğundan `GUID` olarak bilinen formunda onaltılık basamak arkasından *kayıt defteri* biçimi: 8-4-4-4-tek tırnak içine alınmış 12.</span><span class="sxs-lookup"><span data-stu-id="99214-170">It is a sequence formed by the keyword `GUID` followed by hexadecimal digits in the form known as *registry* format: 8-4-4-4-12 enclosed in single quotes.</span></span> <span data-ttu-id="99214-171">Onaltılık basamak büyük/küçük harfe duyarsızdır.</span><span class="sxs-lookup"><span data-stu-id="99214-171">Hexadecimal digits are case insensitive.</span></span>  
  
 <span data-ttu-id="99214-172">Herhangi bir sayıda GUID simgesi ve hazır değer yükü, ancak hiç yeni satır arasında boşluk olabilir.</span><span class="sxs-lookup"><span data-stu-id="99214-172">There can be any number of spaces between the GUID symbol and the literal payload, but no new lines.</span></span>  
  
```  
Guid'1afc7f5c-ffa0-4741-81cf-f12eAAb822bf'  
GUID  '1AFC7F5C-FFA0-4741-81CF-F12EAAB822BF'  
```  
  
## <a name="see-also"></a><span data-ttu-id="99214-173">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="99214-173">See Also</span></span>  
 [<span data-ttu-id="99214-174">Varlık SQL genel bakış</span><span class="sxs-lookup"><span data-stu-id="99214-174">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
