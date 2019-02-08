---
title: İŞLEV (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 0bb88992-37ed-4991-ace5-55be612a2c4d
ms.openlocfilehash: b0ace658de0cc6d1ee2d50c9e86d66dea1ac649a
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827545"
---
# <a name="function-entity-sql"></a><span data-ttu-id="8e4e5-102">İŞLEV (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="8e4e5-102">FUNCTION (Entity SQL)</span></span>
<span data-ttu-id="8e4e5-103">Bir işlev bir varlık SQL sorgusu komutu kapsamında tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8e4e5-103">Defines a function in the scope of an Entity SQL query command.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e4e5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8e4e5-104">Syntax</span></span>  
  
```  
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
  
## <a name="arguments"></a><span data-ttu-id="8e4e5-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8e4e5-105">Arguments</span></span>  
 `function-name`  
 <span data-ttu-id="8e4e5-106">İşlevin adı.</span><span class="sxs-lookup"><span data-stu-id="8e4e5-106">Name of the function.</span></span>  
  
 `parameter-name`  
 <span data-ttu-id="8e4e5-107">İşlev bir parametre adı.</span><span class="sxs-lookup"><span data-stu-id="8e4e5-107">Name of a parameter in the function.</span></span>  
  
 `function_expression`  
 <span data-ttu-id="8e4e5-108">İşlev, geçerli bir varlık SQL ifadesi.</span><span class="sxs-lookup"><span data-stu-id="8e4e5-108">A valid Entity SQL expression that is the function.</span></span> <span data-ttu-id="8e4e5-109">Komut içinde işlev üzerinde işlem yapabileceğiniz `parameter_name` işleve geçirilen parametreler.</span><span class="sxs-lookup"><span data-stu-id="8e4e5-109">The command in the function can act on `parameter_name` parameters passed to the function.</span></span>  
  
 `data_type`  
 <span data-ttu-id="8e4e5-110">Desteklenen bir tür adı.</span><span class="sxs-lookup"><span data-stu-id="8e4e5-110">Name of a supported type.</span></span>  
  
 <span data-ttu-id="8e4e5-111">KOLEKSİYON (< type_definition`>` )</span><span class="sxs-lookup"><span data-stu-id="8e4e5-111">COLLECTION ( <type_definition`>` )</span></span>  
 <span data-ttu-id="8e4e5-112">Desteklenen türler, satır veya başvuruları koleksiyonunu döndüren bir ifade.</span><span class="sxs-lookup"><span data-stu-id="8e4e5-112">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
 <span data-ttu-id="8e4e5-113">REF **(**`data_type`**)**</span><span class="sxs-lookup"><span data-stu-id="8e4e5-113">REF **(**`data_type`**)**</span></span>  
 <span data-ttu-id="8e4e5-114">Bir varlık türü referansı döndüren bir ifade.</span><span class="sxs-lookup"><span data-stu-id="8e4e5-114">An expression that returns a reference to an entity type.</span></span>  
  
 <span data-ttu-id="8e4e5-115">SATIR **(**`row_expression`**)**</span><span class="sxs-lookup"><span data-stu-id="8e4e5-115">ROW **(**`row_expression`**)**</span></span>  
 <span data-ttu-id="8e4e5-116">Anonim, döndüren bir ifade, yapısal olarak bir veya daha fazla değer kayıtlardan yazdınız.</span><span class="sxs-lookup"><span data-stu-id="8e4e5-116">An expression that returns anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="8e4e5-117">Daha fazla bilgi için [satır](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="8e4e5-117">For more information, see [ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e4e5-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8e4e5-118">Remarks</span></span>  
 <span data-ttu-id="8e4e5-119">İşlev imzası farklı olduğu sürece, aynı ada sahip birden çok işlev satır içi olarak bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8e4e5-119">Multiple functions with the same name can be declared inline, as long as the function signatures are different.</span></span> <span data-ttu-id="8e4e5-120">Daha fazla bilgi için [işlev aşırı yükleme çözünürlüğü](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="8e4e5-120">For more information, see [Function Overload Resolution](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).</span></span>  
  
 <span data-ttu-id="8e4e5-121">Bu komutta yalnızca tanımlandıktan sonra bir satır içi işlevi bir varlık SQL komutunu çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="8e4e5-121">An inline function can be called in an Entity SQL command only after it has been defined in that command.</span></span> <span data-ttu-id="8e4e5-122">Ancak, satır içi işlev önce ya da çağrılan işlevi tanımlandıktan sonra başka bir satır içi işlev içinde çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="8e4e5-122">However, an inline function can be called inside another inline function either before or after the called function has been defined.</span></span> <span data-ttu-id="8e4e5-123">B işlevi tanımlanmadan önce aşağıdaki örnekte, B işlevi bir çağrıları işlev:</span><span class="sxs-lookup"><span data-stu-id="8e4e5-123">In the following example, function A calls function B before function B is defined:</span></span>  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 <span data-ttu-id="8e4e5-124">Daha fazla bilgi için [nasıl yapılır: Bir kullanıcı tanımlı işlevi çağırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8e4e5-124">For more information, see [How to: Call a User-Defined Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100)).</span></span>  
  
 <span data-ttu-id="8e4e5-125">İşlevler Ayrıca model içinde bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8e4e5-125">Functions can also be declared in the model itself.</span></span> <span data-ttu-id="8e4e5-126">Model içinde bildirilen işlevlerle aynı şekilde komutta bildirilen satır içi işlevleri gibi yürütülür.</span><span class="sxs-lookup"><span data-stu-id="8e4e5-126">Functions declared in the model are executed in the same way as functions declared inline in the command.</span></span> <span data-ttu-id="8e4e5-127">Daha fazla bilgi için [kullanıcı tanımlı işlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="8e4e5-127">For more information, see [User-Defined Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e4e5-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e4e5-128">Example</span></span>  
 <span data-ttu-id="8e4e5-129">Aşağıdaki varlık SQL komutunu bir işlevi tanımlayan `Products` döndürülen ürünleri filtrelemek için bir tamsayı değeri alır.</span><span class="sxs-lookup"><span data-stu-id="8e4e5-129">The following Entity SQL command defines a function `Products` that takes an integer value to filter the returned products.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function1)]  
  
## <a name="example"></a><span data-ttu-id="8e4e5-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e4e5-130">Example</span></span>  
 <span data-ttu-id="8e4e5-131">Aşağıdaki varlık SQL komutunu bir işlevi tanımlayan `StringReturnsCollection` döndürülen kişiler filtrelemek için dizeleri koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="8e4e5-131">The following Entity SQL command defines a function `StringReturnsCollection` that takes a collection of strings to filter the returned contacts.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function2)]  
  
## <a name="see-also"></a><span data-ttu-id="8e4e5-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e4e5-132">See also</span></span>
- [<span data-ttu-id="8e4e5-133">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="8e4e5-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="8e4e5-134">Entity SQL Dili</span><span class="sxs-lookup"><span data-stu-id="8e4e5-134">Entity SQL Language</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
