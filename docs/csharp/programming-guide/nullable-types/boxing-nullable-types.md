---
title: "Boş Değer Atanabilir Türleri Kutulama (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- boxing [C#], nullable types
- unboxing [C#], nullable types
- nullable types [C#], boxing and unboxing
ms.assetid: bdb5b626-abc0-405d-8f64-0f0a0bf883a4
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 29fccba56f6758fdfd407fa1879baa9260b69187
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="boxing-nullable-types-c-programming-guide"></a><span data-ttu-id="ad095-102">Boş Değer Atanabilir Türleri Kutulama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="ad095-102">Boxing Nullable Types (C# Programming Guide)</span></span>
<span data-ttu-id="ad095-103">Null olmayan nesne ise, boş değer atanabilir türlerine göre nesneleri yalnızca Kutulu.</span><span class="sxs-lookup"><span data-stu-id="ad095-103">Objects based on nullable types are only boxed if the object is non-null.</span></span> <span data-ttu-id="ad095-104">Varsa <xref:System.Nullable%601.HasValue%2A> olan `false`, nesne başvurusu atandığı `null` kutulama yerine.</span><span class="sxs-lookup"><span data-stu-id="ad095-104">If <xref:System.Nullable%601.HasValue%2A> is `false`, the object reference is assigned to `null` instead of boxing.</span></span> <span data-ttu-id="ad095-105">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ad095-105">For example:</span></span>  
  
```csharp  
bool? b = null;  
object o = b;  
// Now o is null.  
```  
  
 <span data-ttu-id="ad095-106">Nesne null olmayan--ise, <xref:System.Nullable%601.HasValue%2A> olan `true` --sonra kutulama oluşur, ancak null atanabilir nesne dayanan temel alınan tür Kutulu.</span><span class="sxs-lookup"><span data-stu-id="ad095-106">If the object is non-null -- if <xref:System.Nullable%601.HasValue%2A> is `true` -- then boxing occurs, but only the underlying type that the nullable object is based on is boxed.</span></span> <span data-ttu-id="ad095-107">Bir null olmayan boş değer atanabilir değer türü kutulama kutular değer türü kendisi değil <xref:System.Nullable%601?displayProperty=nameWithType> değer türü sarmalar.</span><span class="sxs-lookup"><span data-stu-id="ad095-107">Boxing a non-null nullable value type boxes the value type itself, not the <xref:System.Nullable%601?displayProperty=nameWithType> that wraps the value type.</span></span> <span data-ttu-id="ad095-108">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ad095-108">For example:</span></span>  
  
```csharp  
bool? b = false;  
int? i = 44;  
object bBoxed = b; // bBoxed contains a boxed bool.  
object iBoxed = i; // iBoxed contains a boxed int.  
```  
  
 <span data-ttu-id="ad095-109">İki Kutulu nesneleri kutulama null türleri tarafından oluşturulanlar için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="ad095-109">The two boxed objects are identical to those created by boxing non-nullable types.</span></span> <span data-ttu-id="ad095-110">Ve yalnızca null Kutulu türleri gibi aşağıdaki örnekte olduğu gibi boş değer atanabilir türler içine sarmalanmamış olabilir:</span><span class="sxs-lookup"><span data-stu-id="ad095-110">And, just like non-nullable boxed types, they can be unboxed into nullable types, as in the following example:</span></span>  
  
```csharp  
bool? b2 = (bool?)bBoxed;  
int? i2 = (int?)iBoxed;  
```  
  
## <a name="remarks"></a><span data-ttu-id="ad095-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ad095-111">Remarks</span></span>  
 <span data-ttu-id="ad095-112">Kutulu zaman boş değer atanabilir türler davranışını iki avantajları sağlar:</span><span class="sxs-lookup"><span data-stu-id="ad095-112">The behavior of nullable types when boxed provides two advantages:</span></span>  
  
1.  <span data-ttu-id="ad095-113">Boş değer atanabilir nesneler ve onların paketlenmiş karşılık gelen null test edilebilir:</span><span class="sxs-lookup"><span data-stu-id="ad095-113">Nullable objects and their boxed counterpart can be tested for null:</span></span>  
  
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
  
2.  <span data-ttu-id="ad095-114">Paketlenmiş boş değer atanabilir türler, temel alınan tür işlevselliğini tam olarak destekler:</span><span class="sxs-lookup"><span data-stu-id="ad095-114">Boxed nullable types fully support the functionality of the underlying type:</span></span>  
  
    ```csharp  
    double? d = 44.4;  
    object iBoxed = d;  
    // Access IConvertible interface implemented by double.  
    IConvertible ic = (IConvertible)iBoxed;  
    int i = ic.ToInt32(null);  
    string str = ic.ToString();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ad095-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ad095-115">See Also</span></span>  
 [<span data-ttu-id="ad095-116">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ad095-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ad095-117">Boş değer atanabilir türler</span><span class="sxs-lookup"><span data-stu-id="ad095-117">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="ad095-118">Nasıl yapılır: boş değer atanabilir bir tür belirleme</span><span class="sxs-lookup"><span data-stu-id="ad095-118">How to: Identify a Nullable Type</span></span>](../../../csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type.md)
