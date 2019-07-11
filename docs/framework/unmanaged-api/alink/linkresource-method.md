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
ms.openlocfilehash: 335d80255f7a3f5a22e8a69aa91c9e5b0843ea1e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741595"
---
# <a name="linkresource-method"></a><span data-ttu-id="f74d5-102">LinkResource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f74d5-102">LinkResource Method</span></span>
<span data-ttu-id="f74d5-103">Bir kaynak bağlantıları.</span><span class="sxs-lookup"><span data-stu-id="f74d5-103">Links in a resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f74d5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f74d5-104">Syntax</span></span>  
  
```cpp  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="f74d5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f74d5-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="f74d5-106">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="f74d5-106">ID of the assembly.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="f74d5-107">Dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="f74d5-107">Name of the file.</span></span>  
  
 `pszNewLocation`  
 <span data-ttu-id="f74d5-108">Yeni dosya adı isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="f74d5-108">Optional new file name.</span></span> <span data-ttu-id="f74d5-109">NULL olmayan, `pszFileName` pszNewLocation için kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="f74d5-109">If non-NULL, `pszFileName` will be copied to pszNewLocation.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="f74d5-110">Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="f74d5-110">Name of the resource.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="f74d5-111">Erişilebilirlik bayrakları gibi `mrPublic` ve `mrPrivate`.</span><span class="sxs-lookup"><span data-stu-id="f74d5-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="f74d5-112">Bu parametre için geçirilebilir [DefineManifestResource yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).</span><span class="sxs-lookup"><span data-stu-id="f74d5-112">This parameter may be passed to [DefineManifestResource Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f74d5-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f74d5-113">Return Value</span></span>  
 <span data-ttu-id="f74d5-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="f74d5-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f74d5-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f74d5-115">Requirements</span></span>  
 <span data-ttu-id="f74d5-116">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f74d5-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f74d5-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f74d5-117">See also</span></span>

- [<span data-ttu-id="f74d5-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f74d5-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="f74d5-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f74d5-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="f74d5-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="f74d5-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
