---
title: ImportFileEx Yöntemi
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx
helpviewer_keywords:
- ImportFileEx method
ms.assetid: ad276f3f-b303-46ac-97e0-66a377adaa4f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b3cf91ad4e048ddfccb4086f36923f33d754ac0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59131046"
---
# <a name="importfileex-method"></a><span data-ttu-id="d8cdf-102">ImportFileEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8cdf-102">ImportFileEx Method</span></span>
<span data-ttu-id="d8cdf-103">İçeri aktarmalar, derleme veya modül ilişkisiz gösterilir.</span><span class="sxs-lookup"><span data-stu-id="d8cdf-103">Imports indicated assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8cdf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8cdf-104">Syntax</span></span>  
  
```  
HRESULT ImportFileEx(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8cdf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d8cdf-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="d8cdf-106">Alınacağı dosyasının tam adı.</span><span class="sxs-lookup"><span data-stu-id="d8cdf-106">Fully qualified name of file from which to import.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="d8cdf-107">Hedef dosya isteğe bağlı adı.</span><span class="sxs-lookup"><span data-stu-id="d8cdf-107">Optional name of target file.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="d8cdf-108">TRUE ise Importtypes kullanılır, aksi takdirde içe aktarma el ile uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d8cdf-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="d8cdf-109">Boyunca geçirilecek bayrakları [OpenScope yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span><span class="sxs-lookup"><span data-stu-id="d8cdf-109">Flags to be passed along to [OpenScope Method](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="d8cdf-110">İçeri aktarılan dosya Kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="d8cdf-110">Receives ID of the file being imported.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="d8cdf-111">Derleme içeri aktarma kapsamı alır [Imetadataassemblyımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d8cdf-111">Receives assembly import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="d8cdf-112">Dosya bir derleme değilse NULL olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d8cdf-112">Is set to NULL if file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="d8cdf-113">İçeri aktarılan dosyaları ve/veya kapsamları sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="d8cdf-113">Receives count of imported files and/or scopes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d8cdf-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d8cdf-114">Return Value</span></span>  
 <span data-ttu-id="d8cdf-115">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="d8cdf-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8cdf-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8cdf-116">Requirements</span></span>  
 <span data-ttu-id="d8cdf-117">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d8cdf-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8cdf-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8cdf-118">See also</span></span>

- [<span data-ttu-id="d8cdf-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8cdf-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="d8cdf-120">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8cdf-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="d8cdf-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="d8cdf-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
