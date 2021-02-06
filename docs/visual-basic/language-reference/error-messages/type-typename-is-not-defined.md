---
description: "Hakkında daha fazla bilgi edinin: BC30002: Type ' <typename> ' tanımlanmadı"
title: "'<typename>' türü tanımlı değil"
ms.date: 07/20/2015
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
ms.openlocfilehash: 48ee0c38492769aea8c1be2e9d54eaa537e35766
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641134"
---
# <a name="bc30002-type-typename-is-not-defined"></a><span data-ttu-id="fee70-103">BC30002: ' \<typename> ' türü tanımlı değil</span><span class="sxs-lookup"><span data-stu-id="fee70-103">BC30002: Type '\<typename>' is not defined</span></span>

<span data-ttu-id="fee70-104">İfade tanımlanmamış bir türe başvuru yaptı.</span><span class="sxs-lookup"><span data-stu-id="fee70-104">The statement has made reference to a type that has not been defined.</span></span> <span data-ttu-id="fee70-105">,,, Veya gibi bir bildirim bildiriminde bir türü tanımlayabilirsiniz `Enum` `Structure` `Class` `Interface` .</span><span class="sxs-lookup"><span data-stu-id="fee70-105">You can define a type in a declaration statement such as `Enum`, `Structure`, `Class`, or `Interface`.</span></span>

 <span data-ttu-id="fee70-106">**Hata kimliği:** BC30002</span><span class="sxs-lookup"><span data-stu-id="fee70-106">**Error ID:** BC30002</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="fee70-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="fee70-107">To correct this error</span></span>

- <span data-ttu-id="fee70-108">Tür tanımının ve başvurusunun her ikisi de aynı yazımı kullandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="fee70-108">Ensure that the type definition and its reference both use the same spelling.</span></span>

- <span data-ttu-id="fee70-109">Tür tanımına başvuru tarafından erişilebildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="fee70-109">Ensure that the type definition is accessible to the reference.</span></span> <span data-ttu-id="fee70-110">Örneğin, tür başka bir modülse ve bildirilirse `Private` , tür tanımını başvuran modüle taşıyın veya bildirin `Public` .</span><span class="sxs-lookup"><span data-stu-id="fee70-110">For example, if the type is in another module and has been declared `Private`, move the type definition to the referencing module or declare it `Public`.</span></span>

- <span data-ttu-id="fee70-111">Türün ad alanının projeniz içinde yeniden tanımlanmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="fee70-111">Ensure that the namespace of the type is not redefined within your project.</span></span> <span data-ttu-id="fee70-112">Varsa, `Global` tür adını tam olarak nitelemek için anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="fee70-112">If it is, use the `Global` keyword to fully qualify the type name.</span></span> <span data-ttu-id="fee70-113">Örneğin, bir proje adlı bir ad alanını tanımlarsa `System` , <xref:System.Object?displayProperty=nameWithType> tür anahtar sözcüğüyle tam nitelendirilmediği takdirde türe erişilemez `Global` `Global.System.Object` .</span><span class="sxs-lookup"><span data-stu-id="fee70-113">For example, if a project defines a namespace named `System`, the <xref:System.Object?displayProperty=nameWithType> type cannot be accessed unless it is fully qualified with the `Global` keyword: `Global.System.Object`.</span></span>

- <span data-ttu-id="fee70-114">Tür tanımlanmışsa, ancak tanımlanmış olduğu nesne kitaplığı veya tür kitaplığı Visual Basic kayıtlı değilse, **Proje** menüsünde **Başvuru Ekle** ' ye tıklayın ve ardından uygun nesne kitaplığı veya tür kitaplığı ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="fee70-114">If the type is defined, but the object library or type library in which it is defined is not registered in Visual Basic, click **Add Reference** on the **Project** menu, and then select the appropriate object library or type library.</span></span>

- <span data-ttu-id="fee70-115">Türün hedeflenen .NET Framework profilinin parçası olan bir derlemede bulunduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="fee70-115">Ensure that the type is in an assembly that is part of the targeted .NET Framework profile.</span></span> <span data-ttu-id="fee70-116">Daha fazla bilgi için bkz. [.NET Framework Hedefleme hatalarını giderme](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span><span class="sxs-lookup"><span data-stu-id="fee70-116">For more information, see [Troubleshooting .NET Framework Targeting Errors](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span></span>

## <a name="see-also"></a><span data-ttu-id="fee70-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fee70-117">See also</span></span>

- [<span data-ttu-id="fee70-118">Visual Basic'de Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="fee70-118">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="fee70-119">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="fee70-119">Enum Statement</span></span>](../statements/enum-statement.md)
- [<span data-ttu-id="fee70-120">Structure Yapısı</span><span class="sxs-lookup"><span data-stu-id="fee70-120">Structure Statement</span></span>](../statements/structure-statement.md)
- [<span data-ttu-id="fee70-121">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="fee70-121">Class Statement</span></span>](../statements/class-statement.md)
- [<span data-ttu-id="fee70-122">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="fee70-122">Interface Statement</span></span>](../statements/interface-statement.md)
- [<span data-ttu-id="fee70-123">Bir projedeki başvuruları yönetme</span><span class="sxs-lookup"><span data-stu-id="fee70-123">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
