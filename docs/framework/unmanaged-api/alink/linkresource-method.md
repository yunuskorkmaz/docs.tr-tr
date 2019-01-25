---
title: LinkResource Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.LinkResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- LinkResource
helpviewer_keywords:
- LinkResource method
ms.assetid: c404acb3-4c59-4100-9a4c-483cbdb1d736
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7b0b5c6e70afffd12d3f0cdbbb92b20ac3a949e2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54635019"
---
# <a name="linkresource-method"></a><span data-ttu-id="294e8-102">LinkResource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="294e8-102">LinkResource Method</span></span>
<span data-ttu-id="294e8-103">Bir kaynak bağlantıları.</span><span class="sxs-lookup"><span data-stu-id="294e8-103">Links in a resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="294e8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="294e8-104">Syntax</span></span>  
  
```  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="294e8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="294e8-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="294e8-106">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="294e8-106">ID of the assembly.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="294e8-107">Dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="294e8-107">Name of the file.</span></span>  
  
 `pszNewLocation`  
 <span data-ttu-id="294e8-108">Yeni dosya adı isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="294e8-108">Optional new file name.</span></span> <span data-ttu-id="294e8-109">NULL olmayan, `pszFileName` pszNewLocation için kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="294e8-109">If non-NULL, `pszFileName` will be copied to pszNewLocation.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="294e8-110">Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="294e8-110">Name of the resource.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="294e8-111">Erişilebilirlik bayrakları gibi `mrPublic` ve `mrPrivate`.</span><span class="sxs-lookup"><span data-stu-id="294e8-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="294e8-112">Bu parametre için geçirilebilir [DefineManifestResource yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).</span><span class="sxs-lookup"><span data-stu-id="294e8-112">This parameter may be passed to [DefineManifestResource Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="294e8-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="294e8-113">Return Value</span></span>  
 <span data-ttu-id="294e8-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="294e8-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="294e8-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="294e8-115">Requirements</span></span>  
 <span data-ttu-id="294e8-116">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="294e8-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="294e8-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="294e8-117">See also</span></span>
- [<span data-ttu-id="294e8-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="294e8-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="294e8-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="294e8-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="294e8-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="294e8-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
