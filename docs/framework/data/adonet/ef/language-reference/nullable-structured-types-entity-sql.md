---
title: Null yapılabilir yapılandırılmış türler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
ms.openlocfilehash: b155c672d8c0bef8b01fb26fb49908f094add25a
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319480"
---
# <a name="nullable-structured-types-entity-sql"></a><span data-ttu-id="c6215-102">Null yapılabilir yapılandırılmış türler (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c6215-102">Nullable Structured Types (Entity SQL)</span></span>
<span data-ttu-id="c6215-103">Yapılandırılmış bir türün `null` örneği var olmayan bir örnek.</span><span class="sxs-lookup"><span data-stu-id="c6215-103">A `null` instance of a structured type is an instance that does not exist.</span></span> <span data-ttu-id="c6215-104">Bu, tüm özelliklerde `null` değerlerine sahip olan mevcut bir örnekten farklıdır.</span><span class="sxs-lookup"><span data-stu-id="c6215-104">This is different from an existing instance in which all properties have `null` values.</span></span>  
  
 <span data-ttu-id="c6215-105">Bu konuda, hangi türlerin null yapılabilir olduğu ve hangi kod desenlerinin yapılandırılmış null yapılabilir türler `null` örnekleri ürettiği dahil null yapılabilir yapılandırılmış türler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c6215-105">This topic describes the nullable structured types, including which types are nullable and which code patterns produce `null` instances of structured nullable types.</span></span>  
  
## <a name="kinds-of-nullable-structured-types"></a><span data-ttu-id="c6215-106">Null yapılabilir yapılandırılmış türler türü</span><span class="sxs-lookup"><span data-stu-id="c6215-106">Kinds of Nullable Structured Types</span></span>  
 <span data-ttu-id="c6215-107">Üç tür atanabilir yapı türü vardır:</span><span class="sxs-lookup"><span data-stu-id="c6215-107">There are three kinds of nullable structure types:</span></span>  
  
- <span data-ttu-id="c6215-108">Satır türleri.</span><span class="sxs-lookup"><span data-stu-id="c6215-108">Row types.</span></span>  
  
- <span data-ttu-id="c6215-109">Karmaşık türler.</span><span class="sxs-lookup"><span data-stu-id="c6215-109">Complex types.</span></span>  
  
- <span data-ttu-id="c6215-110">Varlık türleri.</span><span class="sxs-lookup"><span data-stu-id="c6215-110">Entity types.</span></span>  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a><span data-ttu-id="c6215-111">Yapılandırılmış türlerin null örneklerini üreten kod desenleri</span><span class="sxs-lookup"><span data-stu-id="c6215-111">Code Patterns that Produce Null Instances of Structured Types</span></span>  
 <span data-ttu-id="c6215-112">Aşağıdaki senaryolar `null` örnekleri üretir:</span><span class="sxs-lookup"><span data-stu-id="c6215-112">The following scenarios produce `null` instances:</span></span>  
  
- <span data-ttu-id="c6215-113">@No__t-0 ' y i yapısal bir tür olarak şekillendirme:</span><span class="sxs-lookup"><span data-stu-id="c6215-113">Shaping `null` as a structured type:</span></span>  
  
    ```sql  
    TREAT (NULL AS StructuredType)  
    ```  
  
- <span data-ttu-id="c6215-114">Bir temel türün türetilmiş bir tür için yukarı ataması:</span><span class="sxs-lookup"><span data-stu-id="c6215-114">Upcasting of a base type to a derived type:</span></span>  
  
    ```sql  
    TREAT (BaseType AS DerivedType)  
    ```  
  
- <span data-ttu-id="c6215-115">Yanlış koşula dış birleşim:</span><span class="sxs-lookup"><span data-stu-id="c6215-115">Outer join on false condition:</span></span>  
  
    ```sql  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="c6215-116">--veya</span><span class="sxs-lookup"><span data-stu-id="c6215-116">--or</span></span>  
  
    ```sql  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="c6215-117">--veya</span><span class="sxs-lookup"><span data-stu-id="c6215-117">--or</span></span>  
  
    ```sql  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
- <span data-ttu-id="c6215-118">@No__t-0 başvurusunun başvurusu:</span><span class="sxs-lookup"><span data-stu-id="c6215-118">Dereferencing a `null` reference:</span></span>  
  
    ```sql  
    DEREF(NullRef)  
    ```  
  
- <span data-ttu-id="c6215-119">Boş bir koleksiyondan ANYELEMENT alma:</span><span class="sxs-lookup"><span data-stu-id="c6215-119">Obtaining ANYELEMENT from an empty collection:</span></span>  
  
    ```sql  
    ANYELEMENT(EmptyCollection)  
    ```  
  
- <span data-ttu-id="c6215-120">Yapılandırılmış türlerin `null` örnekleri denetleniyor:</span><span class="sxs-lookup"><span data-stu-id="c6215-120">Checking for `null` instances of structured types:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c6215-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6215-121">See also</span></span>

- [<span data-ttu-id="c6215-122">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c6215-122">Entity SQL Overview</span></span>](entity-sql-overview.md)
