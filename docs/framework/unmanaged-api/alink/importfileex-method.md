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
ms.openlocfilehash: fcf714cb0c1c1dd59ae2ec56279870c0bb3e1c4a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741728"
---
# <a name="importfileex-method"></a><span data-ttu-id="c5fe5-102">ImportFileEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c5fe5-102">ImportFileEx Method</span></span>
<span data-ttu-id="c5fe5-103">İçeri aktarmalar, derleme veya modül ilişkisiz gösterilir.</span><span class="sxs-lookup"><span data-stu-id="c5fe5-103">Imports indicated assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5fe5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5fe5-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="c5fe5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c5fe5-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="c5fe5-106">Alınacağı dosyasının tam adı.</span><span class="sxs-lookup"><span data-stu-id="c5fe5-106">Fully qualified name of file from which to import.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="c5fe5-107">Hedef dosya isteğe bağlı adı.</span><span class="sxs-lookup"><span data-stu-id="c5fe5-107">Optional name of target file.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="c5fe5-108">TRUE ise Importtypes kullanılır, aksi takdirde içe aktarma el ile uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5fe5-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="c5fe5-109">Boyunca geçirilecek bayrakları [OpenScope yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span><span class="sxs-lookup"><span data-stu-id="c5fe5-109">Flags to be passed along to [OpenScope Method](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="c5fe5-110">İçeri aktarılan dosya Kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="c5fe5-110">Receives ID of the file being imported.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="c5fe5-111">Derleme içeri aktarma kapsamı alır [Imetadataassemblyımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="c5fe5-111">Receives assembly import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="c5fe5-112">Dosya bir derleme değilse NULL olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c5fe5-112">Is set to NULL if file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="c5fe5-113">İçeri aktarılan dosyaları ve/veya kapsamları sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="c5fe5-113">Receives count of imported files and/or scopes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c5fe5-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c5fe5-114">Return Value</span></span>  
 <span data-ttu-id="c5fe5-115">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="c5fe5-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5fe5-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c5fe5-116">Requirements</span></span>  
 <span data-ttu-id="c5fe5-117">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c5fe5-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5fe5-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5fe5-118">See also</span></span>

- [<span data-ttu-id="c5fe5-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c5fe5-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="c5fe5-120">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c5fe5-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="c5fe5-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="c5fe5-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
