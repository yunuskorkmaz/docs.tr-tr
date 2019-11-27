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
ms.openlocfilehash: 31b4fe001f2b8a62ac30488053c57cd186020421
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347274"
---
# <a name="references-and-the-imports-statement-visual-basic"></a><span data-ttu-id="6e881-102">References ve Imports Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e881-102">References and the Imports Statement (Visual Basic)</span></span>
<span data-ttu-id="6e881-103">**Proje** menüsünde **Başvuru Ekle** komutunu seçerek dış nesneleri projeniz için kullanılabilir hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e881-103">You can make external objects available to your project by choosing the **Add Reference** command on the **Project** menu.</span></span> <span data-ttu-id="6e881-104">Visual Basic başvurular tür kitaplıkları gibi olan ancak daha fazla bilgi içeren derlemelere işaret edebilir.</span><span class="sxs-lookup"><span data-stu-id="6e881-104">References in Visual Basic can point to assemblies, which are like type libraries but contain more information.</span></span>  
  
## <a name="the-imports-statement"></a><span data-ttu-id="6e881-105">Imports ekstresi</span><span class="sxs-lookup"><span data-stu-id="6e881-105">The Imports Statement</span></span>  
 <span data-ttu-id="6e881-106">Derlemeler bir veya daha fazla ad alanı içerir.</span><span class="sxs-lookup"><span data-stu-id="6e881-106">Assemblies include one or more namespaces.</span></span> <span data-ttu-id="6e881-107">Bir derlemeye başvuru eklediğinizde, bu derlemenin modül içindeki ad alanlarının görünürlüğünü denetleyen bir modüle `Imports` deyiminizi de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e881-107">When you add a reference to an assembly, you can also add an `Imports` statement to a module that controls the visibility of that assembly's namespaces within the module.</span></span> <span data-ttu-id="6e881-108">`Imports` ifade, benzersiz bir başvuru sağlamak için gereken ad alanının yalnızca bir kısmını kullanmanıza imkan tanıyan bir kapsam bağlamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6e881-108">The `Imports` statement provides a scoping context that lets you use only the portion of the namespace necessary to supply a unique reference.</span></span>  
  
 <span data-ttu-id="6e881-109">`Imports` deyimin sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="6e881-109">The `Imports` statement has the following syntax:</span></span>  
  
 `Imports [Aliasname =] Namespace`  
  
 <span data-ttu-id="6e881-110">`Aliasname`, içeri aktarılan bir ad alanına başvurmak için kod içinde kullanabileceğiniz kısa bir ad anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6e881-110">`Aliasname` refers to a short name you can use within code to refer to an imported namespace.</span></span> <span data-ttu-id="6e881-111">`Namespace`, proje başvurusu aracılığıyla veya proje içindeki bir tanım aracılığıyla ya da önceki bir `Imports` ifadesiyle kullanılabilir bir ad alanıdır.</span><span class="sxs-lookup"><span data-stu-id="6e881-111">`Namespace` is a namespace available through either a project reference, through a definition within the project, or through a previous `Imports` statement.</span></span>  
  
 <span data-ttu-id="6e881-112">Modül, herhangi bir sayıda `Imports` deyimi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="6e881-112">A module may contain any number of `Imports` statements.</span></span> <span data-ttu-id="6e881-113">Varsa, varsa, herhangi bir `Option` deyimden sonra, diğer koddan önce gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="6e881-113">They must appear after any `Option` statements, if present, but before any other code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e881-114">Proje başvurularını `Imports` ifadesiyle veya `Declare` ifadesiyle karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="6e881-114">Do not confuse project references with the `Imports` statement or the `Declare` statement.</span></span> <span data-ttu-id="6e881-115">Proje başvuruları, derlemelerdeki nesneler gibi dış nesneleri Visual Basic projeleri için kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="6e881-115">Project references make external objects, such as objects in assemblies, available to Visual Basic projects.</span></span> <span data-ttu-id="6e881-116">`Imports` deyimleri proje başvurularına erişimi basitleştirmek için kullanılır, ancak bu nesnelere erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="6e881-116">The `Imports` statement is used to simplify access to project references, but does not provide access to these objects.</span></span> <span data-ttu-id="6e881-117">`Declare` deyimleri, bir dinamik bağlantı kitaplığı (DLL) içinde bir dış yordama başvuru bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6e881-117">The `Declare` statement is used to declare a reference to an external procedure in a dynamic-link library (DLL).</span></span>  
  
