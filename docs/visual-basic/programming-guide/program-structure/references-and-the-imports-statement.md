---
title: References ve Imports Deyimi (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 739934b65241a7846b5323d5e75446832d83e5d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="references-and-the-imports-statement-visual-basic"></a><span data-ttu-id="7c2eb-102">References ve Imports Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c2eb-102">References and the Imports Statement (Visual Basic)</span></span>
<span data-ttu-id="7c2eb-103">Dış nesneleri kullanılabilir projenize seçerek yapabileceğiniz **Başvuru Ekle** komutunu **proje** menüsü.</span><span class="sxs-lookup"><span data-stu-id="7c2eb-103">You can make external objects available to your project by choosing the **Add Reference** command on the **Project** menu.</span></span> <span data-ttu-id="7c2eb-104">Başvurur [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] tür kitaplıklarının ancak daha fazla bilgi içeriyor gibi olan derlemeler için işaret edebilir.</span><span class="sxs-lookup"><span data-stu-id="7c2eb-104">References in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] can point to assemblies, which are like type libraries but contain more information.</span></span>  
  
## <a name="the-imports-statement"></a><span data-ttu-id="7c2eb-105">Imports deyimi</span><span class="sxs-lookup"><span data-stu-id="7c2eb-105">The Imports Statement</span></span>  
 <span data-ttu-id="7c2eb-106">Derlemeler, bir veya daha fazla ad içerir.</span><span class="sxs-lookup"><span data-stu-id="7c2eb-106">Assemblies include one or more namespaces.</span></span> <span data-ttu-id="7c2eb-107">Bir derleme başvurusu eklediğinizde, bu da ekleyebilirsiniz bir `Imports` o derlemenin ad alanları modülü içinde görünürlüğünü denetleyen bir modüle deyimi.</span><span class="sxs-lookup"><span data-stu-id="7c2eb-107">When you add a reference to an assembly, you can also add an `Imports` statement to a module that controls the visibility of that assembly's namespaces within the module.</span></span> <span data-ttu-id="7c2eb-108">`Imports` Deyimi yalnızca benzersiz bir başvuruyu sağlamak gerekli ad alanı bölümünü kullanmanıza olanak sağlayan bir kapsam bağlamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="7c2eb-108">The `Imports` statement provides a scoping context that lets you use only the portion of the namespace necessary to supply a unique reference.</span></span>  
  
 <span data-ttu-id="7c2eb-109">`Imports` Deyiminin aşağıdaki söz dizimini şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7c2eb-109">The `Imports` statement has the following syntax:</span></span>  
  
 <span data-ttu-id="7c2eb-110">`Imports` [`|``Aliasname` =] `Namespace`</span><span class="sxs-lookup"><span data-stu-id="7c2eb-110">`Imports` [`|``Aliasname` =] `Namespace`</span></span>  
  
 <span data-ttu-id="7c2eb-111">`Aliasname`kod içinde içeri aktarılan ad alanına başvurmak için kullanabileceğiniz kısa bir ad belirtir.</span><span class="sxs-lookup"><span data-stu-id="7c2eb-111">`Aliasname` refers to a short name you can use within code to refer to an imported namespace.</span></span> <span data-ttu-id="7c2eb-112">`Namespace`proje başvurusu tanımı projesi içinde veya önceki bir ad alanı aracılığıyla kullanılabilir olan `Imports` deyimi.</span><span class="sxs-lookup"><span data-stu-id="7c2eb-112">`Namespace` is a namespace available through either a project reference, through a definition within the project, or through a previous `Imports` statement.</span></span>  
  
 <span data-ttu-id="7c2eb-113">Bir modül herhangi bir sayıda içerebilir `Imports` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="7c2eb-113">A module may contain any number of `Imports` statements.</span></span> <span data-ttu-id="7c2eb-114">Herhangi bir sonra görünmelidir `Option` deyimleri, varsa, ancak başka bir kod önce.</span><span class="sxs-lookup"><span data-stu-id="7c2eb-114">They must appear after any `Option` statements, if present, but before any other code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c2eb-115">Proje başvuruları ile karıştırmayın `Imports` deyimi veya `Declare` deyimi.</span><span class="sxs-lookup"><span data-stu-id="7c2eb-115">Do not confuse project references with the `Imports` statement or the `Declare` statement.</span></span> <span data-ttu-id="7c2eb-116">Proje başvuruları derlemeler, nesneleri gibi dış nesneler için kullanılabilir duruma [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] projeleri.</span><span class="sxs-lookup"><span data-stu-id="7c2eb-116">Project references make external objects, such as objects in assemblies, available to [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] projects.</span></span> <span data-ttu-id="7c2eb-117">`Imports` Deyimi proje başvuruları erişimi kolaylaştırmak için kullanılır, ancak bu nesnelere erişimi sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="7c2eb-117">The `Imports` statement is used to simplify access to project references, but does not provide access to these objects.</span></span> <span data-ttu-id="7c2eb-118">`Declare` Deyimi, bir dinamik bağlantı kitaplığı (DLL) dış bir yordamda başvuru bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7c2eb-118">The `Declare` statement is used to declare a reference to an external procedure in a dynamic-link library (DLL).</span></span>  
  
