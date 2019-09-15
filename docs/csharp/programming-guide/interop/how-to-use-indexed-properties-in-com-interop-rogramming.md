---
title: 'Nasıl yapılır: COM birlikte çalışma programlama- C# programlama kılavuzunda dizinli özellikleri kullanma'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: f1be14ad7ddb6973cc89f10c1735ba2ebce13f97
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971657"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a><span data-ttu-id="13a52-102">Nasıl yapılır: COM birlikte çalışma programlamada dizinli özellikleri kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="13a52-102">How to: Use Indexed Properties in COM Interop Programming (C# Programming Guide)</span></span>
<span data-ttu-id="13a52-103">*Dizinli Özellikler* , programlama içinde C# parametreleri olan com özelliklerinin hangi şekilde tüketildiğini geliştirir.</span><span class="sxs-lookup"><span data-stu-id="13a52-103">*Indexed properties* improve the way in which COM properties that have parameters are consumed in C# programming.</span></span> <span data-ttu-id="13a52-104">Dizinli Özellikler C#, Microsoft Office programlamayı geliştirmek için [adlandırılmış ve isteğe bağlı bağımsız değişkenler](../classes-and-structs/named-and-optional-arguments.md), yeni bir tür ([dinamik](../../language-reference/keywords/dynamic.md)) ve [katıştırılmış tür bilgileri](../../../standard/assembly/embed-types-visual-studio.md)gibi görseldeki diğer özelliklerle birlikte çalışır.</span><span class="sxs-lookup"><span data-stu-id="13a52-104">Indexed properties work together with other features in Visual C#, such as [named and optional arguments](../classes-and-structs/named-and-optional-arguments.md), a new type ([dynamic](../../language-reference/keywords/dynamic.md)), and [embedded type information](../../../standard/assembly/embed-types-visual-studio.md), to enhance Microsoft Office programming.</span></span>  
  
 <span data-ttu-id="13a52-105">Önceki sürümlerinde C#yöntemlere yalnızca `get` yöntemin parametresi `set` yoksa ve yöntemi bir ve yalnızca bir değer parametresi varsa özellikler olarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="13a52-105">In earlier versions of C#, methods are accessible as properties only if the `get` method has no parameters and the `set` method has one and only one value parameter.</span></span> <span data-ttu-id="13a52-106">Ancak, tüm COM özellikleri bu kısıtlamaları karşılamıyor.</span><span class="sxs-lookup"><span data-stu-id="13a52-106">However, not all COM properties meet those restrictions.</span></span> <span data-ttu-id="13a52-107">Örneğin, Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> özelliğinin, Aralık adı için `get` bir parametre gerektiren bir erişimcisi vardır.</span><span class="sxs-lookup"><span data-stu-id="13a52-107">For example, the Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> property has a `get` accessor that requires a parameter for the name of the range.</span></span> <span data-ttu-id="13a52-108">Geçmişte, `Range` özelliği doğrudan erişemediği için, aşağıdaki örnekte gösterildiği gibi `get_Range` yöntemini kullanmanız gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="13a52-108">In the past, because you could not access the `Range` property directly, you had to use the `get_Range` method instead, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#1)]  
  
 <span data-ttu-id="13a52-109">Dizini oluşturulmuş Özellikler bunun yerine aşağıdakini yazmanızı sağlar:</span><span class="sxs-lookup"><span data-stu-id="13a52-109">Indexed properties enable you to write the following instead:</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#2)]  
  
