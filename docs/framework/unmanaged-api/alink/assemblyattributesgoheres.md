---
title: AssemblyAttributesGoHereS
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHereS
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHereS
helpviewer_keywords:
- AssemblyAttributesGoHereS type
- Alink API, AssemblyAttributesGoHereS type
ms.assetid: 4e817f35-a2bc-4403-9e6f-f731e6b9fe23
topic_type:
- apiref
ms.openlocfilehash: 128268bab77c8be5dc809eaa6d2548fc34f13cbd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446612"
---
# <a name="assemblyattributesgoheres"></a><span data-ttu-id="be6b3-102">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="be6b3-102">AssemblyAttributesGoHereS</span></span>

<span data-ttu-id="be6b3-103">ALink tarafından özel öznitelikler hakkında bilgi depolamak için bir yer tutucu olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="be6b3-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>

## <a name="syntax"></a><span data-ttu-id="be6b3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be6b3-104">Syntax</span></span>

```csharp
internal sealed class AssemblyAttributesGoHereS
```

## <a name="remarks"></a><span data-ttu-id="be6b3-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="be6b3-105">Remarks</span></span>

<span data-ttu-id="be6b3-106">Bu türe yapılan başvurular, kaynakları derleme özel öznitelikleri içeren netmodule 'ler içine gömülebilir.</span><span class="sxs-lookup"><span data-stu-id="be6b3-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="be6b3-107">Bu türlere başvurular içeren bir veya daha fazla netmodule 'ler öğesinden bir derleme bildirimi oluştururken, ALink, gerçek özel öznitelikleri yaymak için bu başvurulara eklenen bilgileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="be6b3-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="be6b3-108">Bu nedenle, bu tür hiçbir şekilde örneklenemez ve yalnızca derleme işleminin bir parçası olarak kullanılır ve son derlemede hiçbir amaca uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="be6b3-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>

<span data-ttu-id="be6b3-109">Bu türe başvurular, güvenlikle ilgili olan ve çoklu kullanım olmayan özel öznitelikleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="be6b3-109">References to this type indicate custom attributes that are security related and are not multiple-use.</span></span>

<span data-ttu-id="be6b3-110">Bu türler, .NET Framework içinde "iç" olarak işaretlenir ve <xref:System.Runtime.CompilerServices> ad alanında bulunur.</span><span class="sxs-lookup"><span data-stu-id="be6b3-110">These types are marked "internal" within the .NET Framework and are located in the <xref:System.Runtime.CompilerServices> namespace.</span></span>

## <a name="requirements"></a><span data-ttu-id="be6b3-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="be6b3-111">Requirements</span></span>

<span data-ttu-id="be6b3-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="be6b3-112">mscorlib.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="be6b3-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be6b3-113">See also</span></span>

- [<span data-ttu-id="be6b3-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="be6b3-114">AssemblyAttributesGoHere</span></span>](assemblyattributesgohere.md)
- [<span data-ttu-id="be6b3-115">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="be6b3-115">AssemblyAttributesGoHereM</span></span>](assemblyattributesgoherem.md)
- [<span data-ttu-id="be6b3-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="be6b3-116">AssemblyAttributesGoHereSM</span></span>](assemblyattributesgoheresm.md)
