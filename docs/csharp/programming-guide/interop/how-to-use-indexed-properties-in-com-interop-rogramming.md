---
title: 'Nasıl yapılır: COM birlikte çalışma programlama- C# programlama kılavuzunda dizinli özellikleri kullanma'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: 0d4e85646a1e7f8c4ee9a73fbf7bf5a01b10b14b
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423216"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a><span data-ttu-id="dc6de-102">Nasıl yapılır: COM Birlikte Çalışma Programlamada Dizin Oluşturulmuş Özellikleri Kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="dc6de-102">How to: Use Indexed Properties in COM Interop Programming (C# Programming Guide)</span></span>
<span data-ttu-id="dc6de-103">*Dizinli Özellikler* , programlama içinde C# parametreleri olan com özelliklerinin hangi şekilde tüketildiğini geliştirir.</span><span class="sxs-lookup"><span data-stu-id="dc6de-103">*Indexed properties* improve the way in which COM properties that have parameters are consumed in C# programming.</span></span> <span data-ttu-id="dc6de-104">Dizinli Özellikler C#, Microsoft Office programlamayı geliştirmek için [adlandırılmış ve isteğe bağlı bağımsız değişkenler](../classes-and-structs/named-and-optional-arguments.md), yeni bir tür ([dinamik](../../language-reference/builtin-types/reference-types.md)) ve [katıştırılmış tür bilgileri](../../../standard/assembly/embed-types-visual-studio.md)gibi görseldeki diğer özelliklerle birlikte çalışır.</span><span class="sxs-lookup"><span data-stu-id="dc6de-104">Indexed properties work together with other features in Visual C#, such as [named and optional arguments](../classes-and-structs/named-and-optional-arguments.md), a new type ([dynamic](../../language-reference/builtin-types/reference-types.md)), and [embedded type information](../../../standard/assembly/embed-types-visual-studio.md), to enhance Microsoft Office programming.</span></span>  
  
 <span data-ttu-id="dc6de-105">Önceki sürümlerinde C#, yöntemler yalnızca `get` yönteminin parametresi yoksa ve `set` yöntemi bir ve yalnızca bir değer parametresi içeriyorsa özellikler olarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="dc6de-105">In earlier versions of C#, methods are accessible as properties only if the `get` method has no parameters and the `set` method has one and only one value parameter.</span></span> <span data-ttu-id="dc6de-106">Ancak, tüm COM özellikleri bu kısıtlamaları karşılamıyor.</span><span class="sxs-lookup"><span data-stu-id="dc6de-106">However, not all COM properties meet those restrictions.</span></span> <span data-ttu-id="dc6de-107">Örneğin, Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> özelliğinin, Aralık adı için bir parametre gerektiren bir `get` erişimcisi vardır.</span><span class="sxs-lookup"><span data-stu-id="dc6de-107">For example, the Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> property has a `get` accessor that requires a parameter for the name of the range.</span></span> <span data-ttu-id="dc6de-108">Geçmişte, `Range` özelliğine doğrudan erişemediği için, aşağıdaki örnekte gösterildiği gibi, bunun yerine `get_Range` yöntemini kullanmanız gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="dc6de-108">In the past, because you could not access the `Range` property directly, you had to use the `get_Range` method instead, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#1)]  
  
 <span data-ttu-id="dc6de-109">Dizini oluşturulmuş Özellikler bunun yerine aşağıdakini yazmanızı sağlar:</span><span class="sxs-lookup"><span data-stu-id="dc6de-109">Indexed properties enable you to write the following instead:</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#2)]  
  
