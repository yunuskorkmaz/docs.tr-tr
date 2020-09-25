---
title: Giriş karakter kümesi (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 13d291d3-e6bc-4719-b953-758b61a590b6
ms.openlocfilehash: 94615a8f4aec51347f451d6f6a53b9d5b459a336
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203663"
---
# <a name="input-character-set-entity-sql"></a><span data-ttu-id="0c787-102">Giriş karakter kümesi (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0c787-102">Input Character Set (Entity SQL)</span></span>

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="0c787-103">UTF-16 ' da kodlanmış UNICODE karakterlerini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="0c787-103">accepts UNICODE characters encoded in UTF-16.</span></span>  
  
 <span data-ttu-id="0c787-104">Dize sabit değerleri, tek tırnak içine alınmış herhangi bir UTF-16 karakteri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="0c787-104">String literals can contain any UTF-16 character enclosed in single quotes.</span></span> <span data-ttu-id="0c787-105">Örneğin, N ' 文字列リテラル '.</span><span class="sxs-lookup"><span data-stu-id="0c787-105">For example, N'文字列リテラル'.</span></span> <span data-ttu-id="0c787-106">Dize sabit değerleri karşılaştırıldığı zaman, özgün UTF-16 değerleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0c787-106">When string literals are compared, the original UTF-16 values are used.</span></span> <span data-ttu-id="0c787-107">Örneğin, N'ABC ' Japonca ve Latin kod sayfalarında farklıdır.</span><span class="sxs-lookup"><span data-stu-id="0c787-107">For example, N'ABC' is different in Japanese and Latin codepages.</span></span>  
  
 <span data-ttu-id="0c787-108">Yorumlar herhangi bir UTF-16 karakteri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="0c787-108">Comments can contain any UTF-16 character.</span></span>  
  
 <span data-ttu-id="0c787-109">Kaçışlı tanımlayıcılar, köşeli ayraçlar içinde herhangi bir UTF-16 karakteri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="0c787-109">Escaped identifiers can contain any UTF-16 character enclosed in square brackets.</span></span> <span data-ttu-id="0c787-110">Örneğin, [エスケープされた識別子].</span><span class="sxs-lookup"><span data-stu-id="0c787-110">For example, [エスケープされた識別子].</span></span> <span data-ttu-id="0c787-111">UTF-16 kaçışlı tanımlayıcıların karşılaştırması büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="0c787-111">The comparison of UTF-16 escaped identifiers is case insensitive.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="0c787-112">aynı görünen, ancak farklı kod sayfalarından farklı karakter olan harflerin sürümlerini değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="0c787-112">treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="0c787-113">Örneğin, karşılık gelen karakterler aynı kod sayfasından ise [ABC], [abc] ile eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="0c787-113">For example, [ABC] is equivalent to [abc] if the corresponding characters are from the same code page.</span></span> <span data-ttu-id="0c787-114">Ancak, aynı iki tanımlayıcı farklı kod sayfalarından ise eşdeğer değildir.</span><span class="sxs-lookup"><span data-stu-id="0c787-114">However, if the same two identifiers are from different code pages, they are not equivalent.</span></span>  
  
 <span data-ttu-id="0c787-115">Boşluk, UTF-16 boşluk karakteridir.</span><span class="sxs-lookup"><span data-stu-id="0c787-115">White space is any UTF-16 white space character.</span></span>  
  
 <span data-ttu-id="0c787-116">Yeni satır, normalleştirilmiş UTF-16 yeni satır karakteri olur.</span><span class="sxs-lookup"><span data-stu-id="0c787-116">A newline is any normalized UTF-16 newline character.</span></span> <span data-ttu-id="0c787-117">Örneğin, ' \n ' ve ' \r\n ' yeni satır karakterleri olarak değerlendirilir, ancak ' \r ' bir yeni satır karakteri değildir.</span><span class="sxs-lookup"><span data-stu-id="0c787-117">For example, '\n' and '\r\n' are considered newline characters, but '\r' is not a newline character.</span></span>  
  
 <span data-ttu-id="0c787-118">Anahtar sözcükler, ifadeler ve noktalama, Latin 'e normalleştirir UTF-16 karakteri olabilir.</span><span class="sxs-lookup"><span data-stu-id="0c787-118">Keywords, expressions, and punctuation can be any UTF-16 character that normalizes to Latin.</span></span> <span data-ttu-id="0c787-119">Örneğin, Japonca kod sayfasında SEÇIM geçerli bir anahtar sözcüktür.</span><span class="sxs-lookup"><span data-stu-id="0c787-119">For example, SELECT in a Japanese codepage is a valid keyword.</span></span>  
  
 <span data-ttu-id="0c787-120">Anahtar sözcükler, ifadeler ve noktalama yalnızca Latin karakter olabilir.</span><span class="sxs-lookup"><span data-stu-id="0c787-120">Keywords, expressions, and punctuation can only be Latin characters.</span></span> <span data-ttu-id="0c787-121">`SELECT` Japonca kod sayfasında anahtar sözcük değildir.</span><span class="sxs-lookup"><span data-stu-id="0c787-121">`SELECT` in a Japanese codepage is not a keyword.</span></span> <span data-ttu-id="0c787-122">+,-, \* ,/, =, (,), ', [,] ve burada tırnak içine alınmış diğer dil yapısı yalnızca Latin karakter olabilir.</span><span class="sxs-lookup"><span data-stu-id="0c787-122">+, -, \*, /, =, (, ), ‘, [, ] and any other language construct not quoted here can only be Latin characters.</span></span>  
  
 <span data-ttu-id="0c787-123">Basit tanımlayıcılar yalnızca Latin karakter olabilir.</span><span class="sxs-lookup"><span data-stu-id="0c787-123">Simple identifiers can only be Latin characters.</span></span> <span data-ttu-id="0c787-124">Bu, özgün değerler karşılaştırıldığından karşılaştırma sırasında karışıklığı önler.</span><span class="sxs-lookup"><span data-stu-id="0c787-124">This avoids ambiguity during comparison, because original values are compared.</span></span> <span data-ttu-id="0c787-125">Örneğin, ABC Japonca ve Latin kod sayfalarında farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="0c787-125">For example, ABC would be different in Japanese and Latin codepages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c787-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c787-126">See also</span></span>

- [<span data-ttu-id="0c787-127">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0c787-127">Entity SQL Overview</span></span>](entity-sql-overview.md)
