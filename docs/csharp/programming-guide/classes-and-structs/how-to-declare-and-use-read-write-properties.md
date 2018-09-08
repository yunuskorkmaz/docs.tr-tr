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
ms.openlocfilehash: 77db2841d6ef9af21d38736f39e6041699ca13d5
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44180268"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a><span data-ttu-id="287ea-102">Nasıl yapılır: okuma yazma özellikleri (C# programlama Kılavuzu) bildirme ve kullanma</span><span class="sxs-lookup"><span data-stu-id="287ea-102">How to: Declare and Use Read Write Properties (C# Programming Guide)</span></span>
<span data-ttu-id="287ea-103">Özellikler, ortak veri üyeleri olmadan bir nesnenin verilere korumasız, denetlenmeyen ve doğrulanmamış erişimle gelen riskleri kolaylık sağlar.</span><span class="sxs-lookup"><span data-stu-id="287ea-103">Properties provide the convenience of public data members without the risks that come with unprotected, uncontrolled, and unverified access to an object's data.</span></span> <span data-ttu-id="287ea-104">Bu aracılığıyla gerçekleştirilir *erişimcileri*: atayın ve temel alınan veri üyesinden değerleri almak özel yöntemler.</span><span class="sxs-lookup"><span data-stu-id="287ea-104">This is accomplished through *accessors*: special methods that assign and retrieve values from the underlying data member.</span></span> <span data-ttu-id="287ea-105">[Ayarlamak](../../../csharp/language-reference/keywords/set.md) erişimci veri üyeleri atanmasına olanak sağlar ve [alma](../../../csharp/language-reference/keywords/get.md) erişimci veri üyesi değerler alır.</span><span class="sxs-lookup"><span data-stu-id="287ea-105">The [set](../../../csharp/language-reference/keywords/set.md) accessor enables data members to be assigned, and the [get](../../../csharp/language-reference/keywords/get.md) accessor retrieves data member values.</span></span>  
  
 <span data-ttu-id="287ea-106">Bu örnek, gösterir bir `Person` sınıfı iki özelliğe sahiptir: `Name` (dize) ve `Age` (int).</span><span class="sxs-lookup"><span data-stu-id="287ea-106">This sample shows a `Person` class that has two properties: `Name` (string) and `Age` (int).</span></span> <span data-ttu-id="287ea-107">Her iki özellik sağlayan `get` ve `set` kabul edilir şekilde erişimcileri okuma/yazma özellikleri.</span><span class="sxs-lookup"><span data-stu-id="287ea-107">Both properties provide `get` and `set` accessors, so they are considered read/write properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="287ea-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="287ea-108">Example</span></span>  
 [!code-csharp[csProgGuideObjects#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="287ea-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="287ea-109">Robust Programming</span></span>  
 <span data-ttu-id="287ea-110">Önceki örnekte, `Name` ve `Age` özellikleri [genel](../../../csharp/language-reference/keywords/public.md) ve her ikisi de dahil bir `get` ve `set` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="287ea-110">In the previous example, the `Name` and `Age` properties are [public](../../../csharp/language-reference/keywords/public.md) and include both a `get` and a `set` accessor.</span></span> <span data-ttu-id="287ea-111">Bu, herhangi bir nesne okuma ve yazma bu özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="287ea-111">This allows any object to read and write these properties.</span></span> <span data-ttu-id="287ea-112">Bu bazen ancak erişimcileri biri hariç tutmak için önerilir.</span><span class="sxs-lookup"><span data-stu-id="287ea-112">It is sometimes desirable, however, to exclude one of the accessors.</span></span> <span data-ttu-id="287ea-113">Atlama `set` erişimci salt okunur özelliği gibi yapar:</span><span class="sxs-lookup"><span data-stu-id="287ea-113">Omitting the `set` accessor, for example, makes the property read-only:</span></span>  
  
 [!code-csharp[csProgGuideObjects#87](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_2.cs)]  
  
 <span data-ttu-id="287ea-114">Alternatif olarak, bir erişimci genel olarak kullanıma sunar ancak diğer özel veya korumalı hale getirin.</span><span class="sxs-lookup"><span data-stu-id="287ea-114">Alternatively, you can expose one accessor publicly but make the other private or protected.</span></span> <span data-ttu-id="287ea-115">Daha fazla bilgi için [asimetrik erişimci erişilebilirliği](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="287ea-115">For more information, see [Asymmetric Accessor Accessibility](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span></span>  
  
 <span data-ttu-id="287ea-116">Bildirilen özellikler sonra sınıfın alanları değilmiş gibi bunlar kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="287ea-116">Once the properties are declared, they can be used as if they were fields of the class.</span></span> <span data-ttu-id="287ea-117">Bu hem alma hem de aşağıdaki deyimleri olduğu gibi bir özelliğin değerini ayarlamak çok doğal bir sözdizimi sağlar:</span><span class="sxs-lookup"><span data-stu-id="287ea-117">This allows for a very natural syntax when both getting and setting the value of a property, as in the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#35](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_3.cs)]  
  
 <span data-ttu-id="287ea-118">Bir özelliğin unutmayın `set` yöntemi özel bir `value` değişkeni kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="287ea-118">Note that in a property `set` method a special `value` variable is available.</span></span> <span data-ttu-id="287ea-119">Bu değişken, kullanıcının belirttiğiniz, örneğin değeri içerir:</span><span class="sxs-lookup"><span data-stu-id="287ea-119">This variable contains the value that the user specified, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_4.cs)]  
  
 <span data-ttu-id="287ea-120">Artan temiz söz dizimi fark `Age` özelliği bir `Person` nesnesi:</span><span class="sxs-lookup"><span data-stu-id="287ea-120">Notice the clean syntax for incrementing the `Age` property on a `Person` object:</span></span>  
  
 [!code-csharp[csProgGuideObjects#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_5.cs)]  
  
 <span data-ttu-id="287ea-121">Ayrı varsa `set` ve `get` yöntemler, Özellikler modellemek için kullanılmış, eşdeğer kod şu şekilde görünebilir:</span><span class="sxs-lookup"><span data-stu-id="287ea-121">If separate `set` and `get` methods were used to model properties, the equivalent code might look like this:</span></span>  
  
```csharp  
person.SetAge(person.GetAge() + 1);   
```  
  
 <span data-ttu-id="287ea-122">`ToString` Bu örnekte yöntemi geçersiz kılmışsa:</span><span class="sxs-lookup"><span data-stu-id="287ea-122">The `ToString` method is overridden in this example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_6.cs)]  
  
 <span data-ttu-id="287ea-123">Dikkat `ToString` programda açıkça kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="287ea-123">Notice that `ToString` is not explicitly used in the program.</span></span> <span data-ttu-id="287ea-124">Varsayılan olarak tarafından çağrılan `WriteLine` çağırır.</span><span class="sxs-lookup"><span data-stu-id="287ea-124">It is invoked by default by the `WriteLine` calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="287ea-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="287ea-125">See Also</span></span>

- [<span data-ttu-id="287ea-126">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="287ea-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="287ea-127">Özellikler</span><span class="sxs-lookup"><span data-stu-id="287ea-127">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
- [<span data-ttu-id="287ea-128">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="287ea-128">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
