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
ms.openlocfilehash: 135938c4ed91423145ca46b743620f4236f7f818
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742249"
---
# <a name="assemblyattributesgoheres"></a><span data-ttu-id="089a1-102">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="089a1-102">AssemblyAttributesGoHereS</span></span>

<span data-ttu-id="089a1-103">ALINK tarafından özel öznitelikler hakkında bilgi depolamak için bir yer tutucu olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="089a1-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>

## <a name="syntax"></a><span data-ttu-id="089a1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="089a1-104">Syntax</span></span>

```csharp
internal sealed class AssemblyAttributesGoHereS
```

## <a name="remarks"></a><span data-ttu-id="089a1-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="089a1-105">Remarks</span></span>

<span data-ttu-id="089a1-106">Bu tür başvurularını kaynakları içeren derlemenin özel öznitelikleri netmodule'ler içinde gömülü olması.</span><span class="sxs-lookup"><span data-stu-id="089a1-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="089a1-107">Bu tür başvurular içeren bir veya daha fazla netmodule'ler gelen bir derleme bildirimi oluşturulurken ALink bu başvuruları bağlı bilgileri yayma gerçek özel öznitelikler için kullanır.</span><span class="sxs-lookup"><span data-stu-id="089a1-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="089a1-108">Bu nedenle, bu tür hiç örneklenmemiş ve başvuruları yalnızca yapı işleminin bir parçası olarak kullanılır ve son derlemeye hiçbir amaca hizmet.</span><span class="sxs-lookup"><span data-stu-id="089a1-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>

<span data-ttu-id="089a1-109">Bu tür başvurularını güvenlikle ilgili özel öznitelikleri belirtmek ve çoklu kullanım değildir.</span><span class="sxs-lookup"><span data-stu-id="089a1-109">References to this type indicate custom attributes that are security related and are not multiple-use.</span></span>

<span data-ttu-id="089a1-110">Bu tür ".NET Framework içinde iç" olarak işaretlenir ve bulunan <xref:System.Runtime.CompilerServices> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="089a1-110">These types are marked "internal" within the .NET Framework and are located in the <xref:System.Runtime.CompilerServices> namespace.</span></span>

## <a name="requirements"></a><span data-ttu-id="089a1-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="089a1-111">Requirements</span></span>

<span data-ttu-id="089a1-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="089a1-112">mscorlib.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="089a1-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="089a1-113">See also</span></span>

- [<span data-ttu-id="089a1-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="089a1-114">AssemblyAttributesGoHere</span></span>](assemblyattributesgohere.md)
- [<span data-ttu-id="089a1-115">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="089a1-115">AssemblyAttributesGoHereM</span></span>](assemblyattributesgoherem.md)
- [<span data-ttu-id="089a1-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="089a1-116">AssemblyAttributesGoHereSM</span></span>](assemblyattributesgoheresm.md)
