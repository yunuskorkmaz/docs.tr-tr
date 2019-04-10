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
ms.openlocfilehash: 622e57aedf6c49e95dc2d7e40ba598361b3e6a26
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222867"
---
# <a name="importtypes-method"></a><span data-ttu-id="29d58-102">ImportTypes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="29d58-102">ImportTypes Method</span></span>
<span data-ttu-id="29d58-103">Türleri aracılığıyla alınan her bir kapsamdan içeri aktarma başlatır [ImportFile yöntemi](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="29d58-103">Initiates the importing of types from each scope imported via [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29d58-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="29d58-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="29d58-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="29d58-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="29d58-106">Almak için derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="29d58-106">ID of the assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="29d58-107">Alınacak dosya kimliği.</span><span class="sxs-lookup"><span data-stu-id="29d58-107">ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="29d58-108">İçeri aktarmak için sıfır tabanlı kapsam.</span><span class="sxs-lookup"><span data-stu-id="29d58-108">Zero-based scope to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="29d58-109">Numaralandırıcı tanıtıcı türleri için bu kapsamda yer alır.</span><span class="sxs-lookup"><span data-stu-id="29d58-109">Receives enumerator handle for the types in this scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="29d58-110">İsteğe bağlı olarak alan [Imetadataımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="29d58-110">Optionally receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="29d58-111">İsteğe bağlı olarak belirtilen kapsamda türleri sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="29d58-111">Optionally receives count of types in the indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29d58-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="29d58-112">Return Value</span></span>  
 <span data-ttu-id="29d58-113">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="29d58-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29d58-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="29d58-114">Requirements</span></span>  
 <span data-ttu-id="29d58-115">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="29d58-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29d58-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29d58-116">See also</span></span>

- [<span data-ttu-id="29d58-117">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="29d58-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="29d58-118">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="29d58-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="29d58-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="29d58-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
