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
ms.openlocfilehash: 075f0ce7001573bb4e61a3e059e699d15275ea0b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403194"
---
# <a name="assemblyattributesgoherem"></a><span data-ttu-id="b1366-102">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="b1366-102">AssemblyAttributesGoHereM</span></span>
<span data-ttu-id="b1366-103">ALink tarafından yer tutucu olarak özel öznitelikler hakkında bilgi depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b1366-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1366-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1366-104">Syntax</span></span>  
  
```  
AssemblyAttributesGoHereM  
```  
  
## <a name="remarks"></a><span data-ttu-id="b1366-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b1366-105">Remarks</span></span>  
 <span data-ttu-id="b1366-106">Bu tür başvuruları, kaynaklarının derlemenin özel öznitelikleri içeren netmodule'ler katıştırılmış.</span><span class="sxs-lookup"><span data-stu-id="b1366-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="b1366-107">Bu tür başvuruları içeren bir veya daha fazla netmodule'ler derleme bildirimden oluştururken ALink gerçek özel öznitelikler yayma için bu başvurular bağlı bilgileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="b1366-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="b1366-108">Bu nedenle, bu tür hiçbir zaman örneği ve başvuruları yalnızca derleme işleminin bir parçası olarak kullanılır ve son derlemesinde hiçbir amaca hizmet eder.</span><span class="sxs-lookup"><span data-stu-id="b1366-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>  
  
 <span data-ttu-id="b1366-109">Bu tür başvuruları güvenlikle ilgili olmayan ancak çoklu kullanım özel öznitelikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1366-109">References to this type indicate custom attributes that are not security related but are multiple-use.</span></span>  
  
 <span data-ttu-id="b1366-110">Bu tür ".NET Framework içinde iç" olarak işaretlenir ve bulunan <xref:System.Runtime.CompilerServices>.</span><span class="sxs-lookup"><span data-stu-id="b1366-110">These types are marked "internal" within the .NET Framework, and are located in <xref:System.Runtime.CompilerServices>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1366-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b1366-111">Requirements</span></span>  
 <span data-ttu-id="b1366-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="b1366-112">mscorlib.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1366-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b1366-113">See Also</span></span>  
 [<span data-ttu-id="b1366-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="b1366-114">AssemblyAttributesGoHere</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgohere.md)  
 [<span data-ttu-id="b1366-115">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="b1366-115">AssemblyAttributesGoHereS</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheres.md)  
 [<span data-ttu-id="b1366-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="b1366-116">AssemblyAttributesGoHereSM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheresm.md)
