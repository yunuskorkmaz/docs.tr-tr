---
title: AssemblyAttributesGoHereSM
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
- AssemblyAttributesGoHereSM
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyAttributesGoHereSM
helpviewer_keywords:
- AssemblyAttributesGoHereSM type
- Alink API, AssemblyAttributesGoHereSM type
ms.assetid: 4cf9bf39-1527-49e0-a0e9-55e7a018bf66
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5a753d596d198f7645fc44c48de9c360e15cc269
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="assemblyattributesgoheresm"></a><span data-ttu-id="009de-102">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="009de-102">AssemblyAttributesGoHereSM</span></span>
<span data-ttu-id="009de-103">ALink tarafından yer tutucu olarak özel öznitelikler hakkında bilgi depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="009de-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="009de-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="009de-104">Syntax</span></span>  
  
```  
AssemblyAttributeGoHereSM  
```  
  
## <a name="remarks"></a><span data-ttu-id="009de-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="009de-105">Remarks</span></span>  
 <span data-ttu-id="009de-106">Bu tür başvuruları, kaynaklarının derlemenin özel öznitelikleri içeren netmodule'ler katıştırılmış.</span><span class="sxs-lookup"><span data-stu-id="009de-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="009de-107">Bu tür başvuruları içeren bir veya daha fazla netmodule'ler derleme bildirimden oluştururken ALink gerçek özel öznitelikler yayma için bu başvurular bağlı bilgileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="009de-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="009de-108">Bu nedenle, bu tür hiçbir zaman örneği ve başvuruları yalnızca derleme işleminin bir parçası olarak kullanılır ve son derlemesinde hiçbir amaca hizmet eder.</span><span class="sxs-lookup"><span data-stu-id="009de-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>  
  
 <span data-ttu-id="009de-109">Bu tür başvuruları güvenlik ilgili ve çoklu kullanım özel öznitelikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="009de-109">References to this type indicate custom attributes that are security related and multiple-use.</span></span>  
  
 <span data-ttu-id="009de-110">Bu tür ".NET Framework içinde iç" olarak işaretlenir ve bulunan <xref:System.Runtime.CompilerServices>.</span><span class="sxs-lookup"><span data-stu-id="009de-110">These types are marked "internal" within the .NET Framework, and are located in <xref:System.Runtime.CompilerServices>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="009de-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="009de-111">Requirements</span></span>  
 <span data-ttu-id="009de-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="009de-112">mscorlib.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="009de-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="009de-113">See Also</span></span>  
 [<span data-ttu-id="009de-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="009de-114">AssemblyAttributesGoHere</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgohere.md)  
 [<span data-ttu-id="009de-115">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="009de-115">AssemblyAttributesGoHereM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoherem.md)  
 [<span data-ttu-id="009de-116">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="009de-116">AssemblyAttributesGoHereS</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheres.md)