> [!NOTE]
> <span data-ttu-id="dc6de-110">Önceki örnek ayrıca, `Type.Missing`atlamanızı sağlayan [isteğe bağlı bağımsız değişkenler](../classes-and-structs/named-and-optional-arguments.md) özelliğini de kullanır.</span><span class="sxs-lookup"><span data-stu-id="dc6de-110">The previous example also uses the [optional arguments](../classes-and-structs/named-and-optional-arguments.md) feature, which enables you to omit `Type.Missing`.</span></span>  
  
 <span data-ttu-id="dc6de-111">Benzer şekilde, C# 3,0 ve önceki sürümlerde bir <xref:Microsoft.Office.Interop.Excel.Range> nesnesinin `Value` özelliğinin değerini ayarlamak için iki bağımsız değişken gereklidir.</span><span class="sxs-lookup"><span data-stu-id="dc6de-111">Similarly to set the value of the `Value` property of a <xref:Microsoft.Office.Interop.Excel.Range> object in C# 3.0 and earlier, two arguments are required.</span></span> <span data-ttu-id="dc6de-112">Bir, Aralık değerinin türünü belirten isteğe bağlı bir parametre için bağımsız değişken sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc6de-112">One supplies an argument for an optional parameter that specifies the type of the range value.</span></span> <span data-ttu-id="dc6de-113">Diğeri `Value` özelliği için değer sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc6de-113">The other supplies the value for the `Value` property.</span></span> <span data-ttu-id="dc6de-114">Aşağıdaki örneklerde bu teknikler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="dc6de-114">The following examples illustrate these techniques.</span></span> <span data-ttu-id="dc6de-115">Her ikisi de a1 hücresinin değerini `Name`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="dc6de-115">Both set the value of the A1 cell to `Name`.</span></span>
  
 [!code-csharp[csProgGuideIndexedProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#3)]  
  
 <span data-ttu-id="dc6de-116">Dizini oluşturulmuş Özellikler bunun yerine aşağıdaki kodu yazmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc6de-116">Indexed properties enable you to write the following code instead.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#4)]  
  
 <span data-ttu-id="dc6de-117">Kendinizinkini dizinli Özellikler oluşturamazsınız.</span><span class="sxs-lookup"><span data-stu-id="dc6de-117">You cannot create indexed properties of your own.</span></span> <span data-ttu-id="dc6de-118">Özelliği yalnızca var olan dizinli özelliklerin kullanımını destekler.</span><span class="sxs-lookup"><span data-stu-id="dc6de-118">The feature only supports consumption of existing indexed properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc6de-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="dc6de-119">Example</span></span>  
 <span data-ttu-id="dc6de-120">Aşağıdaki kod, bir örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="dc6de-120">The following code shows a complete example.</span></span> <span data-ttu-id="dc6de-121">Office API 'sine erişen bir projeyi ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: Visual C# özelliklerini kullanarak Office birlikte çalışma nesnelerine erişme](./how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="dc6de-121">For more information about how to set up a project that accesses the Office API, see [How to: Access Office Interop Objects by Using Visual C# Features](./how-to-access-office-onterop-objects.md).</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="dc6de-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc6de-122">See also</span></span>

- [<span data-ttu-id="dc6de-123">Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="dc6de-123">Named and Optional Arguments</span></span>](../classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="dc6de-124">dynamic</span><span class="sxs-lookup"><span data-stu-id="dc6de-124">dynamic</span></span>](../../language-reference/builtin-types/reference-types.md)
- [<span data-ttu-id="dc6de-125">Tür dinamiği kullanma</span><span class="sxs-lookup"><span data-stu-id="dc6de-125">Using Type dynamic</span></span>](../types/using-type-dynamic.md)
- [<span data-ttu-id="dc6de-126">Nasıl yapılır: Office Programlamada Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="dc6de-126">How to: Use Named and Optional Arguments in Office Programming</span></span>](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [<span data-ttu-id="dc6de-127">Nasıl yapılır: Visual C# Özelliklerini Kullanarak Office Birlikte Çalışma Nesnelerine Erişim</span><span class="sxs-lookup"><span data-stu-id="dc6de-127">How to: Access Office Interop Objects by Using Visual C# Features</span></span>](./how-to-access-office-onterop-objects.md)
- [<span data-ttu-id="dc6de-128">İzlenecek yol: Office programlama</span><span class="sxs-lookup"><span data-stu-id="dc6de-128">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)
