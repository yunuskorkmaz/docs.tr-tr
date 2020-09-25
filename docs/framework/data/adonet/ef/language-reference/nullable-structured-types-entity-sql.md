---
title: Null yapılabilir yapılandırılmış türler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
ms.openlocfilehash: fc2230401ef98c005ab52a845de37482c0dcf698
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202271"
---
# <a name="nullable-structured-types-entity-sql"></a><span data-ttu-id="f2e8a-102">Null yapılabilir yapılandırılmış türler (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f2e8a-102">Nullable Structured Types (Entity SQL)</span></span>

<span data-ttu-id="f2e8a-103">`null`Yapılandırılmış bir türün örneği mevcut olmayan bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="f2e8a-103">A `null` instance of a structured type is an instance that does not exist.</span></span> <span data-ttu-id="f2e8a-104">Bu, tüm özelliklerde değer bulunan mevcut bir örnekten farklıdır `null` .</span><span class="sxs-lookup"><span data-stu-id="f2e8a-104">This is different from an existing instance in which all properties have `null` values.</span></span>  
  
 <span data-ttu-id="f2e8a-105">Bu konuda, hangi türlerin null yapılabilir olduğu ve hangi kod desenlerinin `null` yapılandırılmış null yapılabilir türleri örnekleri oluşturulduğu dahil null yapılabilir yapılandırılmış türler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f2e8a-105">This topic describes the nullable structured types, including which types are nullable and which code patterns produce `null` instances of structured nullable types.</span></span>  
  
## <a name="kinds-of-nullable-structured-types"></a><span data-ttu-id="f2e8a-106">Null yapılabilir yapılandırılmış türler türü</span><span class="sxs-lookup"><span data-stu-id="f2e8a-106">Kinds of Nullable Structured Types</span></span>  

 <span data-ttu-id="f2e8a-107">Üç tür atanabilir yapı türü vardır:</span><span class="sxs-lookup"><span data-stu-id="f2e8a-107">There are three kinds of nullable structure types:</span></span>  
  
- <span data-ttu-id="f2e8a-108">Satır türleri.</span><span class="sxs-lookup"><span data-stu-id="f2e8a-108">Row types.</span></span>  
  
- <span data-ttu-id="f2e8a-109">Karmaşık türler.</span><span class="sxs-lookup"><span data-stu-id="f2e8a-109">Complex types.</span></span>  
  
- <span data-ttu-id="f2e8a-110">Varlık türleri.</span><span class="sxs-lookup"><span data-stu-id="f2e8a-110">Entity types.</span></span>  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a><span data-ttu-id="f2e8a-111">Yapılandırılmış türlerin null örneklerini üreten kod desenleri</span><span class="sxs-lookup"><span data-stu-id="f2e8a-111">Code Patterns that Produce Null Instances of Structured Types</span></span>  

 <span data-ttu-id="f2e8a-112">Aşağıdaki senaryolar örnekleri üretir `null` :</span><span class="sxs-lookup"><span data-stu-id="f2e8a-112">The following scenarios produce `null` instances:</span></span>  
  
- <span data-ttu-id="f2e8a-113">`null`Yapılandırılmış bir tür olarak şekillendirme:</span><span class="sxs-lookup"><span data-stu-id="f2e8a-113">Shaping `null` as a structured type:</span></span>  
  
    ```sql  
    TREAT (NULL AS StructuredType)  
    ```  
  
- <span data-ttu-id="f2e8a-114">Bir temel türün türetilmiş bir tür için yukarı ataması:</span><span class="sxs-lookup"><span data-stu-id="f2e8a-114">Upcasting of a base type to a derived type:</span></span>  
  
    ```sql  
    TREAT (BaseType AS DerivedType)  
    ```  
  
- <span data-ttu-id="f2e8a-115">Yanlış koşula dış birleşim:</span><span class="sxs-lookup"><span data-stu-id="f2e8a-115">Outer join on false condition:</span></span>  
  
    ```sql  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="f2e8a-116">--veya</span><span class="sxs-lookup"><span data-stu-id="f2e8a-116">--or</span></span>  
  
    ```sql  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="f2e8a-117">--veya</span><span class="sxs-lookup"><span data-stu-id="f2e8a-117">--or</span></span>  
  
    ```sql  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
- <span data-ttu-id="f2e8a-118">Başvurunun başvurusunu kaldırma `null` :</span><span class="sxs-lookup"><span data-stu-id="f2e8a-118">Dereferencing a `null` reference:</span></span>  
  
    ```sql  
    DEREF(NullRef)  
    ```  
  
- <span data-ttu-id="f2e8a-119">Boş bir koleksiyondan ANYELEMENT alma:</span><span class="sxs-lookup"><span data-stu-id="f2e8a-119">Obtaining ANYELEMENT from an empty collection:</span></span>  
  
    ```sql  
    ANYELEMENT(EmptyCollection)  
    ```  
  
- <span data-ttu-id="f2e8a-120">`null`Yapılandırılmış türlerin örnekleri denetleniyor:</span><span class="sxs-lookup"><span data-stu-id="f2e8a-120">Checking for `null` instances of structured types:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f2e8a-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2e8a-121">See also</span></span>

- [<span data-ttu-id="f2e8a-122">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f2e8a-122">Entity SQL Overview</span></span>](entity-sql-overview.md)
