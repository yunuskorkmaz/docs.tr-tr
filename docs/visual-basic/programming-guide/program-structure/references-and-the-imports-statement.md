---
title: References ve Imports Deyimi
ms.date: 07/20/2015
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
ms.openlocfilehash: 13f250e1b015e5a821da83e557033bc878a8a3b8
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097910"
---
# <a name="references-and-the-imports-statement-visual-basic"></a><span data-ttu-id="c7fa1-102">References ve Imports Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7fa1-102">References and the Imports Statement (Visual Basic)</span></span>

<span data-ttu-id="c7fa1-103">**Proje** menüsünde **Başvuru Ekle** komutunu seçerek dış nesneleri projeniz için kullanılabilir hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7fa1-103">You can make external objects available to your project by choosing the **Add Reference** command on the **Project** menu.</span></span> <span data-ttu-id="c7fa1-104">Visual Basic başvurular tür kitaplıkları gibi olan ancak daha fazla bilgi içeren derlemelere işaret edebilir.</span><span class="sxs-lookup"><span data-stu-id="c7fa1-104">References in Visual Basic can point to assemblies, which are like type libraries but contain more information.</span></span>  
  
## <a name="the-imports-statement"></a><span data-ttu-id="c7fa1-105">Imports ekstresi</span><span class="sxs-lookup"><span data-stu-id="c7fa1-105">The Imports Statement</span></span>  

 <span data-ttu-id="c7fa1-106">Derlemeler bir veya daha fazla ad alanı içerir.</span><span class="sxs-lookup"><span data-stu-id="c7fa1-106">Assemblies include one or more namespaces.</span></span> <span data-ttu-id="c7fa1-107">Bir derlemeye başvuru eklediğinizde, `Imports` Bu derlemenin modül içindeki ad alanlarının görünürlüğünü denetleyen bir modüle de bir ifade ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7fa1-107">When you add a reference to an assembly, you can also add an `Imports` statement to a module that controls the visibility of that assembly's namespaces within the module.</span></span> <span data-ttu-id="c7fa1-108">`Imports`Bu ifade, benzersiz bir başvuru sağlamak için gereken ad alanının yalnızca bir kısmını kullanmanıza imkan tanıyan bir kapsam bağlamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7fa1-108">The `Imports` statement provides a scoping context that lets you use only the portion of the namespace necessary to supply a unique reference.</span></span>  
  
 <span data-ttu-id="c7fa1-109">`Imports`İfadesinin sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="c7fa1-109">The `Imports` statement has the following syntax:</span></span>  
  
 `Imports [Aliasname =] Namespace`  
  
 <span data-ttu-id="c7fa1-110">`Aliasname` İçeri aktarılan bir ad alanına başvurmak için kod içinde kullanabileceğiniz kısa bir ad anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c7fa1-110">`Aliasname` refers to a short name you can use within code to refer to an imported namespace.</span></span> <span data-ttu-id="c7fa1-111">`Namespace` proje başvurusu aracılığıyla, proje içindeki bir tanım aracılığıyla veya önceki bir ifadeyle bulunan bir ad alanıdır `Imports` .</span><span class="sxs-lookup"><span data-stu-id="c7fa1-111">`Namespace` is a namespace available through either a project reference, through a definition within the project, or through a previous `Imports` statement.</span></span>  
  
 <span data-ttu-id="c7fa1-112">Modül, herhangi bir sayıda deyim içerebilir `Imports` .</span><span class="sxs-lookup"><span data-stu-id="c7fa1-112">A module may contain any number of `Imports` statements.</span></span> <span data-ttu-id="c7fa1-113">Varsa, varsa tüm `Option` deyimlerden sonra, diğer koddan önce gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="c7fa1-113">They must appear after any `Option` statements, if present, but before any other code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c7fa1-114">Proje başvurularını `Imports` deyimle veya `Declare` ifadesiyle karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="c7fa1-114">Do not confuse project references with the `Imports` statement or the `Declare` statement.</span></span> <span data-ttu-id="c7fa1-115">Proje başvuruları, derlemelerdeki nesneler gibi dış nesneleri Visual Basic projeleri için kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="c7fa1-115">Project references make external objects, such as objects in assemblies, available to Visual Basic projects.</span></span> <span data-ttu-id="c7fa1-116">`Imports`İfade, proje başvurularına erişimi basitleştirmek için kullanılır, ancak bu nesnelere erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="c7fa1-116">The `Imports` statement is used to simplify access to project references, but does not provide access to these objects.</span></span> <span data-ttu-id="c7fa1-117">İfade, bir `Declare` dinamik bağlantı kitaplığı (dll) içinde bir dış yordama başvuru bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c7fa1-117">The `Declare` statement is used to declare a reference to an external procedure in a dynamic-link library (DLL).</span></span>  
  
