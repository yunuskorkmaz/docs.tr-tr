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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 74447f52c75ae22e513c6f07950630d37bad191a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969836"
---
# <a name="assemblyattributesgoheres"></a><span data-ttu-id="2d91f-102">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="2d91f-102">AssemblyAttributesGoHereS</span></span>

<span data-ttu-id="2d91f-103">ALINK tarafından özel öznitelikler hakkında bilgi depolamak için bir yer tutucu olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2d91f-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>

## <a name="syntax"></a><span data-ttu-id="2d91f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2d91f-104">Syntax</span></span>

```
internal sealed class AssemblyAttributesGoHereS
```

## <a name="remarks"></a><span data-ttu-id="2d91f-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d91f-105">Remarks</span></span>

<span data-ttu-id="2d91f-106">Bu tür başvurularını kaynakları içeren derlemenin özel öznitelikleri netmodule'ler içinde gömülü olması.</span><span class="sxs-lookup"><span data-stu-id="2d91f-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="2d91f-107">Bu tür başvurular içeren bir veya daha fazla netmodule'ler gelen bir derleme bildirimi oluşturulurken ALink bu başvuruları bağlı bilgileri yayma gerçek özel öznitelikler için kullanır.</span><span class="sxs-lookup"><span data-stu-id="2d91f-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="2d91f-108">Bu nedenle, bu tür hiç örneklenmemiş ve başvuruları yalnızca yapı işleminin bir parçası olarak kullanılır ve son derlemeye hiçbir amaca hizmet.</span><span class="sxs-lookup"><span data-stu-id="2d91f-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>

<span data-ttu-id="2d91f-109">Bu tür başvurularını güvenlikle ilgili özel öznitelikleri belirtmek ve çoklu kullanım değildir.</span><span class="sxs-lookup"><span data-stu-id="2d91f-109">References to this type indicate custom attributes that are security related and are not multiple-use.</span></span>

<span data-ttu-id="2d91f-110">Bu tür ".NET Framework içinde iç" olarak işaretlenir ve bulunan <xref:System.Runtime.CompilerServices> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="2d91f-110">These types are marked "internal" within the .NET Framework and are located in the <xref:System.Runtime.CompilerServices> namespace.</span></span>

## <a name="requirements"></a><span data-ttu-id="2d91f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2d91f-111">Requirements</span></span>

<span data-ttu-id="2d91f-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="2d91f-112">mscorlib.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="2d91f-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d91f-113">See also</span></span>

- [<span data-ttu-id="2d91f-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="2d91f-114">AssemblyAttributesGoHere</span></span>](assemblyattributesgohere.md)
- [<span data-ttu-id="2d91f-115">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="2d91f-115">AssemblyAttributesGoHereM</span></span>](assemblyattributesgoherem.md)
- [<span data-ttu-id="2d91f-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="2d91f-116">AssemblyAttributesGoHereSM</span></span>](assemblyattributesgoheresm.md)
