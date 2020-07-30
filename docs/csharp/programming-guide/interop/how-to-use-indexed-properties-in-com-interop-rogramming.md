---
title: COM birlikte çalışma programlamada dizinli özellikleri kullanma-C# Programlama Kılavuzu
description: Dizine alınmış özelliklerin, bu C# örneğinde, parametreleri olan COM özelliklerinin hangi şekilde geliştirileceğini nasıl artıracağınızı öğrenin.
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: abd785864bd79d455024cb4501c76a21b349aa91
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303016"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a><span data-ttu-id="63918-103">COM birlikte çalışma programlamada Dizin oluşturulmuş özellikleri kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="63918-103">How to use indexed properties in COM interop programming (C# Programming Guide)</span></span>
<span data-ttu-id="63918-104">*Dizinli Özellikler* , C# programlamasında PARAMETRELERI olan com özelliklerinin hangi şekilde tüketildiğini geliştirir.</span><span class="sxs-lookup"><span data-stu-id="63918-104">*Indexed properties* improve the way in which COM properties that have parameters are consumed in C# programming.</span></span> <span data-ttu-id="63918-105">Dizinli özellikler, Microsoft Office programlamayı geliştirmek için [adlandırılmış ve isteğe bağlı bağımsız değişkenler](../classes-and-structs/named-and-optional-arguments.md), yeni bir tür ([dinamik](../../language-reference/builtin-types/reference-types.md)) ve [katıştırılmış tür bilgileri](../../../standard/assembly/embed-types-visual-studio.md)gibi Visual C# ' deki diğer özelliklerle birlikte çalışır.</span><span class="sxs-lookup"><span data-stu-id="63918-105">Indexed properties work together with other features in Visual C#, such as [named and optional arguments](../classes-and-structs/named-and-optional-arguments.md), a new type ([dynamic](../../language-reference/builtin-types/reference-types.md)), and [embedded type information](../../../standard/assembly/embed-types-visual-studio.md), to enhance Microsoft Office programming.</span></span>  
  
 <span data-ttu-id="63918-106">C# ' nin önceki sürümlerinde yöntemlere yalnızca `get` yöntemin parametresi yoksa ve `set` yöntemi bir ve yalnızca bir değer parametresi yoksa özellikler olarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="63918-106">In earlier versions of C#, methods are accessible as properties only if the `get` method has no parameters and the `set` method has one and only one value parameter.</span></span> <span data-ttu-id="63918-107">Ancak, tüm COM özellikleri bu kısıtlamaları karşılamıyor.</span><span class="sxs-lookup"><span data-stu-id="63918-107">However, not all COM properties meet those restrictions.</span></span> <span data-ttu-id="63918-108">Örneğin, Excel özelliğinin, <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> `get` Aralık adı için bir parametre gerektiren bir erişimcisi vardır.</span><span class="sxs-lookup"><span data-stu-id="63918-108">For example, the Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> property has a `get` accessor that requires a parameter for the name of the range.</span></span> <span data-ttu-id="63918-109">Geçmişte, `Range` özelliği doğrudan erişemediği için, `get_Range` Aşağıdaki örnekte gösterildiği gibi yöntemini kullanmanız gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="63918-109">In the past, because you could not access the `Range` property directly, you had to use the `get_Range` method instead, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#1)]  
  
 <span data-ttu-id="63918-110">Dizini oluşturulmuş Özellikler bunun yerine aşağıdakini yazmanızı sağlar:</span><span class="sxs-lookup"><span data-stu-id="63918-110">Indexed properties enable you to write the following instead:</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#2)]  
  
