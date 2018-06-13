---
title: 'Nasıl yapılır: okuma yazma özellikleri (C# programlama Kılavuzu) bildirme ve kullanma'
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: d6a7083e1c0cf0dc5c076a69dee15fc39e234d53
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172336"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a><span data-ttu-id="2f81e-102">Nasıl yapılır: okuma yazma özellikleri (C# programlama Kılavuzu) bildirme ve kullanma</span><span class="sxs-lookup"><span data-stu-id="2f81e-102">How to: Declare and Use Read Write Properties (C# Programming Guide)</span></span>
<span data-ttu-id="2f81e-103">Özellikler, ortak veri üyeleri nesnenin verileri korumasız, denetlenmeyen ve doğrulanmamış erişimle gelen riskleri olmadan kolaylık sağlar.</span><span class="sxs-lookup"><span data-stu-id="2f81e-103">Properties provide the convenience of public data members without the risks that come with unprotected, uncontrolled, and unverified access to an object's data.</span></span> <span data-ttu-id="2f81e-104">Bu aracılığıyla gerçekleştirilir *erişimciler*: atayın ve temel alınan veri üyeden değerleri almak özel yöntemler.</span><span class="sxs-lookup"><span data-stu-id="2f81e-104">This is accomplished through *accessors*: special methods that assign and retrieve values from the underlying data member.</span></span> <span data-ttu-id="2f81e-105">[Ayarlamak](../../../csharp/language-reference/keywords/set.md) erişimci atanması, veri üyelerin sağlar ve [almak](../../../csharp/language-reference/keywords/get.md) erişimci veri üyesi değerlerini alır.</span><span class="sxs-lookup"><span data-stu-id="2f81e-105">The [set](../../../csharp/language-reference/keywords/set.md) accessor enables data members to be assigned, and the [get](../../../csharp/language-reference/keywords/get.md) accessor retrieves data member values.</span></span>  
  
 <span data-ttu-id="2f81e-106">Bu örnek gösteren bir `Person` iki özelliğe sahip sınıfı: `Name` (dize) ve `Age` (int).</span><span class="sxs-lookup"><span data-stu-id="2f81e-106">This sample shows a `Person` class that has two properties: `Name` (string) and `Age` (int).</span></span> <span data-ttu-id="2f81e-107">Her iki özellik sağlamak `get` ve `set` kabul edilen şekilde erişimciler okuma/yazma özellikleri.</span><span class="sxs-lookup"><span data-stu-id="2f81e-107">Both properties provide `get` and `set` accessors, so they are considered read/write properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f81e-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="2f81e-108">Example</span></span>  
 [!code-csharp[csProgGuideObjects#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="2f81e-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="2f81e-109">Robust Programming</span></span>  
 <span data-ttu-id="2f81e-110">Önceki örnekte, `Name` ve `Age` özellikleri [ortak](../../../csharp/language-reference/keywords/public.md) ve her ikisi de dahil bir `get` ve `set` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="2f81e-110">In the previous example, the `Name` and `Age` properties are [public](../../../csharp/language-reference/keywords/public.md) and include both a `get` and a `set` accessor.</span></span> <span data-ttu-id="2f81e-111">Bu, bu özellikleri okumasına ve yazmasına herhangi bir nesne sağlar.</span><span class="sxs-lookup"><span data-stu-id="2f81e-111">This allows any object to read and write these properties.</span></span> <span data-ttu-id="2f81e-112">Bu bazen ancak erişimciler birini dışlamak için önerilir.</span><span class="sxs-lookup"><span data-stu-id="2f81e-112">It is sometimes desirable, however, to exclude one of the accessors.</span></span> <span data-ttu-id="2f81e-113">Atlama `set` erişimci salt okunur özelliği gibi yapar:</span><span class="sxs-lookup"><span data-stu-id="2f81e-113">Omitting the `set` accessor, for example, makes the property read-only:</span></span>  
  
 [!code-csharp[csProgGuideObjects#87](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_2.cs)]  
  
 <span data-ttu-id="2f81e-114">Alternatif olarak, bir erişimci genel olarak kullanıma ancak diğer özel veya korumalı hale getirin.</span><span class="sxs-lookup"><span data-stu-id="2f81e-114">Alternatively, you can expose one accessor publicly but make the other private or protected.</span></span> <span data-ttu-id="2f81e-115">Daha fazla bilgi için bkz: [asimetrik erişimci erişilebilirliğini](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="2f81e-115">For more information, see [Asymmetric Accessor Accessibility](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span></span>  
  
 <span data-ttu-id="2f81e-116">Özellikler bildirilen sonra bunlar sınıfın alanları değilmiş gibi kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2f81e-116">Once the properties are declared, they can be used as if they were fields of the class.</span></span> <span data-ttu-id="2f81e-117">Bu hem alma ve aşağıdaki deyimleri olduğu gibi bir özelliğin değerini ayarlama çok doğal bir sözdizimi sağlar:</span><span class="sxs-lookup"><span data-stu-id="2f81e-117">This allows for a very natural syntax when both getting and setting the value of a property, as in the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#35](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_3.cs)]  
  
 <span data-ttu-id="2f81e-118">Bir özelliğin unutmayın `set` özel bir yöntem `value` değişkeni, kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2f81e-118">Note that in a property `set` method a special `value` variable is available.</span></span> <span data-ttu-id="2f81e-119">Bu değişken kullanıcı belirtilen, örneğin değer içeriyor:</span><span class="sxs-lookup"><span data-stu-id="2f81e-119">This variable contains the value that the user specified, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_4.cs)]  
  
 <span data-ttu-id="2f81e-120">Artan temiz söz dizimi fark `Age` özelliği bir `Person` nesnesi:</span><span class="sxs-lookup"><span data-stu-id="2f81e-120">Notice the clean syntax for incrementing the `Age` property on a `Person` object:</span></span>  
  
 [!code-csharp[csProgGuideObjects#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_5.cs)]  
  
 <span data-ttu-id="2f81e-121">Ayrı varsa `set` ve `get` yöntemleri özellikleri model kullanıldı, eşdeğer kod şuna benzeyebilir:</span><span class="sxs-lookup"><span data-stu-id="2f81e-121">If separate `set` and `get` methods were used to model properties, the equivalent code might look like this:</span></span>  
  
```csharp  
person.SetAge(person.GetAge() + 1);   
```  
  
 <span data-ttu-id="2f81e-122">`ToString` Bu örnekte, yöntem geçersiz:</span><span class="sxs-lookup"><span data-stu-id="2f81e-122">The `ToString` method is overridden in this example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_6.cs)]  
  
 <span data-ttu-id="2f81e-123">Dikkat `ToString` açıkça programa kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="2f81e-123">Notice that `ToString` is not explicitly used in the program.</span></span> <span data-ttu-id="2f81e-124">Varsayılan olarak tarafından çağrılan `WriteLine` çağrıları.</span><span class="sxs-lookup"><span data-stu-id="2f81e-124">It is invoked by default by the `WriteLine` calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f81e-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2f81e-125">See Also</span></span>  
 [<span data-ttu-id="2f81e-126">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2f81e-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2f81e-127">Özellikler</span><span class="sxs-lookup"><span data-stu-id="2f81e-127">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [<span data-ttu-id="2f81e-128">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="2f81e-128">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
