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
ms.openlocfilehash: 9e31d22cd7502ffd405af23bd1fabe8685190221
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518132"
---
# <a name="references-and-the-imports-statement-visual-basic"></a><span data-ttu-id="19f50-102">References ve Imports Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19f50-102">References and the Imports Statement (Visual Basic)</span></span>
<span data-ttu-id="19f50-103">Dış nesneler kullanılabilir projenize seçerek yapabileceğiniz **Başvuru Ekle** komutunu **proje** menüsü.</span><span class="sxs-lookup"><span data-stu-id="19f50-103">You can make external objects available to your project by choosing the **Add Reference** command on the **Project** menu.</span></span> <span data-ttu-id="19f50-104">Başvuruları Visual Basic'te tür kitaplıkları, ancak daha fazla bilgi içeren gibi olan derlemeler için işaret edebilir.</span><span class="sxs-lookup"><span data-stu-id="19f50-104">References in Visual Basic can point to assemblies, which are like type libraries but contain more information.</span></span>  
  
## <a name="the-imports-statement"></a><span data-ttu-id="19f50-105">Imports deyimi</span><span class="sxs-lookup"><span data-stu-id="19f50-105">The Imports Statement</span></span>  
 <span data-ttu-id="19f50-106">Derlemeler, bir veya daha fazla ad alanı içerir.</span><span class="sxs-lookup"><span data-stu-id="19f50-106">Assemblies include one or more namespaces.</span></span> <span data-ttu-id="19f50-107">Bir derlemeye bir başvuru eklediğinizde, bu da ekleyebilirsiniz bir `Imports` o derlemenin ad alanları modülü içinde görünürlüğünü denetleyen bir modüle deyimi.</span><span class="sxs-lookup"><span data-stu-id="19f50-107">When you add a reference to an assembly, you can also add an `Imports` statement to a module that controls the visibility of that assembly's namespaces within the module.</span></span> <span data-ttu-id="19f50-108">`Imports` Deyimi yalnızca bir benzersiz başvuru sağlamanız için gereken ad alanının bölümü kullanmanıza olanak sağlayan bir kapsam bağlamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="19f50-108">The `Imports` statement provides a scoping context that lets you use only the portion of the namespace necessary to supply a unique reference.</span></span>  
  
 <span data-ttu-id="19f50-109">`Imports` Deyimi sözdizimine sahiptir:</span><span class="sxs-lookup"><span data-stu-id="19f50-109">The `Imports` statement has the following syntax:</span></span>  
  
 <span data-ttu-id="19f50-110">`Imports` [`|``Aliasname` =] `Namespace`</span><span class="sxs-lookup"><span data-stu-id="19f50-110">`Imports` [`|``Aliasname` =] `Namespace`</span></span>  
  
 <span data-ttu-id="19f50-111">`Aliasname` kod içinde bir içeri aktarılan ad alanına başvurmak için kullanabileceğiniz bir kısa ad belirtir.</span><span class="sxs-lookup"><span data-stu-id="19f50-111">`Aliasname` refers to a short name you can use within code to refer to an imported namespace.</span></span> <span data-ttu-id="19f50-112">`Namespace` Proje içinde bir tanımı veya önceki bir proje başvurusu bir ad alanı aracılığıyla kullanılabilir olan `Imports` deyimi.</span><span class="sxs-lookup"><span data-stu-id="19f50-112">`Namespace` is a namespace available through either a project reference, through a definition within the project, or through a previous `Imports` statement.</span></span>  
  
 <span data-ttu-id="19f50-113">Bir modülün herhangi bir sayıda içerebilir `Imports` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="19f50-113">A module may contain any number of `Imports` statements.</span></span> <span data-ttu-id="19f50-114">Herhangi bir sonra görünmelidir `Option` deyimleri, varsa, ancak herhangi bir kod önce.</span><span class="sxs-lookup"><span data-stu-id="19f50-114">They must appear after any `Option` statements, if present, but before any other code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19f50-115">Proje başvuruları ile karıştırmayın `Imports` deyimi veya `Declare` deyimi.</span><span class="sxs-lookup"><span data-stu-id="19f50-115">Do not confuse project references with the `Imports` statement or the `Declare` statement.</span></span> <span data-ttu-id="19f50-116">Proje başvuruları, derlemelere nesneleri gibi dış nesneleri Visual Basic projeleri kullanılabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="19f50-116">Project references make external objects, such as objects in assemblies, available to Visual Basic projects.</span></span> <span data-ttu-id="19f50-117">`Imports` Deyimi proje başvuruları erişimini basitleştirmek için kullanılır, ancak bu nesnelere erişimi sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="19f50-117">The `Imports` statement is used to simplify access to project references, but does not provide access to these objects.</span></span> <span data-ttu-id="19f50-118">`Declare` Deyimi bir dış yordam bir dinamik bağlantı kitaplığı (DLL) içinde bir başvuru bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="19f50-118">The `Declare` statement is used to declare a reference to an external procedure in a dynamic-link library (DLL).</span></span>  
  
