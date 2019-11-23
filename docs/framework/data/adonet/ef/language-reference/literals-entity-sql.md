---
title: Değişmez değerler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 092ef693-6e5f-41b4-b868-5b9e82928abf
ms.openlocfilehash: e07dd3217e133fff98beb11ecad47e1474e4974a
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319658"
---
# <a name="literals-entity-sql"></a><span data-ttu-id="5446f-102">Değişmez değerler (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5446f-102">Literals (Entity SQL)</span></span>
<span data-ttu-id="5446f-103">Bu konuda, sabit değerler için [!INCLUDE[esql](../../../../../../includes/esql-md.md)] desteği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5446f-103">This topic describes [!INCLUDE[esql](../../../../../../includes/esql-md.md)] support for literals.</span></span>  
  
## <a name="null"></a><span data-ttu-id="5446f-104">Null</span><span class="sxs-lookup"><span data-stu-id="5446f-104">Null</span></span>  
 <span data-ttu-id="5446f-105">Null sabit değeri herhangi bir tür için null değerini temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5446f-105">The null literal is used to represent the value null for any type.</span></span> <span data-ttu-id="5446f-106">Null sabit değeri herhangi bir türle uyumludur.</span><span class="sxs-lookup"><span data-stu-id="5446f-106">A null literal is compatible with any type.</span></span>  
  
 <span data-ttu-id="5446f-107">Türü belirtilmiş null değerler, null değişmez değer üzerinden bir atama ile oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="5446f-107">Typed nulls can be created by a cast over a null literal.</span></span> <span data-ttu-id="5446f-108">Daha fazla bilgi için bkz. [cast](cast-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="5446f-108">For more information, see [CAST](cast-entity-sql.md).</span></span>  
  
 <span data-ttu-id="5446f-109">Boş kayan null sabit değerlerinin kullanılabileceği durumlar hakkında kurallar için bkz. [null sabit değerler ve tür çıkarımı](null-literals-and-type-inference-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="5446f-109">For rules about where free floating null literals can be used, see [Null Literals and Type Inference](null-literals-and-type-inference-entity-sql.md).</span></span>  
  
## <a name="boolean"></a><span data-ttu-id="5446f-110">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="5446f-110">Boolean</span></span>  
 <span data-ttu-id="5446f-111">Boolean sabit değerleri, `true` ve `false`anahtar sözcükleriyle temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="5446f-111">Boolean literals are represented by the keywords `true` and `false`.</span></span>  
  
## <a name="integer"></a><span data-ttu-id="5446f-112">Tamsayı</span><span class="sxs-lookup"><span data-stu-id="5446f-112">Integer</span></span>  
 <span data-ttu-id="5446f-113">Tamsayı sabit değerleri <xref:System.Int32> veya <xref:System.Int64>türünde olabilir.</span><span class="sxs-lookup"><span data-stu-id="5446f-113">Integer literals can be of type <xref:System.Int32> or <xref:System.Int64>.</span></span> <span data-ttu-id="5446f-114"><xref:System.Int32> değişmez değeri bir dizi sayısal karakterdir.</span><span class="sxs-lookup"><span data-stu-id="5446f-114">An <xref:System.Int32> literal is a series of numeric characters.</span></span> <span data-ttu-id="5446f-115"><xref:System.Int64> değişmez değeri, bir büyük L 'nin ardından gelen sayısal karakterlerin serisidir.</span><span class="sxs-lookup"><span data-stu-id="5446f-115">An <xref:System.Int64> literal is series of numeric characters followed by an uppercase L.</span></span>  
  
## <a name="decimal"></a><span data-ttu-id="5446f-116">Ondalık</span><span class="sxs-lookup"><span data-stu-id="5446f-116">Decimal</span></span>  
 <span data-ttu-id="5446f-117">Sabit noktalı sayı (ondalık), bir dizi sayısal karakter, nokta (.) ve başka bir sayısal karakter serisi, büyük bir "ı" ile izlenir.</span><span class="sxs-lookup"><span data-stu-id="5446f-117">A fixed-point number (decimal) is a series of numeric characters, a dot (.) and another series of numeric characters followed by an uppercase "M".</span></span>  
  
## <a name="float-double"></a><span data-ttu-id="5446f-118">Float, Double</span><span class="sxs-lookup"><span data-stu-id="5446f-118">Float, Double</span></span>  
 <span data-ttu-id="5446f-119">Çift duyarlıklı kayan noktalı sayı, bir dizi sayısal karakter, nokta (.) ve başka bir sayısal karakter serisi olabilir.</span><span class="sxs-lookup"><span data-stu-id="5446f-119">A double-precision floating point number is a series of numeric characters, a dot (.) and another series of numeric characters possibly followed by an exponent.</span></span> <span data-ttu-id="5446f-120">Tek duyarlıklı kayan noktalı sayı (veya float), bir çift duyarlıklı kayan noktalı sayı sözdizimidir ve ardından küçük harfli f.</span><span class="sxs-lookup"><span data-stu-id="5446f-120">A single-precisions floating point number (or float) is a double-precision floating point number syntax followed by the lowercase f.</span></span>  
  
## <a name="string"></a><span data-ttu-id="5446f-121">Dize</span><span class="sxs-lookup"><span data-stu-id="5446f-121">String</span></span>  
 <span data-ttu-id="5446f-122">Dize, tırnak işaretleri içine alınmış bir karakter dizisidir.</span><span class="sxs-lookup"><span data-stu-id="5446f-122">A string is a series of characters enclosed in quote marks.</span></span> <span data-ttu-id="5446f-123">Tırnak işaretleri hem tek tırnak (`'`) hem de çift tırnak işareti (") olabilir.</span><span class="sxs-lookup"><span data-stu-id="5446f-123">Quotes can be either both single-quotes (`'`) or both double-quotes (").</span></span> <span data-ttu-id="5446f-124">Karakter dizesi sabit değerleri Unicode veya Unicode olmayan bir değer olabilir.</span><span class="sxs-lookup"><span data-stu-id="5446f-124">Character string literals can be either Unicode or non-Unicode.</span></span> <span data-ttu-id="5446f-125">Unicode olarak bir karakter dizesi hazır değeri bildirmek için, sabit değeri büyük harfle ("N") önek olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5446f-125">To declare a character string literal as Unicode, prefix the literal with an uppercase "N".</span></span> <span data-ttu-id="5446f-126">Varsayılan değer Unicode olmayan karakter dizesi değişmez değerleri.</span><span class="sxs-lookup"><span data-stu-id="5446f-126">The default is non-Unicode character string literals.</span></span> <span data-ttu-id="5446f-127">N ile dize değişmez değeri arasında boşluk olamaz ve N büyük harf olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5446f-127">There can be no spaces between the N and the string literal payload, and the N must be uppercase.</span></span>  
  
```sql  
'hello' -- non-Unicode character string literal  
N'hello' -- Unicode character string literal  
"x"  
N"This is a string!"  
'so is THIS'  
```  
  
## <a name="datetime"></a><span data-ttu-id="5446f-128">DateTime</span><span class="sxs-lookup"><span data-stu-id="5446f-128">DateTime</span></span>  
 <span data-ttu-id="5446f-129">DateTime sabit değeri yerel ayardan bağımsızdır ve bir tarih bölümünden ve saat bölümünden oluşur.</span><span class="sxs-lookup"><span data-stu-id="5446f-129">A datetime literal is independent of locale and is composed of a date part and a time part.</span></span> <span data-ttu-id="5446f-130">Hem tarih hem de saat bölümlerinin ikisi de zorunludur ve varsayılan değer yoktur.</span><span class="sxs-lookup"><span data-stu-id="5446f-130">Both date and time parts are mandatory and there are no default values.</span></span>  
  
 <span data-ttu-id="5446f-131">Tarih Bölümü, `YYYY`-`MM`-`DD`olmalıdır; burada `YYYY`, 0001 ve 9999 arasında dört basamaklı bir yıl değeridir, `MM` 1 ile 12 arasında geçerli olan gün değeridir `DD`.`MM`</span><span class="sxs-lookup"><span data-stu-id="5446f-131">The date part must have the format: `YYYY`-`MM`-`DD`, where `YYYY` is a four digit year value between 0001 and 9999, `MM` is the month between 1 and 12 and `DD` is the day value that is valid for the given month `MM`.</span></span>  
  
 <span data-ttu-id="5446f-132">Zaman kısmı şu biçimde olmalıdır: `HH`:`MM`[:`SS`[. fffffff]]; burada `HH`, 0 ile 23 arasında bir Hour değeri, 59 `MM` 0 ile 59 arasındaki ikinci değerdir ve fffffff 0 ile 9999999 arasında kesirli ikinci değerdir.`SS`</span><span class="sxs-lookup"><span data-stu-id="5446f-132">The time part must have the format: `HH`:`MM`[:`SS`[.fffffff]], where `HH` is the hour value between 0 and 23, `MM` is the minute value between 0 and 59, `SS` is the second value between 0 and 59 and fffffff is the fractional second value between 0 and 9999999.</span></span> <span data-ttu-id="5446f-133">Tüm değer aralıkları dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="5446f-133">All value ranges are inclusive.</span></span> <span data-ttu-id="5446f-134">Kesirli saniyeler isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="5446f-134">Fractional seconds are optional.</span></span> <span data-ttu-id="5446f-135">Kesirli saniyeler belirtilmediği takdirde saniyeler isteğe bağlıdır; Bu durumda, saniyeler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5446f-135">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="5446f-136">Saniye veya Kesirli saniyeler belirtilmediğinde bunun yerine varsayılan sıfır değeri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5446f-136">When seconds or fractional seconds are not specified, the default value of zero will be used instead.</span></span>  
  
 <span data-ttu-id="5446f-137">DATETIME simgesiyle sabit değer yükü arasında herhangi bir sayıda boşluk olabilir, ancak yeni satır yoktur.</span><span class="sxs-lookup"><span data-stu-id="5446f-137">There can be any number of spaces between the DATETIME symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
DATETIME'2006-10-1 23:11'  
DATETIME'2006-12-25 01:01:00.0000000' -- same as DATETIME'2006-12-25 01:01'  
```  
  
## <a name="time"></a><span data-ttu-id="5446f-138">Time</span><span class="sxs-lookup"><span data-stu-id="5446f-138">Time</span></span>  
 <span data-ttu-id="5446f-139">Bir zaman sabiti, yerel ayardan bağımsızdır ve yalnızca bir zaman kısmından oluşur.</span><span class="sxs-lookup"><span data-stu-id="5446f-139">A time literal is independent of locale and composed of a time part only.</span></span> <span data-ttu-id="5446f-140">Saat bölümü zorunludur ve varsayılan değer yoktur.</span><span class="sxs-lookup"><span data-stu-id="5446f-140">The time part is mandatory and there is no default value.</span></span> <span data-ttu-id="5446f-141">HH: MM [: SS [. fffffff]] biçiminde olmalıdır; burada ss, 0 ile 23 arasında bir Hour değeridir, 59 MM 0 ile 59 arasındaki ikinci değerdir ve fffffff 0 ile 9999999 arasında ikinci kesir değeridir.</span><span class="sxs-lookup"><span data-stu-id="5446f-141">It must have the format HH:MM[:SS[.fffffff]], where HH is the hour value between 0 and 23, MM is the minute value between 0 and 59, SS is the second value between 0 and 59, and fffffff is the second fraction value between 0 and 9999999.</span></span> <span data-ttu-id="5446f-142">Tüm değer aralıkları dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="5446f-142">All value ranges are inclusive.</span></span> <span data-ttu-id="5446f-143">Kesirli saniyeler isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="5446f-143">Fractional seconds are optional.</span></span> <span data-ttu-id="5446f-144">Kesirli saniyeler belirtilmediği takdirde saniyeler isteğe bağlıdır; Bu durumda, saniyeler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5446f-144">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="5446f-145">Saniyeler veya kesirler belirtilmediğinde bunun yerine varsayılan sıfır değeri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5446f-145">When seconds or fractions are not specified, the default value of zero will be used instead.</span></span>  
  
 <span data-ttu-id="5446f-146">ZAMAN simgesi ve değişmez değer yükü arasında herhangi bir sayıda boşluk olabilir, ancak yeni satır olamaz.</span><span class="sxs-lookup"><span data-stu-id="5446f-146">There can be any number of spaces between the TIME symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
TIME‘23:11’  
TIME‘01:01:00.1234567’  
```  
  
## <a name="datetimeoffset"></a><span data-ttu-id="5446f-147">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="5446f-147">DateTimeOffset</span></span>  
 <span data-ttu-id="5446f-148">DateTimeOffset sabit değeri yerel ayardan bağımsızdır ve bir tarih bölümünden, bir saat bölümünden ve bir konum bölümünden oluşur.</span><span class="sxs-lookup"><span data-stu-id="5446f-148">A datetimeoffset literal is independent of locale and composed of a date part, a time part, and an offset part.</span></span> <span data-ttu-id="5446f-149">Tüm tarih, saat ve konum bölümleri zorunludur ve varsayılan değer yoktur.</span><span class="sxs-lookup"><span data-stu-id="5446f-149">All date, time, and offset parts are mandatory and there are no default values.</span></span> <span data-ttu-id="5446f-150">Tarih kısmı YYYY-AA-GG biçiminde olmalıdır. burada YYYY, 0001 ile 9999 arasında dört basamaklı bir yıl değeri, aa ise 1 ile 12 arasında bir, gg ise verilen ay için geçerli olan gün değeridir.</span><span class="sxs-lookup"><span data-stu-id="5446f-150">The date part must have the format YYYY-MM-DD, where YYYY is a four digit year value between 0001 and 9999, MM is the month between 1 and 12, and DD is the day value that is valid for the given month.</span></span> <span data-ttu-id="5446f-151">Zaman bölümü HH: MM [: SS [. fffffff]] biçiminde olmalıdır; burada ss, 0 ile 23 arasında bir Hour değeri, 59 MM 0 ile 59 arasındaki ikinci değerdir ve fffffff 0 ile 9999999 arasındaki kesirli ikinci değerdir.</span><span class="sxs-lookup"><span data-stu-id="5446f-151">The time part must have the format HH:MM[:SS[.fffffff]], where HH is the hour value between 0 and 23, MM is the minute value between 0 and 59, SS is the second value between 0 and 59, and fffffff is the fractional second value between 0 and 9999999.</span></span> <span data-ttu-id="5446f-152">Tüm değer aralıkları dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="5446f-152">All value ranges are inclusive.</span></span> <span data-ttu-id="5446f-153">Kesirli saniyeler isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="5446f-153">Fractional seconds are optional.</span></span> <span data-ttu-id="5446f-154">Kesirli saniyeler belirtilmediği takdirde saniyeler isteğe bağlıdır; Bu durumda, saniyeler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5446f-154">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="5446f-155">Saniyeler veya kesirler belirtilmediğinde bunun yerine varsayılan sıfır değeri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5446f-155">When seconds or fractions are not specified, the default value of zero will be used instead.</span></span> <span data-ttu-id="5446f-156">Konum bölümü {+&#124;-} hh: mm biçiminde olmalıdır; burada SS ve dd, saat bölümünde olduğu gibi anlamdadır.</span><span class="sxs-lookup"><span data-stu-id="5446f-156">The offset part must have the format {+&#124;-}HH:MM, where HH and MM have the same meaning as in the time part.</span></span> <span data-ttu-id="5446f-157">Ancak, kaydırın aralığı-14:00 ile + 14:00 arasında olmalıdır</span><span class="sxs-lookup"><span data-stu-id="5446f-157">The range of the offset, however, must be between -14:00 and + 14:00</span></span>  
  
 <span data-ttu-id="5446f-158">DATETIMEOFFSET sembolü ve değişmez değer yükü arasında herhangi bir sayıda boşluk olabilir, ancak yeni satır olamaz.</span><span class="sxs-lookup"><span data-stu-id="5446f-158">There can be any number of spaces between the DATETIMEOFFSET symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
DATETIMEOFFSET‘2006-10-1 23:11 +02:00’  
DATETIMEOFFSET‘2006-12-25 01:01:00.0000000 -08:30’  
```  
  
> [!NOTE]
> <span data-ttu-id="5446f-159">Geçerli bir Entity SQL sabit değeri CLR veya veri kaynağı için desteklenen aralıkların dışında olabilir.</span><span class="sxs-lookup"><span data-stu-id="5446f-159">A valid Entity SQL literal value can fall outside the supported ranges for CLR or the data source.</span></span> <span data-ttu-id="5446f-160">Bu durum bir özel durumla sonuçlanabilir</span><span class="sxs-lookup"><span data-stu-id="5446f-160">This might result in an exception</span></span>  
  
## <a name="binary"></a><span data-ttu-id="5446f-161">İkili</span><span class="sxs-lookup"><span data-stu-id="5446f-161">Binary</span></span>  
 <span data-ttu-id="5446f-162">İkili dize sabit değeri, ikili anahtar sözcüğünün veya `X` ya da `x`kısayol sembolünden sonra tek tırnak ile ayrılmış bir onaltılık basamaklar dizisidir.</span><span class="sxs-lookup"><span data-stu-id="5446f-162">A binary string literal is a sequence of hexadecimal digits delimited by single quotes following the keyword binary or the shortcut symbol `X` or `x`.</span></span> <span data-ttu-id="5446f-163">`X` kısayol simgesi, büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="5446f-163">The shortcut symbol `X` is case insensitive.</span></span> <span data-ttu-id="5446f-164">Anahtar sözcük `binary` ve ikili dize değeri arasında sıfır veya daha fazla boşluk yapılmasına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="5446f-164">A zero or more spaces are allowed between the keyword `binary` and the binary string value.</span></span>  
  
 <span data-ttu-id="5446f-165">Onaltılık karakterler de büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="5446f-165">Hexadecimal characters are also case insensitive.</span></span> <span data-ttu-id="5446f-166">Sabit değer tek sayıda onaltılı basamaktan oluşuyorsa, değişmez değer, onaltılı sıfır basamağı ile değişmez değer eklenerek, sonraki çift onaltılık basamağa hizalanır.</span><span class="sxs-lookup"><span data-stu-id="5446f-166">If the literal is composed of an odd number of hexadecimal digits, the literal will be aligned to the next even hexadecimal digit by prefixing the literal with a hexadecimal zero digit.</span></span> <span data-ttu-id="5446f-167">İkili dizenin boyutunda bir biçimsel sınır yoktur.</span><span class="sxs-lookup"><span data-stu-id="5446f-167">There is no formal limit on the size of the binary string.</span></span>  
  
```sql  
Binary'00ffaabb'  
X'ABCabc'  
BINARY    '0f0f0f0F0F0F0F0F0F0F'  
X'' –- empty binary string  
```  
  
## <a name="guid"></a><span data-ttu-id="5446f-168">Guid</span><span class="sxs-lookup"><span data-stu-id="5446f-168">Guid</span></span>  
 <span data-ttu-id="5446f-169">`GUID` değişmez değeri, genel olarak benzersiz tanımlayıcıyı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5446f-169">A `GUID` literal represents a globally unique identifier.</span></span> <span data-ttu-id="5446f-170">Bu, anahtar kelimesiyle oluşturulan bir dizidir `GUID`, ardından formda *kayıt defteri* biçimi olarak bilinen onaltılık basamaklar: tek tırnak içine alınmış 8-4-4-4-12.</span><span class="sxs-lookup"><span data-stu-id="5446f-170">It is a sequence formed by the keyword `GUID` followed by hexadecimal digits in the form known as *registry* format: 8-4-4-4-12 enclosed in single quotes.</span></span> <span data-ttu-id="5446f-171">Onaltılık basamaklar büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="5446f-171">Hexadecimal digits are case insensitive.</span></span>  
  
 <span data-ttu-id="5446f-172">GUID sembolü ve değişmez değer yükü arasında herhangi bir sayıda boşluk olabilir, ancak yeni satır olamaz.</span><span class="sxs-lookup"><span data-stu-id="5446f-172">There can be any number of spaces between the GUID symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
Guid'1afc7f5c-ffa0-4741-81cf-f12eAAb822bf'  
GUID  '1AFC7F5C-FFA0-4741-81CF-F12EAAB822BF'  
```  
  
## <a name="see-also"></a><span data-ttu-id="5446f-173">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5446f-173">See also</span></span>

- [<span data-ttu-id="5446f-174">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5446f-174">Entity SQL Overview</span></span>](entity-sql-overview.md)
