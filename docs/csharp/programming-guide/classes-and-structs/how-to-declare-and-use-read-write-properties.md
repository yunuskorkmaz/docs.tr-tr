---
title: 'Nasıl yapılır: Okuma yazma özellikleri - bildirme ve kullanma C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: b4dc9364e64f7ebfd495671b852b98d8f56c80b5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646468"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a><span data-ttu-id="324bc-102">Nasıl yapılır: Okuma yazma özellikleri bildirme ve kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="324bc-102">How to: Declare and Use Read Write Properties (C# Programming Guide)</span></span>
<span data-ttu-id="324bc-103">Özellikler, ortak veri üyeleri olmadan bir nesnenin verilere korumasız, denetlenmeyen ve doğrulanmamış erişimle gelen riskleri kolaylık sağlar.</span><span class="sxs-lookup"><span data-stu-id="324bc-103">Properties provide the convenience of public data members without the risks that come with unprotected, uncontrolled, and unverified access to an object's data.</span></span> <span data-ttu-id="324bc-104">Bu aracılığıyla gerçekleştirilir *erişimcileri*: atayın ve temel alınan veri üyesinden değerleri almak özel yöntemler.</span><span class="sxs-lookup"><span data-stu-id="324bc-104">This is accomplished through *accessors*: special methods that assign and retrieve values from the underlying data member.</span></span> <span data-ttu-id="324bc-105">[Ayarlamak](../../../csharp/language-reference/keywords/set.md) erişimci veri üyeleri atanmasına olanak sağlar ve [alma](../../../csharp/language-reference/keywords/get.md) erişimci veri üyesi değerler alır.</span><span class="sxs-lookup"><span data-stu-id="324bc-105">The [set](../../../csharp/language-reference/keywords/set.md) accessor enables data members to be assigned, and the [get](../../../csharp/language-reference/keywords/get.md) accessor retrieves data member values.</span></span>  
  
 <span data-ttu-id="324bc-106">Bu örnek, gösterir bir `Person` sınıfı iki özelliğe sahiptir: `Name` (dize) ve `Age` (int).</span><span class="sxs-lookup"><span data-stu-id="324bc-106">This sample shows a `Person` class that has two properties: `Name` (string) and `Age` (int).</span></span> <span data-ttu-id="324bc-107">Her iki özellik sağlayan `get` ve `set` kabul edilir şekilde erişimcileri okuma/yazma özellikleri.</span><span class="sxs-lookup"><span data-stu-id="324bc-107">Both properties provide `get` and `set` accessors, so they are considered read/write properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="324bc-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="324bc-108">Example</span></span>  
 [!code-csharp[csProgGuideObjects#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#33)]  
  
## <a name="robust-programming"></a><span data-ttu-id="324bc-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="324bc-109">Robust Programming</span></span>  
 <span data-ttu-id="324bc-110">Önceki örnekte, `Name` ve `Age` özellikleri [genel](../../../csharp/language-reference/keywords/public.md) ve her ikisi de dahil bir `get` ve `set` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="324bc-110">In the previous example, the `Name` and `Age` properties are [public](../../../csharp/language-reference/keywords/public.md) and include both a `get` and a `set` accessor.</span></span> <span data-ttu-id="324bc-111">Bu, herhangi bir nesne okuma ve yazma bu özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="324bc-111">This allows any object to read and write these properties.</span></span> <span data-ttu-id="324bc-112">Bu bazen ancak erişimcileri biri hariç tutmak için önerilir.</span><span class="sxs-lookup"><span data-stu-id="324bc-112">It is sometimes desirable, however, to exclude one of the accessors.</span></span> <span data-ttu-id="324bc-113">Atlama `set` erişimci salt okunur özelliği gibi yapar:</span><span class="sxs-lookup"><span data-stu-id="324bc-113">Omitting the `set` accessor, for example, makes the property read-only:</span></span>  
  
 [!code-csharp[csProgGuideObjects#87](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#87)]  
  
 <span data-ttu-id="324bc-114">Alternatif olarak, bir erişimci genel olarak kullanıma sunar ancak diğer özel veya korumalı hale getirin.</span><span class="sxs-lookup"><span data-stu-id="324bc-114">Alternatively, you can expose one accessor publicly but make the other private or protected.</span></span> <span data-ttu-id="324bc-115">Daha fazla bilgi için [asimetrik erişimci erişilebilirliği](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="324bc-115">For more information, see [Asymmetric Accessor Accessibility](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span></span>  
  
 <span data-ttu-id="324bc-116">Bildirilen özellikler sonra sınıfın alanları değilmiş gibi bunlar kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="324bc-116">Once the properties are declared, they can be used as if they were fields of the class.</span></span> <span data-ttu-id="324bc-117">Bu hem alma hem de aşağıdaki deyimleri olduğu gibi bir özelliğin değerini ayarlamak çok doğal bir sözdizimi sağlar:</span><span class="sxs-lookup"><span data-stu-id="324bc-117">This allows for a very natural syntax when both getting and setting the value of a property, as in the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#35)]  
  
 <span data-ttu-id="324bc-118">Bir özelliğin unutmayın `set` yöntemi özel bir `value` değişkeni kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="324bc-118">Note that in a property `set` method a special `value` variable is available.</span></span> <span data-ttu-id="324bc-119">Bu değişken, kullanıcının belirttiğiniz, örneğin değeri içerir:</span><span class="sxs-lookup"><span data-stu-id="324bc-119">This variable contains the value that the user specified, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#36)]  
  
 <span data-ttu-id="324bc-120">Artan temiz söz dizimi fark `Age` özelliği bir `Person` nesnesi:</span><span class="sxs-lookup"><span data-stu-id="324bc-120">Notice the clean syntax for incrementing the `Age` property on a `Person` object:</span></span>  
  
 [!code-csharp[csProgGuideObjects#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#37)]  
  
 <span data-ttu-id="324bc-121">Ayrı varsa `set` ve `get` yöntemler, Özellikler modellemek için kullanılmış, eşdeğer kod şu şekilde görünebilir:</span><span class="sxs-lookup"><span data-stu-id="324bc-121">If separate `set` and `get` methods were used to model properties, the equivalent code might look like this:</span></span>  
  
```csharp  
person.SetAge(person.GetAge() + 1);   
```  
  
 <span data-ttu-id="324bc-122">`ToString` Bu örnekte yöntemi geçersiz kılmışsa:</span><span class="sxs-lookup"><span data-stu-id="324bc-122">The `ToString` method is overridden in this example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#38)]  
  
 <span data-ttu-id="324bc-123">Dikkat `ToString` programda açıkça kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="324bc-123">Notice that `ToString` is not explicitly used in the program.</span></span> <span data-ttu-id="324bc-124">Varsayılan olarak tarafından çağrılan `WriteLine` çağırır.</span><span class="sxs-lookup"><span data-stu-id="324bc-124">It is invoked by default by the `WriteLine` calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="324bc-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="324bc-125">See also</span></span>

- [<span data-ttu-id="324bc-126">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="324bc-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="324bc-127">Özellikler</span><span class="sxs-lookup"><span data-stu-id="324bc-127">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [<span data-ttu-id="324bc-128">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="324bc-128">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