## <a name="using-aliases-with-the-imports-statement"></a><span data-ttu-id="6e881-118">Imports Ifadesiyle diğer adları kullanma</span><span class="sxs-lookup"><span data-stu-id="6e881-118">Using Aliases with the Imports Statement</span></span>  
 <span data-ttu-id="6e881-119">`Imports` ifade, başvuruların tam adlarını açıkça yazma gereğini ortadan kaldırarak sınıfların yöntemlerine erişmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="6e881-119">The `Imports` statement makes it easier to access methods of classes by eliminating the need to explicitly type the fully qualified names of references.</span></span> <span data-ttu-id="6e881-120">Diğer adlar, bir ad alanının yalnızca bir kısmına kolay bir ad atamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6e881-120">Aliases let you assign a friendlier name to just one part of a namespace.</span></span> <span data-ttu-id="6e881-121">Örneğin, tek bir metin parçasının birden çok satırda görüntülenmesine neden olan satır başı/satır besleme sırası, <xref:Microsoft.VisualBasic?displayProperty=nameWithType> ad alanındaki <xref:Microsoft.VisualBasic.ControlChars> modülünün bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="6e881-121">For example, the carriage return/line feed sequence that causes a single piece of text to be displayed on multiple lines is part of the <xref:Microsoft.VisualBasic.ControlChars> module in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="6e881-122">Diğer adı olmayan bir programda bu sabiti kullanmak için aşağıdaki kodu yazmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="6e881-122">To use this constant in a program without an alias, you would need to type the following code:</span></span>  
  
 [!code-vb[VbVbalrApplication#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#3)]  
  
 <span data-ttu-id="6e881-123">`Imports` deyimleri her zaman bir modüldeki tüm `Option` deyimlerinin hemen ardından ilk satır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6e881-123">`Imports` statements must always be the first lines immediately following any `Option` statements in a module.</span></span> <span data-ttu-id="6e881-124">Aşağıdaki kod parçası <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> modülüne nasıl bir diğer ad aktarılacağını ve atanacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="6e881-124">The following code fragment shows how to import and assign an alias to the <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> module:</span></span>  
  
 [!code-vb[VbVbalrApplication#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#4)]  
  
 <span data-ttu-id="6e881-125">Bu ad alanına gelecekteki başvurular önemli ölçüde daha kısa olabilir:</span><span class="sxs-lookup"><span data-stu-id="6e881-125">Future references to this namespace can be considerably shorter:</span></span>  
  
 [!code-vb[VbVbalrApplication#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#5)]  
  
 <span data-ttu-id="6e881-126">`Imports` bir ifade bir diğer ad içermiyorsa, içeri aktarılan ad alanı içinde tanımlanan öğeler, hiçbir nitelemeden modülde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6e881-126">If an `Imports` statement does not include an alias name, elements defined within the imported namespace can be used in the module without qualification.</span></span> <span data-ttu-id="6e881-127">Diğer ad belirtilmişse, bu ad alanı içinde yer alan adlara yönelik bir niteleyici olarak kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6e881-127">If the alias name is specified, it must be used as a qualifier for names contained within that namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e881-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e881-128">See also</span></span>

- <xref:Microsoft.VisualBasic.ControlChars>
- <xref:Microsoft.VisualBasic>
- [<span data-ttu-id="6e881-129">Visual Basic ad alanları</span><span class="sxs-lookup"><span data-stu-id="6e881-129">Namespaces in Visual Basic</span></span>](namespaces.md)
- [<span data-ttu-id="6e881-130">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="6e881-130">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="6e881-131">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="6e881-131">Imports Statement (.NET Namespace and Type)</span></span>](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
