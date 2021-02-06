---
description: 'Daha fazla bilgi edinin: AssemblyAttributesGoHere Class'
title: AssemblyAttributesGoHere sınıfı (System. Runtime. CompilerServices)
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHere
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHere
helpviewer_keywords:
- AssemblyAttributesGoHere type
- Alink API, AssemblyAttributesGoHere type
ms.assetid: 7b26fcb6-94f4-4f09-933e-b33efe451f4f
topic_type:
- apiref
ms.openlocfilehash: b95ff377f7fa0ffc85136dd69eb4a32121a50dc2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638593"
---
# <a name="assemblyattributesgohere-class"></a><span data-ttu-id="2ab20-103">AssemblyAttributesGoHere sınıfı</span><span class="sxs-lookup"><span data-stu-id="2ab20-103">AssemblyAttributesGoHere Class</span></span>

<span data-ttu-id="2ab20-104">ALink tarafından özel öznitelikler hakkında bilgi depolamak için bir yer tutucu olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2ab20-104">Used by ALink as a placeholder to store information about custom attributes.</span></span>

## <a name="syntax"></a><span data-ttu-id="2ab20-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="2ab20-105">Syntax</span></span>

```csharp
internal sealed class AssemblyAttributesGoHere
```

## <a name="remarks"></a><span data-ttu-id="2ab20-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2ab20-106">Remarks</span></span>

<span data-ttu-id="2ab20-107">Bu türe yapılan başvurular, kaynakları derleme özel öznitelikleri içeren netmodule 'ler içine gömülebilir.</span><span class="sxs-lookup"><span data-stu-id="2ab20-107">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="2ab20-108">Bu türlere başvurular içeren bir veya daha fazla netmodule 'ler öğesinden bir derleme bildirimi oluştururken, ALink, gerçek özel öznitelikleri yaymak için bu başvurulara eklenen bilgileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="2ab20-108">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="2ab20-109">Bu nedenle, bu tür hiçbir şekilde örneklenemez ve yalnızca derleme işleminin bir parçası olarak kullanılır ve son derlemede hiçbir amaca uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="2ab20-109">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>

<span data-ttu-id="2ab20-110">Bu türe başvurular, güvenlikle ilgili olmayan ve çoklu kullanım olmayan özel öznitelikleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="2ab20-110">References to this type indicate custom attributes that are not security related and are not multiple-use.</span></span>

<span data-ttu-id="2ab20-111">Bu türler, .NET Framework içinde "iç" olarak işaretlenir ve <xref:System.Runtime.CompilerServices> ad alanında bulunur.</span><span class="sxs-lookup"><span data-stu-id="2ab20-111">These types are marked "internal" within the .NET Framework and are located in the <xref:System.Runtime.CompilerServices> namespace.</span></span>

## <a name="requirements"></a><span data-ttu-id="2ab20-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2ab20-112">Requirements</span></span>

<span data-ttu-id="2ab20-113">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="2ab20-113">mscorlib.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="2ab20-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ab20-114">See also</span></span>

- [<span data-ttu-id="2ab20-115">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="2ab20-115">AssemblyAttributesGoHereM</span></span>](assemblyattributesgoherem.md)
- [<span data-ttu-id="2ab20-116">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="2ab20-116">AssemblyAttributesGoHereS</span></span>](assemblyattributesgoheres.md)
- [<span data-ttu-id="2ab20-117">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="2ab20-117">AssemblyAttributesGoHereSM</span></span>](assemblyattributesgoheresm.md)
