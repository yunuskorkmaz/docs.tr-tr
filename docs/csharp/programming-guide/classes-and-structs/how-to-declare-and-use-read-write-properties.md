---
title: Okuma yazma özellikleri nasıl beyan edilir ve kullanılır - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: 4b9db5f15746ab9a1f42239150c6783154723371
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170292"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a><span data-ttu-id="494dd-102">Okuma yazma özelliklerini bildirme ve kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="494dd-102">How to declare and use read write properties (C# Programming Guide)</span></span>
<span data-ttu-id="494dd-103">Özellikler, bir nesnenin verilerine korumasız, denetimsiz ve doğrulanmamış erişimle gelen riskler olmadan ortak veri üyelerinin rahatlığını sağlar.</span><span class="sxs-lookup"><span data-stu-id="494dd-103">Properties provide the convenience of public data members without the risks that come with unprotected, uncontrolled, and unverified access to an object's data.</span></span> <span data-ttu-id="494dd-104">Bu, *accessörler*aracılığıyla gerçekleştirilir: temel veri üyesinden değer atayabilen ve alan özel yöntemler.</span><span class="sxs-lookup"><span data-stu-id="494dd-104">This is accomplished through *accessors*: special methods that assign and retrieve values from the underlying data member.</span></span> <span data-ttu-id="494dd-105">[Ayarlanan](../../language-reference/keywords/set.md) erişimci veri üyelerinin atanmasını sağlar ve [erişimci veri](../../language-reference/keywords/get.md) üye değerlerini alır.</span><span class="sxs-lookup"><span data-stu-id="494dd-105">The [set](../../language-reference/keywords/set.md) accessor enables data members to be assigned, and the [get](../../language-reference/keywords/get.md) accessor retrieves data member values.</span></span>  
  
 <span data-ttu-id="494dd-106">Bu örnek, `Person` iki özelliği olan `Name` bir sınıf `Age` gösterir: (dize) ve (int).</span><span class="sxs-lookup"><span data-stu-id="494dd-106">This sample shows a `Person` class that has two properties: `Name` (string) and `Age` (int).</span></span> <span data-ttu-id="494dd-107">Her iki `get` `set` özellik de sağlar ve erişilenler, bu nedenle okuma/yazma özellikleri olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="494dd-107">Both properties provide `get` and `set` accessors, so they are considered read/write properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="494dd-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="494dd-108">Example</span></span>  
 [!code-csharp[csProgGuideObjects#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#33)]  
  
## <a name="robust-programming"></a><span data-ttu-id="494dd-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="494dd-109">Robust Programming</span></span>  
 <span data-ttu-id="494dd-110">Önceki örnekte, `Name` ve `Age` özellikleri [ortak](../../language-reference/keywords/public.md) ve `get` hem `set` bir hem de bir erişimci içerir.</span><span class="sxs-lookup"><span data-stu-id="494dd-110">In the previous example, the `Name` and `Age` properties are [public](../../language-reference/keywords/public.md) and include both a `get` and a `set` accessor.</span></span> <span data-ttu-id="494dd-111">Bu, herhangi bir nesnenin bu özellikleri okumasına ve yazmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="494dd-111">This allows any object to read and write these properties.</span></span> <span data-ttu-id="494dd-112">Ancak bazen erişimcilerden birini dışlamak istenir.</span><span class="sxs-lookup"><span data-stu-id="494dd-112">It is sometimes desirable, however, to exclude one of the accessors.</span></span> <span data-ttu-id="494dd-113">Örneğin, erişimcinin `set` atlanması özelliğin salt okunur hale getirir:</span><span class="sxs-lookup"><span data-stu-id="494dd-113">Omitting the `set` accessor, for example, makes the property read-only:</span></span>  
  
 [!code-csharp[csProgGuideObjects#87](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#87)]  
  
 <span data-ttu-id="494dd-114">Alternatif olarak, bir aksesuarı herkese açık hale getirebilir, ancak diğerini özel veya korumalı hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="494dd-114">Alternatively, you can expose one accessor publicly but make the other private or protected.</span></span> <span data-ttu-id="494dd-115">Daha fazla bilgi için [Asimetrik Erişime Erişime Uygunluk'a](./restricting-accessor-accessibility.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="494dd-115">For more information, see [Asymmetric Accessor Accessibility](./restricting-accessor-accessibility.md).</span></span>  
  
 <span data-ttu-id="494dd-116">Özellikler beyan edildikten sonra, sınıfın alanları gibi kullanılabilirler.</span><span class="sxs-lookup"><span data-stu-id="494dd-116">Once the properties are declared, they can be used as if they were fields of the class.</span></span> <span data-ttu-id="494dd-117">Bu, aşağıdaki ifadelerde olduğu gibi, bir özelliğin değerini alırken ve ayarlarken çok doğal bir sözdizimine izin verir:</span><span class="sxs-lookup"><span data-stu-id="494dd-117">This allows for a very natural syntax when both getting and setting the value of a property, as in the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#35)]  
  
 <span data-ttu-id="494dd-118">Özellik `set` yönteminde özel `value` bir değişken in kullanılabildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="494dd-118">Note that in a property `set` method a special `value` variable is available.</span></span> <span data-ttu-id="494dd-119">Bu değişken, örneğin, kullanıcının belirttiği değeri içerir:</span><span class="sxs-lookup"><span data-stu-id="494dd-119">This variable contains the value that the user specified, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#36)]  
  
 <span data-ttu-id="494dd-120">Özelliği bir `Person` nesne üzerinde artımlı `Age` olarak temiz sözdizimine dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="494dd-120">Notice the clean syntax for incrementing the `Age` property on a `Person` object:</span></span>  
  
 [!code-csharp[csProgGuideObjects#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#37)]  
  
 <span data-ttu-id="494dd-121">Özellikleri `set` modellemek için ayrı ve `get` yöntemler kullanıldıysa, eşdeğer kod aşağıdaki gibi görünebilir:</span><span class="sxs-lookup"><span data-stu-id="494dd-121">If separate `set` and `get` methods were used to model properties, the equivalent code might look like this:</span></span>  
  
```csharp  
person.SetAge(person.GetAge() + 1);
```  
  
 <span data-ttu-id="494dd-122">Yöntem `ToString` bu örnekte geçersiz kılınmış:</span><span class="sxs-lookup"><span data-stu-id="494dd-122">The `ToString` method is overridden in this example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#38)]  
  
 <span data-ttu-id="494dd-123">`ToString` Programda açıkça kullanılmayana dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="494dd-123">Notice that `ToString` is not explicitly used in the program.</span></span> <span data-ttu-id="494dd-124">`WriteLine` Aramalar tarafından varsayılan olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="494dd-124">It is invoked by default by the `WriteLine` calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="494dd-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="494dd-125">See also</span></span>

- [<span data-ttu-id="494dd-126">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="494dd-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="494dd-127">Özellikler</span><span class="sxs-lookup"><span data-stu-id="494dd-127">Properties</span></span>](./properties.md)
- [<span data-ttu-id="494dd-128">Sınıflar ve Structs</span><span class="sxs-lookup"><span data-stu-id="494dd-128">Classes and Structs</span></span>](./index.md)
