---
title: AssemblyAttributesGoHere
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
- AssemblyAttributesGoHere
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyAttributesGoHere
helpviewer_keywords:
- AssemblyAttributesGoHere type
- Alink API, AssemblyAttributesGoHere type
ms.assetid: 7b26fcb6-94f4-4f09-933e-b33efe451f4f
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f3363ac5bd53688cfaa667a57afce17b6b52b1f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="assemblyattributesgohere"></a><span data-ttu-id="b96d7-102">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="b96d7-102">AssemblyAttributesGoHere</span></span>
<span data-ttu-id="b96d7-103">ALink tarafından yer tutucu olarak özel öznitelikler hakkında bilgi depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b96d7-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b96d7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b96d7-104">Syntax</span></span>  
  
```  
AssemblyAttributesGoHere  
```  
  
## <a name="remarks"></a><span data-ttu-id="b96d7-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b96d7-105">Remarks</span></span>  
 <span data-ttu-id="b96d7-106">Bu tür başvuruları, kaynaklarının derlemenin özel öznitelikleri içeren netmodule'ler katıştırılmış.</span><span class="sxs-lookup"><span data-stu-id="b96d7-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="b96d7-107">Bu tür başvuruları içeren bir veya daha fazla netmodule'ler derleme bildirimden oluştururken ALink gerçek özel öznitelikler yayma için bu başvurular bağlı bilgileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="b96d7-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="b96d7-108">Bu nedenle, bu tür hiçbir zaman örneği ve başvuruları yalnızca derleme işleminin bir parçası olarak kullanılır ve son derlemesinde hiçbir amaca hizmet eder.</span><span class="sxs-lookup"><span data-stu-id="b96d7-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>  
  
 <span data-ttu-id="b96d7-109">Bu tür başvuruları güvenlikle ilgili olmayan özel öznitelikleri belirtmek ve çoklu kullanım değildir.</span><span class="sxs-lookup"><span data-stu-id="b96d7-109">References to this type indicate custom attributes that are not security related and are not multiple-use.</span></span>  
  
 <span data-ttu-id="b96d7-110">Bu tür ".NET Framework içinde iç" olarak işaretlenir ve bulunan <xref:System.Runtime.CompilerServices>.</span><span class="sxs-lookup"><span data-stu-id="b96d7-110">These types are marked "internal" within the .NET Framework, and are located in <xref:System.Runtime.CompilerServices>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b96d7-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b96d7-111">Requirements</span></span>  
 <span data-ttu-id="b96d7-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="b96d7-112">mscorlib.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b96d7-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b96d7-113">See Also</span></span>  
 [<span data-ttu-id="b96d7-114">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="b96d7-114">AssemblyAttributesGoHereM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoherem.md)  
 [<span data-ttu-id="b96d7-115">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="b96d7-115">AssemblyAttributesGoHereS</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheres.md)  
 [<span data-ttu-id="b96d7-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="b96d7-116">AssemblyAttributesGoHereSM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheresm.md)