## <a name="using-aliases-with-the-imports-statement"></a><span data-ttu-id="7c2eb-119">Imports deyimi ile diğer adlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="7c2eb-119">Using Aliases with the Imports Statement</span></span>  
 <span data-ttu-id="7c2eb-120">`Imports` Deyimi kolaylaştırır erişim yöntemlerine sınıfların açıkça tam olarak nitelenmiş adlar başvuruları yazma gereğini ortadan kaldırarak.</span><span class="sxs-lookup"><span data-stu-id="7c2eb-120">The `Imports` statement makes it easier to access methods of classes by eliminating the need to explicitly type the fully qualified names of references.</span></span> <span data-ttu-id="7c2eb-121">Diğer adlar, bir ad alanının yalnızca bir parçası yaşamanızı bir ad atamak olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="7c2eb-121">Aliases let you assign a friendlier name to just one part of a namespace.</span></span> <span data-ttu-id="7c2eb-122">Örneğin, satır başı/tek bir birden çok satırda görüntülenecek metni neden dizisi satır besleme parçası olan <xref:Microsoft.VisualBasic.ControlChars> modülünde <xref:Microsoft.VisualBasic?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="7c2eb-122">For example, the carriage return/line feed sequence that causes a single piece of text to be displayed on multiple lines is part of the <xref:Microsoft.VisualBasic.ControlChars> module in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="7c2eb-123">Bu sabit bir diğer ad olmadan bir programda kullanmak için aşağıdaki kod yazmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="7c2eb-123">To use this constant in a program without an alias, you would need to type the following code:</span></span>  
  
 [!code-vb[VbVbalrApplication#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]  
  
 <span data-ttu-id="7c2eb-124">`Imports`deyimleri her zaman hemen herhangi aşağıdaki ilk satırı olmalıdır `Option` bir modül deyimlerinde.</span><span class="sxs-lookup"><span data-stu-id="7c2eb-124">`Imports` statements must always be the first lines immediately following any `Option` statements in a module.</span></span> <span data-ttu-id="7c2eb-125">Aşağıdaki kod parçası, almak ve bir diğer ad atamak gösterilmiştir <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> Modülü:</span><span class="sxs-lookup"><span data-stu-id="7c2eb-125">The following code fragment shows how to import and assign an alias to the <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> module:</span></span>  
  
 [!code-vb[VbVbalrApplication#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]  
  
 <span data-ttu-id="7c2eb-126">Bu ad alanına gelecek başvuruları önemli ölçüde daha kısa olabilir:</span><span class="sxs-lookup"><span data-stu-id="7c2eb-126">Future references to this namespace can be considerably shorter:</span></span>  
  
 [!code-vb[VbVbalrApplication#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]  
  
 <span data-ttu-id="7c2eb-127">Varsa bir `Imports` deyimi bir diğer ad içermez, içeri aktarılan ad alanında tanımlanan öğe niteliğe olmadan modül kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7c2eb-127">If an `Imports` statement does not include an alias name, elements defined within the imported namespace can be used in the module without qualification.</span></span> <span data-ttu-id="7c2eb-128">Diğer ad belirtilmezse, bir niteleyici olarak ad alanında yer alan adları için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7c2eb-128">If the alias name is specified, it must be used as a qualifier for names contained within that namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c2eb-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7c2eb-129">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ControlChars>  
 <xref:Microsoft.VisualBasic>  
 [<span data-ttu-id="7c2eb-130">NIB nasıl yapılır: başvuru ekleme veya kaldırma Başvuru Ekle iletişim kutusunu kullanarak</span><span class="sxs-lookup"><span data-stu-id="7c2eb-130">NIB How to: Add or Remove References By Using the Add Reference Dialog Box</span></span>](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)  
 [<span data-ttu-id="7c2eb-131">Visual Basic'de ad alanları</span><span class="sxs-lookup"><span data-stu-id="7c2eb-131">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="7c2eb-132">Derlemeler ve Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="7c2eb-132">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="7c2eb-133">Nasıl yapılır: komut satırını kullanarak derlemeler oluşturma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="7c2eb-133">How to: Create and Use Assemblies Using the Command Line</span></span>](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)  
 [<span data-ttu-id="7c2eb-134">Imports deyimi (.NET Namespace ve türü)</span><span class="sxs-lookup"><span data-stu-id="7c2eb-134">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
