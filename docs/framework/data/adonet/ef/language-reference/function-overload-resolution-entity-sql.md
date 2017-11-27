---
title: "İşlev aşırı yükleme çözümü (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c648054-3808-4a69-9d3e-98e6a4f9c5ca
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f46bc1712946ec26f2ab1cbece7603a5336a831e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="function-overload-resolution-entity-sql"></a><span data-ttu-id="e38cc-102">İşlev aşırı yükleme çözümü (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="e38cc-102">Function Overload Resolution (Entity SQL)</span></span>
<span data-ttu-id="e38cc-103">Bu konuda açıklanmaktadır nasıl [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işlevleri giderilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e38cc-103">This topic describes how [!INCLUDE[esql](../../../../../../includes/esql-md.md)] functions are resolved.</span></span>  
  
 <span data-ttu-id="e38cc-104">Benzersiz imzaları işlevleri olduğu sürece aynı ada sahip birden fazla işlev tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="e38cc-104">More than one function can be defined with the same name, as long as the functions have unique signatures.</span></span>  
  
 <span data-ttu-id="e38cc-105">Bu durumda, hangi işlevi, belirtilen ifade tarafından başvurulan belirlemek için aşağıdaki ölçütleri uygulanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e38cc-105">When this is the case, the following criteria must be applied to determine which function is referenced by a given expression.</span></span> <span data-ttu-id="e38cc-106">Bu ölçütler sırayla uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e38cc-106">These criteria are applied in sequence.</span></span> <span data-ttu-id="e38cc-107">Yalnızca tek bir işleve uygulayan ilk ölçütü çözümlenen bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="e38cc-107">The first criterion that applies only to a single function is the resolved function.</span></span>  
  
1.  <span data-ttu-id="e38cc-108">**Numaralı parametre**.</span><span class="sxs-lookup"><span data-stu-id="e38cc-108">**Parameter number**.</span></span> <span data-ttu-id="e38cc-109">Aynı deyimde parametre sayısı belirtilmiş işlevi içeriyor.</span><span class="sxs-lookup"><span data-stu-id="e38cc-109">The function has the same number of parameters specified in the expression.</span></span>  
  
2.  <span data-ttu-id="e38cc-110">**Tam eşleşme türündeki**.</span><span class="sxs-lookup"><span data-stu-id="e38cc-110">**Exact match on type**.</span></span> <span data-ttu-id="e38cc-111">Her bağımsız değişken türü işlevinin tam olarak parametre türüyle eşleşen veya null sabit değer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e38cc-111">Each argument type of the function exactly matches the parameter type, or is the null literal.</span></span>  
  
3.  <span data-ttu-id="e38cc-112">**Alt eşleşme**.</span><span class="sxs-lookup"><span data-stu-id="e38cc-112">**Match on subtype**.</span></span> <span data-ttu-id="e38cc-113">Her bağımsız değişken türü işlevinin tam olarak eşleşen veya parametre türü bir alt türü ya da bağımsız değişkeni null sabit değer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e38cc-113">Each argument type of the function exactly matches or is a sub-type of the parameter type, or the argument is the null literal.</span></span> <span data-ttu-id="e38cc-114">Çeşitli işlevler yalnızca farklı gerektiğinde, alt türü dönüştürme sayısı gerekli, en az işlev çözümlenmiş işlevi alt türü dönüşümleri sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="e38cc-114">In the event that several functions differ only in the number of sub-type conversions required, the function with the least number of sub-type conversions is the resolved function.</span></span>  
  
4.  <span data-ttu-id="e38cc-115">**Alt türü veya türü yükseltme eşleşme**.</span><span class="sxs-lookup"><span data-stu-id="e38cc-115">**Match on subtype or type promotion**.</span></span> <span data-ttu-id="e38cc-116">Her bağımsız değişken türü işlevinin tam olarak eşleşir, bir alt türü veya parametre türüne yükseltilebilir ya da bağımsız değişkeni null sabit değer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e38cc-116">Each argument type of the function exactly matches, is a sub-type of, or can be promoted to the parameter type, or the argument is the null literal.</span></span> <span data-ttu-id="e38cc-117">Tekrar sayısı alt tür dönüştürmeleri ve promosyonlar, en az işlev içinde yalnızca bazı işlevler farklı olay alt tür dönüştürmeleri ve promosyonlar sayısıdır çözümlenmiş işlevi.</span><span class="sxs-lookup"><span data-stu-id="e38cc-117">Again, in the event that several functions differ only in the number of sub-type conversions and promotions, the function with the least number of sub-type conversions and promotions is the resolved function.</span></span>  
  
 <span data-ttu-id="e38cc-118">Bu ölçütler hiçbiri seçilmesini tek bir işlevinde sağlamazsa, işlev çağırma ifadesi belirsiz.</span><span class="sxs-lookup"><span data-stu-id="e38cc-118">If none of these criteria result in a single function being selected, the function invocation expression is ambiguous.</span></span>  
  
 <span data-ttu-id="e38cc-119">Bu kurallar kullanarak tek bir işlev ayıklanabilir olsa bile, bağımsız değişkenler parametreleri hala eşleşmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="e38cc-119">Even if a single function can be extracted using these rules, the arguments still might not match the parameters.</span></span> <span data-ttu-id="e38cc-120">Bu durumda bir hata ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="e38cc-120">An error is raised in this case.</span></span>  
  
 <span data-ttu-id="e38cc-121">Bile, kullanıcı tanımlı işlev için daha iyi bir eşleşme imzayla modeli tanımlı bir işlev mevcut olduğunda kullanıcı tanımlı işlevler, satır içi bir sorgu işlev tanımı önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="e38cc-121">For user-defined functions, the definition for an inline query function takes precedence even when a model-defined function exists with a signature that is a better match for the user-defined function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e38cc-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e38cc-122">See Also</span></span>  
 [<span data-ttu-id="e38cc-123">Varlık SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="e38cc-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="e38cc-124">Varlık SQL genel bakış</span><span class="sxs-lookup"><span data-stu-id="e38cc-124">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="e38cc-125">İşlevler</span><span class="sxs-lookup"><span data-stu-id="e38cc-125">Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
