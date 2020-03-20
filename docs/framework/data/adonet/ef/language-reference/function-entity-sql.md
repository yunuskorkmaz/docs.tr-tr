---
title: İşLEV (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 0bb88992-37ed-4991-ace5-55be612a2c4d
ms.openlocfilehash: fd7f484733e7135d2d6c8094b6527d672a988088
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150304"
---
# <a name="function-entity-sql"></a><span data-ttu-id="87c68-102">İşLEV (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="87c68-102">FUNCTION (Entity SQL)</span></span>
<span data-ttu-id="87c68-103">Varlık SQL sorgu komutu kapsamındaki bir işlevi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="87c68-103">Defines a function in the scope of an Entity SQL query command.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87c68-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="87c68-104">Syntax</span></span>  
  
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
  
## <a name="arguments"></a><span data-ttu-id="87c68-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="87c68-105">Arguments</span></span>  
 `function-name`  
 <span data-ttu-id="87c68-106">Fonksiyonun adı.</span><span class="sxs-lookup"><span data-stu-id="87c68-106">Name of the function.</span></span>  
  
 `parameter-name`  
 <span data-ttu-id="87c68-107">İşlevdeki bir parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="87c68-107">Name of a parameter in the function.</span></span>  
  
 `function_expression`  
 <span data-ttu-id="87c68-108">İşlev olan geçerli bir Entity SQL ifadesi.</span><span class="sxs-lookup"><span data-stu-id="87c68-108">A valid Entity SQL expression that is the function.</span></span> <span data-ttu-id="87c68-109">İşlevdeki komut, işleve geçirilen parametrelere göre `parameter_name` hareket edebilir.</span><span class="sxs-lookup"><span data-stu-id="87c68-109">The command in the function can act on `parameter_name` parameters passed to the function.</span></span>  
  
 `data_type`  
 <span data-ttu-id="87c68-110">Desteklenen bir türün adı.</span><span class="sxs-lookup"><span data-stu-id="87c68-110">Name of a supported type.</span></span>  
  
 <span data-ttu-id="87c68-111">TOPLAMA (`>` <type_definition )</span><span class="sxs-lookup"><span data-stu-id="87c68-111">COLLECTION ( <type_definition`>` )</span></span>  
 <span data-ttu-id="87c68-112">Desteklenen türler, satırlar veya başvurular koleksiyonunu döndüren bir ifade.</span><span class="sxs-lookup"><span data-stu-id="87c68-112">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
 <span data-ttu-id="87c68-113">REF **(**`data_type`**)**</span><span class="sxs-lookup"><span data-stu-id="87c68-113">REF **(**`data_type`**)**</span></span>  
 <span data-ttu-id="87c68-114">Bir varlık türüne başvuru döndüren bir ifade.</span><span class="sxs-lookup"><span data-stu-id="87c68-114">An expression that returns a reference to an entity type.</span></span>  
  
 <span data-ttu-id="87c68-115">SATıR **(**`row_expression`**)**</span><span class="sxs-lookup"><span data-stu-id="87c68-115">ROW **(**`row_expression`**)**</span></span>  
 <span data-ttu-id="87c68-116">Bir veya daha fazla değerden anonim, yapısal olarak yazılan kayıtları döndüren bir ifade.</span><span class="sxs-lookup"><span data-stu-id="87c68-116">An expression that returns anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="87c68-117">Daha fazla bilgi için [ROW'a](row-entity-sql.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="87c68-117">For more information, see [ROW](row-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87c68-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="87c68-118">Remarks</span></span>  
 <span data-ttu-id="87c68-119">İşlev imzaları farklı olduğu sürece, aynı ada sahip birden çok işlev satır içinde bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="87c68-119">Multiple functions with the same name can be declared inline, as long as the function signatures are different.</span></span> <span data-ttu-id="87c68-120">Daha fazla bilgi için [bkz.](function-overload-resolution-entity-sql.md)</span><span class="sxs-lookup"><span data-stu-id="87c68-120">For more information, see [Function Overload Resolution](function-overload-resolution-entity-sql.md).</span></span>  
  
 <span data-ttu-id="87c68-121">Bir satır arası işlev, varlık SQL komutunda ancak bu komutta tanımlandıktan sonra çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="87c68-121">An inline function can be called in an Entity SQL command only after it has been defined in that command.</span></span> <span data-ttu-id="87c68-122">Ancak, bir satır içi işlev, çağrılan işlev tanımlandıktan önce veya sonra başka bir satır içi işlevin içinde çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="87c68-122">However, an inline function can be called inside another inline function either before or after the called function has been defined.</span></span> <span data-ttu-id="87c68-123">Aşağıdaki örnekte, B işlevi tanımlanmadan önce A işlevi B'yi çağırır:</span><span class="sxs-lookup"><span data-stu-id="87c68-123">In the following example, function A calls function B before function B is defined:</span></span>  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 <span data-ttu-id="87c68-124">Daha fazla bilgi için [bkz: Kullanıcı Tanımlı İşlev'i çağırın.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="87c68-124">For more information, see [How to: Call a User-Defined Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100)).</span></span>  
  
 <span data-ttu-id="87c68-125">İşlevler modelin kendisinde de bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="87c68-125">Functions can also be declared in the model itself.</span></span> <span data-ttu-id="87c68-126">Modelde bildirilen işlevler, komutta satır içinde bildirilen işlevler gibi yürütülür.</span><span class="sxs-lookup"><span data-stu-id="87c68-126">Functions declared in the model are executed in the same way as functions declared inline in the command.</span></span> <span data-ttu-id="87c68-127">Daha fazla bilgi için [Bkz. Kullanıcı Tanımlı Fonksiyonlar.](user-defined-functions-entity-sql.md)</span><span class="sxs-lookup"><span data-stu-id="87c68-127">For more information, see [User-Defined Functions](user-defined-functions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="87c68-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="87c68-128">Example</span></span>  
 <span data-ttu-id="87c68-129">Aşağıdaki Entity SQL komutu, `Products` döndürülen ürünleri filtrelemek için tamsayı değeri alan bir işlev tanımlar.</span><span class="sxs-lookup"><span data-stu-id="87c68-129">The following Entity SQL command defines a function `Products` that takes an integer value to filter the returned products.</span></span>  
  
 [!code-sql[DP EntityServices Concepts#FUNCTION1](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#function1)]  
  
## <a name="example"></a><span data-ttu-id="87c68-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="87c68-130">Example</span></span>  
 <span data-ttu-id="87c68-131">Aşağıdaki Entity SQL komutu, `StringReturnsCollection` döndürülen kişileri filtrelemek için dize ler koleksiyonu alan bir işlev tanımlar.</span><span class="sxs-lookup"><span data-stu-id="87c68-131">The following Entity SQL command defines a function `StringReturnsCollection` that takes a collection of strings to filter the returned contacts.</span></span>  
  
 [!code-sql[DP EntityServices Concepts#FUNCTION2](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#function2)]  
  
## <a name="see-also"></a><span data-ttu-id="87c68-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87c68-132">See also</span></span>

- [<span data-ttu-id="87c68-133">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="87c68-133">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="87c68-134">Entity SQL Dili</span><span class="sxs-lookup"><span data-stu-id="87c68-134">Entity SQL Language</span></span>](entity-sql-language.md)
