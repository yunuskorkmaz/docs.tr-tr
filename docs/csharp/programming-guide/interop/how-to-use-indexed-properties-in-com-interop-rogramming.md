---
title: 'Nasıl Yapılır: Özellikleri - COM birlikte çalışma programlamada dizin oluşturulmuş kullanma C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: 58b3b2646fec0284dc3e04c152b183ce05e05932
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245382"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a><span data-ttu-id="c47b3-102">Nasıl Yapılır: Özellikleri COM birlikte çalışma programlamada dizin oluşturulmuş kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c47b3-102">How to: Use Indexed Properties in COM Interop Programming (C# Programming Guide)</span></span>
<span data-ttu-id="c47b3-103">*Dizin oluşturulmuş özellikleri* parametrelere sahip özellikler COM kullandığı şeklini geliştirmek C# programlama.</span><span class="sxs-lookup"><span data-stu-id="c47b3-103">*Indexed properties* improve the way in which COM properties that have parameters are consumed in C# programming.</span></span> <span data-ttu-id="c47b3-104">Diğer özellikler Visual C#, birlikte çalışma özellikleri gibi dizine [adlandırılmış ve isteğe bağlı bağımsız değişkenler](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), yeni bir tür ([dinamik](../../../csharp/language-reference/keywords/dynamic.md)), ve [gömülü tür bilgileri](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md), Microsoft Office programlama geliştirin.</span><span class="sxs-lookup"><span data-stu-id="c47b3-104">Indexed properties work together with other features in Visual C#, such as [named and optional arguments](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), a new type ([dynamic](../../../csharp/language-reference/keywords/dynamic.md)), and [embedded type information](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md), to enhance Microsoft Office programming.</span></span>  
  
 <span data-ttu-id="c47b3-105">Önceki sürümlerde, C#, yöntemler yalnızca şu durumlarda özellikler erişilebilir `get` yönteminin parametresiz vardır ve `set` yöntemi yalnızca tek değer parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="c47b3-105">In earlier versions of C#, methods are accessible as properties only if the `get` method has no parameters and the `set` method has one and only one value parameter.</span></span> <span data-ttu-id="c47b3-106">Ancak, tüm COM özellikleri bu kısıtlamaları karşılayın.</span><span class="sxs-lookup"><span data-stu-id="c47b3-106">However, not all COM properties meet those restrictions.</span></span> <span data-ttu-id="c47b3-107">Örneğin, Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> özelliğine sahip bir `get` aralığın adı için bir parametre gerektiren erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="c47b3-107">For example, the Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> property has a `get` accessor that requires a parameter for the name of the range.</span></span> <span data-ttu-id="c47b3-108">Geçmişte, olmayan erişim çünkü `Range` özelliği doğrudan tablonuz kullanılacak `get_Range` yöntemi yerine, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="c47b3-108">In the past, because you could not access the `Range` property directly, you had to use the `get_Range` method instead, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_1.cs)]  
  
 <span data-ttu-id="c47b3-109">Dizinli Özellikler, bunun yerine aşağıdaki yazma olanak sağlar:</span><span class="sxs-lookup"><span data-stu-id="c47b3-109">Indexed properties enable you to write the following instead:</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_2.cs)]  
  
> [!NOTE]
>  <span data-ttu-id="c47b3-110">Ayrıca önceki örneğin kullandığı [isteğe bağlı bağımsız değişkenlere](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) atlamak sağlayan bir özellik `Type.Missing`.</span><span class="sxs-lookup"><span data-stu-id="c47b3-110">The previous example also uses the [optional arguments](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) feature, which enables you to omit `Type.Missing`.</span></span>  
  
 <span data-ttu-id="c47b3-111">Benzer şekilde değerini ayarlamak için `Value` özelliği bir <xref:Microsoft.Office.Interop.Excel.Range> nesne Visual C# 2008 ve önceki sürümlerinde, iki bağımsız değişkeni gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c47b3-111">Similarly to set the value of the `Value` property of a <xref:Microsoft.Office.Interop.Excel.Range> object in Visual C# 2008 and earlier, two arguments are required.</span></span> <span data-ttu-id="c47b3-112">Bir aralık değeri türünü belirten isteğe bağlı parametresi için bağımsız değişken sağlar.</span><span class="sxs-lookup"><span data-stu-id="c47b3-112">One supplies an argument for an optional parameter that specifies the type of the range value.</span></span> <span data-ttu-id="c47b3-113">Diğer değeri sağlayan `Value` özelliği.</span><span class="sxs-lookup"><span data-stu-id="c47b3-113">The other supplies the value for the `Value` property.</span></span> <span data-ttu-id="c47b3-114">Aşağıdaki örnekler, bu teknikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="c47b3-114">The following examples illustrate these techniques.</span></span> <span data-ttu-id="c47b3-115">Her ikisi de A1 hücresine değerini `Name`.</span><span class="sxs-lookup"><span data-stu-id="c47b3-115">Both set the value of the A1 cell to `Name`.</span></span>
  
 [!code-csharp[csProgGuideIndexedProperties#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_3.cs)]  
  
 <span data-ttu-id="c47b3-116">Dizinli Özellikler, bunun yerine aşağıdaki kodu yazmak etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="c47b3-116">Indexed properties enable you to write the following code instead.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_4.cs)]  
  
 <span data-ttu-id="c47b3-117">Dizinli Özellikler kendi oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="c47b3-117">You cannot create indexed properties of your own.</span></span> <span data-ttu-id="c47b3-118">Özelliği, yalnızca mevcut Dizinlenmiş özelliklerin tüketimini destekler.</span><span class="sxs-lookup"><span data-stu-id="c47b3-118">The feature only supports consumption of existing indexed properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c47b3-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="c47b3-119">Example</span></span>  
 <span data-ttu-id="c47b3-120">Aşağıdaki kod, tam bir örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="c47b3-120">The following code shows a complete example.</span></span> <span data-ttu-id="c47b3-121">Office API'si erişen bir projeyi ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: Visual kullanarak Office birlikte çalışma nesnelerine erişim C# özellikleri](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="c47b3-121">For more information about how to set up a project that accesses the Office API, see [How to: Access Office Interop Objects by Using Visual C# Features](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_5.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c47b3-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c47b3-122">See Also</span></span>

- [<span data-ttu-id="c47b3-123">Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="c47b3-123">Named and Optional Arguments</span></span>](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)  
- [<span data-ttu-id="c47b3-124">dynamic</span><span class="sxs-lookup"><span data-stu-id="c47b3-124">dynamic</span></span>](../../../csharp/language-reference/keywords/dynamic.md)  
- [<span data-ttu-id="c47b3-125">Tür dinamiği kullanma</span><span class="sxs-lookup"><span data-stu-id="c47b3-125">Using Type dynamic</span></span>](../../../csharp/programming-guide/types/using-type-dynamic.md)  
- [<span data-ttu-id="c47b3-126">Nasıl yapılır: Office Programlamada adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanma</span><span class="sxs-lookup"><span data-stu-id="c47b3-126">How to: Use Named and Optional Arguments in Office Programming</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)  
- [<span data-ttu-id="c47b3-127">Nasıl yapılır: Visual kullanarak Office birlikte çalışma nesnelerine erişim C# özellikleri</span><span class="sxs-lookup"><span data-stu-id="c47b3-127">How to: Access Office Interop Objects by Using Visual C# Features</span></span>](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
- [<span data-ttu-id="c47b3-128">İzlenecek yol: Office programlama</span><span class="sxs-lookup"><span data-stu-id="c47b3-128">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
