---
title: İŞLEV (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 0bb88992-37ed-4991-ace5-55be612a2c4d
ms.openlocfilehash: 6da7c1c11cb6211764fac5ca7b210788784a7c21
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54697367"
---
# <a name="function-entity-sql"></a><span data-ttu-id="3a826-102">İŞLEV (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="3a826-102">FUNCTION (Entity SQL)</span></span>
<span data-ttu-id="3a826-103">Bir işlev bir varlık SQL sorgusu komutu kapsamında tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3a826-103">Defines a function in the scope of an Entity SQL query command.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a826-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3a826-104">Syntax</span></span>  
  
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
  
## <a name="arguments"></a><span data-ttu-id="3a826-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3a826-105">Arguments</span></span>  
 `function-name`  
 <span data-ttu-id="3a826-106">İşlevin adı.</span><span class="sxs-lookup"><span data-stu-id="3a826-106">Name of the function.</span></span>  
  
 `parameter-name`  
 <span data-ttu-id="3a826-107">İşlev bir parametre adı.</span><span class="sxs-lookup"><span data-stu-id="3a826-107">Name of a parameter in the function.</span></span>  
  
 `function_expression`  
 <span data-ttu-id="3a826-108">İşlev, geçerli bir varlık SQL ifadesi.</span><span class="sxs-lookup"><span data-stu-id="3a826-108">A valid Entity SQL expression that is the function.</span></span> <span data-ttu-id="3a826-109">Komut içinde işlev üzerinde işlem yapabileceğiniz `parameter_name` işleve geçirilen parametreler.</span><span class="sxs-lookup"><span data-stu-id="3a826-109">The command in the function can act on `parameter_name` parameters passed to the function.</span></span>  
  
 `data_type`  
 <span data-ttu-id="3a826-110">Desteklenen bir tür adı.</span><span class="sxs-lookup"><span data-stu-id="3a826-110">Name of a supported type.</span></span>  
  
 <span data-ttu-id="3a826-111">KOLEKSİYON (< type_definition`>` )</span><span class="sxs-lookup"><span data-stu-id="3a826-111">COLLECTION ( <type_definition`>` )</span></span>  
 <span data-ttu-id="3a826-112">Desteklenen türler, satır veya başvuruları koleksiyonunu döndüren bir ifade.</span><span class="sxs-lookup"><span data-stu-id="3a826-112">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
 <span data-ttu-id="3a826-113">REF **(**`data_type`**)**</span><span class="sxs-lookup"><span data-stu-id="3a826-113">REF **(**`data_type`**)**</span></span>  
 <span data-ttu-id="3a826-114">Bir varlık türü referansı döndüren bir ifade.</span><span class="sxs-lookup"><span data-stu-id="3a826-114">An expression that returns a reference to an entity type.</span></span>  
  
 <span data-ttu-id="3a826-115">SATIR **(**`row_expression`**)**</span><span class="sxs-lookup"><span data-stu-id="3a826-115">ROW **(**`row_expression`**)**</span></span>  
 <span data-ttu-id="3a826-116">Anonim, döndüren bir ifade, yapısal olarak bir veya daha fazla değer kayıtlardan yazdınız.</span><span class="sxs-lookup"><span data-stu-id="3a826-116">An expression that returns anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="3a826-117">Daha fazla bilgi için [satır](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="3a826-117">For more information, see [ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a826-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3a826-118">Remarks</span></span>  
 <span data-ttu-id="3a826-119">İşlev imzası farklı olduğu sürece, aynı ada sahip birden çok işlev satır içi olarak bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="3a826-119">Multiple functions with the same name can be declared inline, as long as the function signatures are different.</span></span> <span data-ttu-id="3a826-120">Daha fazla bilgi için [işlev aşırı yükleme çözünürlüğü](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="3a826-120">For more information, see [Function Overload Resolution](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).</span></span>  
  
 <span data-ttu-id="3a826-121">Bu komutta yalnızca tanımlandıktan sonra bir satır içi işlevi bir varlık SQL komutunu çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="3a826-121">An inline function can be called in an Entity SQL command only after it has been defined in that command.</span></span> <span data-ttu-id="3a826-122">Ancak, satır içi işlev önce ya da çağrılan işlevi tanımlandıktan sonra başka bir satır içi işlev içinde çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="3a826-122">However, an inline function can be called inside another inline function either before or after the called function has been defined.</span></span> <span data-ttu-id="3a826-123">B işlevi tanımlanmadan önce aşağıdaki örnekte, B işlevi bir çağrıları işlev:</span><span class="sxs-lookup"><span data-stu-id="3a826-123">In the following example, function A calls function B before function B is defined:</span></span>  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 <span data-ttu-id="3a826-124">Daha fazla bilgi için [nasıl yapılır: Bir kullanıcı tanımlı işlevi çağırma](https://msdn.microsoft.com/library/ad131b86-8b4e-4747-8605-d4fc64fb9d02).</span><span class="sxs-lookup"><span data-stu-id="3a826-124">For more information, see [How to: Call a User-Defined Function](https://msdn.microsoft.com/library/ad131b86-8b4e-4747-8605-d4fc64fb9d02).</span></span>  
  
 <span data-ttu-id="3a826-125">İşlevler Ayrıca model içinde bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="3a826-125">Functions can also be declared in the model itself.</span></span> <span data-ttu-id="3a826-126">Model içinde bildirilen işlevlerle aynı şekilde komutta bildirilen satır içi işlevleri gibi yürütülür.</span><span class="sxs-lookup"><span data-stu-id="3a826-126">Functions declared in the model are executed in the same way as functions declared inline in the command.</span></span> <span data-ttu-id="3a826-127">Daha fazla bilgi için [kullanıcı tanımlı işlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="3a826-127">For more information, see [User-Defined Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a826-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="3a826-128">Example</span></span>  
 <span data-ttu-id="3a826-129">Aşağıdaki varlık SQL komutunu bir işlevi tanımlayan `Products` döndürülen ürünleri filtrelemek için bir tamsayı değeri alır.</span><span class="sxs-lookup"><span data-stu-id="3a826-129">The following Entity SQL command defines a function `Products` that takes an integer value to filter the returned products.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function1)]  
  
## <a name="example"></a><span data-ttu-id="3a826-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="3a826-130">Example</span></span>  
 <span data-ttu-id="3a826-131">Aşağıdaki varlık SQL komutunu bir işlevi tanımlayan `StringReturnsCollection` döndürülen kişiler filtrelemek için dizeleri koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="3a826-131">The following Entity SQL command defines a function `StringReturnsCollection` that takes a collection of strings to filter the returned contacts.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function2)]  
  
## <a name="see-also"></a><span data-ttu-id="3a826-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a826-132">See also</span></span>
- [<span data-ttu-id="3a826-133">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="3a826-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="3a826-134">Entity SQL Dili</span><span class="sxs-lookup"><span data-stu-id="3a826-134">Entity SQL Language</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
