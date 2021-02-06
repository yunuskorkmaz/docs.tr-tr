---
description: 'Daha fazla bilgi edinin: AssemblyAttributesGoHereM Class'
title: AssemblyAttributesGoHereM sınıfı (System. Runtime. CompilerServices)
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHereM
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHereM
helpviewer_keywords:
- AssemblyAttributesGoHereM type
- Alink API, AssemblyAttributesGoHereM type
ms.assetid: caaa8ba9-b4bb-4dd6-934d-57e436b2f3e5
topic_type:
- apiref
ms.openlocfilehash: 9afa72e5adbd539acaf8dfe45b446a61862df49e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638580"
---
# <a name="assemblyattributesgoherem-class"></a><span data-ttu-id="38885-103">AssemblyAttributesGoHereM sınıfı</span><span class="sxs-lookup"><span data-stu-id="38885-103">AssemblyAttributesGoHereM Class</span></span>

<span data-ttu-id="38885-104">ALink tarafından özel öznitelikler hakkında bilgi depolamak için bir yer tutucu olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="38885-104">Used by ALink as a placeholder to store information about custom attributes.</span></span>

## <a name="syntax"></a><span data-ttu-id="38885-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="38885-105">Syntax</span></span>

```csharp
internal sealed class AssemblyAttributesGoHereM
```

## <a name="remarks"></a><span data-ttu-id="38885-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="38885-106">Remarks</span></span>

<span data-ttu-id="38885-107">Bu türe yapılan başvurular, kaynakları derleme özel öznitelikleri içeren netmodule 'ler içine gömülebilir.</span><span class="sxs-lookup"><span data-stu-id="38885-107">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="38885-108">Bu türlere başvurular içeren bir veya daha fazla netmodule 'ler öğesinden bir derleme bildirimi oluştururken, ALink, gerçek özel öznitelikleri yaymak için bu başvurulara eklenen bilgileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="38885-108">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="38885-109">Bu nedenle, bu tür hiçbir şekilde örneklenemez ve yalnızca derleme işleminin bir parçası olarak kullanılır ve son derlemede hiçbir amaca uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="38885-109">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>

<span data-ttu-id="38885-110">Bu türe başvurular, güvenlikle ilgili olmayan ancak birden çok kullanımda olan özel öznitelikleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="38885-110">References to this type indicate custom attributes that are not security related but are multiple-use.</span></span>

<span data-ttu-id="38885-111">Bu türler, .NET Framework içinde "iç" olarak işaretlenir ve <xref:System.Runtime.CompilerServices> ad alanında bulunur.</span><span class="sxs-lookup"><span data-stu-id="38885-111">These types are marked "internal" within the .NET Framework and are located in the <xref:System.Runtime.CompilerServices> namespace.</span></span>

## <a name="requirements"></a><span data-ttu-id="38885-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="38885-112">Requirements</span></span>

<span data-ttu-id="38885-113">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="38885-113">mscorlib.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="38885-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38885-114">See also</span></span>

- [<span data-ttu-id="38885-115">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="38885-115">AssemblyAttributesGoHere</span></span>](assemblyattributesgohere.md)
- [<span data-ttu-id="38885-116">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="38885-116">AssemblyAttributesGoHereS</span></span>](assemblyattributesgoheres.md)
- [<span data-ttu-id="38885-117">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="38885-117">AssemblyAttributesGoHereSM</span></span>](assemblyattributesgoheresm.md)
