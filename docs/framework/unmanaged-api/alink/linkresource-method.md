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
ms.openlocfilehash: 4f75ebc3a40bddbaf2347b9ef559139888f83900
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401114"
---
# <a name="linkresource-method"></a><span data-ttu-id="bf5b6-102">LinkResource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bf5b6-102">LinkResource Method</span></span>
<span data-ttu-id="bf5b6-103">Bir kaynak bağlantıları.</span><span class="sxs-lookup"><span data-stu-id="bf5b6-103">Links in a resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf5b6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bf5b6-104">Syntax</span></span>  
  
```  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bf5b6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bf5b6-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="bf5b6-106">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="bf5b6-106">ID of the assembly.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="bf5b6-107">Dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="bf5b6-107">Name of the file.</span></span>  
  
 `pszNewLocation`  
 <span data-ttu-id="bf5b6-108">Yeni dosya adı isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="bf5b6-108">Optional new file name.</span></span> <span data-ttu-id="bf5b6-109">NULL olmayan, `pszFileName` pszNewLocation için kopyalanacak.</span><span class="sxs-lookup"><span data-stu-id="bf5b6-109">If non-NULL, `pszFileName` will be copied to pszNewLocation.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="bf5b6-110">Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="bf5b6-110">Name of the resource.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="bf5b6-111">Erişilebilirlik bayrakları gibi `mrPublic` ve `mrPrivate`.</span><span class="sxs-lookup"><span data-stu-id="bf5b6-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="bf5b6-112">Bu parametre için geçirilebilir [DefineManifestResource yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).</span><span class="sxs-lookup"><span data-stu-id="bf5b6-112">This parameter may be passed to [DefineManifestResource Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bf5b6-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bf5b6-113">Return Value</span></span>  
 <span data-ttu-id="bf5b6-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="bf5b6-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf5b6-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bf5b6-115">Requirements</span></span>  
 <span data-ttu-id="bf5b6-116">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="bf5b6-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf5b6-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bf5b6-117">See Also</span></span>  
 [<span data-ttu-id="bf5b6-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bf5b6-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="bf5b6-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bf5b6-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="bf5b6-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="bf5b6-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
