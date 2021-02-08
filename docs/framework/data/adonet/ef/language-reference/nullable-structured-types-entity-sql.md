---
description: 'Şu konuda daha fazla bilgi edinin: null atanabilir yapılandırılmış türler (Entity SQL)'
title: Null yapılabilir yapılandırılmış türler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
ms.openlocfilehash: bf303c9cd61fad2c2a8ffedf338bb3a8876db27b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802092"
---
# <a name="nullable-structured-types-entity-sql"></a><span data-ttu-id="0fdc7-103">Null yapılabilir yapılandırılmış türler (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0fdc7-103">Nullable Structured Types (Entity SQL)</span></span>

<span data-ttu-id="0fdc7-104">`null`Yapılandırılmış bir türün örneği mevcut olmayan bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="0fdc7-104">A `null` instance of a structured type is an instance that does not exist.</span></span> <span data-ttu-id="0fdc7-105">Bu, tüm özelliklerde değer bulunan mevcut bir örnekten farklıdır `null` .</span><span class="sxs-lookup"><span data-stu-id="0fdc7-105">This is different from an existing instance in which all properties have `null` values.</span></span>  
  
 <span data-ttu-id="0fdc7-106">Bu konuda, hangi türlerin null yapılabilir olduğu ve hangi kod desenlerinin `null` yapılandırılmış null yapılabilir türleri örnekleri oluşturulduğu dahil null yapılabilir yapılandırılmış türler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0fdc7-106">This topic describes the nullable structured types, including which types are nullable and which code patterns produce `null` instances of structured nullable types.</span></span>  
  
## <a name="kinds-of-nullable-structured-types"></a><span data-ttu-id="0fdc7-107">Null yapılabilir yapılandırılmış türler türü</span><span class="sxs-lookup"><span data-stu-id="0fdc7-107">Kinds of Nullable Structured Types</span></span>  

 <span data-ttu-id="0fdc7-108">Üç tür atanabilir yapı türü vardır:</span><span class="sxs-lookup"><span data-stu-id="0fdc7-108">There are three kinds of nullable structure types:</span></span>  
  
- <span data-ttu-id="0fdc7-109">Satır türleri.</span><span class="sxs-lookup"><span data-stu-id="0fdc7-109">Row types.</span></span>  
  
- <span data-ttu-id="0fdc7-110">Karmaşık türler.</span><span class="sxs-lookup"><span data-stu-id="0fdc7-110">Complex types.</span></span>  
  
- <span data-ttu-id="0fdc7-111">Varlık türleri.</span><span class="sxs-lookup"><span data-stu-id="0fdc7-111">Entity types.</span></span>  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a><span data-ttu-id="0fdc7-112">Yapılandırılmış türlerin null örneklerini üreten kod desenleri</span><span class="sxs-lookup"><span data-stu-id="0fdc7-112">Code Patterns that Produce Null Instances of Structured Types</span></span>  

 <span data-ttu-id="0fdc7-113">Aşağıdaki senaryolar örnekleri üretir `null` :</span><span class="sxs-lookup"><span data-stu-id="0fdc7-113">The following scenarios produce `null` instances:</span></span>  
  
- <span data-ttu-id="0fdc7-114">`null`Yapılandırılmış bir tür olarak şekillendirme:</span><span class="sxs-lookup"><span data-stu-id="0fdc7-114">Shaping `null` as a structured type:</span></span>  
  
    ```sql  
    TREAT (NULL AS StructuredType)  
    ```  
  
- <span data-ttu-id="0fdc7-115">Bir temel türün türetilmiş bir tür için yukarı ataması:</span><span class="sxs-lookup"><span data-stu-id="0fdc7-115">Upcasting of a base type to a derived type:</span></span>  
  
    ```sql  
    TREAT (BaseType AS DerivedType)  
    ```  
  
- <span data-ttu-id="0fdc7-116">Yanlış koşula dış birleşim:</span><span class="sxs-lookup"><span data-stu-id="0fdc7-116">Outer join on false condition:</span></span>  
  
    ```sql  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="0fdc7-117">--veya</span><span class="sxs-lookup"><span data-stu-id="0fdc7-117">--or</span></span>  
  
    ```sql  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="0fdc7-118">--veya</span><span class="sxs-lookup"><span data-stu-id="0fdc7-118">--or</span></span>  
  
    ```sql  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
- <span data-ttu-id="0fdc7-119">Başvurunun başvurusunu kaldırma `null` :</span><span class="sxs-lookup"><span data-stu-id="0fdc7-119">Dereferencing a `null` reference:</span></span>  
  
    ```sql  
    DEREF(NullRef)  
    ```  
  
- <span data-ttu-id="0fdc7-120">Boş bir koleksiyondan ANYELEMENT alma:</span><span class="sxs-lookup"><span data-stu-id="0fdc7-120">Obtaining ANYELEMENT from an empty collection:</span></span>  
  
    ```sql  
    ANYELEMENT(EmptyCollection)  
    ```  
  
- <span data-ttu-id="0fdc7-121">`null`Yapılandırılmış türlerin örnekleri denetleniyor:</span><span class="sxs-lookup"><span data-stu-id="0fdc7-121">Checking for `null` instances of structured types:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0fdc7-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0fdc7-122">See also</span></span>

- [<span data-ttu-id="0fdc7-123">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0fdc7-123">Entity SQL Overview</span></span>](entity-sql-overview.md)
