---
title: Boş değer atanabilir yapılandırılmış türler (varlık SQL)
ms.date: 03/30/2017
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
ms.openlocfilehash: 632b092e1d0d99a2a40cc3cd4b323e234de6232b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760330"
---
# <a name="nullable-structured-types-entity-sql"></a><span data-ttu-id="37890-102">Boş değer atanabilir yapılandırılmış türler (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="37890-102">Nullable Structured Types (Entity SQL)</span></span>
<span data-ttu-id="37890-103">A `null` yapılandırılmış bir tür örneği örneği yok.</span><span class="sxs-lookup"><span data-stu-id="37890-103">A `null` instance of a structured type is an instance that does not exist.</span></span> <span data-ttu-id="37890-104">Bu, tüm özelliklere sahip mevcut bir örneğinden farklı `null` değerleri.</span><span class="sxs-lookup"><span data-stu-id="37890-104">This is different from an existing instance in which all properties have `null` values.</span></span>  
  
 <span data-ttu-id="37890-105">Bu konuda, hangi türlerin boş değer atanabilir ve ürün hangi kod desenleri gibi boş değer atanabilir yapılandırılmış türler açıklanmaktadır `null` boş değer atanabilir yapılandırılmış türler örnekleri.</span><span class="sxs-lookup"><span data-stu-id="37890-105">This topic describes the nullable structured types, including which types are nullable and which code patterns produce `null` instances of structured nullable types.</span></span>  
  
## <a name="kinds-of-nullable-structured-types"></a><span data-ttu-id="37890-106">Tür boş değer atanabilir yapılandırılmış türler</span><span class="sxs-lookup"><span data-stu-id="37890-106">Kinds of Nullable Structured Types</span></span>  
 <span data-ttu-id="37890-107">Boş değer atanabilir yapı türleri üç tür vardır:</span><span class="sxs-lookup"><span data-stu-id="37890-107">There are three kinds of nullable structure types:</span></span>  
  
- <span data-ttu-id="37890-108">Satır türü.</span><span class="sxs-lookup"><span data-stu-id="37890-108">Row types.</span></span>  
  
- <span data-ttu-id="37890-109">Karmaşık türler.</span><span class="sxs-lookup"><span data-stu-id="37890-109">Complex types.</span></span>  
  
- <span data-ttu-id="37890-110">Varlık türleri.</span><span class="sxs-lookup"><span data-stu-id="37890-110">Entity types.</span></span>  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a><span data-ttu-id="37890-111">Null yapılandırılmış türlerin örneklerini oluşturan kod desenleri</span><span class="sxs-lookup"><span data-stu-id="37890-111">Code Patterns that Produce Null Instances of Structured Types</span></span>  
 <span data-ttu-id="37890-112">Aşağıdaki senaryolarda üretmek `null` örnekleri:</span><span class="sxs-lookup"><span data-stu-id="37890-112">The following scenarios produce `null` instances:</span></span>  
  
- <span data-ttu-id="37890-113">Şekillendirme `null` yapılandırılmış bir tür olarak:</span><span class="sxs-lookup"><span data-stu-id="37890-113">Shaping `null` as a structured type:</span></span>  
  
    ```  
    TREAT (NULL AS StructuredType)  
    ```  
  
- <span data-ttu-id="37890-114">Türetilmiş bir tür için bir temel türden yukarı çevrim:</span><span class="sxs-lookup"><span data-stu-id="37890-114">Upcasting of a base type to a derived type:</span></span>  
  
    ```  
    TREAT (BaseType AS DerivedType)  
    ```  
  
- <span data-ttu-id="37890-115">Dış birleşim koşul false üzerinde:</span><span class="sxs-lookup"><span data-stu-id="37890-115">Outer join on false condition:</span></span>  
  
    ```  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="37890-116">--or</span><span class="sxs-lookup"><span data-stu-id="37890-116">--or</span></span>  
  
    ```  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="37890-117">--or</span><span class="sxs-lookup"><span data-stu-id="37890-117">--or</span></span>  
  
    ```  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
- <span data-ttu-id="37890-118">Başvuruluyor bir `null` başvurusu:</span><span class="sxs-lookup"><span data-stu-id="37890-118">Dereferencing a `null` reference:</span></span>  
  
    ```  
    DEREF(NullRef)  
    ```  
  
- <span data-ttu-id="37890-119">ANYELEMENT öğesinden boş koleksiyon alma:</span><span class="sxs-lookup"><span data-stu-id="37890-119">Obtaining ANYELEMENT from an empty collection:</span></span>  
  
    ```  
    ANYELEMENT(EmptyCollection)  
    ```  
  
- <span data-ttu-id="37890-120">Denetleme `null` yapılandırılmış türleri örnekleri:</span><span class="sxs-lookup"><span data-stu-id="37890-120">Checking for `null` instances of structured types:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="37890-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37890-121">See also</span></span>

- [<span data-ttu-id="37890-122">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="37890-122">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
