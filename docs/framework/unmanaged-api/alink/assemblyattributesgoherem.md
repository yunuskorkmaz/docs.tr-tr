---
title: AssemblyAttributesGoHereM
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: be60619077a04784152ece1a64551a1b9e5eb80a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="assemblyattributesgoherem"></a><span data-ttu-id="f42a2-102">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="f42a2-102">AssemblyAttributesGoHereM</span></span>
<span data-ttu-id="f42a2-103">ALink tarafından yer tutucu olarak özel öznitelikler hakkında bilgi depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f42a2-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f42a2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f42a2-104">Syntax</span></span>  
  
```  
AssemblyAttributesGoHereM  
```  
  
## <a name="remarks"></a><span data-ttu-id="f42a2-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f42a2-105">Remarks</span></span>  
 <span data-ttu-id="f42a2-106">Bu tür başvuruları, kaynaklarının derlemenin özel öznitelikleri içeren netmodule'ler katıştırılmış.</span><span class="sxs-lookup"><span data-stu-id="f42a2-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="f42a2-107">Bu tür başvuruları içeren bir veya daha fazla netmodule'ler derleme bildirimden oluştururken ALink gerçek özel öznitelikler yayma için bu başvurular bağlı bilgileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="f42a2-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="f42a2-108">Bu nedenle, bu tür hiçbir zaman örneği ve başvuruları yalnızca derleme işleminin bir parçası olarak kullanılır ve son derlemesinde hiçbir amaca hizmet eder.</span><span class="sxs-lookup"><span data-stu-id="f42a2-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>  
  
 <span data-ttu-id="f42a2-109">Bu tür başvuruları güvenlikle ilgili olmayan ancak çoklu kullanım özel öznitelikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="f42a2-109">References to this type indicate custom attributes that are not security related but are multiple-use.</span></span>  
  
 <span data-ttu-id="f42a2-110">Bu tür ".NET Framework içinde iç" olarak işaretlenir ve bulunan <xref:System.Runtime.CompilerServices>.</span><span class="sxs-lookup"><span data-stu-id="f42a2-110">These types are marked "internal" within the .NET Framework, and are located in <xref:System.Runtime.CompilerServices>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f42a2-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f42a2-111">Requirements</span></span>  
 <span data-ttu-id="f42a2-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="f42a2-112">mscorlib.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f42a2-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f42a2-113">See Also</span></span>  
 [<span data-ttu-id="f42a2-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="f42a2-114">AssemblyAttributesGoHere</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgohere.md)  
 [<span data-ttu-id="f42a2-115">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="f42a2-115">AssemblyAttributesGoHereS</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheres.md)  
 [<span data-ttu-id="f42a2-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="f42a2-116">AssemblyAttributesGoHereSM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheresm.md)
