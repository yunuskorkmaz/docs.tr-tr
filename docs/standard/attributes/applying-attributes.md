---
title: Öznitelikleri Uygulama
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], attributes
- attributes [.NET Framework], applying
ms.assetid: dd7604eb-9fa3-4b60-b2dd-b47739fa3148
ms.openlocfilehash: 76591de6a4305b21b89d348f9ffe53f4e67e7334
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162836"
---
# <a name="apply-attributes"></a><span data-ttu-id="1a58b-102">Öznitelikleri uygulama</span><span class="sxs-lookup"><span data-stu-id="1a58b-102">Apply attributes</span></span>

<span data-ttu-id="1a58b-103">Kodunuzdaki bir öğeye bir öznitelik uygulamak için aşağıdaki işlemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="1a58b-103">Use the following process to apply an attribute to an element of your code.</span></span>

1. <span data-ttu-id="1a58b-104">Yeni bir öznitelik tanımlayın veya var olan bir .NET özniteliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="1a58b-104">Define a new attribute or use an existing .NET attribute.</span></span>

2. <span data-ttu-id="1a58b-105">Özniteliği öğenin hemen önüne ekleyerek kod öğesine uygulayın.</span><span class="sxs-lookup"><span data-stu-id="1a58b-105">Apply the attribute to the code element by placing it immediately before the element.</span></span>

     <span data-ttu-id="1a58b-106">Her dilin kendi öznitelik sözdizimi bulunur.</span><span class="sxs-lookup"><span data-stu-id="1a58b-106">Each language has its own attribute syntax.</span></span> <span data-ttu-id="1a58b-107">C++ ve C#'de öznitelik, köşeli ayraç içine alınır ve öğeden, satır sonu da içerebilen boşluk ile ayrılır.</span><span class="sxs-lookup"><span data-stu-id="1a58b-107">In C++ and C#, the attribute is surrounded by square brackets and separated from the element by white space, which can include a line break.</span></span> <span data-ttu-id="1a58b-108">Visual Basic'te öznitelik, açılı ayraç içine alınır ve aynı mantıksal satırda bulunması gerekir; eğer bir satır sonu isterseniz satır devamı karakteri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a58b-108">In Visual Basic, the attribute is surrounded by angle brackets and must be on the same logical line; the line continuation character can be used if a line break is desired.</span></span>

3. <span data-ttu-id="1a58b-109">Öznitelik için konumsal parametreleri ve adlandırılmış parametreleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="1a58b-109">Specify positional parameters and named parameters for the attribute.</span></span>

     <span data-ttu-id="1a58b-110">*Konumsal* Parametreler gereklidir ve adlandırılmış parametrelerden önce gelmelidir; öznitelik oluşturucularından birinin parametrelerine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="1a58b-110">*Positional* parameters are required and must come before any named parameters; they correspond to the parameters of one of the attribute's constructors.</span></span> <span data-ttu-id="1a58b-111">*Adlandırılmış* parametreler isteğe bağlıdır ve özniteliğin okuma/yazma özelliklerine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="1a58b-111">*Named* parameters are optional and correspond to read/write properties of the attribute.</span></span> <span data-ttu-id="1a58b-112">C++ ve C# ' de, `name=value` her bir isteğe bağlı parametre için belirtin; burada `name` özelliğin adıdır.</span><span class="sxs-lookup"><span data-stu-id="1a58b-112">In C++, and C#, specify `name=value` for each optional parameter, where `name` is the name of the property.</span></span> <span data-ttu-id="1a58b-113">Visual Basic ' de, belirtin `name:=value` .</span><span class="sxs-lookup"><span data-stu-id="1a58b-113">In Visual Basic, specify `name:=value`.</span></span>

 <span data-ttu-id="1a58b-114">Kodunuzu derlediğinizde öznitelik meta verilere yayılır ve çalışma zamanı yansıma hizmetleri ile ortak dil çalışma zamanı ve herhangi bir özel araç veya uygulama tarafından kullanılabilir olur.</span><span class="sxs-lookup"><span data-stu-id="1a58b-114">The attribute is emitted into metadata when you compile your code and is available to the common language runtime and any custom tool or application through the runtime reflection services.</span></span>

 <span data-ttu-id="1a58b-115">Kurala göre, tüm öznitelik adları "Attribute" ile biter.</span><span class="sxs-lookup"><span data-stu-id="1a58b-115">By convention, all attribute names end with "Attribute".</span></span> <span data-ttu-id="1a58b-116">Ancak, Visual Basic ve C# gibi çalışma zamanını hedef alan çeşitli diller, bir özniteliğin tam adını belirtmenizi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="1a58b-116">However, several languages that target the runtime, such as Visual Basic and C#, do not require you to specify the full name of an attribute.</span></span> <span data-ttu-id="1a58b-117">Örneğin, başlatmak istiyorsanız <xref:System.ObsoleteAttribute?displayProperty=nameWithType> , yalnızca **eski**olarak başvurulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1a58b-117">For example, if you want to initialize <xref:System.ObsoleteAttribute?displayProperty=nameWithType>, you only need to reference it as **Obsolete**.</span></span>

