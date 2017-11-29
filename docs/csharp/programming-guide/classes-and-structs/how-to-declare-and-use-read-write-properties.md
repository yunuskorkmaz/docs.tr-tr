---
title: "Nasıl yapılır: okuma yazma özellikleri (C# programlama Kılavuzu) bildirme ve kullanma"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c17bdd05196f834b491c69f648bec0b7cb6e3cd9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a><span data-ttu-id="f665b-102">Nasıl yapılır: okuma yazma özellikleri (C# programlama Kılavuzu) bildirme ve kullanma</span><span class="sxs-lookup"><span data-stu-id="f665b-102">How to: Declare and Use Read Write Properties (C# Programming Guide)</span></span>
<span data-ttu-id="f665b-103">Özellikler, ortak veri üyeleri nesnenin verileri korumasız, denetlenmeyen ve doğrulanmamış erişimle gelen riskleri olmadan kolaylık sağlar.</span><span class="sxs-lookup"><span data-stu-id="f665b-103">Properties provide the convenience of public data members without the risks that come with unprotected, uncontrolled, and unverified access to an object's data.</span></span> <span data-ttu-id="f665b-104">Bu aracılığıyla gerçekleştirilir *erişimciler*: atayın ve temel alınan veri üyeden değerleri almak özel yöntemler.</span><span class="sxs-lookup"><span data-stu-id="f665b-104">This is accomplished through *accessors*: special methods that assign and retrieve values from the underlying data member.</span></span> <span data-ttu-id="f665b-105">[Ayarlamak](../../../csharp/language-reference/keywords/set.md) erişimci atanması, veri üyelerin sağlar ve [almak](../../../csharp/language-reference/keywords/get.md) erişimci veri üyesi değerlerini alır.</span><span class="sxs-lookup"><span data-stu-id="f665b-105">The [set](../../../csharp/language-reference/keywords/set.md) accessor enables data members to be assigned, and the [get](../../../csharp/language-reference/keywords/get.md) accessor retrieves data member values.</span></span>  
  
 <span data-ttu-id="f665b-106">Bu örnek gösteren bir `Person` iki özelliğe sahip sınıfı: `Name` (dize) ve `Age` (int).</span><span class="sxs-lookup"><span data-stu-id="f665b-106">This sample shows a `Person` class that has two properties: `Name` (string) and `Age` (int).</span></span> <span data-ttu-id="f665b-107">Her iki özellik sağlamak `get` ve `set` kabul edilen şekilde erişimciler okuma/yazma özellikleri.</span><span class="sxs-lookup"><span data-stu-id="f665b-107">Both properties provide `get` and `set` accessors, so they are considered read/write properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f665b-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="f665b-108">Example</span></span>  
 [!code-csharp[csProgGuideObjects#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="f665b-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="f665b-109">Robust Programming</span></span>  
 <span data-ttu-id="f665b-110">Önceki örnekte, `Name` ve `Age` özellikleri [ortak](../../../csharp/language-reference/keywords/public.md) ve her ikisi de dahil bir `get` ve `set` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="f665b-110">In the previous example, the `Name` and `Age` properties are [public](../../../csharp/language-reference/keywords/public.md) and include both a `get` and a `set` accessor.</span></span> <span data-ttu-id="f665b-111">Bu, bu özellikleri okumasına ve yazmasına herhangi bir nesne sağlar.</span><span class="sxs-lookup"><span data-stu-id="f665b-111">This allows any object to read and write these properties.</span></span> <span data-ttu-id="f665b-112">Bu bazen ancak erişimciler birini dışlamak için önerilir.</span><span class="sxs-lookup"><span data-stu-id="f665b-112">It is sometimes desirable, however, to exclude one of the accessors.</span></span> <span data-ttu-id="f665b-113">Atlama `set` erişimci salt okunur özelliği gibi yapar:</span><span class="sxs-lookup"><span data-stu-id="f665b-113">Omitting the `set` accessor, for example, makes the property read-only:</span></span>  
  
 [!code-csharp[csProgGuideObjects#87](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_2.cs)]  
  
 <span data-ttu-id="f665b-114">Alternatif olarak, bir erişimci genel olarak kullanıma ancak diğer özel veya korumalı hale getirin.</span><span class="sxs-lookup"><span data-stu-id="f665b-114">Alternatively, you can expose one accessor publicly but make the other private or protected.</span></span> <span data-ttu-id="f665b-115">Daha fazla bilgi için bkz: [asimetrik erişimci erişilebilirliğini](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="f665b-115">For more information, see [Asymmetric Accessor Accessibility](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span></span>  
  
 <span data-ttu-id="f665b-116">Özellikler bildirilen sonra bunlar sınıfın alanları değilmiş gibi kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f665b-116">Once the properties are declared, they can be used as if they were fields of the class.</span></span> <span data-ttu-id="f665b-117">Bu hem alma ve aşağıdaki deyimleri olduğu gibi bir özelliğin değerini ayarlama çok doğal bir sözdizimi sağlar:</span><span class="sxs-lookup"><span data-stu-id="f665b-117">This allows for a very natural syntax when both getting and setting the value of a property, as in the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#35](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_3.cs)]  
  
 <span data-ttu-id="f665b-118">Bir özelliğin unutmayın `set` özel bir yöntem `value` değişkeni, kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f665b-118">Note that in a property `set` method a special `value` variable is available.</span></span> <span data-ttu-id="f665b-119">Bu değişken kullanıcı belirtilen, örneğin değer içeriyor:</span><span class="sxs-lookup"><span data-stu-id="f665b-119">This variable contains the value that the user specified, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_4.cs)]  
  
 <span data-ttu-id="f665b-120">Artan temiz söz dizimi fark `Age` özelliği bir `Person` nesnesi:</span><span class="sxs-lookup"><span data-stu-id="f665b-120">Notice the clean syntax for incrementing the `Age` property on a `Person` object:</span></span>  
  
 [!code-csharp[csProgGuideObjects#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_5.cs)]  
  
 <span data-ttu-id="f665b-121">Ayrı varsa `set` ve `get` yöntemleri özellikleri model kullanıldı, eşdeğer kod şuna benzeyebilir:</span><span class="sxs-lookup"><span data-stu-id="f665b-121">If separate `set` and `get` methods were used to model properties, the equivalent code might look like this:</span></span>  
  
```  
person.SetAge(person.GetAge() + 1);   
```  
  
 <span data-ttu-id="f665b-122">`ToString` Bu örnekte, yöntem geçersiz:</span><span class="sxs-lookup"><span data-stu-id="f665b-122">The `ToString` method is overridden in this example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_6.cs)]  
  
 <span data-ttu-id="f665b-123">Dikkat `ToString` açıkça programa kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="f665b-123">Notice that `ToString` is not explicitly used in the program.</span></span> <span data-ttu-id="f665b-124">Varsayılan olarak tarafından çağrılan `WriteLine` çağrıları.</span><span class="sxs-lookup"><span data-stu-id="f665b-124">It is invoked by default by the `WriteLine` calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f665b-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f665b-125">See Also</span></span>  
 [<span data-ttu-id="f665b-126">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f665b-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f665b-127">Özellikleri</span><span class="sxs-lookup"><span data-stu-id="f665b-127">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [<span data-ttu-id="f665b-128">Sınıflar ve yapılar</span><span class="sxs-lookup"><span data-stu-id="f665b-128">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
