---
title: AssemblyAttributesGoHereM
ms.date: 03/30/2017
api_name:
- AssemblyAttributesGoHereM
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyAttributesGoHereM
helpviewer_keywords:
- AssemblyAttributesGoHereM type
- Alink API, AssemblyAttributesGoHereM type
ms.assetid: caaa8ba9-b4bb-4dd6-934d-57e436b2f3e5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bbd5428039144fd38796ed6865c24a605f236ccd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54733811"
---
# <a name="assemblyattributesgoherem"></a><span data-ttu-id="247cb-102">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="247cb-102">AssemblyAttributesGoHereM</span></span>
<span data-ttu-id="247cb-103">ALINK tarafından özel öznitelikler hakkında bilgi depolamak için bir yer tutucu olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="247cb-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="247cb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="247cb-104">Syntax</span></span>  
  
```  
AssemblyAttributesGoHereM  
```  
  
## <a name="remarks"></a><span data-ttu-id="247cb-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="247cb-105">Remarks</span></span>  
 <span data-ttu-id="247cb-106">Bu tür başvurularını kaynakları içeren derlemenin özel öznitelikleri netmodule'ler içinde gömülü olması.</span><span class="sxs-lookup"><span data-stu-id="247cb-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="247cb-107">Bu tür başvurular içeren bir veya daha fazla netmodule'ler gelen bir derleme bildirimi oluşturulurken ALink bu başvuruları bağlı bilgileri yayma gerçek özel öznitelikler için kullanır.</span><span class="sxs-lookup"><span data-stu-id="247cb-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="247cb-108">Bu nedenle, bu tür hiç örneklenmemiş ve başvuruları yalnızca yapı işleminin bir parçası olarak kullanılır ve son derlemeye hiçbir amaca hizmet.</span><span class="sxs-lookup"><span data-stu-id="247cb-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>  
  
 <span data-ttu-id="247cb-109">Bu tür başvurularını güvenlikle ilgili olmayan ancak çoklu kullanım özel özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="247cb-109">References to this type indicate custom attributes that are not security related but are multiple-use.</span></span>  
  
 <span data-ttu-id="247cb-110">Bu tür ".NET Framework içinde iç" olarak işaretlenir ve bulunan <xref:System.Runtime.CompilerServices>.</span><span class="sxs-lookup"><span data-stu-id="247cb-110">These types are marked "internal" within the .NET Framework, and are located in <xref:System.Runtime.CompilerServices>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="247cb-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="247cb-111">Requirements</span></span>  
 <span data-ttu-id="247cb-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="247cb-112">mscorlib.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="247cb-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="247cb-113">See also</span></span>
- [<span data-ttu-id="247cb-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="247cb-114">AssemblyAttributesGoHere</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgohere.md)
- [<span data-ttu-id="247cb-115">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="247cb-115">AssemblyAttributesGoHereS</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheres.md)
- [<span data-ttu-id="247cb-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="247cb-116">AssemblyAttributesGoHereSM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheresm.md)
