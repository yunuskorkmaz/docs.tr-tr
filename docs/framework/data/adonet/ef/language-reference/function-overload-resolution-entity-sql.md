---
title: İşlev aşırı yükleme çözümü (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 9c648054-3808-4a69-9d3e-98e6a4f9c5ca
ms.openlocfilehash: 0248fdd3f3ba6afb5c7edca740d9aad3ca74bd03
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302523"
---
# <a name="function-overload-resolution-entity-sql"></a><span data-ttu-id="91f12-102">İşlev aşırı yükleme çözümü (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="91f12-102">Function Overload Resolution (Entity SQL)</span></span>
<span data-ttu-id="91f12-103">Bu konu açıklar nasıl [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işlevleri giderilmiştir.</span><span class="sxs-lookup"><span data-stu-id="91f12-103">This topic describes how [!INCLUDE[esql](../../../../../../includes/esql-md.md)] functions are resolved.</span></span>  
  
 <span data-ttu-id="91f12-104">Benzersiz imzaları işlevleri olduğu sürece, aynı ada sahip birden fazla işlev tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="91f12-104">More than one function can be defined with the same name, as long as the functions have unique signatures.</span></span>  
  
 <span data-ttu-id="91f12-105">Bu durumda, hangi işlevi, belirtilen bir ifade tarafından başvurulan belirlemek için aşağıdaki ölçütleri uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="91f12-105">When this is the case, the following criteria must be applied to determine which function is referenced by a given expression.</span></span> <span data-ttu-id="91f12-106">Bu ölçütler sırayla uygulanır.</span><span class="sxs-lookup"><span data-stu-id="91f12-106">These criteria are applied in sequence.</span></span> <span data-ttu-id="91f12-107">Yalnızca tek bir işleve uygulayan bir ilk ölçütü çözümlenen bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="91f12-107">The first criterion that applies only to a single function is the resolved function.</span></span>  
  
1. <span data-ttu-id="91f12-108">**Parametre numarası**.</span><span class="sxs-lookup"><span data-stu-id="91f12-108">**Parameter number**.</span></span> <span data-ttu-id="91f12-109">Aynı deyimde parametre sayısı belirtilmiş işlevi vardır.</span><span class="sxs-lookup"><span data-stu-id="91f12-109">The function has the same number of parameters specified in the expression.</span></span>  
  
2. <span data-ttu-id="91f12-110">**Tam eşleşme türü**.</span><span class="sxs-lookup"><span data-stu-id="91f12-110">**Exact match on type**.</span></span> <span data-ttu-id="91f12-111">Her işlevin bağımsız değişken türü tam olarak parametre türüyle eşleşen veya null bir sabit değer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="91f12-111">Each argument type of the function exactly matches the parameter type, or is the null literal.</span></span>  
  
3. <span data-ttu-id="91f12-112">**Alt eşleşme**.</span><span class="sxs-lookup"><span data-stu-id="91f12-112">**Match on subtype**.</span></span> <span data-ttu-id="91f12-113">İşlev bağımsız değişken türlerinin tam olarak eşleşen veya parametre türü bir alt tür ya da bağımsız değişken null bir sabit değer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="91f12-113">Each argument type of the function exactly matches or is a sub-type of the parameter type, or the argument is the null literal.</span></span> <span data-ttu-id="91f12-114">Çeşitli işlevler yalnızca farklı olay, alt tür dönüştürmeleri sayısı gerekli, en az işlev çözümlenen işlevi alt tür dönüştürmeleri sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="91f12-114">In the event that several functions differ only in the number of sub-type conversions required, the function with the least number of sub-type conversions is the resolved function.</span></span>  
  
4. <span data-ttu-id="91f12-115">**Alt tür veya tür promosyonu eşleşmeye**.</span><span class="sxs-lookup"><span data-stu-id="91f12-115">**Match on subtype or type promotion**.</span></span> <span data-ttu-id="91f12-116">İşlev bağımsız değişken türlerinin tam olarak eşleşir, bir alt tür veya parametre türüne yükseltilebilir veya bağımsız değişken null bir sabit değer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="91f12-116">Each argument type of the function exactly matches, is a sub-type of, or can be promoted to the parameter type, or the argument is the null literal.</span></span> <span data-ttu-id="91f12-117">Yeniden çeşitli işlevler yalnızca alt tür dönüştürmeleri ve promosyonlar, en az işlev sayısı, farklı olay alt tür dönüştürmeleri ve promosyonlar sayısıdır çözümlenen işlevi.</span><span class="sxs-lookup"><span data-stu-id="91f12-117">Again, in the event that several functions differ only in the number of sub-type conversions and promotions, the function with the least number of sub-type conversions and promotions is the resolved function.</span></span>  
  
 <span data-ttu-id="91f12-118">İşlev çağrısı ifadesi, bu ölçütlerin hiçbiri seçili tek bir işlevde yol açarsa belirsiz.</span><span class="sxs-lookup"><span data-stu-id="91f12-118">If none of these criteria result in a single function being selected, the function invocation expression is ambiguous.</span></span>  
  
 <span data-ttu-id="91f12-119">Bu kuralları kullanarak tek bir işlev ayıklanabileceği olsa bile, bağımsız değişkenler parametrelerini hala eşleşmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="91f12-119">Even if a single function can be extracted using these rules, the arguments still might not match the parameters.</span></span> <span data-ttu-id="91f12-120">Bu durumda bir hata ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="91f12-120">An error is raised in this case.</span></span>  
  
 <span data-ttu-id="91f12-121">Daha iyi bir eşleşme için kullanıcı tanımlı işlev imzası ile model tanımlı bir işlev mevcut olduğunda kullanıcı tanımlı işlevler için bir satır içi sorgu işlev tanımı önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="91f12-121">For user-defined functions, the definition for an inline query function takes precedence even when a model-defined function exists with a signature that is a better match for the user-defined function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91f12-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91f12-122">See also</span></span>

- [<span data-ttu-id="91f12-123">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="91f12-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="91f12-124">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="91f12-124">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="91f12-125">İşlevler</span><span class="sxs-lookup"><span data-stu-id="91f12-125">Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