## <a name="using-aliases-with-the-imports-statement"></a><span data-ttu-id="c7fa1-118">Imports Ifadesiyle diğer adları kullanma</span><span class="sxs-lookup"><span data-stu-id="c7fa1-118">Using Aliases with the Imports Statement</span></span>  

 <span data-ttu-id="c7fa1-119">`Imports`İfade, başvuruların tam adlarını açıkça yazma gereğini ortadan kaldırarak sınıfların yöntemlerine erişmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="c7fa1-119">The `Imports` statement makes it easier to access methods of classes by eliminating the need to explicitly type the fully qualified names of references.</span></span> <span data-ttu-id="c7fa1-120">Diğer adlar, bir ad alanının yalnızca bir kısmına kolay bir ad atamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7fa1-120">Aliases let you assign a friendlier name to just one part of a namespace.</span></span> <span data-ttu-id="c7fa1-121">Örneğin, tek bir metin parçasının birden çok satırda görüntülenmesine neden olan satır başı/satır besleme sırası, <xref:Microsoft.VisualBasic.ControlChars> ad alanındaki modülün bir parçasıdır <xref:Microsoft.VisualBasic?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c7fa1-121">For example, the carriage return/line feed sequence that causes a single piece of text to be displayed on multiple lines is part of the <xref:Microsoft.VisualBasic.ControlChars> module in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="c7fa1-122">Diğer adı olmayan bir programda bu sabiti kullanmak için aşağıdaki kodu yazmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="c7fa1-122">To use this constant in a program without an alias, you would need to type the following code:</span></span>  
  
 [!code-vb[VbVbalrApplication#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#3)]  
  
 <span data-ttu-id="c7fa1-123">`Imports` deyimler her zaman `Option` bir modüldeki deyimlerden hemen sonra gelen ilk satır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c7fa1-123">`Imports` statements must always be the first lines immediately following any `Option` statements in a module.</span></span> <span data-ttu-id="c7fa1-124">Aşağıdaki kod parçası, modüle bir diğer adın nasıl içeri aktarılacağını ve atanacağını gösterir <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="c7fa1-124">The following code fragment shows how to import and assign an alias to the <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> module:</span></span>  
  
 [!code-vb[VbVbalrApplication#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#4)]  
  
 <span data-ttu-id="c7fa1-125">Bu ad alanına gelecekteki başvurular önemli ölçüde daha kısa olabilir:</span><span class="sxs-lookup"><span data-stu-id="c7fa1-125">Future references to this namespace can be considerably shorter:</span></span>  
  
 [!code-vb[VbVbalrApplication#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#5)]  
  
 <span data-ttu-id="c7fa1-126">Bir `Imports` ifade bir diğer ad içermiyorsa, içeri aktarılan ad alanı içinde tanımlanan öğeler, bir nitelik olmadan modülde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c7fa1-126">If an `Imports` statement does not include an alias name, elements defined within the imported namespace can be used in the module without qualification.</span></span> <span data-ttu-id="c7fa1-127">Diğer ad belirtilmişse, bu ad alanı içinde yer alan adlara yönelik bir niteleyici olarak kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7fa1-127">If the alias name is specified, it must be used as a qualifier for names contained within that namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7fa1-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7fa1-128">See also</span></span>

- <xref:Microsoft.VisualBasic.ControlChars>
- <xref:Microsoft.VisualBasic>
- [<span data-ttu-id="c7fa1-129">Visual Basic'de Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="c7fa1-129">Namespaces in Visual Basic</span></span>](namespaces.md)
- [<span data-ttu-id="c7fa1-130">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="c7fa1-130">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="c7fa1-131">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="c7fa1-131">Imports Statement (.NET Namespace and Type)</span></span>](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
