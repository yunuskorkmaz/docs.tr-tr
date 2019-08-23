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
ms.openlocfilehash: 99afa42994dd09d0b5faaeaf534fbc4b41816998
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962488"
---
# <a name="references-and-the-imports-statement-visual-basic"></a><span data-ttu-id="40427-102">References ve Imports Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40427-102">References and the Imports Statement (Visual Basic)</span></span>
<span data-ttu-id="40427-103">**Proje** menüsünde **Başvuru Ekle** komutunu seçerek dış nesneleri projeniz için kullanılabilir hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40427-103">You can make external objects available to your project by choosing the **Add Reference** command on the **Project** menu.</span></span> <span data-ttu-id="40427-104">Visual Basic başvurular tür kitaplıkları gibi olan ancak daha fazla bilgi içeren derlemelere işaret edebilir.</span><span class="sxs-lookup"><span data-stu-id="40427-104">References in Visual Basic can point to assemblies, which are like type libraries but contain more information.</span></span>  
  
## <a name="the-imports-statement"></a><span data-ttu-id="40427-105">Imports ekstresi</span><span class="sxs-lookup"><span data-stu-id="40427-105">The Imports Statement</span></span>  
 <span data-ttu-id="40427-106">Derlemeler bir veya daha fazla ad alanı içerir.</span><span class="sxs-lookup"><span data-stu-id="40427-106">Assemblies include one or more namespaces.</span></span> <span data-ttu-id="40427-107">Bir derlemeye başvuru eklediğinizde, bu derlemenin modül içindeki ad alanlarının görünürlüğünü denetleyen bir `Imports` modüle de bir ifade ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40427-107">When you add a reference to an assembly, you can also add an `Imports` statement to a module that controls the visibility of that assembly's namespaces within the module.</span></span> <span data-ttu-id="40427-108">Bu `Imports` ifade, benzersiz bir başvuru sağlamak için gereken ad alanının yalnızca bir kısmını kullanmanıza imkan tanıyan bir kapsam bağlamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="40427-108">The `Imports` statement provides a scoping context that lets you use only the portion of the namespace necessary to supply a unique reference.</span></span>  
  
 <span data-ttu-id="40427-109">`Imports` İfadesinin sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="40427-109">The `Imports` statement has the following syntax:</span></span>  
  
 `Imports [Aliasname =] Namespace`  
  
 <span data-ttu-id="40427-110">`Aliasname`İçeri aktarılan bir ad alanına başvurmak için kod içinde kullanabileceğiniz kısa bir ad anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="40427-110">`Aliasname` refers to a short name you can use within code to refer to an imported namespace.</span></span> <span data-ttu-id="40427-111">`Namespace`proje başvurusu aracılığıyla, proje içindeki bir tanım aracılığıyla veya önceki `Imports` bir ifadeyle bulunan bir ad alanıdır.</span><span class="sxs-lookup"><span data-stu-id="40427-111">`Namespace` is a namespace available through either a project reference, through a definition within the project, or through a previous `Imports` statement.</span></span>  
  
 <span data-ttu-id="40427-112">Modül, herhangi bir sayıda `Imports` deyim içerebilir.</span><span class="sxs-lookup"><span data-stu-id="40427-112">A module may contain any number of `Imports` statements.</span></span> <span data-ttu-id="40427-113">Varsa, varsa tüm `Option` deyimlerden sonra, diğer koddan önce gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="40427-113">They must appear after any `Option` statements, if present, but before any other code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40427-114">Proje başvurularını `Imports` deyimle `Declare` veya ifadesiyle karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="40427-114">Do not confuse project references with the `Imports` statement or the `Declare` statement.</span></span> <span data-ttu-id="40427-115">Proje başvuruları, derlemelerdeki nesneler gibi dış nesneleri Visual Basic projeleri için kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="40427-115">Project references make external objects, such as objects in assemblies, available to Visual Basic projects.</span></span> <span data-ttu-id="40427-116">`Imports` İfade, proje başvurularına erişimi basitleştirmek için kullanılır, ancak bu nesnelere erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="40427-116">The `Imports` statement is used to simplify access to project references, but does not provide access to these objects.</span></span> <span data-ttu-id="40427-117">İfade `Declare` , bir dinamik bağlantı kitaplığı (dll) içinde bir dış yordama başvuru bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="40427-117">The `Declare` statement is used to declare a reference to an external procedure in a dynamic-link library (DLL).</span></span>  
  
