---
title: AssemblyAttributesGoHereS
ms.date: 03/30/2017
api_name:
- AssemblyAttributesGoHereS
api_location:
- alink.dll
api_type:
- COM
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
ms.openlocfilehash: d68450d05f667851404a009c0984f8722253e71e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402916"
---
# <a name="assemblyattributesgoheres"></a><span data-ttu-id="d5c64-102">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="d5c64-102">AssemblyAttributesGoHereS</span></span>
<span data-ttu-id="d5c64-103">ALink tarafından yer tutucu olarak özel öznitelikler hakkında bilgi depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d5c64-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5c64-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d5c64-104">Syntax</span></span>  
  
```  
AssemblyAttributesGoHereS  
```  
  
## <a name="remarks"></a><span data-ttu-id="d5c64-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d5c64-105">Remarks</span></span>  
 <span data-ttu-id="d5c64-106">Bu tür başvuruları, kaynaklarının derlemenin özel öznitelikleri içeren netmodule'ler katıştırılmış.</span><span class="sxs-lookup"><span data-stu-id="d5c64-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="d5c64-107">Bu tür başvuruları içeren bir veya daha fazla netmodule'ler derleme bildirimden oluştururken ALink gerçek özel öznitelikler yayma için bu başvurular bağlı bilgileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="d5c64-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="d5c64-108">Bu nedenle, bu tür hiçbir zaman örneği ve başvuruları yalnızca derleme işleminin bir parçası olarak kullanılır ve son derlemesinde hiçbir amaca hizmet eder.</span><span class="sxs-lookup"><span data-stu-id="d5c64-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>  
  
 <span data-ttu-id="d5c64-109">Bu tür başvuruları güvenlikle ilgili özel öznitelikleri belirtmek ve çoklu kullanım değildir.</span><span class="sxs-lookup"><span data-stu-id="d5c64-109">References to this type indicate custom attributes that are security related and are not multiple-use.</span></span>  
  
 <span data-ttu-id="d5c64-110">Bu tür ".NET Framework içinde iç" olarak işaretlenir ve bulunan <xref:System.Runtime.CompilerServices>.</span><span class="sxs-lookup"><span data-stu-id="d5c64-110">These types are marked "internal" within the .NET Framework, and are located in <xref:System.Runtime.CompilerServices>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5c64-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d5c64-111">Requirements</span></span>  
 <span data-ttu-id="d5c64-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="d5c64-112">mscorlib.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5c64-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d5c64-113">See Also</span></span>  
 [<span data-ttu-id="d5c64-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="d5c64-114">AssemblyAttributesGoHere</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgohere.md)  
 [<span data-ttu-id="d5c64-115">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="d5c64-115">AssemblyAttributesGoHereM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoherem.md)  
 [<span data-ttu-id="d5c64-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="d5c64-116">AssemblyAttributesGoHereSM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheresm.md)