## <a name="apply-an-attribute-to-a-method"></a><span data-ttu-id="1a58b-118">Bir yönteme öznitelik uygulama</span><span class="sxs-lookup"><span data-stu-id="1a58b-118">Apply an attribute to a method</span></span>

 <span data-ttu-id="1a58b-119">Aşağıdaki kod örneği, kodu eski olarak işaretleyen **System. Kullanımdan kaldırılmış Teattribute**'un nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="1a58b-119">The following code example shows how to use **System.ObsoleteAttribute**, which marks code as obsolete.</span></span> <span data-ttu-id="1a58b-120">`"Will be removed in next version"` dizesi özniteliğe geçirilir.</span><span class="sxs-lookup"><span data-stu-id="1a58b-120">The string `"Will be removed in next version"` is passed to the attribute.</span></span> <span data-ttu-id="1a58b-121">Bu öznitelik, özniteliğin açıkladığı kod çağırıldığında geçirilen dizeyi görüntüleyen bir derleyici uyarısına neden olur.</span><span class="sxs-lookup"><span data-stu-id="1a58b-121">This attribute causes a compiler warning that displays the passed string when code that the attribute describes is called.</span></span>

 [!code-cpp[Conceptual.Attributes.Usage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#3)]
 [!code-csharp[Conceptual.Attributes.Usage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#3)]
 [!code-vb[Conceptual.Attributes.Usage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#3)]

## <a name="apply-attributes-at-the-assembly-level"></a><span data-ttu-id="1a58b-122">Öznitelikleri derleme düzeyinde Uygula</span><span class="sxs-lookup"><span data-stu-id="1a58b-122">Apply attributes at the assembly level</span></span>

 <span data-ttu-id="1a58b-123">Derleme düzeyinde bir öznitelik uygulamak istiyorsanız, `assembly` ( `Assembly` Visual Basic) anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="1a58b-123">If you want to apply an attribute at the assembly level, use the `assembly` (`Assembly` in Visual Basic) keyword.</span></span> <span data-ttu-id="1a58b-124">Aşağıdaki kod, derleme düzeyinde uygulanan **Assemblytitleözniteliğini** gösterir.</span><span class="sxs-lookup"><span data-stu-id="1a58b-124">The following code shows the **AssemblyTitleAttribute** applied at the assembly level.</span></span>

 [!code-cpp[Conceptual.Attributes.Usage#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#2)]
 [!code-csharp[Conceptual.Attributes.Usage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#2)]
 [!code-vb[Conceptual.Attributes.Usage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#2)]

 <span data-ttu-id="1a58b-125">Bu öznitelik uygulandığında `"My Assembly"` dizesi, dosyanın meta veri bölümündeki derleme bildirimine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1a58b-125">When this attribute is applied, the string `"My Assembly"` is placed in the assembly manifest in the metadata portion of the file.</span></span> <span data-ttu-id="1a58b-126">Özniteliği, [MSIL Disassembler (Ildasm.exe)](../../framework/tools/ildasm-exe-il-disassembler.md) kullanarak ya da özniteliği almak için özel bir program oluşturarak görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a58b-126">You can view the attribute either by using the [MSIL Disassembler (Ildasm.exe)](../../framework/tools/ildasm-exe-il-disassembler.md) or by creating a custom program to retrieve the attribute.</span></span>

## <a name="see-also"></a><span data-ttu-id="1a58b-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a58b-127">See also</span></span>

- [<span data-ttu-id="1a58b-128">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1a58b-128">Attributes</span></span>](index.md)
- [<span data-ttu-id="1a58b-129">Özniteliklerde Depolanan Bilgileri Alma</span><span class="sxs-lookup"><span data-stu-id="1a58b-129">Retrieving Information Stored in Attributes</span></span>](retrieving-information-stored-in-attributes.md)
- [<span data-ttu-id="1a58b-130">Kavramlar</span><span class="sxs-lookup"><span data-stu-id="1a58b-130">Concepts</span></span>](/cpp/windows/attributed-programming-concepts)
- [<span data-ttu-id="1a58b-131">Öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="1a58b-131">Attributes (C#)</span></span>](../../csharp/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="1a58b-132">Özniteliklere genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1a58b-132">Attributes overview (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/attributes/index.md)
