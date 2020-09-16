---
title: Işlev (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 0bb88992-37ed-4991-ace5-55be612a2c4d
ms.openlocfilehash: a3cc843c7f16f667508aeaea65879de6842478bc
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544498"
---
# <a name="function-entity-sql"></a><span data-ttu-id="ee4f1-102">Işlev (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ee4f1-102">FUNCTION (Entity SQL)</span></span>
<span data-ttu-id="ee4f1-103">Bir Entity SQL sorgu komutunun kapsamındaki bir işlevi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ee4f1-103">Defines a function in the scope of an Entity SQL query command.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee4f1-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ee4f1-104">Syntax</span></span>  
  
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
  
## <a name="arguments"></a><span data-ttu-id="ee4f1-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="ee4f1-105">Arguments</span></span>  
 `function-name`  
 <span data-ttu-id="ee4f1-106">İşlevin adı.</span><span class="sxs-lookup"><span data-stu-id="ee4f1-106">Name of the function.</span></span>  
  
 `parameter-name`  
 <span data-ttu-id="ee4f1-107">İşlevdeki bir parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="ee4f1-107">Name of a parameter in the function.</span></span>  
  
 `function_expression`  
 <span data-ttu-id="ee4f1-108">İşlevi olan geçerli bir Entity SQL ifadesi.</span><span class="sxs-lookup"><span data-stu-id="ee4f1-108">A valid Entity SQL expression that is the function.</span></span> <span data-ttu-id="ee4f1-109">İşlevindeki komut, `parameter_name` işleve geçirilen parametrelere göre hareket edebilir.</span><span class="sxs-lookup"><span data-stu-id="ee4f1-109">The command in the function can act on `parameter_name` parameters passed to the function.</span></span>  
  
 `data_type`  
 <span data-ttu-id="ee4f1-110">Desteklenen bir türün adı.</span><span class="sxs-lookup"><span data-stu-id="ee4f1-110">Name of a supported type.</span></span>  
  
 <span data-ttu-id="ee4f1-111">KOLEKSIYON (<type_definition `>` )</span><span class="sxs-lookup"><span data-stu-id="ee4f1-111">COLLECTION ( <type_definition`>` )</span></span>  
 <span data-ttu-id="ee4f1-112">Desteklenen türlerin, satırların veya başvuruların koleksiyonunu döndüren bir ifade.</span><span class="sxs-lookup"><span data-stu-id="ee4f1-112">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
 <span data-ttu-id="ee4f1-113">REF **(** `data_type` **)**</span><span class="sxs-lookup"><span data-stu-id="ee4f1-113">REF **(**`data_type`**)**</span></span>  
 <span data-ttu-id="ee4f1-114">Bir varlık türüne başvuru döndüren bir ifade.</span><span class="sxs-lookup"><span data-stu-id="ee4f1-114">An expression that returns a reference to an entity type.</span></span>  
  
 <span data-ttu-id="ee4f1-115">SATıR **(** `row_expression` **)**</span><span class="sxs-lookup"><span data-stu-id="ee4f1-115">ROW **(**`row_expression`**)**</span></span>  
 <span data-ttu-id="ee4f1-116">Bir veya daha fazla değerden adsız, yapısal olarak yazılmış kayıtlar döndüren bir ifade.</span><span class="sxs-lookup"><span data-stu-id="ee4f1-116">An expression that returns anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="ee4f1-117">Daha fazla bilgi için bkz. [satır](row-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="ee4f1-117">For more information, see [ROW](row-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee4f1-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ee4f1-118">Remarks</span></span>  
 <span data-ttu-id="ee4f1-119">İşlev imzaları farklı olduğu sürece, aynı ada sahip birden çok işlev satır içi olarak bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="ee4f1-119">Multiple functions with the same name can be declared inline, as long as the function signatures are different.</span></span> <span data-ttu-id="ee4f1-120">Daha fazla bilgi için bkz. [Işlev aşırı yükleme çözünürlüğü](function-overload-resolution-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="ee4f1-120">For more information, see [Function Overload Resolution](function-overload-resolution-entity-sql.md).</span></span>  
  
 <span data-ttu-id="ee4f1-121">Satır içi bir işlev, bir Entity SQL komutunda, yalnızca bu komutta tanımlandıktan sonra çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="ee4f1-121">An inline function can be called in an Entity SQL command only after it has been defined in that command.</span></span> <span data-ttu-id="ee4f1-122">Ancak, satır içi bir işlev başka bir satır içi işlevin içinde, çağrılan işlev tanımlanmadan önce veya sonra çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="ee4f1-122">However, an inline function can be called inside another inline function either before or after the called function has been defined.</span></span> <span data-ttu-id="ee4f1-123">Aşağıdaki örnekte, B işlevi tanımlanmadan önce bir çağrı işlevi B işlevini işle:</span><span class="sxs-lookup"><span data-stu-id="ee4f1-123">In the following example, function A calls function B before function B is defined:</span></span>  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 <span data-ttu-id="ee4f1-124">Daha fazla bilgi için bkz. [nasıl yapılır: Kullanıcı tanımlı bir Işlevi çağırma](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ee4f1-124">For more information, see [How to: Call a User-Defined Function](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100)).</span></span>  
  
 <span data-ttu-id="ee4f1-125">İşlevler ayrıca modelin kendisinde de belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="ee4f1-125">Functions can also be declared in the model itself.</span></span> <span data-ttu-id="ee4f1-126">Modelde belirtilen işlevler, komutta satır içi olarak belirtilen işlevlerle aynı şekilde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="ee4f1-126">Functions declared in the model are executed in the same way as functions declared inline in the command.</span></span> <span data-ttu-id="ee4f1-127">Daha fazla bilgi için bkz. [Kullanıcı tanımlı işlevler](user-defined-functions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="ee4f1-127">For more information, see [User-Defined Functions](user-defined-functions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee4f1-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="ee4f1-128">Example</span></span>  
 <span data-ttu-id="ee4f1-129">Aşağıdaki Entity SQL komutu `Products` döndürülen ürünlerin filtreleneceği bir tamsayı değeri alan bir işlevi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ee4f1-129">The following Entity SQL command defines a function `Products` that takes an integer value to filter the returned products.</span></span>  
  
 [!code-sql[DP EntityServices Concepts#FUNCTION1](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#function1)]  
  
## <a name="example"></a><span data-ttu-id="ee4f1-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="ee4f1-130">Example</span></span>  
 <span data-ttu-id="ee4f1-131">Aşağıdaki Entity SQL komutu, `StringReturnsCollection` döndürülen kişileri filtrelemek için bir dize koleksiyonu alan bir işlevi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ee4f1-131">The following Entity SQL command defines a function `StringReturnsCollection` that takes a collection of strings to filter the returned contacts.</span></span>  
  
 [!code-sql[DP EntityServices Concepts#FUNCTION2](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#function2)]  
  
## <a name="see-also"></a><span data-ttu-id="ee4f1-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee4f1-132">See also</span></span>

- [<span data-ttu-id="ee4f1-133">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="ee4f1-133">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="ee4f1-134">Entity SQL Dili</span><span class="sxs-lookup"><span data-stu-id="ee4f1-134">Entity SQL Language</span></span>](entity-sql-language.md)