> [!NOTE]
> <span data-ttu-id="63918-111">Önceki örnek ayrıca, öğesini atlamanızı sağlayan [isteğe bağlı bağımsız değişkenler](../classes-and-structs/named-and-optional-arguments.md) özelliğini de kullanır `Type.Missing` .</span><span class="sxs-lookup"><span data-stu-id="63918-111">The previous example also uses the [optional arguments](../classes-and-structs/named-and-optional-arguments.md) feature, which enables you to omit `Type.Missing`.</span></span>  
  
 <span data-ttu-id="63918-112">Benzer şekilde `Value` <xref:Microsoft.Office.Interop.Excel.Range> , C# 3,0 ve önceki bir nesnenin özelliğinin değerini ayarlamak için iki bağımsız değişken gereklidir.</span><span class="sxs-lookup"><span data-stu-id="63918-112">Similarly to set the value of the `Value` property of a <xref:Microsoft.Office.Interop.Excel.Range> object in C# 3.0 and earlier, two arguments are required.</span></span> <span data-ttu-id="63918-113">Bir, Aralık değerinin türünü belirten isteğe bağlı bir parametre için bağımsız değişken sağlar.</span><span class="sxs-lookup"><span data-stu-id="63918-113">One supplies an argument for an optional parameter that specifies the type of the range value.</span></span> <span data-ttu-id="63918-114">Diğer, özelliğinin değerini sağlar `Value` .</span><span class="sxs-lookup"><span data-stu-id="63918-114">The other supplies the value for the `Value` property.</span></span> <span data-ttu-id="63918-115">Aşağıdaki örneklerde bu teknikler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="63918-115">The following examples illustrate these techniques.</span></span> <span data-ttu-id="63918-116">Her ikisi de a1 hücresinin değerini olarak ayarlayın `Name` .</span><span class="sxs-lookup"><span data-stu-id="63918-116">Both set the value of the A1 cell to `Name`.</span></span>
  
 [!code-csharp[csProgGuideIndexedProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#3)]  
  
 <span data-ttu-id="63918-117">Dizini oluşturulmuş Özellikler bunun yerine aşağıdaki kodu yazmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="63918-117">Indexed properties enable you to write the following code instead.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#4)]  
  
 <span data-ttu-id="63918-118">Kendinizinkini dizinli Özellikler oluşturamazsınız.</span><span class="sxs-lookup"><span data-stu-id="63918-118">You cannot create indexed properties of your own.</span></span> <span data-ttu-id="63918-119">Özelliği yalnızca var olan dizinli özelliklerin kullanımını destekler.</span><span class="sxs-lookup"><span data-stu-id="63918-119">The feature only supports consumption of existing indexed properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63918-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="63918-120">Example</span></span>  
 <span data-ttu-id="63918-121">Aşağıdaki kod, bir örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="63918-121">The following code shows a complete example.</span></span> <span data-ttu-id="63918-122">Office API 'sine erişen bir projeyi ayarlama hakkında daha fazla bilgi için bkz. [C# özelliklerini kullanarak Office birlikte çalışma nesnelerine erişme](./how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="63918-122">For more information about how to set up a project that accesses the Office API, see [How to access Office interop objects by using C# features](./how-to-access-office-onterop-objects.md).</span></span>
  
 [!code-csharp[csProgGuideIndexedProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="63918-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63918-123">See also</span></span>

- [<span data-ttu-id="63918-124">Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="63918-124">Named and Optional Arguments</span></span>](../classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="63918-125">dinamik</span><span class="sxs-lookup"><span data-stu-id="63918-125">dynamic</span></span>](../../language-reference/builtin-types/reference-types.md)
- [<span data-ttu-id="63918-126">Tür dinamiği kullanma</span><span class="sxs-lookup"><span data-stu-id="63918-126">Using Type dynamic</span></span>](../types/using-type-dynamic.md)
- [<span data-ttu-id="63918-127">Office programlamada adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanma</span><span class="sxs-lookup"><span data-stu-id="63918-127">How to use named and optional arguments in Office programming</span></span>](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [<span data-ttu-id="63918-128">Visual C# özelliklerini kullanarak Office birlikte çalışma nesnelerine erişim</span><span class="sxs-lookup"><span data-stu-id="63918-128">How to access Office interop objects by using C# features</span></span>](./how-to-access-office-onterop-objects.md)
- [<span data-ttu-id="63918-129">İzlenecek yol: Office programlama</span><span class="sxs-lookup"><span data-stu-id="63918-129">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)
