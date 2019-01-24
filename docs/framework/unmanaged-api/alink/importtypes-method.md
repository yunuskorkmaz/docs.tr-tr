---
title: ImportTypes Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.ImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes
helpviewer_keywords:
- ImportTypes method
ms.assetid: 351d4b4c-c939-486d-9471-51914a55f471
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6591fb4a2b4944dc0d02f70f0f90ffd87e071c47
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54735015"
---
# <a name="importtypes-method"></a><span data-ttu-id="af915-102">ImportTypes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="af915-102">ImportTypes Method</span></span>
<span data-ttu-id="af915-103">Türleri aracılığıyla alınan her bir kapsamdan içeri aktarma başlatır [ImportFile yöntemi](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="af915-103">Initiates the importing of types from each scope imported via [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af915-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="af915-104">Syntax</span></span>  
  
```  
HRESULT ImportTypes(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="af915-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="af915-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="af915-106">Almak için derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="af915-106">ID of the assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="af915-107">Alınacak dosya kimliği.</span><span class="sxs-lookup"><span data-stu-id="af915-107">ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="af915-108">İçeri aktarmak için sıfır tabanlı kapsam.</span><span class="sxs-lookup"><span data-stu-id="af915-108">Zero-based scope to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="af915-109">Numaralandırıcı tanıtıcı türleri için bu kapsamda yer alır.</span><span class="sxs-lookup"><span data-stu-id="af915-109">Receives enumerator handle for the types in this scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="af915-110">İsteğe bağlı olarak alan [Imetadataımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="af915-110">Optionally receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="af915-111">İsteğe bağlı olarak belirtilen kapsamda türleri sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="af915-111">Optionally receives count of types in the indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="af915-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="af915-112">Return Value</span></span>  
 <span data-ttu-id="af915-113">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="af915-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af915-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="af915-114">Requirements</span></span>  
 <span data-ttu-id="af915-115">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="af915-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af915-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af915-116">See also</span></span>
- [<span data-ttu-id="af915-117">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="af915-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="af915-118">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="af915-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="af915-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="af915-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
