---
description: 'Hakkında daha fazla bilgi edinin: Işlev (Entity SQL)'
title: Işlev (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 0bb88992-37ed-4991-ace5-55be612a2c4d
ms.openlocfilehash: d61aafce03dc7b82b678f1eb107afb79c6c3ed2f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786322"
---
# <a name="function-entity-sql"></a><span data-ttu-id="0d833-103">Işlev (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0d833-103">FUNCTION (Entity SQL)</span></span>

<span data-ttu-id="0d833-104">Bir Entity SQL sorgu komutunun kapsamındaki bir işlevi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0d833-104">Defines a function in the scope of an Entity SQL query command.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d833-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0d833-105">Syntax</span></span>  
  
```sql  
FUNCTION function-name  
( [ { parameter_name <type_definition>
        [ ,...n ]  
  ]  
) AS ( function_expression )
  
<type_definition>::=  
    { data_type | COLLECTION ( <type_definition> )
                | REF ( data_type )
                | ROW ( row_expression )
        }
```  
  
## <a name="arguments"></a><span data-ttu-id="0d833-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="0d833-106">Arguments</span></span>  

 `function-name`  
 <span data-ttu-id="0d833-107">İşlevin adı.</span><span class="sxs-lookup"><span data-stu-id="0d833-107">Name of the function.</span></span>  
  
 `parameter-name`  
 <span data-ttu-id="0d833-108">İşlevdeki bir parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="0d833-108">Name of a parameter in the function.</span></span>  
  
 `function_expression`  
 <span data-ttu-id="0d833-109">İşlevi olan geçerli bir Entity SQL ifadesi.</span><span class="sxs-lookup"><span data-stu-id="0d833-109">A valid Entity SQL expression that is the function.</span></span> <span data-ttu-id="0d833-110">İşlevindeki komut, `parameter_name` işleve geçirilen parametrelere göre hareket edebilir.</span><span class="sxs-lookup"><span data-stu-id="0d833-110">The command in the function can act on `parameter_name` parameters passed to the function.</span></span>  
  
 `data_type`  
 <span data-ttu-id="0d833-111">Desteklenen bir türün adı.</span><span class="sxs-lookup"><span data-stu-id="0d833-111">Name of a supported type.</span></span>  
  
 <span data-ttu-id="0d833-112">KOLEKSIYON (<type_definition `>` )</span><span class="sxs-lookup"><span data-stu-id="0d833-112">COLLECTION ( <type_definition`>` )</span></span>  
 <span data-ttu-id="0d833-113">Desteklenen türlerin, satırların veya başvuruların koleksiyonunu döndüren bir ifade.</span><span class="sxs-lookup"><span data-stu-id="0d833-113">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
 <span data-ttu-id="0d833-114">REF **(** `data_type` **)**</span><span class="sxs-lookup"><span data-stu-id="0d833-114">REF **(**`data_type`**)**</span></span>  
 <span data-ttu-id="0d833-115">Bir varlık türüne başvuru döndüren bir ifade.</span><span class="sxs-lookup"><span data-stu-id="0d833-115">An expression that returns a reference to an entity type.</span></span>  
  
 <span data-ttu-id="0d833-116">SATıR **(** `row_expression` **)**</span><span class="sxs-lookup"><span data-stu-id="0d833-116">ROW **(**`row_expression`**)**</span></span>  
 <span data-ttu-id="0d833-117">Bir veya daha fazla değerden adsız, yapısal olarak yazılmış kayıtlar döndüren bir ifade.</span><span class="sxs-lookup"><span data-stu-id="0d833-117">An expression that returns anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="0d833-118">Daha fazla bilgi için bkz. [satır](row-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="0d833-118">For more information, see [ROW](row-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d833-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0d833-119">Remarks</span></span>  

 <span data-ttu-id="0d833-120">İşlev imzaları farklı olduğu sürece, aynı ada sahip birden çok işlev satır içi olarak bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="0d833-120">Multiple functions with the same name can be declared inline, as long as the function signatures are different.</span></span> <span data-ttu-id="0d833-121">Daha fazla bilgi için bkz. [Işlev aşırı yükleme çözünürlüğü](function-overload-resolution-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="0d833-121">For more information, see [Function Overload Resolution](function-overload-resolution-entity-sql.md).</span></span>  
  
 <span data-ttu-id="0d833-122">Satır içi bir işlev, bir Entity SQL komutunda, yalnızca bu komutta tanımlandıktan sonra çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="0d833-122">An inline function can be called in an Entity SQL command only after it has been defined in that command.</span></span> <span data-ttu-id="0d833-123">Ancak, satır içi bir işlev başka bir satır içi işlevin içinde, çağrılan işlev tanımlanmadan önce veya sonra çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="0d833-123">However, an inline function can be called inside another inline function either before or after the called function has been defined.</span></span> <span data-ttu-id="0d833-124">Aşağıdaki örnekte, B işlevi tanımlanmadan önce bir çağrı işlevi B işlevini işle:</span><span class="sxs-lookup"><span data-stu-id="0d833-124">In the following example, function A calls function B before function B is defined:</span></span>  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 <span data-ttu-id="0d833-125">Daha fazla bilgi için bkz. [nasıl yapılır: çağrı User-Defined işlevi](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0d833-125">For more information, see [How to: Call a User-Defined Function](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100)).</span></span>  
  
 <span data-ttu-id="0d833-126">İşlevler ayrıca modelin kendisinde de belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="0d833-126">Functions can also be declared in the model itself.</span></span> <span data-ttu-id="0d833-127">Modelde belirtilen işlevler, komutta satır içi olarak belirtilen işlevlerle aynı şekilde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="0d833-127">Functions declared in the model are executed in the same way as functions declared inline in the command.</span></span> <span data-ttu-id="0d833-128">Daha fazla bilgi için bkz. [Kullanıcı tanımlı işlevler](user-defined-functions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="0d833-128">For more information, see [User-Defined Functions](user-defined-functions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d833-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="0d833-129">Example</span></span>  

 <span data-ttu-id="0d833-130">Aşağıdaki Entity SQL komutu `Products` döndürülen ürünlerin filtreleneceği bir tamsayı değeri alan bir işlevi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0d833-130">The following Entity SQL command defines a function `Products` that takes an integer value to filter the returned products.</span></span>  
  
 [!code-sql[DP EntityServices Concepts#FUNCTION1](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#function1)]  
  
## <a name="example"></a><span data-ttu-id="0d833-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="0d833-131">Example</span></span>  

 <span data-ttu-id="0d833-132">Aşağıdaki Entity SQL komutu, `StringReturnsCollection` döndürülen kişileri filtrelemek için bir dize koleksiyonu alan bir işlevi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0d833-132">The following Entity SQL command defines a function `StringReturnsCollection` that takes a collection of strings to filter the returned contacts.</span></span>  
  
 [!code-sql[DP EntityServices Concepts#FUNCTION2](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#function2)]  
  
## <a name="see-also"></a><span data-ttu-id="0d833-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d833-133">See also</span></span>

- [<span data-ttu-id="0d833-134">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="0d833-134">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="0d833-135">Entity SQL Dili</span><span class="sxs-lookup"><span data-stu-id="0d833-135">Entity SQL Language</span></span>](entity-sql-language.md)
