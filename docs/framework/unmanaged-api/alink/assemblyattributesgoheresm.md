---
title: AssemblyAttributesGoHereSM sınıfı (System. Runtime. CompilerServices)
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHereSM
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHereSM
helpviewer_keywords:
- AssemblyAttributesGoHereSM type
- Alink API, AssemblyAttributesGoHereSM type
ms.assetid: 4cf9bf39-1527-49e0-a0e9-55e7a018bf66
topic_type:
- apiref
ms.openlocfilehash: 379ba20ebf675bec71e6e5f5bcfc0dc2fbd1f92c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446603"
---
# <a name="assemblyattributesgoheresm-class"></a><span data-ttu-id="34542-102">AssemblyAttributesGoHereSM sınıfı</span><span class="sxs-lookup"><span data-stu-id="34542-102">AssemblyAttributesGoHereSM Class</span></span>

<span data-ttu-id="34542-103">ALink tarafından özel öznitelikler hakkında bilgi depolamak için bir yer tutucu olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="34542-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>

## <a name="syntax"></a><span data-ttu-id="34542-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34542-104">Syntax</span></span>

```csharp
internal sealed class AssemblyAttributesGoHereSM
```

## <a name="remarks"></a><span data-ttu-id="34542-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="34542-105">Remarks</span></span>

<span data-ttu-id="34542-106">Bu türe yapılan başvurular, kaynakları derleme özel öznitelikleri içeren netmodule 'ler içine gömülebilir.</span><span class="sxs-lookup"><span data-stu-id="34542-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="34542-107">Bu türlere başvurular içeren bir veya daha fazla netmodule 'ler öğesinden bir derleme bildirimi oluştururken, ALink, gerçek özel öznitelikleri yaymak için bu başvurulara eklenen bilgileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="34542-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="34542-108">Bu nedenle, bu tür hiçbir şekilde örneklenemez ve yalnızca derleme işleminin bir parçası olarak kullanılır ve son derlemede hiçbir amaca uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="34542-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>

<span data-ttu-id="34542-109">Bu türe başvurular, güvenlikle ilgili ve çoklu kullanıma yönelik özel öznitelikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="34542-109">References to this type indicate custom attributes that are security related and multiple-use.</span></span>

<span data-ttu-id="34542-110">Bu türler, .NET Framework içinde "iç" olarak işaretlenir ve <xref:System.Runtime.CompilerServices> ad alanında bulunur.</span><span class="sxs-lookup"><span data-stu-id="34542-110">These types are marked "internal" within the .NET Framework and are located in the <xref:System.Runtime.CompilerServices> namespace.</span></span>

## <a name="requirements"></a><span data-ttu-id="34542-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="34542-111">Requirements</span></span>

<span data-ttu-id="34542-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="34542-112">mscorlib.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="34542-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34542-113">See also</span></span>

- [<span data-ttu-id="34542-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="34542-114">AssemblyAttributesGoHere</span></span>](assemblyattributesgohere.md)
- [<span data-ttu-id="34542-115">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="34542-115">AssemblyAttributesGoHereM</span></span>](assemblyattributesgoherem.md)
- [<span data-ttu-id="34542-116">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="34542-116">AssemblyAttributesGoHereS</span></span>](assemblyattributesgoheres.md)
