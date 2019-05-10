---
title: "'<typename>' türü tanımlı değil"
ms.date: 07/20/2015
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
ms.openlocfilehash: 1f66b86a61fb0344a449bf0aa46b7655813c7c30
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664251"
---
# <a name="type-typename-is-not-defined"></a><span data-ttu-id="84c4c-102">Türü '\<typename >' tanımlı değil</span><span class="sxs-lookup"><span data-stu-id="84c4c-102">Type '\<typename>' is not defined</span></span>
<span data-ttu-id="84c4c-103">İfade tanımlanmadı bir türe başvuru yaptı.</span><span class="sxs-lookup"><span data-stu-id="84c4c-103">The statement has made reference to a type that has not been defined.</span></span> <span data-ttu-id="84c4c-104">Bir bildirim deyiminde gibi bir tür tanımlayabilirsiniz `Enum`, `Structure`, `Class`, veya `Interface`.</span><span class="sxs-lookup"><span data-stu-id="84c4c-104">You can define a type in a declaration statement such as `Enum`, `Structure`, `Class`, or `Interface`.</span></span>  
  
 <span data-ttu-id="84c4c-105">**Hata Kimliği:** BC30002</span><span class="sxs-lookup"><span data-stu-id="84c4c-105">**Error ID:** BC30002</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="84c4c-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="84c4c-106">To correct this error</span></span>  
  
- <span data-ttu-id="84c4c-107">Tür tanımını ve onun başvurusu aynı yazım kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="84c4c-107">Ensure that the type definition and its reference both use the same spelling.</span></span>  
  
- <span data-ttu-id="84c4c-108">Tür tanımını başvuru erişilebilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="84c4c-108">Ensure that the type definition is accessible to the reference.</span></span> <span data-ttu-id="84c4c-109">Örneğin, tür başka bir modül ve bildirilmiş `Private`, tür tanımını başvuran modülüne taşıyın veya bildirirken `Public`.</span><span class="sxs-lookup"><span data-stu-id="84c4c-109">For example, if the type is in another module and has been declared `Private`, move the type definition to the referencing module or declare it `Public`.</span></span>  
  
- <span data-ttu-id="84c4c-110">Türün ad alanı içinde projenizi yeniden değil emin olun.</span><span class="sxs-lookup"><span data-stu-id="84c4c-110">Ensure that the namespace of the type is not redefined within your project.</span></span> <span data-ttu-id="84c4c-111">İse, kullanın `Global` tür adı tam olarak nitelemek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="84c4c-111">If it is, use the `Global` keyword to fully qualify the type name.</span></span> <span data-ttu-id="84c4c-112">Örneğin, bir proje adındaki bir ad tanımlar `System`, <xref:System.Object?displayProperty=nameWithType> türü ile tam olmadığı sürece erişilemez `Global` anahtar sözcüğü: `Global.System.Object`.</span><span class="sxs-lookup"><span data-stu-id="84c4c-112">For example, if a project defines a namespace named `System`, the <xref:System.Object?displayProperty=nameWithType> type cannot be accessed unless it is fully qualified with the `Global` keyword: `Global.System.Object`.</span></span>  
  
- <span data-ttu-id="84c4c-113">Türü tanımlandı, ancak nesne kitaplığı veya tür kitaplığı içinde tanımlanmış olduğu Visual Basic, tıklama kayıtlı değil **Başvuru Ekle** üzerinde **proje** menüsüne ve ardından uygun nesne kitaplık veya tür kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="84c4c-113">If the type is defined, but the object library or type library in which it is defined is not registered in Visual Basic, click **Add Reference** on the **Project** menu, and then select the appropriate object library or type library.</span></span>  
  
- <span data-ttu-id="84c4c-114">Türü hedeflenen .NET Framework profilinin bir parçası olan bir derlemede olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="84c4c-114">Ensure that the type is in an assembly that is part of the targeted .NET Framework profile.</span></span> <span data-ttu-id="84c4c-115">Daha fazla bilgi için [.NET Framework hedefleme hataları giderme](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span><span class="sxs-lookup"><span data-stu-id="84c4c-115">For more information, see [Troubleshooting .NET Framework Targeting Errors](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84c4c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84c4c-116">See also</span></span>

- [<span data-ttu-id="84c4c-117">Visual Basic'de ad alanları</span><span class="sxs-lookup"><span data-stu-id="84c4c-117">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="84c4c-118">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="84c4c-118">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)
- [<span data-ttu-id="84c4c-119">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="84c4c-119">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="84c4c-120">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="84c4c-120">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="84c4c-121">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="84c4c-121">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="84c4c-122">Bir projedeki başvuruları yönetme</span><span class="sxs-lookup"><span data-stu-id="84c4c-122">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
