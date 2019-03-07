---
title: GetScope Metodu
ms.date: 03/30/2017
api_name:
- IALink.GetScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope
helpviewer_keywords:
- GetScope method
ms.assetid: e1555328-2c71-4ece-b357-9eb6d3a8efc4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c8de6c745b1d32c3d98f1b54e822ab084f0574b2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57486205"
---
# <a name="getscope-method"></a><span data-ttu-id="30417-102">GetScope Metodu</span><span class="sxs-lookup"><span data-stu-id="30417-102">GetScope Method</span></span>
<span data-ttu-id="30417-103">Bir içeri aktarma kapsamı alır.</span><span class="sxs-lookup"><span data-stu-id="30417-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30417-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30417-104">Syntax</span></span>  
  
```  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="30417-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="30417-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="30417-106">Derleme için alınacak benzersiz kimliği.</span><span class="sxs-lookup"><span data-stu-id="30417-106">Unique ID of assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="30417-107">Alınacak benzersiz kimliği dosyanın.</span><span class="sxs-lookup"><span data-stu-id="30417-107">Unique ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="30417-108">İçeri aktarmak için sıfır tabanlı kapsam.</span><span class="sxs-lookup"><span data-stu-id="30417-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="30417-109">Alan [Imetadataımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) kapsam için arabirim.</span><span class="sxs-lookup"><span data-stu-id="30417-109">Receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface for the scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30417-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="30417-110">Return Value</span></span>  
 <span data-ttu-id="30417-111">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="30417-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30417-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="30417-112">Requirements</span></span>  
 <span data-ttu-id="30417-113">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="30417-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30417-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30417-114">See also</span></span>
- [<span data-ttu-id="30417-115">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="30417-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="30417-116">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="30417-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="30417-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="30417-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
