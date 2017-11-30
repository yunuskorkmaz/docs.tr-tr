---
title: "Giriş karakter kümesi (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13d291d3-e6bc-4719-b953-758b61a590b6
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 691f29a04b1b1f997be501330ec887d6815d7531
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="input-character-set-entity-sql"></a><span data-ttu-id="a838c-102">Giriş karakter kümesi (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="a838c-102">Input Character Set (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="a838c-103">UTF-16 kodlu UNICODE karakterler kabul eder.</span><span class="sxs-lookup"><span data-stu-id="a838c-103"> accepts UNICODE characters encoded in UTF-16.</span></span>  
  
 <span data-ttu-id="a838c-104">Dize değişmez değerleri tek tırnak içine alınmış herhangi bir UTF-16 karakter içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a838c-104">String literals can contain any UTF-16 character enclosed in single quotes.</span></span> <span data-ttu-id="a838c-105">Örneğin, N '文字列リテラル'.</span><span class="sxs-lookup"><span data-stu-id="a838c-105">For example, N'文字列リテラル'.</span></span> <span data-ttu-id="a838c-106">Dize değişmez değerleri karşılaştırıldığında, özgün UTF-16 değerler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a838c-106">When string literals are compared, the original UTF-16 values are used.</span></span> <span data-ttu-id="a838c-107">Örneğin, N'ABC' Japonca ve Latin kod sayfaları farklıdır.</span><span class="sxs-lookup"><span data-stu-id="a838c-107">For example, N'ABC' is different in Japanese and Latin codepages.</span></span>  
  
 <span data-ttu-id="a838c-108">Yorumlar herhangi bir UTF-16 karakter içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a838c-108">Comments can contain any UTF-16 character.</span></span>  
  
 <span data-ttu-id="a838c-109">Kaçış karakterli tanımlayıcılar köşeli ayraçlar içinde herhangi bir UTF-16 karakter içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a838c-109">Escaped identifiers can contain any UTF-16 character enclosed in square brackets.</span></span> <span data-ttu-id="a838c-110">Örneğin, [エスケープされた識別子].</span><span class="sxs-lookup"><span data-stu-id="a838c-110">For example, [エスケープされた識別子].</span></span> <span data-ttu-id="a838c-111">UTF-16 kaçışlı tanımlayıcıları karşılaştırma büyük küçük harfe duyarlı.</span><span class="sxs-lookup"><span data-stu-id="a838c-111">The comparison of UTF-16 escaped identifiers is case insensitive.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="a838c-112">aynı görünür, ancak farklı karakter olarak farklı kod sayfalarından olan harf sürümlerini değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="a838c-112"> treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="a838c-113">Örneğin, aynı kod sayfasından karşılık gelen karakter ise [ABC] [abc] eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="a838c-113">For example, [ABC] is equivalent to [abc] if the corresponding characters are from the same code page.</span></span> <span data-ttu-id="a838c-114">Aynı iki farklı kod sayfaları tanımlayıcılardır, ancak eşdeğer değiller.</span><span class="sxs-lookup"><span data-stu-id="a838c-114">However, if the same two identifiers are from different code pages, they are not equivalent.</span></span>  
  
 <span data-ttu-id="a838c-115">Beyaz alan tüm UTF-16 boşluk karakterdir.</span><span class="sxs-lookup"><span data-stu-id="a838c-115">White space is any UTF-16 white space character.</span></span>  
  
 <span data-ttu-id="a838c-116">Bir satır başı karakteri herhangi normalleştirilmiş UTF-16 yeni satır karakteri ' dir.</span><span class="sxs-lookup"><span data-stu-id="a838c-116">A newline is any normalized UTF-16 newline character.</span></span> <span data-ttu-id="a838c-117">Örneğin, '\n' ve '\r\n' satırbaşı karakterlerini olarak kabul edilir, ancak '\r' yeni satır karakteri değil.</span><span class="sxs-lookup"><span data-stu-id="a838c-117">For example, '\n' and '\r\n' are considered newline characters, but '\r' is not a newline character.</span></span>  
  
 <span data-ttu-id="a838c-118">Anahtar sözcükler, ifadeler ve noktalama için Latin normalleştirir herhangi bir UTF-16 karakter olabilir.</span><span class="sxs-lookup"><span data-stu-id="a838c-118">Keywords, expressions, and punctuation can be any UTF-16 character that normalizes to Latin.</span></span> <span data-ttu-id="a838c-119">Örneğin, Japonca codepage seçin, geçerli bir anahtar sözcüktür.</span><span class="sxs-lookup"><span data-stu-id="a838c-119">For example, SELECT in a Japanese codepage is a valid keyword.</span></span>  
  
 <span data-ttu-id="a838c-120">Anahtar sözcükler, ifadeler ve noktalama yalnızca Latin karakterler olabilir.</span><span class="sxs-lookup"><span data-stu-id="a838c-120">Keywords, expressions, and punctuation can only be Latin characters.</span></span> <span data-ttu-id="a838c-121">`SELECT`Japonca kod sayfasında bir anahtar değil.</span><span class="sxs-lookup"><span data-stu-id="a838c-121">`SELECT` in a Japanese codepage is not a keyword.</span></span> <span data-ttu-id="a838c-122">+,-, *, /, =, (,), ', [,] ve burada tırnak içine alınmış değil başka bir dil yapısı yalnızca Latin karakterler olabilir.</span><span class="sxs-lookup"><span data-stu-id="a838c-122">+, -, *, /, =, (, ), ‘, [, ] and any other language construct not quoted here can only be Latin characters.</span></span>  
  
 <span data-ttu-id="a838c-123">Basit tanımlayıcıları yalnızca Latin karakterler olabilir.</span><span class="sxs-lookup"><span data-stu-id="a838c-123">Simple identifiers can only be Latin characters.</span></span> <span data-ttu-id="a838c-124">Özgün değerler karşılaştırıldığından bu karşılaştırma sırasında belirsizlik önler.</span><span class="sxs-lookup"><span data-stu-id="a838c-124">This avoids ambiguity during comparison, because original values are compared.</span></span> <span data-ttu-id="a838c-125">Örneğin, ABC Japonca ve Latin kod sayfaları farklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a838c-125">For example, ABC would be different in in Japanese and Latin codepages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a838c-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a838c-126">See Also</span></span>  
 [<span data-ttu-id="a838c-127">Varlık SQL genel bakış</span><span class="sxs-lookup"><span data-stu-id="a838c-127">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
