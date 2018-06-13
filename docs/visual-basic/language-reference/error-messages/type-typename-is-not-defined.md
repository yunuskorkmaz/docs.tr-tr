---
title: Tür &#39; &lt;typename&gt; &#39; tanımlı değil
ms.date: 07/20/2015
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
ms.openlocfilehash: 20f36a06000d0197ad80b83766f6612a474d5758
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595192"
---
# <a name="type-39lttypenamegt39-is-not-defined"></a><span data-ttu-id="79dd2-102">Tür &#39; &lt;typename&gt; &#39; tanımlı değil</span><span class="sxs-lookup"><span data-stu-id="79dd2-102">Type &#39;&lt;typename&gt;&#39; is not defined</span></span>
<span data-ttu-id="79dd2-103">Deyim tanımlanmamış bir tür referansı yaptı.</span><span class="sxs-lookup"><span data-stu-id="79dd2-103">The statement has made reference to a type that has not been defined.</span></span> <span data-ttu-id="79dd2-104">Bir bildirim deyiminde gibi bir tür tanımlayabilirsiniz `Enum`, `Structure`, `Class`, veya `Interface`.</span><span class="sxs-lookup"><span data-stu-id="79dd2-104">You can define a type in a declaration statement such as `Enum`, `Structure`, `Class`, or `Interface`.</span></span>  
  
 <span data-ttu-id="79dd2-105">**Hata Kimliği:** BC30002</span><span class="sxs-lookup"><span data-stu-id="79dd2-105">**Error ID:** BC30002</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="79dd2-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="79dd2-106">To correct this error</span></span>  
  
-   <span data-ttu-id="79dd2-107">Tür tanımı ve kendi başvuru her ikisi de aynı yazım kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="79dd2-107">Ensure that the type definition and its reference both use the same spelling.</span></span>  
  
-   <span data-ttu-id="79dd2-108">Tür tanımı referansı erişilebilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="79dd2-108">Ensure that the type definition is accessible to the reference.</span></span> <span data-ttu-id="79dd2-109">Örneğin, türü başka bir modülde ise ve bildirilmiş `Private`, tür tanımı için başvuru modülü taşımak veya bildirirken `Public`.</span><span class="sxs-lookup"><span data-stu-id="79dd2-109">For example, if the type is in another module and has been declared `Private`, move the type definition to the referencing module or declare it `Public`.</span></span>  
  
-   <span data-ttu-id="79dd2-110">Türünün ad alanını, projeyi yeniden değil emin olun.</span><span class="sxs-lookup"><span data-stu-id="79dd2-110">Ensure that the namespace of the type is not redefined within your project.</span></span> <span data-ttu-id="79dd2-111">Gerekiyorsa, kullanın `Global` tür adı tam olarak nitelemek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="79dd2-111">If it is, use the `Global` keyword to fully qualify the type name.</span></span> <span data-ttu-id="79dd2-112">Örneğin, bir proje adlı bir ad alanını tanımlayan `System`, <xref:System.Object?displayProperty=nameWithType> türü ile tam olmadığı sürece erişilemiyor `Global` anahtar sözcüğü: `Global.System.Object`.</span><span class="sxs-lookup"><span data-stu-id="79dd2-112">For example, if a project defines a namespace named `System`, the <xref:System.Object?displayProperty=nameWithType> type cannot be accessed unless it is fully qualified with the `Global` keyword: `Global.System.Object`.</span></span>  
  
-   <span data-ttu-id="79dd2-113">Tür tanımlandı, ancak nesne kitaplığı ya da tanımlanmış tür kitaplığı Visual Basic, tıklatın kaydedilmemiş **Başvuru Ekle** üzerinde **proje** menüsüne ve ardından uygun nesnesi kitaplığı veya tür kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="79dd2-113">If the type is defined, but the object library or type library in which it is defined is not registered in Visual Basic, click **Add Reference** on the **Project** menu, and then select the appropriate object library or type library.</span></span>  
  
-   <span data-ttu-id="79dd2-114">Türü hedef .NET Framework profilinin parçası olan bir derlemede olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="79dd2-114">Ensure that the type is in an assembly that is part of the targeted .NET Framework profile.</span></span> <span data-ttu-id="79dd2-115">Daha fazla bilgi için bkz: [.NET Framework hedefleme hataları giderme](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span><span class="sxs-lookup"><span data-stu-id="79dd2-115">For more information, see [Troubleshooting .NET Framework Targeting Errors](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79dd2-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="79dd2-116">See Also</span></span>  
 [<span data-ttu-id="79dd2-117">Visual Basic'de ad alanları</span><span class="sxs-lookup"><span data-stu-id="79dd2-117">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="79dd2-118">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="79dd2-118">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
 [<span data-ttu-id="79dd2-119">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="79dd2-119">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="79dd2-120">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="79dd2-120">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="79dd2-121">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="79dd2-121">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="79dd2-122">Bir projedeki başvuruları yönetme</span><span class="sxs-lookup"><span data-stu-id="79dd2-122">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
