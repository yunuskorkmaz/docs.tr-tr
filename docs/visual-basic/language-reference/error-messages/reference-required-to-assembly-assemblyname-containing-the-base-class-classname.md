---
description: "Daha fazla bilgi edinin: BC30007: <assemblyname> ' ' temel sınıfını içeren ' ' derlemesine başvuru gereklidir <classname>"
title: "'<assemblyname>' temel sınıfını içeren '<classname>' derlemesine başvuru gereklidir"
ms.date: 07/20/2015
f1_keywords:
- bc30007
- vbc30007
helpviewer_keywords:
- BC30007
ms.assetid: 5f34cf47-6c6e-4954-bd8e-d6b020b75fb7
ms.openlocfilehash: e6d4cf660453078d9a0f9825bc81bb990c1f55b9
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100456893"
---
# <a name="bc30007-reference-required-to-assembly-assemblyname-containing-the-base-class-classname"></a><span data-ttu-id="3b0e7-103">BC30007: \<assemblyname> ' ' temel sınıfını içeren ' ' derlemesine başvuru gerekiyor \<classname></span><span class="sxs-lookup"><span data-stu-id="3b0e7-103">BC30007: Reference required to assembly '\<assemblyname>' containing the base class '\<classname>'</span></span>

<span data-ttu-id="3b0e7-104">' ' \<assemblyname> Temel sınıfını içeren ' ' derlemesine başvuru gerekiyor \<classname> .</span><span class="sxs-lookup"><span data-stu-id="3b0e7-104">Reference required to assembly '\<assemblyname>' containing the base class '\<classname>'.</span></span> <span data-ttu-id="3b0e7-105">Projenize bir tane ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3b0e7-105">Add one to your project.</span></span>

 <span data-ttu-id="3b0e7-106">Sınıfı, projenizde doğrudan başvurulmayan bir dinamik bağlantı kitaplığı (DLL) veya bütünleştirilmiş kodda tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="3b0e7-106">The class is defined in a dynamic-link library (DLL) or assembly that is not directly referenced in your project.</span></span> <span data-ttu-id="3b0e7-107">Visual Basic derleyici, sınıfın birden fazla DLL veya derlemede tanımlanması durumunda belirsizlik olmaması için bir başvuru gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3b0e7-107">The Visual Basic compiler requires a reference to avoid ambiguity in case the class is defined in more than one DLL or assembly.</span></span>

 <span data-ttu-id="3b0e7-108">**Hata kimliği:** BC30007</span><span class="sxs-lookup"><span data-stu-id="3b0e7-108">**Error ID:** BC30007</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="3b0e7-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="3b0e7-109">To correct this error</span></span>

- <span data-ttu-id="3b0e7-110">Başvurulmayan DLL veya derlemenin adını Proje başvurularında ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3b0e7-110">Include the name of the unreferenced DLL or assembly in your project references.</span></span>

## <a name="see-also"></a><span data-ttu-id="3b0e7-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b0e7-111">See also</span></span>

- [<span data-ttu-id="3b0e7-112">Bir projedeki başvuruları yönetme</span><span class="sxs-lookup"><span data-stu-id="3b0e7-112">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="3b0e7-113">Bozuk Başvurularda Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="3b0e7-113">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
