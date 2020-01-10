---
title: COM birlikte çalışma programlama- C# programlama kılavuzunda dizinli özellikleri kullanma
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: 864e2274f0e0e79b4843e0bb67b5c4384eac8588
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712071"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a><span data-ttu-id="89c11-102">COM birlikte çalışma programlamada Dizin oluşturulmuş özellikleri kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="89c11-102">How to use indexed properties in COM interop programming (C# Programming Guide)</span></span>
<span data-ttu-id="89c11-103">*Dizinli Özellikler* , programlama içinde C# parametreleri olan com özelliklerinin hangi şekilde tüketildiğini geliştirir.</span><span class="sxs-lookup"><span data-stu-id="89c11-103">*Indexed properties* improve the way in which COM properties that have parameters are consumed in C# programming.</span></span> <span data-ttu-id="89c11-104">Dizinli Özellikler C#, Microsoft Office programlamayı geliştirmek için [adlandırılmış ve isteğe bağlı bağımsız değişkenler](../classes-and-structs/named-and-optional-arguments.md), yeni bir tür ([dinamik](../../language-reference/builtin-types/reference-types.md)) ve [katıştırılmış tür bilgileri](../../../standard/assembly/embed-types-visual-studio.md)gibi görseldeki diğer özelliklerle birlikte çalışır.</span><span class="sxs-lookup"><span data-stu-id="89c11-104">Indexed properties work together with other features in Visual C#, such as [named and optional arguments](../classes-and-structs/named-and-optional-arguments.md), a new type ([dynamic](../../language-reference/builtin-types/reference-types.md)), and [embedded type information](../../../standard/assembly/embed-types-visual-studio.md), to enhance Microsoft Office programming.</span></span>  
  
 <span data-ttu-id="89c11-105">Önceki sürümlerinde C#, yöntemler yalnızca `get` yönteminin parametresi yoksa ve `set` yöntemi bir ve yalnızca bir değer parametresi içeriyorsa özellikler olarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="89c11-105">In earlier versions of C#, methods are accessible as properties only if the `get` method has no parameters and the `set` method has one and only one value parameter.</span></span> <span data-ttu-id="89c11-106">Ancak, tüm COM özellikleri bu kısıtlamaları karşılamıyor.</span><span class="sxs-lookup"><span data-stu-id="89c11-106">However, not all COM properties meet those restrictions.</span></span> <span data-ttu-id="89c11-107">Örneğin, Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> özelliğinin, Aralık adı için bir parametre gerektiren bir `get` erişimcisi vardır.</span><span class="sxs-lookup"><span data-stu-id="89c11-107">For example, the Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> property has a `get` accessor that requires a parameter for the name of the range.</span></span> <span data-ttu-id="89c11-108">Geçmişte, `Range` özelliğine doğrudan erişemediği için, aşağıdaki örnekte gösterildiği gibi, bunun yerine `get_Range` yöntemini kullanmanız gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="89c11-108">In the past, because you could not access the `Range` property directly, you had to use the `get_Range` method instead, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#1)]  
  
 <span data-ttu-id="89c11-109">Dizini oluşturulmuş Özellikler bunun yerine aşağıdakini yazmanızı sağlar:</span><span class="sxs-lookup"><span data-stu-id="89c11-109">Indexed properties enable you to write the following instead:</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#2)]  
  
