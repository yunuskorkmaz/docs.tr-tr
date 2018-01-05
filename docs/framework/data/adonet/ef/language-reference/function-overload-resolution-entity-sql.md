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
ms.workload: dotnet
ms.openlocfilehash: 3a303ca917a9f6cfee42d11456a1f80b52ffd2ef
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="function-overload-resolution-entity-sql"></a><span data-ttu-id="ca30b-102">İşlev aşırı yükleme çözümü (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="ca30b-102">Function Overload Resolution (Entity SQL)</span></span>
<span data-ttu-id="ca30b-103">Bu konuda açıklanmaktadır nasıl [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işlevleri giderilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ca30b-103">This topic describes how [!INCLUDE[esql](../../../../../../includes/esql-md.md)] functions are resolved.</span></span>  
  
 <span data-ttu-id="ca30b-104">Benzersiz imzaları işlevleri olduğu sürece aynı ada sahip birden fazla işlev tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="ca30b-104">More than one function can be defined with the same name, as long as the functions have unique signatures.</span></span>  
  
 <span data-ttu-id="ca30b-105">Bu durumda, hangi işlevi, belirtilen ifade tarafından başvurulan belirlemek için aşağıdaki ölçütleri uygulanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ca30b-105">When this is the case, the following criteria must be applied to determine which function is referenced by a given expression.</span></span> <span data-ttu-id="ca30b-106">Bu ölçütler sırayla uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ca30b-106">These criteria are applied in sequence.</span></span> <span data-ttu-id="ca30b-107">Yalnızca tek bir işleve uygulayan ilk ölçütü çözümlenen bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="ca30b-107">The first criterion that applies only to a single function is the resolved function.</span></span>  
  
1.  <span data-ttu-id="ca30b-108">**Numaralı parametre**.</span><span class="sxs-lookup"><span data-stu-id="ca30b-108">**Parameter number**.</span></span> <span data-ttu-id="ca30b-109">Aynı deyimde parametre sayısı belirtilmiş işlevi içeriyor.</span><span class="sxs-lookup"><span data-stu-id="ca30b-109">The function has the same number of parameters specified in the expression.</span></span>  
  
2.  <span data-ttu-id="ca30b-110">**Tam eşleşme türündeki**.</span><span class="sxs-lookup"><span data-stu-id="ca30b-110">**Exact match on type**.</span></span> <span data-ttu-id="ca30b-111">Her bağımsız değişken türü işlevinin tam olarak parametre türüyle eşleşen veya null sabit değer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ca30b-111">Each argument type of the function exactly matches the parameter type, or is the null literal.</span></span>  
  
3.  <span data-ttu-id="ca30b-112">**Alt eşleşme**.</span><span class="sxs-lookup"><span data-stu-id="ca30b-112">**Match on subtype**.</span></span> <span data-ttu-id="ca30b-113">Her bağımsız değişken türü işlevinin tam olarak eşleşen veya parametre türü bir alt türü ya da bağımsız değişkeni null sabit değer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ca30b-113">Each argument type of the function exactly matches or is a sub-type of the parameter type, or the argument is the null literal.</span></span> <span data-ttu-id="ca30b-114">Çeşitli işlevler yalnızca farklı gerektiğinde, alt türü dönüştürme sayısı gerekli, en az işlev çözümlenmiş işlevi alt türü dönüşümleri sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="ca30b-114">In the event that several functions differ only in the number of sub-type conversions required, the function with the least number of sub-type conversions is the resolved function.</span></span>  
  
4.  <span data-ttu-id="ca30b-115">**Alt türü veya türü yükseltme eşleşme**.</span><span class="sxs-lookup"><span data-stu-id="ca30b-115">**Match on subtype or type promotion**.</span></span> <span data-ttu-id="ca30b-116">Her bağımsız değişken türü işlevinin tam olarak eşleşir, bir alt türü veya parametre türüne yükseltilebilir ya da bağımsız değişkeni null sabit değer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ca30b-116">Each argument type of the function exactly matches, is a sub-type of, or can be promoted to the parameter type, or the argument is the null literal.</span></span> <span data-ttu-id="ca30b-117">Tekrar sayısı alt tür dönüştürmeleri ve promosyonlar, en az işlev içinde yalnızca bazı işlevler farklı olay alt tür dönüştürmeleri ve promosyonlar sayısıdır çözümlenmiş işlevi.</span><span class="sxs-lookup"><span data-stu-id="ca30b-117">Again, in the event that several functions differ only in the number of sub-type conversions and promotions, the function with the least number of sub-type conversions and promotions is the resolved function.</span></span>  
  
 <span data-ttu-id="ca30b-118">Bu ölçütler hiçbiri seçilmesini tek bir işlevinde sağlamazsa, işlev çağırma ifadesi belirsiz.</span><span class="sxs-lookup"><span data-stu-id="ca30b-118">If none of these criteria result in a single function being selected, the function invocation expression is ambiguous.</span></span>  
  
 <span data-ttu-id="ca30b-119">Bu kurallar kullanarak tek bir işlev ayıklanabilir olsa bile, bağımsız değişkenler parametreleri hala eşleşmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="ca30b-119">Even if a single function can be extracted using these rules, the arguments still might not match the parameters.</span></span> <span data-ttu-id="ca30b-120">Bu durumda bir hata ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="ca30b-120">An error is raised in this case.</span></span>  
  
 <span data-ttu-id="ca30b-121">Bile, kullanıcı tanımlı işlev için daha iyi bir eşleşme imzayla modeli tanımlı bir işlev mevcut olduğunda kullanıcı tanımlı işlevler, satır içi bir sorgu işlev tanımı önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="ca30b-121">For user-defined functions, the definition for an inline query function takes precedence even when a model-defined function exists with a signature that is a better match for the user-defined function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca30b-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ca30b-122">See Also</span></span>  
 [<span data-ttu-id="ca30b-123">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="ca30b-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="ca30b-124">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ca30b-124">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="ca30b-125">İşlevler</span><span class="sxs-lookup"><span data-stu-id="ca30b-125">Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
