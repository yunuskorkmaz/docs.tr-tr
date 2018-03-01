---
title: "EmbedResource Yöntemi"
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
- IALink.EmbedResource
- EmbedResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmbedResource
helpviewer_keywords:
- EmbedResource method
ms.assetid: 667bd954-6dc6-4020-a3cb-0e8224179993
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 815e4b6abbb56b0998a12c096f0ba7cb678778ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="embedresource-method"></a><span data-ttu-id="3f4ee-102">EmbedResource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f4ee-102">EmbedResource Method</span></span>
<span data-ttu-id="3f4ee-103">Katıştırılmış bir kaynağı bildirir.</span><span class="sxs-lookup"><span data-stu-id="3f4ee-103">Declares an embedded resource.</span></span> <span data-ttu-id="3f4ee-104">Bu yöntem kaynağın gerçekte katıştırmak değil.</span><span class="sxs-lookup"><span data-stu-id="3f4ee-104">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f4ee-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f4ee-105">Syntax</span></span>  
  
```  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3f4ee-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3f4ee-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="3f4ee-107">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="3f4ee-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="3f4ee-108">Dosya belirteci ya da derleme kaynağı içeren dosyanın kimliği.</span><span class="sxs-lookup"><span data-stu-id="3f4ee-108">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="3f4ee-109">Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="3f4ee-109">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="3f4ee-110">RVA kaynaktan uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="3f4ee-110">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="3f4ee-111">Erişilebilirlik bayrakları gibi `mrPublic` ve `mrPrivate`.</span><span class="sxs-lookup"><span data-stu-id="3f4ee-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="3f4ee-112">Bu bayrakların geçirilen [DefineExportedType yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="3f4ee-112">These flags may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f4ee-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3f4ee-113">Return Value</span></span>  
 <span data-ttu-id="3f4ee-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="3f4ee-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f4ee-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f4ee-115">Requirements</span></span>  
 <span data-ttu-id="3f4ee-116">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3f4ee-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f4ee-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3f4ee-117">See Also</span></span>  
 [<span data-ttu-id="3f4ee-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f4ee-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="3f4ee-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f4ee-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="3f4ee-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="3f4ee-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
