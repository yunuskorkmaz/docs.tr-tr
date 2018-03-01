---
title: "ImportTypes Yöntemi"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 39e7cfb3c811a89ae88d6984946f72a9b1f469db
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="importtypes-method"></a><span data-ttu-id="9736a-102">ImportTypes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9736a-102">ImportTypes Method</span></span>
<span data-ttu-id="9736a-103">Üzerinden içe aktarılan her kapsam türlerinden alma başlatır [ImportFile yöntemi](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="9736a-103">Initiates the importing of types from each scope imported via [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9736a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9736a-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="9736a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9736a-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="9736a-106">Almak için derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="9736a-106">ID of the assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="9736a-107">Alınacak dosya kimliği.</span><span class="sxs-lookup"><span data-stu-id="9736a-107">ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="9736a-108">İçeri aktarmak için sıfır tabanlı kapsamı.</span><span class="sxs-lookup"><span data-stu-id="9736a-108">Zero-based scope to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="9736a-109">Numaralandırıcı tanıtıcı türleri için bu kapsamda alır.</span><span class="sxs-lookup"><span data-stu-id="9736a-109">Receives enumerator handle for the types in this scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="9736a-110">İsteğe bağlı olarak alan [Imetadataımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="9736a-110">Optionally receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="9736a-111">İsteğe bağlı olarak belirtilen kapsamda türleri sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="9736a-111">Optionally receives count of types in the indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9736a-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9736a-112">Return Value</span></span>  
 <span data-ttu-id="9736a-113">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="9736a-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9736a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9736a-114">Requirements</span></span>  
 <span data-ttu-id="9736a-115">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="9736a-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9736a-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9736a-116">See Also</span></span>  
 [<span data-ttu-id="9736a-117">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9736a-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="9736a-118">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9736a-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="9736a-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="9736a-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
