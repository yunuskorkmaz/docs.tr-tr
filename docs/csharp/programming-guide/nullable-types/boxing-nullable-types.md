---
title: Boş Değer Atanabilir Türleri Kutulama (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- boxing [C#], nullable types
- unboxing [C#], nullable types
- nullable types [C#], boxing and unboxing
ms.assetid: bdb5b626-abc0-405d-8f64-0f0a0bf883a4
ms.openlocfilehash: e2c7602bf45f1861d3a32a73824e9fedf0a4d29d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334762"
---
# <a name="boxing-nullable-types-c-programming-guide"></a><span data-ttu-id="e2198-102">Boş Değer Atanabilir Türleri Kutulama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e2198-102">Boxing Nullable Types (C# Programming Guide)</span></span>
<span data-ttu-id="e2198-103">Null olmayan nesne ise, boş değer atanabilir türlerine göre nesneleri yalnızca Kutulu.</span><span class="sxs-lookup"><span data-stu-id="e2198-103">Objects based on nullable types are only boxed if the object is non-null.</span></span> <span data-ttu-id="e2198-104">Varsa <xref:System.Nullable%601.HasValue%2A> olan `false`, nesne başvurusu atandığı `null` kutulama yerine.</span><span class="sxs-lookup"><span data-stu-id="e2198-104">If <xref:System.Nullable%601.HasValue%2A> is `false`, the object reference is assigned to `null` instead of boxing.</span></span> <span data-ttu-id="e2198-105">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="e2198-105">For example:</span></span>  
  
```csharp  
bool? b = null;  
object o = b;  
// Now o is null.  
```  
  
 <span data-ttu-id="e2198-106">Nesne null olmayan--ise, <xref:System.Nullable%601.HasValue%2A> olan `true` --sonra kutulama oluşur, ancak null atanabilir nesne dayanan temel alınan tür Kutulu.</span><span class="sxs-lookup"><span data-stu-id="e2198-106">If the object is non-null -- if <xref:System.Nullable%601.HasValue%2A> is `true` -- then boxing occurs, but only the underlying type that the nullable object is based on is boxed.</span></span> <span data-ttu-id="e2198-107">Bir null olmayan boş değer atanabilir değer türü kutulama kutular değer türü kendisi değil <xref:System.Nullable%601?displayProperty=nameWithType> değer türü sarmalar.</span><span class="sxs-lookup"><span data-stu-id="e2198-107">Boxing a non-null nullable value type boxes the value type itself, not the <xref:System.Nullable%601?displayProperty=nameWithType> that wraps the value type.</span></span> <span data-ttu-id="e2198-108">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="e2198-108">For example:</span></span>  
  
```csharp  
bool? b = false;  
int? i = 44;  
object bBoxed = b; // bBoxed contains a boxed bool.  
object iBoxed = i; // iBoxed contains a boxed int.  
```  
  
 <span data-ttu-id="e2198-109">İki Kutulu nesneleri kutulama null türleri tarafından oluşturulanlar için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="e2198-109">The two boxed objects are identical to those created by boxing non-nullable types.</span></span> <span data-ttu-id="e2198-110">Ve yalnızca null Kutulu türleri gibi aşağıdaki örnekte olduğu gibi boş değer atanabilir türler içine sarmalanmamış olabilir:</span><span class="sxs-lookup"><span data-stu-id="e2198-110">And, just like non-nullable boxed types, they can be unboxed into nullable types, as in the following example:</span></span>  
  
```csharp  
bool? b2 = (bool?)bBoxed;  
int? i2 = (int?)iBoxed;  
```  
  
## <a name="remarks"></a><span data-ttu-id="e2198-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e2198-111">Remarks</span></span>  
 <span data-ttu-id="e2198-112">Kutulu zaman boş değer atanabilir türler davranışını iki avantajları sağlar:</span><span class="sxs-lookup"><span data-stu-id="e2198-112">The behavior of nullable types when boxed provides two advantages:</span></span>  
  
1.  <span data-ttu-id="e2198-113">Boş değer atanabilir nesneler ve onların paketlenmiş karşılık gelen null test edilebilir:</span><span class="sxs-lookup"><span data-stu-id="e2198-113">Nullable objects and their boxed counterpart can be tested for null:</span></span>  
  
    ```csharp  
    bool? b = null;  
    object boxedB = b;  
    if (b == null)  
    {  
      // True.  
    }  
    if (boxedB == null)  
    {  
      // Also true.  
    }  
    ```  
  
2.  <span data-ttu-id="e2198-114">Paketlenmiş boş değer atanabilir türler, temel alınan tür işlevselliğini tam olarak destekler:</span><span class="sxs-lookup"><span data-stu-id="e2198-114">Boxed nullable types fully support the functionality of the underlying type:</span></span>  
  
    ```csharp  
    double? d = 44.4;  
    object iBoxed = d;  
    // Access IConvertible interface implemented by double.  
    IConvertible ic = (IConvertible)iBoxed;  
    int i = ic.ToInt32(null);  
    string str = ic.ToString();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e2198-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e2198-115">See Also</span></span>  
 [<span data-ttu-id="e2198-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e2198-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e2198-117">Boş Değer Atanabilir Tipler</span><span class="sxs-lookup"><span data-stu-id="e2198-117">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="e2198-118">Nasıl yapılır: Boş Değer Atanabilir Tipi Tanımlama</span><span class="sxs-lookup"><span data-stu-id="e2198-118">How to: Identify a Nullable Type</span></span>](../../../csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type.md)
