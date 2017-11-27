---
title: "LinkResource Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.LinkResource
api_location: alink.dll
api_type: COM
f1_keywords: LinkResource
helpviewer_keywords: LinkResource method
ms.assetid: c404acb3-4c59-4100-9a4c-483cbdb1d736
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8cb1f985c1d735fa20507ab90d478e97025c9e2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="linkresource-method"></a><span data-ttu-id="97238-102">LinkResource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="97238-102">LinkResource Method</span></span>
<span data-ttu-id="97238-103">Bir kaynak bağlantıları.</span><span class="sxs-lookup"><span data-stu-id="97238-103">Links in a resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97238-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="97238-104">Syntax</span></span>  
  
```  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="97238-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="97238-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="97238-106">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="97238-106">ID of the assembly.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="97238-107">Dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="97238-107">Name of the file.</span></span>  
  
 `pszNewLocation`  
 <span data-ttu-id="97238-108">Yeni dosya adı isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="97238-108">Optional new file name.</span></span> <span data-ttu-id="97238-109">NULL olmayan, `pszFileName` pszNewLocation için kopyalanacak.</span><span class="sxs-lookup"><span data-stu-id="97238-109">If non-NULL, `pszFileName` will be copied to pszNewLocation.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="97238-110">Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="97238-110">Name of the resource.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="97238-111">Erişilebilirlik bayrakları gibi `mrPublic` ve `mrPrivate`.</span><span class="sxs-lookup"><span data-stu-id="97238-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="97238-112">Bu parametre için geçirilebilir [DefineManifestResource yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).</span><span class="sxs-lookup"><span data-stu-id="97238-112">This parameter may be passed to [DefineManifestResource Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97238-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="97238-113">Return Value</span></span>  
 <span data-ttu-id="97238-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="97238-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97238-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="97238-115">Requirements</span></span>  
 <span data-ttu-id="97238-116">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="97238-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97238-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="97238-117">See Also</span></span>  
 [<span data-ttu-id="97238-118">Ialink arabirimi</span><span class="sxs-lookup"><span data-stu-id="97238-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="97238-119">Ialink2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="97238-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="97238-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="97238-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
