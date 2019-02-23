---
title: References ve Imports Deyimi (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
ms.openlocfilehash: d9a227f60edf142832ab41e3ea99f33c53a42229
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748316"
---
# <a name="references-and-the-imports-statement-visual-basic"></a><span data-ttu-id="eb6d4-102">References ve Imports Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb6d4-102">References and the Imports Statement (Visual Basic)</span></span>
<span data-ttu-id="eb6d4-103">Dış nesneler kullanılabilir projenize seçerek yapabileceğiniz **Başvuru Ekle** komutunu **proje** menüsü.</span><span class="sxs-lookup"><span data-stu-id="eb6d4-103">You can make external objects available to your project by choosing the **Add Reference** command on the **Project** menu.</span></span> <span data-ttu-id="eb6d4-104">Başvuruları Visual Basic'te tür kitaplıkları, ancak daha fazla bilgi içeren gibi olan derlemeler için işaret edebilir.</span><span class="sxs-lookup"><span data-stu-id="eb6d4-104">References in Visual Basic can point to assemblies, which are like type libraries but contain more information.</span></span>  
  
## <a name="the-imports-statement"></a><span data-ttu-id="eb6d4-105">Imports deyimi</span><span class="sxs-lookup"><span data-stu-id="eb6d4-105">The Imports Statement</span></span>  
 <span data-ttu-id="eb6d4-106">Derlemeler, bir veya daha fazla ad alanı içerir.</span><span class="sxs-lookup"><span data-stu-id="eb6d4-106">Assemblies include one or more namespaces.</span></span> <span data-ttu-id="eb6d4-107">Bir derlemeye bir başvuru eklediğinizde, bu da ekleyebilirsiniz bir `Imports` o derlemenin ad alanları modülü içinde görünürlüğünü denetleyen bir modüle deyimi.</span><span class="sxs-lookup"><span data-stu-id="eb6d4-107">When you add a reference to an assembly, you can also add an `Imports` statement to a module that controls the visibility of that assembly's namespaces within the module.</span></span> <span data-ttu-id="eb6d4-108">`Imports` Deyimi yalnızca bir benzersiz başvuru sağlamanız için gereken ad alanının bölümü kullanmanıza olanak sağlayan bir kapsam bağlamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="eb6d4-108">The `Imports` statement provides a scoping context that lets you use only the portion of the namespace necessary to supply a unique reference.</span></span>  
  
 <span data-ttu-id="eb6d4-109">`Imports` Deyimi sözdizimine sahiptir:</span><span class="sxs-lookup"><span data-stu-id="eb6d4-109">The `Imports` statement has the following syntax:</span></span>  
  
 `Imports [Aliasname =] Namespace`  
  
 <span data-ttu-id="eb6d4-110">`Aliasname` kod içinde bir içeri aktarılan ad alanına başvurmak için kullanabileceğiniz bir kısa ad belirtir.</span><span class="sxs-lookup"><span data-stu-id="eb6d4-110">`Aliasname` refers to a short name you can use within code to refer to an imported namespace.</span></span> <span data-ttu-id="eb6d4-111">`Namespace` Proje içinde bir tanımı veya önceki bir proje başvurusu bir ad alanı aracılığıyla kullanılabilir olan `Imports` deyimi.</span><span class="sxs-lookup"><span data-stu-id="eb6d4-111">`Namespace` is a namespace available through either a project reference, through a definition within the project, or through a previous `Imports` statement.</span></span>  
  
 <span data-ttu-id="eb6d4-112">Bir modülün herhangi bir sayıda içerebilir `Imports` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="eb6d4-112">A module may contain any number of `Imports` statements.</span></span> <span data-ttu-id="eb6d4-113">Herhangi bir sonra görünmelidir `Option` deyimleri, varsa, ancak herhangi bir kod önce.</span><span class="sxs-lookup"><span data-stu-id="eb6d4-113">They must appear after any `Option` statements, if present, but before any other code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eb6d4-114">Proje başvuruları ile karıştırmayın `Imports` deyimi veya `Declare` deyimi.</span><span class="sxs-lookup"><span data-stu-id="eb6d4-114">Do not confuse project references with the `Imports` statement or the `Declare` statement.</span></span> <span data-ttu-id="eb6d4-115">Proje başvuruları, derlemelere nesneleri gibi dış nesneleri Visual Basic projeleri kullanılabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="eb6d4-115">Project references make external objects, such as objects in assemblies, available to Visual Basic projects.</span></span> <span data-ttu-id="eb6d4-116">`Imports` Deyimi proje başvuruları erişimini basitleştirmek için kullanılır, ancak bu nesnelere erişimi sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="eb6d4-116">The `Imports` statement is used to simplify access to project references, but does not provide access to these objects.</span></span> <span data-ttu-id="eb6d4-117">`Declare` Deyimi bir dış yordam bir dinamik bağlantı kitaplığı (DLL) içinde bir başvuru bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eb6d4-117">The `Declare` statement is used to declare a reference to an external procedure in a dynamic-link library (DLL).</span></span>  
  
## <a name="using-aliases-with-the-imports-statement"></a><span data-ttu-id="eb6d4-118">Imports deyimi ile diğer adların kullanımı</span><span class="sxs-lookup"><span data-stu-id="eb6d4-118">Using Aliases with the Imports Statement</span></span>  
 <span data-ttu-id="eb6d4-119">`Imports` Deyimi kolaylaştırır, sınıfların erişim yöntemlerine açıkça tam olarak nitelenmiş adlar başvuru türüne gereksinimini ortadan kaldırarak.</span><span class="sxs-lookup"><span data-stu-id="eb6d4-119">The `Imports` statement makes it easier to access methods of classes by eliminating the need to explicitly type the fully qualified names of references.</span></span> <span data-ttu-id="eb6d4-120">Diğer adlar, daha kolay adı bir ad alanının yalnızca bir bölümü atamak sağlar.</span><span class="sxs-lookup"><span data-stu-id="eb6d4-120">Aliases let you assign a friendlier name to just one part of a namespace.</span></span> <span data-ttu-id="eb6d4-121">Örneğin, satır başı/birden çok satırda görüntülenecek metni tek bir parçasını neden dizisi satır besleme parçası olan <xref:Microsoft.VisualBasic.ControlChars> modülünde <xref:Microsoft.VisualBasic?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="eb6d4-121">For example, the carriage return/line feed sequence that causes a single piece of text to be displayed on multiple lines is part of the <xref:Microsoft.VisualBasic.ControlChars> module in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="eb6d4-122">Bu sabit bir diğer ad olmadan bir programda kullanmak için aşağıdaki kod yazmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="eb6d4-122">To use this constant in a program without an alias, you would need to type the following code:</span></span>  
  
 [!code-vb[VbVbalrApplication#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]  
  
 <span data-ttu-id="eb6d4-123">`Imports` deyimleri her zaman takip herhangi ilk satırı olmalıdır `Option` Modül içindeki deyimler.</span><span class="sxs-lookup"><span data-stu-id="eb6d4-123">`Imports` statements must always be the first lines immediately following any `Option` statements in a module.</span></span> <span data-ttu-id="eb6d4-124">Aşağıdaki kod parçası, içeri aktarma ve diğer ad atamak gösterilmektedir <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> Modülü:</span><span class="sxs-lookup"><span data-stu-id="eb6d4-124">The following code fragment shows how to import and assign an alias to the <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> module:</span></span>  
  
 [!code-vb[VbVbalrApplication#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]  
  
 <span data-ttu-id="eb6d4-125">Bu ad gelecekte başvurular önemli ölçüde daha kısa olabilir:</span><span class="sxs-lookup"><span data-stu-id="eb6d4-125">Future references to this namespace can be considerably shorter:</span></span>  
  
 [!code-vb[VbVbalrApplication#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]  
  
 <span data-ttu-id="eb6d4-126">Varsa bir `Imports` deyimi bir diğer ad içermez, içeri aktarılan ad alanı içinde tanımlanan öğeler, nitelik olmadan bir modülde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eb6d4-126">If an `Imports` statement does not include an alias name, elements defined within the imported namespace can be used in the module without qualification.</span></span> <span data-ttu-id="eb6d4-127">Diğer ad belirtilmezse, bu Niteleyici olarak bu ad alanı içinde yer alan adları için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="eb6d4-127">If the alias name is specified, it must be used as a qualifier for names contained within that namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb6d4-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb6d4-128">See also</span></span>

- <xref:Microsoft.VisualBasic.ControlChars>
- <xref:Microsoft.VisualBasic>
- [<span data-ttu-id="eb6d4-129">Visual Basic'de ad alanları</span><span class="sxs-lookup"><span data-stu-id="eb6d4-129">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="eb6d4-130">.NET derlemeleri</span><span class="sxs-lookup"><span data-stu-id="eb6d4-130">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="eb6d4-131">Nasıl yapılır: Komut satırını kullanarak derlemeler oluşturma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="eb6d4-131">How to: Create and Use Assemblies Using the Command Line</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)
- [<span data-ttu-id="eb6d4-132">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="eb6d4-132">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