> [!NOTE]
> <span data-ttu-id="89c11-110">Önceki örnek ayrıca, `Type.Missing`atlamanızı sağlayan [isteğe bağlı bağımsız değişkenler](../classes-and-structs/named-and-optional-arguments.md) özelliğini de kullanır.</span><span class="sxs-lookup"><span data-stu-id="89c11-110">The previous example also uses the [optional arguments](../classes-and-structs/named-and-optional-arguments.md) feature, which enables you to omit `Type.Missing`.</span></span>  
  
 <span data-ttu-id="89c11-111">Benzer şekilde, C# 3,0 ve önceki sürümlerde bir <xref:Microsoft.Office.Interop.Excel.Range> nesnesinin `Value` özelliğinin değerini ayarlamak için iki bağımsız değişken gereklidir.</span><span class="sxs-lookup"><span data-stu-id="89c11-111">Similarly to set the value of the `Value` property of a <xref:Microsoft.Office.Interop.Excel.Range> object in C# 3.0 and earlier, two arguments are required.</span></span> <span data-ttu-id="89c11-112">Bir, Aralık değerinin türünü belirten isteğe bağlı bir parametre için bağımsız değişken sağlar.</span><span class="sxs-lookup"><span data-stu-id="89c11-112">One supplies an argument for an optional parameter that specifies the type of the range value.</span></span> <span data-ttu-id="89c11-113">Diğeri `Value` özelliği için değer sağlar.</span><span class="sxs-lookup"><span data-stu-id="89c11-113">The other supplies the value for the `Value` property.</span></span> <span data-ttu-id="89c11-114">Aşağıdaki örneklerde bu teknikler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="89c11-114">The following examples illustrate these techniques.</span></span> <span data-ttu-id="89c11-115">Her ikisi de a1 hücresinin değerini `Name`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="89c11-115">Both set the value of the A1 cell to `Name`.</span></span>
  
 [!code-csharp[csProgGuideIndexedProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#3)]  
  
 <span data-ttu-id="89c11-116">Dizini oluşturulmuş Özellikler bunun yerine aşağıdaki kodu yazmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="89c11-116">Indexed properties enable you to write the following code instead.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#4)]  
  
 <span data-ttu-id="89c11-117">Kendinizinkini dizinli Özellikler oluşturamazsınız.</span><span class="sxs-lookup"><span data-stu-id="89c11-117">You cannot create indexed properties of your own.</span></span> <span data-ttu-id="89c11-118">Özelliği yalnızca var olan dizinli özelliklerin kullanımını destekler.</span><span class="sxs-lookup"><span data-stu-id="89c11-118">The feature only supports consumption of existing indexed properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89c11-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="89c11-119">Example</span></span>  
 <span data-ttu-id="89c11-120">Aşağıdaki kod, bir örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="89c11-120">The following code shows a complete example.</span></span> <span data-ttu-id="89c11-121">Office API 'sine erişen bir projeyi ayarlama hakkında daha fazla bilgi için bkz. [özellikleri kullanarak C# Office birlikte çalışma nesnelerine erişme](./how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="89c11-121">For more information about how to set up a project that accesses the Office API, see [How to access Office interop objects by using C# features](./how-to-access-office-onterop-objects.md).</span></span>
  
 [!code-csharp[csProgGuideIndexedProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="89c11-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89c11-122">See also</span></span>

- [<span data-ttu-id="89c11-123">Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="89c11-123">Named and Optional Arguments</span></span>](../classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="89c11-124">dynamic</span><span class="sxs-lookup"><span data-stu-id="89c11-124">dynamic</span></span>](../../language-reference/builtin-types/reference-types.md)
- [<span data-ttu-id="89c11-125">Tür dinamiği kullanma</span><span class="sxs-lookup"><span data-stu-id="89c11-125">Using Type dynamic</span></span>](../types/using-type-dynamic.md)
- [<span data-ttu-id="89c11-126">Office Programlamada adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanma</span><span class="sxs-lookup"><span data-stu-id="89c11-126">How to use named and optional arguments in Office programming</span></span>](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [<span data-ttu-id="89c11-127">Özellikleri kullanarak C# Office birlikte çalışma nesnelerine erişme</span><span class="sxs-lookup"><span data-stu-id="89c11-127">How to access Office interop objects by using C# features</span></span>](./how-to-access-office-onterop-objects.md)
- [<span data-ttu-id="89c11-128">İzlenecek yol: Office programlama</span><span class="sxs-lookup"><span data-stu-id="89c11-128">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)
