---
description: 'Hakkında daha fazla bilgi edinin: giriş karakter kümesi (Entity SQL)'
title: Giriş karakter kümesi (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 13d291d3-e6bc-4719-b953-758b61a590b6
ms.openlocfilehash: b17b9b2022a49717aace3c9f642ac62a2f30b2b5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748537"
---
# <a name="input-character-set-entity-sql"></a><span data-ttu-id="42a0a-103">Giriş karakter kümesi (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="42a0a-103">Input Character Set (Entity SQL)</span></span>

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="42a0a-104">UTF-16 ' da kodlanmış UNICODE karakterlerini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="42a0a-104">accepts UNICODE characters encoded in UTF-16.</span></span>  
  
 <span data-ttu-id="42a0a-105">Dize sabit değerleri, tek tırnak içine alınmış herhangi bir UTF-16 karakteri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="42a0a-105">String literals can contain any UTF-16 character enclosed in single quotes.</span></span> <span data-ttu-id="42a0a-106">Örneğin, N ' 文字列リテラル '.</span><span class="sxs-lookup"><span data-stu-id="42a0a-106">For example, N'文字列リテラル'.</span></span> <span data-ttu-id="42a0a-107">Dize sabit değerleri karşılaştırıldığı zaman, özgün UTF-16 değerleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="42a0a-107">When string literals are compared, the original UTF-16 values are used.</span></span> <span data-ttu-id="42a0a-108">Örneğin, N'ABC ' Japonca ve Latin kod sayfalarında farklıdır.</span><span class="sxs-lookup"><span data-stu-id="42a0a-108">For example, N'ABC' is different in Japanese and Latin codepages.</span></span>  
  
 <span data-ttu-id="42a0a-109">Yorumlar herhangi bir UTF-16 karakteri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="42a0a-109">Comments can contain any UTF-16 character.</span></span>  
  
 <span data-ttu-id="42a0a-110">Kaçışlı tanımlayıcılar, köşeli ayraçlar içinde herhangi bir UTF-16 karakteri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="42a0a-110">Escaped identifiers can contain any UTF-16 character enclosed in square brackets.</span></span> <span data-ttu-id="42a0a-111">Örneğin, [エスケープされた識別子].</span><span class="sxs-lookup"><span data-stu-id="42a0a-111">For example, [エスケープされた識別子].</span></span> <span data-ttu-id="42a0a-112">UTF-16 kaçışlı tanımlayıcıların karşılaştırması büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="42a0a-112">The comparison of UTF-16 escaped identifiers is case insensitive.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="42a0a-113">aynı görünen, ancak farklı kod sayfalarından farklı karakter olan harflerin sürümlerini değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="42a0a-113">treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="42a0a-114">Örneğin, karşılık gelen karakterler aynı kod sayfasından ise [ABC], [abc] ile eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="42a0a-114">For example, [ABC] is equivalent to [abc] if the corresponding characters are from the same code page.</span></span> <span data-ttu-id="42a0a-115">Ancak, aynı iki tanımlayıcı farklı kod sayfalarından ise eşdeğer değildir.</span><span class="sxs-lookup"><span data-stu-id="42a0a-115">However, if the same two identifiers are from different code pages, they are not equivalent.</span></span>  
  
 <span data-ttu-id="42a0a-116">Boşluk, UTF-16 boşluk karakteridir.</span><span class="sxs-lookup"><span data-stu-id="42a0a-116">White space is any UTF-16 white space character.</span></span>  
  
 <span data-ttu-id="42a0a-117">Yeni satır, normalleştirilmiş UTF-16 yeni satır karakteri olur.</span><span class="sxs-lookup"><span data-stu-id="42a0a-117">A newline is any normalized UTF-16 newline character.</span></span> <span data-ttu-id="42a0a-118">Örneğin, ' \n ' ve ' \r\n ' yeni satır karakterleri olarak değerlendirilir, ancak ' \r ' bir yeni satır karakteri değildir.</span><span class="sxs-lookup"><span data-stu-id="42a0a-118">For example, '\n' and '\r\n' are considered newline characters, but '\r' is not a newline character.</span></span>  
  
 <span data-ttu-id="42a0a-119">Anahtar sözcükler, ifadeler ve noktalama, Latin 'e normalleştirir UTF-16 karakteri olabilir.</span><span class="sxs-lookup"><span data-stu-id="42a0a-119">Keywords, expressions, and punctuation can be any UTF-16 character that normalizes to Latin.</span></span> <span data-ttu-id="42a0a-120">Örneğin, Japonca kod sayfasında SEÇIM geçerli bir anahtar sözcüktür.</span><span class="sxs-lookup"><span data-stu-id="42a0a-120">For example, SELECT in a Japanese codepage is a valid keyword.</span></span>  
  
 <span data-ttu-id="42a0a-121">Anahtar sözcükler, ifadeler ve noktalama yalnızca Latin karakter olabilir.</span><span class="sxs-lookup"><span data-stu-id="42a0a-121">Keywords, expressions, and punctuation can only be Latin characters.</span></span> <span data-ttu-id="42a0a-122">`SELECT` Japonca kod sayfasında anahtar sözcük değildir.</span><span class="sxs-lookup"><span data-stu-id="42a0a-122">`SELECT` in a Japanese codepage is not a keyword.</span></span> <span data-ttu-id="42a0a-123">+,-, \* ,/, =, (,), ', [,] ve burada tırnak içine alınmış diğer dil yapısı yalnızca Latin karakter olabilir.</span><span class="sxs-lookup"><span data-stu-id="42a0a-123">+, -, \*, /, =, (, ), ‘, [, ] and any other language construct not quoted here can only be Latin characters.</span></span>  
  
 <span data-ttu-id="42a0a-124">Basit tanımlayıcılar yalnızca Latin karakter olabilir.</span><span class="sxs-lookup"><span data-stu-id="42a0a-124">Simple identifiers can only be Latin characters.</span></span> <span data-ttu-id="42a0a-125">Bu, özgün değerler karşılaştırıldığından karşılaştırma sırasında karışıklığı önler.</span><span class="sxs-lookup"><span data-stu-id="42a0a-125">This avoids ambiguity during comparison, because original values are compared.</span></span> <span data-ttu-id="42a0a-126">Örneğin, ABC Japonca ve Latin kod sayfalarında farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="42a0a-126">For example, ABC would be different in Japanese and Latin codepages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42a0a-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42a0a-127">See also</span></span>

- [<span data-ttu-id="42a0a-128">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="42a0a-128">Entity SQL Overview</span></span>](entity-sql-overview.md)
