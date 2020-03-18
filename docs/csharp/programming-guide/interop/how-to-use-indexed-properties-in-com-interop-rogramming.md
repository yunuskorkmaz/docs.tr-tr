---
title: COM interop programlamada dizinlenmiş özellikler nasıl kullanılır - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: 864e2274f0e0e79b4843e0bb67b5c4384eac8588
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712071"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a><span data-ttu-id="b438c-102">COM interop programlamada dizinlenmiş özellikler nasıl kullanılır (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="b438c-102">How to use indexed properties in COM interop programming (C# Programming Guide)</span></span>
<span data-ttu-id="b438c-103">*Dizinlenmiş özellikler,* parametreleri olan COM özelliklerinin C# programlamada nasıl tüketildiğini geliştirir.</span><span class="sxs-lookup"><span data-stu-id="b438c-103">*Indexed properties* improve the way in which COM properties that have parameters are consumed in C# programming.</span></span> <span data-ttu-id="b438c-104">Dizine eklenmiş özellikler, Microsoft Office programlamasını geliştirmek için Visual C#'daki [adlandırılmış ve isteğe bağlı bağımsız değişkenler](../classes-and-structs/named-and-optional-arguments.md), yeni bir tür[(dinamik)](../../language-reference/builtin-types/reference-types.md)ve [katıştılı tür bilgileri](../../../standard/assembly/embed-types-visual-studio.md)gibi diğer özelliklerle birlikte çalışır.</span><span class="sxs-lookup"><span data-stu-id="b438c-104">Indexed properties work together with other features in Visual C#, such as [named and optional arguments](../classes-and-structs/named-and-optional-arguments.md), a new type ([dynamic](../../language-reference/builtin-types/reference-types.md)), and [embedded type information](../../../standard/assembly/embed-types-visual-studio.md), to enhance Microsoft Office programming.</span></span>  
  
 <span data-ttu-id="b438c-105">C#'ın önceki sürümlerinde, yöntemlere yalnızca `get` yöntemin parametreleri `set` yoksa ve yöntemin tek ve tek bir değer parametresi varsa özellik olarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="b438c-105">In earlier versions of C#, methods are accessible as properties only if the `get` method has no parameters and the `set` method has one and only one value parameter.</span></span> <span data-ttu-id="b438c-106">Ancak, tüm COM özellikleri bu kısıtlamaları karşılamaz.</span><span class="sxs-lookup"><span data-stu-id="b438c-106">However, not all COM properties meet those restrictions.</span></span> <span data-ttu-id="b438c-107">Örneğin, Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> özelliği, `get` aralığın adı için bir parametre gerektiren bir erişime sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b438c-107">For example, the Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> property has a `get` accessor that requires a parameter for the name of the range.</span></span> <span data-ttu-id="b438c-108">Geçmişte, `Range` özelliğe doğrudan erişemediğiniz için, aşağıdaki örnekte gösterildiği gibi `get_Range` yöntemi kullanmanız gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="b438c-108">In the past, because you could not access the `Range` property directly, you had to use the `get_Range` method instead, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#1)]  
  
 <span data-ttu-id="b438c-109">Dizinlenmiş özellikler yerine aşağıdakileri yazmanızı sağlar:</span><span class="sxs-lookup"><span data-stu-id="b438c-109">Indexed properties enable you to write the following instead:</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#2)]  
  
