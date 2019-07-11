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
ms.openlocfilehash: f3c3142ca12789b086bcd8b5a9c00c943264ae7b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741847"
---
# <a name="getscope-method"></a><span data-ttu-id="3334f-102">GetScope Metodu</span><span class="sxs-lookup"><span data-stu-id="3334f-102">GetScope Method</span></span>
<span data-ttu-id="3334f-103">Bir içeri aktarma kapsamı alır.</span><span class="sxs-lookup"><span data-stu-id="3334f-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3334f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3334f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="3334f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3334f-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="3334f-106">Derleme için alınacak benzersiz kimliği.</span><span class="sxs-lookup"><span data-stu-id="3334f-106">Unique ID of assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="3334f-107">Alınacak benzersiz kimliği dosyanın.</span><span class="sxs-lookup"><span data-stu-id="3334f-107">Unique ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="3334f-108">İçeri aktarmak için sıfır tabanlı kapsam.</span><span class="sxs-lookup"><span data-stu-id="3334f-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="3334f-109">Alan [Imetadataımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) kapsam için arabirim.</span><span class="sxs-lookup"><span data-stu-id="3334f-109">Receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface for the scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3334f-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3334f-110">Return Value</span></span>  
 <span data-ttu-id="3334f-111">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="3334f-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3334f-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3334f-112">Requirements</span></span>  
 <span data-ttu-id="3334f-113">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="3334f-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3334f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3334f-114">See also</span></span>

- [<span data-ttu-id="3334f-115">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3334f-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="3334f-116">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3334f-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="3334f-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="3334f-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