> [!NOTE]
> <span data-ttu-id="13a52-110">Önceki örnek ayrıca, öğesini atlamanızı `Type.Missing`sağlayan [isteğe bağlı bağımsız değişkenler](../classes-and-structs/named-and-optional-arguments.md) özelliğini de kullanır.</span><span class="sxs-lookup"><span data-stu-id="13a52-110">The previous example also uses the [optional arguments](../classes-and-structs/named-and-optional-arguments.md) feature, which enables you to omit `Type.Missing`.</span></span>  
  
 <span data-ttu-id="13a52-111">Benzer şekilde, `Value` C# 3,0 ve önceki bir <xref:Microsoft.Office.Interop.Excel.Range> nesnenin özelliğinin değerini ayarlamak için iki bağımsız değişken gereklidir.</span><span class="sxs-lookup"><span data-stu-id="13a52-111">Similarly to set the value of the `Value` property of a <xref:Microsoft.Office.Interop.Excel.Range> object in C# 3.0 and earlier, two arguments are required.</span></span> <span data-ttu-id="13a52-112">Bir, Aralık değerinin türünü belirten isteğe bağlı bir parametre için bağımsız değişken sağlar.</span><span class="sxs-lookup"><span data-stu-id="13a52-112">One supplies an argument for an optional parameter that specifies the type of the range value.</span></span> <span data-ttu-id="13a52-113">Diğer, `Value` özelliğinin değerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="13a52-113">The other supplies the value for the `Value` property.</span></span> <span data-ttu-id="13a52-114">Aşağıdaki örneklerde bu teknikler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="13a52-114">The following examples illustrate these techniques.</span></span> <span data-ttu-id="13a52-115">Her ikisi de a1 hücresinin değerini olarak `Name`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="13a52-115">Both set the value of the A1 cell to `Name`.</span></span>
  
 [!code-csharp[csProgGuideIndexedProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#3)]  
  
 <span data-ttu-id="13a52-116">Dizini oluşturulmuş Özellikler bunun yerine aşağıdaki kodu yazmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="13a52-116">Indexed properties enable you to write the following code instead.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#4)]  
  
 <span data-ttu-id="13a52-117">Kendinizinkini dizinli Özellikler oluşturamazsınız.</span><span class="sxs-lookup"><span data-stu-id="13a52-117">You cannot create indexed properties of your own.</span></span> <span data-ttu-id="13a52-118">Özelliği yalnızca var olan dizinli özelliklerin kullanımını destekler.</span><span class="sxs-lookup"><span data-stu-id="13a52-118">The feature only supports consumption of existing indexed properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13a52-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="13a52-119">Example</span></span>  
 <span data-ttu-id="13a52-120">Aşağıdaki kod, bir örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="13a52-120">The following code shows a complete example.</span></span> <span data-ttu-id="13a52-121">Office API 'sine erişen bir projeyi ayarlama hakkında daha fazla bilgi için bkz [. nasıl yapılır: Visual C# özelliklerini](./how-to-access-office-onterop-objects.md)kullanarak Office birlikte çalışma nesnelerine erişin.</span><span class="sxs-lookup"><span data-stu-id="13a52-121">For more information about how to set up a project that accesses the Office API, see [How to: Access Office Interop Objects by Using Visual C# Features](./how-to-access-office-onterop-objects.md).</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="13a52-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13a52-122">See also</span></span>

- [<span data-ttu-id="13a52-123">Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="13a52-123">Named and Optional Arguments</span></span>](../classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="13a52-124">dynamic</span><span class="sxs-lookup"><span data-stu-id="13a52-124">dynamic</span></span>](../../language-reference/keywords/dynamic.md)
- [<span data-ttu-id="13a52-125">Tür dinamiği kullanma</span><span class="sxs-lookup"><span data-stu-id="13a52-125">Using Type dynamic</span></span>](../types/using-type-dynamic.md)
- [<span data-ttu-id="13a52-126">Nasıl yapılır: Office Programlamada adlandırılmış ve Isteğe bağlı bağımsız değişkenleri kullanma</span><span class="sxs-lookup"><span data-stu-id="13a52-126">How to: Use Named and Optional Arguments in Office Programming</span></span>](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [<span data-ttu-id="13a52-127">Nasıl yapılır: Visual C# özelliklerini kullanarak Office birlikte çalışma nesnelerine erişin</span><span class="sxs-lookup"><span data-stu-id="13a52-127">How to: Access Office Interop Objects by Using Visual C# Features</span></span>](./how-to-access-office-onterop-objects.md)
- [<span data-ttu-id="13a52-128">İzlenecek yol: Office programlama</span><span class="sxs-lookup"><span data-stu-id="13a52-128">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)
