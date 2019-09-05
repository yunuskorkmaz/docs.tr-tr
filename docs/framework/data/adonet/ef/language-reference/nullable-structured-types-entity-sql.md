---
title: Null yapılabilir yapılandırılmış türler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
ms.openlocfilehash: 6b078ae458aba73e82957f84408b1000b216aef9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249807"
---
# <a name="nullable-structured-types-entity-sql"></a><span data-ttu-id="f2315-102">Null yapılabilir yapılandırılmış türler (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f2315-102">Nullable Structured Types (Entity SQL)</span></span>
<span data-ttu-id="f2315-103">Yapılandırılmış bir türün örneği mevcut olmayan bir örneğidir. `null`</span><span class="sxs-lookup"><span data-stu-id="f2315-103">A `null` instance of a structured type is an instance that does not exist.</span></span> <span data-ttu-id="f2315-104">Bu, tüm özelliklerde `null` değer bulunan mevcut bir örnekten farklıdır.</span><span class="sxs-lookup"><span data-stu-id="f2315-104">This is different from an existing instance in which all properties have `null` values.</span></span>  
  
 <span data-ttu-id="f2315-105">Bu konuda, hangi türlerin null yapılabilir olduğu ve hangi kod desenlerinin `null` yapılandırılmış null yapılabilir türleri örnekleri oluşturulduğu dahil null yapılabilir yapılandırılmış türler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f2315-105">This topic describes the nullable structured types, including which types are nullable and which code patterns produce `null` instances of structured nullable types.</span></span>  
  
## <a name="kinds-of-nullable-structured-types"></a><span data-ttu-id="f2315-106">Null yapılabilir yapılandırılmış türler türü</span><span class="sxs-lookup"><span data-stu-id="f2315-106">Kinds of Nullable Structured Types</span></span>  
 <span data-ttu-id="f2315-107">Üç tür atanabilir yapı türü vardır:</span><span class="sxs-lookup"><span data-stu-id="f2315-107">There are three kinds of nullable structure types:</span></span>  
  
- <span data-ttu-id="f2315-108">Satır türleri.</span><span class="sxs-lookup"><span data-stu-id="f2315-108">Row types.</span></span>  
  
- <span data-ttu-id="f2315-109">Karmaşık türler.</span><span class="sxs-lookup"><span data-stu-id="f2315-109">Complex types.</span></span>  
  
- <span data-ttu-id="f2315-110">Varlık türleri.</span><span class="sxs-lookup"><span data-stu-id="f2315-110">Entity types.</span></span>  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a><span data-ttu-id="f2315-111">Yapılandırılmış türlerin null örneklerini üreten kod desenleri</span><span class="sxs-lookup"><span data-stu-id="f2315-111">Code Patterns that Produce Null Instances of Structured Types</span></span>  
 <span data-ttu-id="f2315-112">Aşağıdaki senaryolar örnekleri üretir `null` :</span><span class="sxs-lookup"><span data-stu-id="f2315-112">The following scenarios produce `null` instances:</span></span>  
  
- <span data-ttu-id="f2315-113">Yapılandırılmış `null` bir tür olarak şekillendirme:</span><span class="sxs-lookup"><span data-stu-id="f2315-113">Shaping `null` as a structured type:</span></span>  
  
    ```  
    TREAT (NULL AS StructuredType)  
    ```  
  
- <span data-ttu-id="f2315-114">Bir temel türün türetilmiş bir tür için yukarı ataması:</span><span class="sxs-lookup"><span data-stu-id="f2315-114">Upcasting of a base type to a derived type:</span></span>  
  
    ```  
    TREAT (BaseType AS DerivedType)  
    ```  
  
- <span data-ttu-id="f2315-115">Yanlış koşula dış birleşim:</span><span class="sxs-lookup"><span data-stu-id="f2315-115">Outer join on false condition:</span></span>  
  
    ```  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="f2315-116">--veya</span><span class="sxs-lookup"><span data-stu-id="f2315-116">--or</span></span>  
  
    ```  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="f2315-117">--veya</span><span class="sxs-lookup"><span data-stu-id="f2315-117">--or</span></span>  
  
    ```  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
- <span data-ttu-id="f2315-118">`null` Başvurunun başvurusunu kaldırma:</span><span class="sxs-lookup"><span data-stu-id="f2315-118">Dereferencing a `null` reference:</span></span>  
  
    ```  
    DEREF(NullRef)  
    ```  
  
- <span data-ttu-id="f2315-119">Boş bir koleksiyondan ANYELEMENT alma:</span><span class="sxs-lookup"><span data-stu-id="f2315-119">Obtaining ANYELEMENT from an empty collection:</span></span>  
  
    ```  
    ANYELEMENT(EmptyCollection)  
    ```  
  
- <span data-ttu-id="f2315-120">Yapılandırılmış türlerin `null` örnekleri denetleniyor:</span><span class="sxs-lookup"><span data-stu-id="f2315-120">Checking for `null` instances of structured types:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f2315-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2315-121">See also</span></span>

- [<span data-ttu-id="f2315-122">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f2315-122">Entity SQL Overview</span></span>](entity-sql-overview.md)
