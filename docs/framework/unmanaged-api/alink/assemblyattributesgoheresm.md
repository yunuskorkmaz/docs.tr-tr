---
title: AssemblyAttributesGoHereSM
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6d47ca3a9134266d1c40447cea6eb8aaf2cc9eb9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706303"
---
# <a name="assemblyattributesgoheresm"></a><span data-ttu-id="ac07a-102">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="ac07a-102">AssemblyAttributesGoHereSM</span></span>
<span data-ttu-id="ac07a-103">ALINK tarafından özel öznitelikler hakkında bilgi depolamak için bir yer tutucu olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ac07a-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac07a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ac07a-104">Syntax</span></span>  
  
```  
AssemblyAttributeGoHereSM  
```  
  
## <a name="remarks"></a><span data-ttu-id="ac07a-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ac07a-105">Remarks</span></span>  
 <span data-ttu-id="ac07a-106">Bu tür başvurularını kaynakları içeren derlemenin özel öznitelikleri netmodule'ler içinde gömülü olması.</span><span class="sxs-lookup"><span data-stu-id="ac07a-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="ac07a-107">Bu tür başvurular içeren bir veya daha fazla netmodule'ler gelen bir derleme bildirimi oluşturulurken ALink bu başvuruları bağlı bilgileri yayma gerçek özel öznitelikler için kullanır.</span><span class="sxs-lookup"><span data-stu-id="ac07a-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="ac07a-108">Bu nedenle, bu tür hiç örneklenmemiş ve başvuruları yalnızca yapı işleminin bir parçası olarak kullanılır ve son derlemeye hiçbir amaca hizmet.</span><span class="sxs-lookup"><span data-stu-id="ac07a-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>  
  
 <span data-ttu-id="ac07a-109">Bu tür başvurularını güvenlik ilgili ve birden çok kullanımı özel öznitelikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac07a-109">References to this type indicate custom attributes that are security related and multiple-use.</span></span>  
  
 <span data-ttu-id="ac07a-110">Bu tür ".NET Framework içinde iç" olarak işaretlenir ve bulunan <xref:System.Runtime.CompilerServices>.</span><span class="sxs-lookup"><span data-stu-id="ac07a-110">These types are marked "internal" within the .NET Framework, and are located in <xref:System.Runtime.CompilerServices>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac07a-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac07a-111">Requirements</span></span>  
 <span data-ttu-id="ac07a-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="ac07a-112">mscorlib.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac07a-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac07a-113">See also</span></span>
- [<span data-ttu-id="ac07a-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="ac07a-114">AssemblyAttributesGoHere</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgohere.md)
- [<span data-ttu-id="ac07a-115">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="ac07a-115">AssemblyAttributesGoHereM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoherem.md)
- [<span data-ttu-id="ac07a-116">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="ac07a-116">AssemblyAttributesGoHereS</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheres.md)
