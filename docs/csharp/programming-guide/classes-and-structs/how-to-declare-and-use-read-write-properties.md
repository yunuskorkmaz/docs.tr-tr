---
title: 'Nasıl yapılır: Okuma yazma özelliklerini bildirme ve kullanma- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: 010c3d4c1ae976091b5382f00a982400746f6436
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596935"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a><span data-ttu-id="625ee-102">Nasıl yapılır: Okuma yazma özelliklerini bildirme ve kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="625ee-102">How to: Declare and Use Read Write Properties (C# Programming Guide)</span></span>
<span data-ttu-id="625ee-103">Özellikler, bir nesnenin verilerine korumasız, denetlenmeyen ve doğrulanmamış erişimle gelen riskler olmadan ortak veri üyelerinin rahatlığını sağlar.</span><span class="sxs-lookup"><span data-stu-id="625ee-103">Properties provide the convenience of public data members without the risks that come with unprotected, uncontrolled, and unverified access to an object's data.</span></span> <span data-ttu-id="625ee-104">Bu, *erişimciler*aracılığıyla gerçekleştirilir: temel alınan veri üyesine değerler atayan ve alan özel yöntemler.</span><span class="sxs-lookup"><span data-stu-id="625ee-104">This is accomplished through *accessors*: special methods that assign and retrieve values from the underlying data member.</span></span> <span data-ttu-id="625ee-105">[Set](../../language-reference/keywords/set.md) erişimcisi veri üyelerinin atanmasını sağlar ve [Get](../../language-reference/keywords/get.md) erişimcisi veri üyesi değerlerini alır.</span><span class="sxs-lookup"><span data-stu-id="625ee-105">The [set](../../language-reference/keywords/set.md) accessor enables data members to be assigned, and the [get](../../language-reference/keywords/get.md) accessor retrieves data member values.</span></span>  
  
 <span data-ttu-id="625ee-106">Bu örnek, iki `Person` özelliği olan bir sınıfı gösterir: `Name` (dize) ve `Age` (int).</span><span class="sxs-lookup"><span data-stu-id="625ee-106">This sample shows a `Person` class that has two properties: `Name` (string) and `Age` (int).</span></span> <span data-ttu-id="625ee-107">Her iki özellik `get` de `set` ve erişimcileri sağlar, bu nedenle okuma/yazma özellikleri olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="625ee-107">Both properties provide `get` and `set` accessors, so they are considered read/write properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="625ee-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="625ee-108">Example</span></span>  
 [!code-csharp[csProgGuideObjects#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#33)]  
  
## <a name="robust-programming"></a><span data-ttu-id="625ee-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="625ee-109">Robust Programming</span></span>  
 <span data-ttu-id="625ee-110">Önceki örnekte `Name` `Age` , ve özellikleri [geneldir](../../language-reference/keywords/public.md) ve hem hem de `get` `set` erişimcisi içerir.</span><span class="sxs-lookup"><span data-stu-id="625ee-110">In the previous example, the `Name` and `Age` properties are [public](../../language-reference/keywords/public.md) and include both a `get` and a `set` accessor.</span></span> <span data-ttu-id="625ee-111">Bu, herhangi bir nesnenin bu özellikleri okumasına ve yazmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="625ee-111">This allows any object to read and write these properties.</span></span> <span data-ttu-id="625ee-112">Ancak erişimcilerinin birini dışlamak bazen tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="625ee-112">It is sometimes desirable, however, to exclude one of the accessors.</span></span> <span data-ttu-id="625ee-113">`set` Erişimci atlanırsa, örneğin, özelliği salt okunurdur:</span><span class="sxs-lookup"><span data-stu-id="625ee-113">Omitting the `set` accessor, for example, makes the property read-only:</span></span>  
  
 [!code-csharp[csProgGuideObjects#87](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#87)]  
  
 <span data-ttu-id="625ee-114">Alternatif olarak, bir erişimciye genel kullanıma sunabilirsiniz, ancak diğerini özel veya korumalı hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="625ee-114">Alternatively, you can expose one accessor publicly but make the other private or protected.</span></span> <span data-ttu-id="625ee-115">Daha fazla bilgi için bkz. [asimetrik erişimci erişilebilirliği](./restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="625ee-115">For more information, see [Asymmetric Accessor Accessibility](./restricting-accessor-accessibility.md).</span></span>  
  
 <span data-ttu-id="625ee-116">Özellikler doğrulandıktan sonra, sınıfının alanları gibi kullanılabilirler.</span><span class="sxs-lookup"><span data-stu-id="625ee-116">Once the properties are declared, they can be used as if they were fields of the class.</span></span> <span data-ttu-id="625ee-117">Bu, aşağıdaki deyimlerde olduğu gibi bir özelliğin değerini alırken ve ayarlarken çok doğal bir sözdizimi sağlar:</span><span class="sxs-lookup"><span data-stu-id="625ee-117">This allows for a very natural syntax when both getting and setting the value of a property, as in the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#35)]  
  
 <span data-ttu-id="625ee-118">Bir özellik `set` yönteminde özel `value` bir değişken bulunduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="625ee-118">Note that in a property `set` method a special `value` variable is available.</span></span> <span data-ttu-id="625ee-119">Bu değişken, kullanıcının belirttiği değeri içerir, örneğin:</span><span class="sxs-lookup"><span data-stu-id="625ee-119">This variable contains the value that the user specified, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#36)]  
  
 <span data-ttu-id="625ee-120">`Age` Bir`Person` nesne üzerindeki özelliği arttırmadan ilgili Temizleme sözdizimine dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="625ee-120">Notice the clean syntax for incrementing the `Age` property on a `Person` object:</span></span>  
  
 [!code-csharp[csProgGuideObjects#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#37)]  
  
 <span data-ttu-id="625ee-121">Özellikleri modellemek `set` için `get` ayrı ve Yöntemler kullanılmışsa, eşdeğer kod şöyle görünebilir:</span><span class="sxs-lookup"><span data-stu-id="625ee-121">If separate `set` and `get` methods were used to model properties, the equivalent code might look like this:</span></span>  
  
```csharp  
person.SetAge(person.GetAge() + 1);   
```  
  
 <span data-ttu-id="625ee-122">`ToString` Yöntemi bu örnekte geçersiz kılınır:</span><span class="sxs-lookup"><span data-stu-id="625ee-122">The `ToString` method is overridden in this example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#38)]  
  
 <span data-ttu-id="625ee-123">`ToString` Programda açıkça kullanılmadığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="625ee-123">Notice that `ToString` is not explicitly used in the program.</span></span> <span data-ttu-id="625ee-124">`WriteLine` Çağrılar tarafından varsayılan olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="625ee-124">It is invoked by default by the `WriteLine` calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="625ee-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="625ee-125">See also</span></span>

- [<span data-ttu-id="625ee-126">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="625ee-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="625ee-127">Özellikler</span><span class="sxs-lookup"><span data-stu-id="625ee-127">Properties</span></span>](./properties.md)
- [<span data-ttu-id="625ee-128">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="625ee-128">Classes and Structs</span></span>](./index.md)
