---
title: AssemblyAttributesGoHere sınıfı (System.Runtime.CompilerServices)
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 571c2f6723e827a1b385f77724c33703ae970ae3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775628"
---
# <a name="assemblyattributesgohere-class"></a><span data-ttu-id="310b7-102">AssemblyAttributesGoHere sınıfı</span><span class="sxs-lookup"><span data-stu-id="310b7-102">AssemblyAttributesGoHere Class</span></span>

<span data-ttu-id="310b7-103">ALINK tarafından özel öznitelikler hakkında bilgi depolamak için bir yer tutucu olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="310b7-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>

## <a name="syntax"></a><span data-ttu-id="310b7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="310b7-104">Syntax</span></span>

```csharp
internal sealed class AssemblyAttributesGoHere
```

## <a name="remarks"></a><span data-ttu-id="310b7-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="310b7-105">Remarks</span></span>

<span data-ttu-id="310b7-106">Bu tür başvurularını kaynakları içeren derlemenin özel öznitelikleri netmodule'ler içinde gömülü olması.</span><span class="sxs-lookup"><span data-stu-id="310b7-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="310b7-107">Bu tür başvurular içeren bir veya daha fazla netmodule'ler gelen bir derleme bildirimi oluşturulurken ALink bu başvuruları bağlı bilgileri yayma gerçek özel öznitelikler için kullanır.</span><span class="sxs-lookup"><span data-stu-id="310b7-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="310b7-108">Bu nedenle, bu tür hiç örneklenmemiş ve başvuruları yalnızca yapı işleminin bir parçası olarak kullanılır ve son derlemeye hiçbir amaca hizmet.</span><span class="sxs-lookup"><span data-stu-id="310b7-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>

<span data-ttu-id="310b7-109">Bu tür başvurularını güvenlikle ilgili olmayan özel öznitelikleri belirtmek ve çoklu kullanım değildir.</span><span class="sxs-lookup"><span data-stu-id="310b7-109">References to this type indicate custom attributes that are not security related and are not multiple-use.</span></span>

<span data-ttu-id="310b7-110">Bu tür ".NET Framework içinde iç" olarak işaretlenir ve bulunan <xref:System.Runtime.CompilerServices> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="310b7-110">These types are marked "internal" within the .NET Framework and are located in the <xref:System.Runtime.CompilerServices> namespace.</span></span>

## <a name="requirements"></a><span data-ttu-id="310b7-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="310b7-111">Requirements</span></span>

<span data-ttu-id="310b7-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="310b7-112">mscorlib.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="310b7-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="310b7-113">See also</span></span>

- [<span data-ttu-id="310b7-114">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="310b7-114">AssemblyAttributesGoHereM</span></span>](assemblyattributesgoherem.md)
- [<span data-ttu-id="310b7-115">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="310b7-115">AssemblyAttributesGoHereS</span></span>](assemblyattributesgoheres.md)
- [<span data-ttu-id="310b7-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="310b7-116">AssemblyAttributesGoHereSM</span></span>](assemblyattributesgoheresm.md)
