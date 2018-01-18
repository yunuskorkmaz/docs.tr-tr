---
title: "(Varlık gibi SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8300e6d2-875b-481e-9ef4-e1e7c12d46fa
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 021a999e79239e3da5c874cb459ac7f03fdb5661
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="like-entity-sql"></a><span data-ttu-id="5b674-102">(Varlık gibi SQL)</span><span class="sxs-lookup"><span data-stu-id="5b674-102">LIKE (Entity SQL)</span></span>
<span data-ttu-id="5b674-103">Belirli bir karakteri olup olmadığını belirleyen `String` belirtilen desenle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="5b674-103">Determines whether a specific character `String` matches a specified pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b674-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5b674-104">Syntax</span></span>  
  
```  
match [NOT] LIKE pattern [ESCAPE escape]  
```  
  
## <a name="arguments"></a><span data-ttu-id="5b674-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="5b674-105">Arguments</span></span>  
 `match`  
 <span data-ttu-id="5b674-106">Bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] veren ifade bir `String`.</span><span class="sxs-lookup"><span data-stu-id="5b674-106">An [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression that evaluates to a `String`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="5b674-107">Belirtilen eşleştirmek için bir desen `String`.</span><span class="sxs-lookup"><span data-stu-id="5b674-107">A pattern to match to the specified `String`.</span></span>  
  
 `escape`  
 <span data-ttu-id="5b674-108">Bir kaçış karakteri.</span><span class="sxs-lookup"><span data-stu-id="5b674-108">An escape character.</span></span>  
  
 <span data-ttu-id="5b674-109">NOT</span><span class="sxs-lookup"><span data-stu-id="5b674-109">NOT</span></span>  
 <span data-ttu-id="5b674-110">BENZER sonucunu tasarruflarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5b674-110">Specifies that the result of LIKE be negated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5b674-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5b674-111">Return Value</span></span>  
 <span data-ttu-id="5b674-112">`true`varsa `string` desenle eşleşen; Aksi halde, `false`.</span><span class="sxs-lookup"><span data-stu-id="5b674-112">`true` if the `string` matches the pattern; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b674-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5b674-113">Remarks</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="5b674-114">LIKE işleci kullanan ifadeler çok eşitlik filtre ölçütü olarak kullanan ifadeler aynı şekilde değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="5b674-114"> expressions that use the LIKE operator are evaluated in much the same way as expressions that use equality as the filter criteria.</span></span> <span data-ttu-id="5b674-115">Ancak, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] LIKE işleci kullanan ifadeler değişmez değerleri ve joker karakterleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="5b674-115">However, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expressions that use the LIKE operator can include both literals and wildcard characters.</span></span>  
  
 <span data-ttu-id="5b674-116">Aşağıdaki tablo düzeni söz dizimi açıklanmıştır `string`.</span><span class="sxs-lookup"><span data-stu-id="5b674-116">The following table describes the syntax of the pattern `string`.</span></span>  
  
|<span data-ttu-id="5b674-117">Joker Karakter</span><span class="sxs-lookup"><span data-stu-id="5b674-117">Wildcard Character</span></span>|<span data-ttu-id="5b674-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5b674-118">Description</span></span>|<span data-ttu-id="5b674-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="5b674-119">Example</span></span>|  
|------------------------|-----------------|-------------|  
|%|<span data-ttu-id="5b674-120">Tüm `string` sıfır veya daha fazla karakter.</span><span class="sxs-lookup"><span data-stu-id="5b674-120">Any `string` of zero or more characters.</span></span>|<span data-ttu-id="5b674-121">`title like '%computer%'`word sahip tüm başlıkları bulur `"computer"` başlığı başka bir yerindeki.</span><span class="sxs-lookup"><span data-stu-id="5b674-121">`title like '%computer%'` finds all titles with the word `"computer"` anywhere in the title.</span></span>|  
|<span data-ttu-id="5b674-122">_ (alt çizgi)</span><span class="sxs-lookup"><span data-stu-id="5b674-122">_ (underscore)</span></span>|<span data-ttu-id="5b674-123">Herhangi bir tek karakteri.</span><span class="sxs-lookup"><span data-stu-id="5b674-123">Any single character.</span></span>|<span data-ttu-id="5b674-124">`firstname like '_ean'`tüm dört harfli ilk ile biten adlarını bulur `"ean`, "Deniz veya Gamze gibi.</span><span class="sxs-lookup"><span data-stu-id="5b674-124">`firstname like '_ean'` finds all four-letter first names that end with `"ean`," such as Dean or Sean.</span></span>|  
|<span data-ttu-id="5b674-125">[ ]</span><span class="sxs-lookup"><span data-stu-id="5b674-125">[ ]</span></span>|<span data-ttu-id="5b674-126">Tüm tek belirtilen aralıkta ([a-f]) karakter veya ([abcdef]) ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="5b674-126">Any single character in the specified range ([a-f]) or set ([abcdef]).</span></span>|<span data-ttu-id="5b674-127">`lastname like '[C-P]arsen'`bulur, "arsen" ile biten ve Carsen veya Etikan gibi P ile C arasındaki herhangi bir tek karakteri ile başlayan son adları.</span><span class="sxs-lookup"><span data-stu-id="5b674-127">`lastname like '[C-P]arsen'` finds last names ending with "arsen" and beginning with any single character between C and P, such as Carsen or Larsen.</span></span>|  
|<span data-ttu-id="5b674-128">[^]</span><span class="sxs-lookup"><span data-stu-id="5b674-128">[^]</span></span>|<span data-ttu-id="5b674-129">Tek bir karakter belirtilen aralık içinde değil ([^ a-f]) veya ayarlayın ([^ abcdef]).</span><span class="sxs-lookup"><span data-stu-id="5b674-129">Any single character not in the specified range ([^a-f]) or set ([^abcdef]).</span></span>|<span data-ttu-id="5b674-130">`lastname like 'de[^l]%'`"de" ile başlamalı ve şu harfini olarak "m" dahil etmeyin, tüm son adlarını bulur.</span><span class="sxs-lookup"><span data-stu-id="5b674-130">`lastname like 'de[^l]%'` finds all last names that begin with "de" and do not include "l" as the following letter.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="5b674-131">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] İşleci ve çıkış yan tümcesi uygulanamaz gibi `System.DateTime` veya `System.Guid` değerleri.</span><span class="sxs-lookup"><span data-stu-id="5b674-131">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] LIKE operator and ESCAPE clause cannot be applied to `System.DateTime` or `System.Guid` values.</span></span>  
  
 <span data-ttu-id="5b674-132">Destekler ASCII desen eşleştirme ve Unicode desen eşleştirme gibi.</span><span class="sxs-lookup"><span data-stu-id="5b674-132">LIKE supports ASCII pattern matching and Unicode pattern matching.</span></span> <span data-ttu-id="5b674-133">Tüm parametreleri ASCII karakterler olduğunda, ASCII desen eşleştirme gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5b674-133">When all parameters are ASCII characters, ASCII pattern matching is performed.</span></span> <span data-ttu-id="5b674-134">Bir veya daha fazla bağımsız değişken Unicode varsa, tüm bağımsız değişkenler Unicode'a dönüştürülür ve Unicode desen eşleştirme gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5b674-134">If one or more of the arguments are Unicode, all arguments are converted to Unicode and Unicode pattern matching is performed.</span></span> <span data-ttu-id="5b674-135">Unicode gibi ile kullandığınızda, sondaki boşlukları önemli; Ancak, Unicode olmayan için sondaki boşlukları önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="5b674-135">When you use Unicode with LIKE, trailing blanks are significant; however, for non-Unicode, trailing blanks are not significant.</span></span> <span data-ttu-id="5b674-136">Desen dizesi söz dizimi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] , aynı [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5b674-136">The pattern string syntax of [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is the same as that of [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="5b674-137">Bir desen normal karakter ve joker karakterler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="5b674-137">A pattern can include regular characters and wildcard characters.</span></span> <span data-ttu-id="5b674-138">Desen eşleştirme sırasında normal karakter tam olarak karakteri belirtilen karakterleri eşleşmelidir `string`.</span><span class="sxs-lookup"><span data-stu-id="5b674-138">During pattern matching, regular characters must exactly match the characters specified in the character `string`.</span></span> <span data-ttu-id="5b674-139">Ancak, joker karakterler rasgele parçalarını karakter dizesiyle eşleşen.</span><span class="sxs-lookup"><span data-stu-id="5b674-139">However, wildcard characters can be matched with arbitrary fragments of the character string.</span></span> <span data-ttu-id="5b674-140">' Den = joker karakterlerle kullanıldığında, LIKE işleci daha esnektir ve! = dize karşılaştırma işleçleri.</span><span class="sxs-lookup"><span data-stu-id="5b674-140">When it is used with wildcard characters, the LIKE operator is more flexible than the = and != string comparison operators.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5b674-141">Belirli bir sağlayıcıyı hedefliyorsanız, sağlayıcıya özgü uzantılar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b674-141">You may use provider-specific extensions if you target a specific provider.</span></span> <span data-ttu-id="5b674-142">Ancak, böyle yapıları farklı şekilde, diğer sağlayıcıları tarafından örneğin kabul.</span><span class="sxs-lookup"><span data-stu-id="5b674-142">However, such constructs may be treated differently by other providers, for example.</span></span> <span data-ttu-id="5b674-143">SqlServer destekler [ilk-son] ve [^ ilk son] tam olarak bir karakter arasında ilk ve son ve arasında değil ikinci eşleşmeleri tam olarak bir karakter önceki eşleştiği desenleri ilk ve son.</span><span class="sxs-lookup"><span data-stu-id="5b674-143">SqlServer supports [first-last] and [^first-last] patterns where the former matches exactly one character between first and last, and the latter matches exactly one character that is not between first and last.</span></span>  
  
### <a name="escape"></a><span data-ttu-id="5b674-144">Esc</span><span class="sxs-lookup"><span data-stu-id="5b674-144">Escape</span></span>  
 <span data-ttu-id="5b674-145">KAÇIŞ yan tümcesini kullanarak, bir dahil karakter dizeleri için arama yapabilirsiniz veya daha fazla özel joker karakter önceki bölümdeki tabloda açıklanan.</span><span class="sxs-lookup"><span data-stu-id="5b674-145">By using the ESCAPE clause, you can search for character strings that include one or more of the special wildcard characters described in the table in the previous section.</span></span> <span data-ttu-id="5b674-146">Örneğin, birkaç belge değişmez değer "% 100" başlığında içerir ve tüm bu belgeler için arama yapmak istediğiniz varsayın.</span><span class="sxs-lookup"><span data-stu-id="5b674-146">For example, assume several documents include the literal "100%" in the title and you want to search for all of those documents.</span></span> <span data-ttu-id="5b674-147">Yüzde (%) karakter joker karakter olduğundan kullanarak kaçış gerekir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] KAÇIŞ başarıyla araması yürütmek için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="5b674-147">Because the percent (%) character is a wildcard character, you must escape it using the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ESCAPE clause to successfully execute the search.</span></span> <span data-ttu-id="5b674-148">Bu filtre, bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5b674-148">The following is an example of this filter.</span></span>  
  
```  
"title like '%100!%%' escape '!'"  
```  
  
 <span data-ttu-id="5b674-149">Bu arama ifadesinde ünlem işareti karakteri (!) hemen ardından yüzde joker karakter (%) bir hazır değer yerine bir joker karakter olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="5b674-149">In this search expression, the percent wildcard character (%) immediately following the exclamation point character (!) is treated as a literal, instead of as a wildcard character.</span></span> <span data-ttu-id="5b674-150">Bir kaçış karakteri dışındaki herhangi bir karakter kullanabilirsiniz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] joker karakterler ve köşeli ayraç (`[ ]`) karakter.</span><span class="sxs-lookup"><span data-stu-id="5b674-150">You can use any character as an escape character except for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wildcard characters and the square bracket (`[ ]`) characters.</span></span> <span data-ttu-id="5b674-151">Önceki örnekte kaçış karakteri ünlem işareti (!) karakterdir.</span><span class="sxs-lookup"><span data-stu-id="5b674-151">In the previous example, the exclamation point (!) character is the escape character.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b674-152">Örnek</span><span class="sxs-lookup"><span data-stu-id="5b674-152">Example</span></span>  
 <span data-ttu-id="5b674-153">Aşağıdaki iki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorguları gibi kullanın ve bir özel karakter dizesi olup olmadığını belirlemek için KAÇIŞ işleçleri belirtilen desenle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="5b674-153">The following two [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries use the LIKE and ESCAPE operators to determine whether a specific character string matches a specified pattern.</span></span> <span data-ttu-id="5b674-154">İlk sorguyu arar `Name` karakterlerle başlayıp `Down_`.</span><span class="sxs-lookup"><span data-stu-id="5b674-154">The first query searches for the `Name` that starts with the characters `Down_`.</span></span> <span data-ttu-id="5b674-155">Bu sorgu KAÇIŞ seçeneği kullanır, çünkü alt çizgi (`_`) bir joker karakterdir.</span><span class="sxs-lookup"><span data-stu-id="5b674-155">This query uses the ESCAPE option because the underscore (`_`) is a wildcard character.</span></span> <span data-ttu-id="5b674-156">KAÇIŞ seçeneğini belirtmeden sorgu aramanıza `Name` sözcüğüyle başlayan değerlerini `Down` alt çizgi karakteri dışındaki herhangi bir tek karakteri arkasından.</span><span class="sxs-lookup"><span data-stu-id="5b674-156">Without specifying the ESCAPE option, the query would search for any `Name` values that start with the word `Down` followed by any single character other than the underscore character.</span></span> <span data-ttu-id="5b674-157">Sorgular AdventureWorks satış modeline dayanır.</span><span class="sxs-lookup"><span data-stu-id="5b674-157">The queries are based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="5b674-158">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="5b674-158">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="5b674-159">Yordamı izleyin [nasıl yapılır: Sorgu döndürür PrimitiveType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="5b674-159">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="5b674-160">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="5b674-160">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LIKE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#like)]  
  
## <a name="see-also"></a><span data-ttu-id="5b674-161">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5b674-161">See Also</span></span>  
 [<span data-ttu-id="5b674-162">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="5b674-162">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
