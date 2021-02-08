---
description: 'Daha fazla bilgi edinin: Işlev aşırı yükleme çözünürlüğü (Entity SQL)'
title: İşlev aşırı yükleme çözünürlüğü (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 9c648054-3808-4a69-9d3e-98e6a4f9c5ca
ms.openlocfilehash: 8fbe0b54ed559d1f962c3e916d25554e0de65737
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786335"
---
# <a name="function-overload-resolution-entity-sql"></a><span data-ttu-id="cbca8-103">İşlev aşırı yükleme çözünürlüğü (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="cbca8-103">Function Overload Resolution (Entity SQL)</span></span>

<span data-ttu-id="cbca8-104">Bu konu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] , işlevlerin nasıl çözümlendiğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="cbca8-104">This topic describes how [!INCLUDE[esql](../../../../../../includes/esql-md.md)] functions are resolved.</span></span>  
  
 <span data-ttu-id="cbca8-105">İşlevlerin benzersiz imzaları olduğu sürece, birden fazla işlev aynı adla tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="cbca8-105">More than one function can be defined with the same name, as long as the functions have unique signatures.</span></span>  
  
 <span data-ttu-id="cbca8-106">Bu durum söz konusu olduğunda, belirli bir ifade tarafından hangi işlevin başvurulduğunu belirleyen aşağıdaki kriterlerin uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cbca8-106">When this is the case, the following criteria must be applied to determine which function is referenced by a given expression.</span></span> <span data-ttu-id="cbca8-107">Bu ölçütler sırayla uygulanır.</span><span class="sxs-lookup"><span data-stu-id="cbca8-107">These criteria are applied in sequence.</span></span> <span data-ttu-id="cbca8-108">Yalnızca tek bir işlev için geçerli olan ilk ölçüt çözümlenen işlevdir.</span><span class="sxs-lookup"><span data-stu-id="cbca8-108">The first criterion that applies only to a single function is the resolved function.</span></span>  
  
1. <span data-ttu-id="cbca8-109">**Parametre numarası**.</span><span class="sxs-lookup"><span data-stu-id="cbca8-109">**Parameter number**.</span></span> <span data-ttu-id="cbca8-110">İşlev, ifadede belirtilen sayıda parametreye sahip.</span><span class="sxs-lookup"><span data-stu-id="cbca8-110">The function has the same number of parameters specified in the expression.</span></span>  
  
2. <span data-ttu-id="cbca8-111">**Tür üzerinde tam eşleşme**.</span><span class="sxs-lookup"><span data-stu-id="cbca8-111">**Exact match on type**.</span></span> <span data-ttu-id="cbca8-112">İşlevin her bağımsız değişken türü parametre türüyle tam olarak eşleşir veya null değişmez değerdir.</span><span class="sxs-lookup"><span data-stu-id="cbca8-112">Each argument type of the function exactly matches the parameter type, or is the null literal.</span></span>  
  
3. <span data-ttu-id="cbca8-113">**Alt tür Ile Eşleştir**.</span><span class="sxs-lookup"><span data-stu-id="cbca8-113">**Match on subtype**.</span></span> <span data-ttu-id="cbca8-114">İşlevin her bağımsız değişken türü tam olarak eşleşir veya parametre türünün bir alt türü veya bağımsız değişkeni null değişmez değerdir.</span><span class="sxs-lookup"><span data-stu-id="cbca8-114">Each argument type of the function exactly matches or is a sub-type of the parameter type, or the argument is the null literal.</span></span> <span data-ttu-id="cbca8-115">Birkaç işlevin yalnızca gereken alt tür dönüştürmelerde farklı olması durumunda, en az sayıda alt tür Dönüştürmelere sahip işlev çözümlenmiş işlevdir.</span><span class="sxs-lookup"><span data-stu-id="cbca8-115">In the event that several functions differ only in the number of sub-type conversions required, the function with the least number of sub-type conversions is the resolved function.</span></span>  
  
4. <span data-ttu-id="cbca8-116">**Alt tür veya tür promosyonu eşleştirin**.</span><span class="sxs-lookup"><span data-stu-id="cbca8-116">**Match on subtype or type promotion**.</span></span> <span data-ttu-id="cbca8-117">İşlevin her bağımsız değişken türü tam olarak eşleşir, bir alt türüdür, veya parametre türüne yükseltilebilir veya bağımsız değişken null değişmez değerdir.</span><span class="sxs-lookup"><span data-stu-id="cbca8-117">Each argument type of the function exactly matches, is a sub-type of, or can be promoted to the parameter type, or the argument is the null literal.</span></span> <span data-ttu-id="cbca8-118">Bu durumda, birkaç işlevin yalnızca alt tür dönüştürmeleri ve yükseltmeleri sayısında farklı olması durumunda, en az sayıda alt tür dönüştürmeleri ve promosyonları çözümlenen işlevdir.</span><span class="sxs-lookup"><span data-stu-id="cbca8-118">Again, in the event that several functions differ only in the number of sub-type conversions and promotions, the function with the least number of sub-type conversions and promotions is the resolved function.</span></span>  
  
 <span data-ttu-id="cbca8-119">Bu ölçütlerden hiçbiri seçili olmayan tek bir işlev ile sonuçlanmadığı takdirde, işlev çağırma ifadesi belirsizdir.</span><span class="sxs-lookup"><span data-stu-id="cbca8-119">If none of these criteria result in a single function being selected, the function invocation expression is ambiguous.</span></span>  
  
 <span data-ttu-id="cbca8-120">Tek bir işlev bu kurallar kullanılarak ayıklanabileceği halde, bağımsız değişkenler parametrelerle eşleşmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="cbca8-120">Even if a single function can be extracted using these rules, the arguments still might not match the parameters.</span></span> <span data-ttu-id="cbca8-121">Bu durumda bir hata ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="cbca8-121">An error is raised in this case.</span></span>  
  
 <span data-ttu-id="cbca8-122">Kullanıcı tanımlı işlevler için, bir satır içi sorgu işlevinin tanımı, Kullanıcı tanımlı işlev için daha iyi bir eşleşme olan imzaya sahip, model tanımlı bir işlev olduğunda bile öncelik kazanır.</span><span class="sxs-lookup"><span data-stu-id="cbca8-122">For user-defined functions, the definition for an inline query function takes precedence even when a model-defined function exists with a signature that is a better match for the user-defined function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbca8-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cbca8-123">See also</span></span>

- [<span data-ttu-id="cbca8-124">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="cbca8-124">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="cbca8-125">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cbca8-125">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="cbca8-126">İşlevler</span><span class="sxs-lookup"><span data-stu-id="cbca8-126">Functions</span></span>](functions-entity-sql.md)