## <a name="using-aliases-with-the-imports-statement"></a><span data-ttu-id="40427-118">Imports Ifadesiyle diğer adları kullanma</span><span class="sxs-lookup"><span data-stu-id="40427-118">Using Aliases with the Imports Statement</span></span>  
 <span data-ttu-id="40427-119">`Imports` İfade, başvuruların tam adlarını açıkça yazma gereğini ortadan kaldırarak sınıfların yöntemlerine erişmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="40427-119">The `Imports` statement makes it easier to access methods of classes by eliminating the need to explicitly type the fully qualified names of references.</span></span> <span data-ttu-id="40427-120">Diğer adlar, bir ad alanının yalnızca bir kısmına kolay bir ad atamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="40427-120">Aliases let you assign a friendlier name to just one part of a namespace.</span></span> <span data-ttu-id="40427-121">Örneğin, tek bir metin parçasının birden çok satırda görüntülenmesine neden olan satır başı/satır besleme sırası, <xref:Microsoft.VisualBasic.ControlChars> <xref:Microsoft.VisualBasic?displayProperty=nameWithType> ad alanındaki modülün bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="40427-121">For example, the carriage return/line feed sequence that causes a single piece of text to be displayed on multiple lines is part of the <xref:Microsoft.VisualBasic.ControlChars> module in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="40427-122">Diğer adı olmayan bir programda bu sabiti kullanmak için aşağıdaki kodu yazmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="40427-122">To use this constant in a program without an alias, you would need to type the following code:</span></span>  
  
 [!code-vb[VbVbalrApplication#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#3)]  
  
 <span data-ttu-id="40427-123">`Imports`deyimler her zaman bir modüldeki deyimlerden hemen sonra gelen `Option` ilk satır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="40427-123">`Imports` statements must always be the first lines immediately following any `Option` statements in a module.</span></span> <span data-ttu-id="40427-124">Aşağıdaki kod parçası, <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> modüle bir diğer adın nasıl içeri aktarılacağını ve atanacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="40427-124">The following code fragment shows how to import and assign an alias to the <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> module:</span></span>  
  
 [!code-vb[VbVbalrApplication#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#4)]  
  
 <span data-ttu-id="40427-125">Bu ad alanına gelecekteki başvurular önemli ölçüde daha kısa olabilir:</span><span class="sxs-lookup"><span data-stu-id="40427-125">Future references to this namespace can be considerably shorter:</span></span>  
  
 [!code-vb[VbVbalrApplication#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#5)]  
  
 <span data-ttu-id="40427-126">Bir `Imports` ifade bir diğer ad içermiyorsa, içeri aktarılan ad alanı içinde tanımlanan öğeler, bir nitelik olmadan modülde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="40427-126">If an `Imports` statement does not include an alias name, elements defined within the imported namespace can be used in the module without qualification.</span></span> <span data-ttu-id="40427-127">Diğer ad belirtilmişse, bu ad alanı içinde yer alan adlara yönelik bir niteleyici olarak kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="40427-127">If the alias name is specified, it must be used as a qualifier for names contained within that namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40427-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40427-128">See also</span></span>

- <xref:Microsoft.VisualBasic.ControlChars>
- <xref:Microsoft.VisualBasic>
- [<span data-ttu-id="40427-129">Visual Basic ad alanları</span><span class="sxs-lookup"><span data-stu-id="40427-129">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="40427-130">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="40427-130">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="40427-131">Nasıl yapılır: Komut satırını kullanarak derlemeler oluşturma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="40427-131">How to: Create and Use Assemblies Using the Command Line</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)
- [<span data-ttu-id="40427-132">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="40427-132">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