> [!NOTE]
> <span data-ttu-id="b438c-110">Önceki örnekte, atlayabilmenizi sağlayan [isteğe bağlı bağımsız değişkenler](../classes-and-structs/named-and-optional-arguments.md) özelliği de `Type.Missing`kullanır.</span><span class="sxs-lookup"><span data-stu-id="b438c-110">The previous example also uses the [optional arguments](../classes-and-structs/named-and-optional-arguments.md) feature, which enables you to omit `Type.Missing`.</span></span>  
  
 <span data-ttu-id="b438c-111">Benzer şekilde C# 3.0 <xref:Microsoft.Office.Interop.Excel.Range> ve daha önce bir nesnenin `Value` özelliğinin değerini ayarlamak için iki bağımsız değişken gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b438c-111">Similarly to set the value of the `Value` property of a <xref:Microsoft.Office.Interop.Excel.Range> object in C# 3.0 and earlier, two arguments are required.</span></span> <span data-ttu-id="b438c-112">Bir aralık değeri türünü belirten isteğe bağlı bir parametre için bir bağımsız değişken sağlar.</span><span class="sxs-lookup"><span data-stu-id="b438c-112">One supplies an argument for an optional parameter that specifies the type of the range value.</span></span> <span data-ttu-id="b438c-113">Diğeri `Value` mülkün değerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b438c-113">The other supplies the value for the `Value` property.</span></span> <span data-ttu-id="b438c-114">Aşağıdaki örneklerde bu teknikler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b438c-114">The following examples illustrate these techniques.</span></span> <span data-ttu-id="b438c-115">Her ikisi de A1 hücresinin değerini `Name`.</span><span class="sxs-lookup"><span data-stu-id="b438c-115">Both set the value of the A1 cell to `Name`.</span></span>
  
 [!code-csharp[csProgGuideIndexedProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#3)]  
  
 <span data-ttu-id="b438c-116">Dizinlenmiş özellikler yerine aşağıdaki kodu yazmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b438c-116">Indexed properties enable you to write the following code instead.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#4)]  
  
 <span data-ttu-id="b438c-117">Kendi dizinlenmiş özellikleri oluşturamazsınız.</span><span class="sxs-lookup"><span data-stu-id="b438c-117">You cannot create indexed properties of your own.</span></span> <span data-ttu-id="b438c-118">Özellik yalnızca varolan dizinlenmiş özelliklerin tüketimini destekler.</span><span class="sxs-lookup"><span data-stu-id="b438c-118">The feature only supports consumption of existing indexed properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b438c-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="b438c-119">Example</span></span>  
 <span data-ttu-id="b438c-120">Aşağıdaki kod tam bir örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="b438c-120">The following code shows a complete example.</span></span> <span data-ttu-id="b438c-121">Office API'sine erişen bir projeyi nasıl ayarladığınız hakkında daha fazla bilgi için [C# özelliklerini kullanarak Office interop nesnelerine nasıl erişilir'e](./how-to-access-office-onterop-objects.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="b438c-121">For more information about how to set up a project that accesses the Office API, see [How to access Office interop objects by using C# features](./how-to-access-office-onterop-objects.md).</span></span>
  
 [!code-csharp[csProgGuideIndexedProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="b438c-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b438c-122">See also</span></span>

- [<span data-ttu-id="b438c-123">Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="b438c-123">Named and Optional Arguments</span></span>](../classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="b438c-124">Dinamik</span><span class="sxs-lookup"><span data-stu-id="b438c-124">dynamic</span></span>](../../language-reference/builtin-types/reference-types.md)
- [<span data-ttu-id="b438c-125">Tür dinamiği kullanma</span><span class="sxs-lookup"><span data-stu-id="b438c-125">Using Type dynamic</span></span>](../types/using-type-dynamic.md)
- [<span data-ttu-id="b438c-126">Office programlamada adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanma</span><span class="sxs-lookup"><span data-stu-id="b438c-126">How to use named and optional arguments in Office programming</span></span>](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [<span data-ttu-id="b438c-127">Visual C# özelliklerini kullanarak Office birlikte çalışma nesnelerine erişim</span><span class="sxs-lookup"><span data-stu-id="b438c-127">How to access Office interop objects by using C# features</span></span>](./how-to-access-office-onterop-objects.md)
- [<span data-ttu-id="b438c-128">Walkthrough: Office Programlama</span><span class="sxs-lookup"><span data-stu-id="b438c-128">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)