## <a name="using-aliases-with-the-imports-statement"></a><span data-ttu-id="19f50-119">Imports deyimi ile diğer adların kullanımı</span><span class="sxs-lookup"><span data-stu-id="19f50-119">Using Aliases with the Imports Statement</span></span>  
 <span data-ttu-id="19f50-120">`Imports` Deyimi kolaylaştırır, sınıfların erişim yöntemlerine açıkça tam olarak nitelenmiş adlar başvuru türüne gereksinimini ortadan kaldırarak.</span><span class="sxs-lookup"><span data-stu-id="19f50-120">The `Imports` statement makes it easier to access methods of classes by eliminating the need to explicitly type the fully qualified names of references.</span></span> <span data-ttu-id="19f50-121">Diğer adlar, daha kolay adı bir ad alanının yalnızca bir bölümü atamak sağlar.</span><span class="sxs-lookup"><span data-stu-id="19f50-121">Aliases let you assign a friendlier name to just one part of a namespace.</span></span> <span data-ttu-id="19f50-122">Örneğin, satır başı/birden çok satırda görüntülenecek metni tek bir parçasını neden dizisi satır besleme parçası olan <xref:Microsoft.VisualBasic.ControlChars> modülünde <xref:Microsoft.VisualBasic?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="19f50-122">For example, the carriage return/line feed sequence that causes a single piece of text to be displayed on multiple lines is part of the <xref:Microsoft.VisualBasic.ControlChars> module in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="19f50-123">Bu sabit bir diğer ad olmadan bir programda kullanmak için aşağıdaki kod yazmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="19f50-123">To use this constant in a program without an alias, you would need to type the following code:</span></span>  
  
 [!code-vb[VbVbalrApplication#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]  
  
 <span data-ttu-id="19f50-124">`Imports` deyimleri her zaman takip herhangi ilk satırı olmalıdır `Option` Modül içindeki deyimler.</span><span class="sxs-lookup"><span data-stu-id="19f50-124">`Imports` statements must always be the first lines immediately following any `Option` statements in a module.</span></span> <span data-ttu-id="19f50-125">Aşağıdaki kod parçası, içeri aktarma ve diğer ad atamak gösterilmektedir <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> Modülü:</span><span class="sxs-lookup"><span data-stu-id="19f50-125">The following code fragment shows how to import and assign an alias to the <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> module:</span></span>  
  
 [!code-vb[VbVbalrApplication#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]  
  
 <span data-ttu-id="19f50-126">Bu ad gelecekte başvurular önemli ölçüde daha kısa olabilir:</span><span class="sxs-lookup"><span data-stu-id="19f50-126">Future references to this namespace can be considerably shorter:</span></span>  
  
 [!code-vb[VbVbalrApplication#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]  
  
 <span data-ttu-id="19f50-127">Varsa bir `Imports` deyimi bir diğer ad içermez, içeri aktarılan ad alanı içinde tanımlanan öğeler, nitelik olmadan bir modülde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="19f50-127">If an `Imports` statement does not include an alias name, elements defined within the imported namespace can be used in the module without qualification.</span></span> <span data-ttu-id="19f50-128">Diğer ad belirtilmezse, bu Niteleyici olarak bu ad alanı içinde yer alan adları için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="19f50-128">If the alias name is specified, it must be used as a qualifier for names contained within that namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19f50-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="19f50-129">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ControlChars>  
 <xref:Microsoft.VisualBasic>  
   
 [<span data-ttu-id="19f50-130">Visual Basic'de ad alanları</span><span class="sxs-lookup"><span data-stu-id="19f50-130">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="19f50-131">Derlemeler ve Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="19f50-131">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="19f50-132">Nasıl yapılır: Komut Satırını Kullanarak Bütünleştirilmiş Kodlar Oluşturma ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="19f50-132">How to: Create and Use Assemblies Using the Command Line</span></span>](https://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)  
 [<span data-ttu-id="19f50-133">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="19f50-133">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
