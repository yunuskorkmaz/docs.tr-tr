---
title: "Boş değer atanabilir yapılandırılmış türler (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3f294088e92951e964c3daa2a105b767bca1d288
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="nullable-structured-types-entity-sql"></a><span data-ttu-id="3dce9-102">Boş değer atanabilir yapılandırılmış türler (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="3dce9-102">Nullable Structured Types (Entity SQL)</span></span>
<span data-ttu-id="3dce9-103">A `null` yapılandırılmış bir tür örneği olan mevcut bir örneği.</span><span class="sxs-lookup"><span data-stu-id="3dce9-103">A `null` instance of a structured type is an instance that does not exist.</span></span> <span data-ttu-id="3dce9-104">Bu, tüm özellikleri olan mevcut örneğinden farklı değildir `null` değerleri.</span><span class="sxs-lookup"><span data-stu-id="3dce9-104">This is different from an existing instance in which all properties have `null` values.</span></span>  
  
 <span data-ttu-id="3dce9-105">Bu konuda, hangi tür boş değer atanabilir ve ürün hangi kod düzenleri dahil olmak üzere boş değer atanabilir yapılandırılmış türler açıklanmaktadır `null` yapılandırılmış boş değer atanabilir türler örnekleri.</span><span class="sxs-lookup"><span data-stu-id="3dce9-105">This topic describes the nullable structured types, including which types are nullable and which code patterns produce `null` instances of structured nullable types.</span></span>  
  
## <a name="kinds-of-nullable-structured-types"></a><span data-ttu-id="3dce9-106">Boş değer atanabilir yapılandırılmış türleri tür</span><span class="sxs-lookup"><span data-stu-id="3dce9-106">Kinds of Nullable Structured Types</span></span>  
 <span data-ttu-id="3dce9-107">Üç tür boş değer atanabilir yapı türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3dce9-107">There are three kinds of nullable structure types:</span></span>  
  
-   <span data-ttu-id="3dce9-108">Satır türleri.</span><span class="sxs-lookup"><span data-stu-id="3dce9-108">Row types.</span></span>  
  
-   <span data-ttu-id="3dce9-109">Karmaşık türler.</span><span class="sxs-lookup"><span data-stu-id="3dce9-109">Complex types.</span></span>  
  
-   <span data-ttu-id="3dce9-110">Varlık türü.</span><span class="sxs-lookup"><span data-stu-id="3dce9-110">Entity types.</span></span>  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a><span data-ttu-id="3dce9-111">Yapılandırılmış türlerin Null örnekleri oluşturan kod düzenleri</span><span class="sxs-lookup"><span data-stu-id="3dce9-111">Code Patterns that Produce Null Instances of Structured Types</span></span>  
 <span data-ttu-id="3dce9-112">Aşağıdaki senaryolarda üretmek `null` örnekleri:</span><span class="sxs-lookup"><span data-stu-id="3dce9-112">The following scenarios produce `null` instances:</span></span>  
  
-   <span data-ttu-id="3dce9-113">Şekillendirme `null` yapılandırılmış bir tür olarak:</span><span class="sxs-lookup"><span data-stu-id="3dce9-113">Shaping `null` as a structured type:</span></span>  
  
    ```  
    TREAT (NULL AS StructuredType)  
    ```  
  
-   <span data-ttu-id="3dce9-114">Üst türe çevirme türetilmiş bir tür için taban türü:</span><span class="sxs-lookup"><span data-stu-id="3dce9-114">Upcasting of a base type to a derived type:</span></span>  
  
    ```  
    TREAT (BaseType AS DerivedType)  
    ```  
  
-   <span data-ttu-id="3dce9-115">Dış birleşim false koşulunu:</span><span class="sxs-lookup"><span data-stu-id="3dce9-115">Outer join on false condition:</span></span>  
  
    ```  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="3dce9-116">--veya</span><span class="sxs-lookup"><span data-stu-id="3dce9-116">--or</span></span>  
  
    ```  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="3dce9-117">--veya</span><span class="sxs-lookup"><span data-stu-id="3dce9-117">--or</span></span>  
  
    ```  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
-   <span data-ttu-id="3dce9-118">Başvurusunun kaldırılmasının bir `null` başvurusu:</span><span class="sxs-lookup"><span data-stu-id="3dce9-118">Dereferencing a `null` reference:</span></span>  
  
    ```  
    DEREF(NullRef)  
    ```  
  
-   <span data-ttu-id="3dce9-119">ANYELEMENT öğesinden boş koleksiyon alma:</span><span class="sxs-lookup"><span data-stu-id="3dce9-119">Obtaining ANYELEMENT from an empty collection:</span></span>  
  
    ```  
    ANYELEMENT(EmptyCollection)  
    ```  
  
-   <span data-ttu-id="3dce9-120">Denetleme `null` yapılandırılmış türlerin örnekleri:</span><span class="sxs-lookup"><span data-stu-id="3dce9-120">Checking for `null` instances of structured types:</span></span>  
  
    ```csharp  
    ...  
    for (int i = 0; i < reader.FieldCount; i++)  
    {  
        if (reader.IsDBNull(i))  
        {  
            Console.WriteLine("[NULL]");  
        }  
        else  
        {  
            Console.WriteLine(reader.GetValue(i).ToString());  
        }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3dce9-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3dce9-121">See Also</span></span>  
 [<span data-ttu-id="3dce9-122">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3dce9-122">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
