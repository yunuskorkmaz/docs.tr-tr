---
title: Okuma yazma özelliklerini bildirme ve kullanma-C# Programlama Kılavuzu
description: C# ' de okuma/yazma özelliklerini kullanmayı öğrenin. Bu örnek, her biri get ve set erişimcilerine sahip olan iki özelliği içerir, bu nedenle Özellikler okuma/yazma olur.
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: a2bfc3f43db84ebf69f9a5f41c118c5981e33c19
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91199152"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a><span data-ttu-id="98b79-104">Okuma yazma özelliklerini bildirme ve kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="98b79-104">How to declare and use read write properties (C# Programming Guide)</span></span>

<span data-ttu-id="98b79-105">Özellikler, bir nesnenin verilerine korumasız, denetlenmeyen ve doğrulanmamış erişimle gelen riskler olmadan ortak veri üyelerinin rahatlığını sağlar.</span><span class="sxs-lookup"><span data-stu-id="98b79-105">Properties provide the convenience of public data members without the risks that come with unprotected, uncontrolled, and unverified access to an object's data.</span></span> <span data-ttu-id="98b79-106">Bu, *erişimciler*aracılığıyla gerçekleştirilir: temel alınan veri üyesine değerler atayan ve alan özel yöntemler.</span><span class="sxs-lookup"><span data-stu-id="98b79-106">This is accomplished through *accessors*: special methods that assign and retrieve values from the underlying data member.</span></span> <span data-ttu-id="98b79-107">[Set](../../language-reference/keywords/set.md) erişimcisi veri üyelerinin atanmasını sağlar ve [Get](../../language-reference/keywords/get.md) erişimcisi veri üyesi değerlerini alır.</span><span class="sxs-lookup"><span data-stu-id="98b79-107">The [set](../../language-reference/keywords/set.md) accessor enables data members to be assigned, and the [get](../../language-reference/keywords/get.md) accessor retrieves data member values.</span></span>  
  
 <span data-ttu-id="98b79-108">Bu örnek `Person` , iki özelliği olan bir sınıfı gösterir: `Name` (dize) ve `Age` (int).</span><span class="sxs-lookup"><span data-stu-id="98b79-108">This sample shows a `Person` class that has two properties: `Name` (string) and `Age` (int).</span></span> <span data-ttu-id="98b79-109">Her iki özellik de `get` ve `set` erişimcileri sağlar, bu nedenle okuma/yazma özellikleri olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="98b79-109">Both properties provide `get` and `set` accessors, so they are considered read/write properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98b79-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="98b79-110">Example</span></span>  

 [!code-csharp[csProgGuideObjects#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#33)]  
  
## <a name="robust-programming"></a><span data-ttu-id="98b79-111">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="98b79-111">Robust Programming</span></span>  

 <span data-ttu-id="98b79-112">Önceki örnekte, `Name` ve `Age` özellikleri [geneldir](../../language-reference/keywords/public.md) ve hem hem de `get` erişimcisi içerir `set` .</span><span class="sxs-lookup"><span data-stu-id="98b79-112">In the previous example, the `Name` and `Age` properties are [public](../../language-reference/keywords/public.md) and include both a `get` and a `set` accessor.</span></span> <span data-ttu-id="98b79-113">Bu, herhangi bir nesnenin bu özellikleri okumasına ve yazmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="98b79-113">This allows any object to read and write these properties.</span></span> <span data-ttu-id="98b79-114">Ancak erişimcilerinin birini dışlamak bazen tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="98b79-114">It is sometimes desirable, however, to exclude one of the accessors.</span></span> <span data-ttu-id="98b79-115">Erişimci atlanırsa `set` , örneğin, özelliği salt okunurdur:</span><span class="sxs-lookup"><span data-stu-id="98b79-115">Omitting the `set` accessor, for example, makes the property read-only:</span></span>  
  
 [!code-csharp[csProgGuideObjects#87](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#87)]  
  
 <span data-ttu-id="98b79-116">Alternatif olarak, bir erişimciye genel kullanıma sunabilirsiniz, ancak diğerini özel veya korumalı hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98b79-116">Alternatively, you can expose one accessor publicly but make the other private or protected.</span></span> <span data-ttu-id="98b79-117">Daha fazla bilgi için bkz. [asimetrik erişimci erişilebilirliği](./restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="98b79-117">For more information, see [Asymmetric Accessor Accessibility](./restricting-accessor-accessibility.md).</span></span>  
  
 <span data-ttu-id="98b79-118">Özellikler doğrulandıktan sonra, sınıfının alanları gibi kullanılabilirler.</span><span class="sxs-lookup"><span data-stu-id="98b79-118">Once the properties are declared, they can be used as if they were fields of the class.</span></span> <span data-ttu-id="98b79-119">Bu, aşağıdaki deyimlerde olduğu gibi bir özelliğin değerini alırken ve ayarlarken çok doğal bir sözdizimi sağlar:</span><span class="sxs-lookup"><span data-stu-id="98b79-119">This allows for a very natural syntax when both getting and setting the value of a property, as in the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#35)]  
  
 <span data-ttu-id="98b79-120">Bir özellik `set` yönteminde özel bir değişken bulunduğunu unutmayın `value` .</span><span class="sxs-lookup"><span data-stu-id="98b79-120">Note that in a property `set` method a special `value` variable is available.</span></span> <span data-ttu-id="98b79-121">Bu değişken, kullanıcının belirttiği değeri içerir, örneğin:</span><span class="sxs-lookup"><span data-stu-id="98b79-121">This variable contains the value that the user specified, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#36)]  
  
 <span data-ttu-id="98b79-122">`Age`Bir nesne üzerindeki özelliği arttırmadan ilgili Temizleme sözdizimine dikkat edin `Person` :</span><span class="sxs-lookup"><span data-stu-id="98b79-122">Notice the clean syntax for incrementing the `Age` property on a `Person` object:</span></span>  
  
 [!code-csharp[csProgGuideObjects#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#37)]  
  
 <span data-ttu-id="98b79-123">`set` `get` Özellikleri modellemek için ayrı ve Yöntemler kullanılmışsa, eşdeğer kod şöyle görünebilir:</span><span class="sxs-lookup"><span data-stu-id="98b79-123">If separate `set` and `get` methods were used to model properties, the equivalent code might look like this:</span></span>  
  
```csharp  
person.SetAge(person.GetAge() + 1);
```  
  
 <span data-ttu-id="98b79-124">`ToString`Yöntemi bu örnekte geçersiz kılınır:</span><span class="sxs-lookup"><span data-stu-id="98b79-124">The `ToString` method is overridden in this example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#38)]  
  
 <span data-ttu-id="98b79-125">`ToString`Programda açıkça kullanılmadığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="98b79-125">Notice that `ToString` is not explicitly used in the program.</span></span> <span data-ttu-id="98b79-126">Çağrılar tarafından varsayılan olarak çağrılır `WriteLine` .</span><span class="sxs-lookup"><span data-stu-id="98b79-126">It is invoked by default by the `WriteLine` calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98b79-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98b79-127">See also</span></span>

- [<span data-ttu-id="98b79-128">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="98b79-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="98b79-129">Özellikler</span><span class="sxs-lookup"><span data-stu-id="98b79-129">Properties</span></span>](./properties.md)
- [<span data-ttu-id="98b79-130">Sınıflar ve yapılar</span><span class="sxs-lookup"><span data-stu-id="98b79-130">Classes and Structs</span></span>](./index.md)
