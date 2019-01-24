---
title: GetScope Method1
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
ms.openlocfilehash: 782697536f5e01fa29830a64e47d960a47fe4eae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663147"
---
# <a name="getscope-method1"></a><span data-ttu-id="10f7f-102">GetScope Method1</span><span class="sxs-lookup"><span data-stu-id="10f7f-102">GetScope Method1</span></span>
<span data-ttu-id="10f7f-103">Bir içeri aktarma kapsamı alır.</span><span class="sxs-lookup"><span data-stu-id="10f7f-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10f7f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="10f7f-104">Syntax</span></span>  
  
```  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="10f7f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="10f7f-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="10f7f-106">Derleme için alınacak benzersiz kimliği.</span><span class="sxs-lookup"><span data-stu-id="10f7f-106">Unique ID of assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="10f7f-107">Alınacak benzersiz kimliği dosyanın.</span><span class="sxs-lookup"><span data-stu-id="10f7f-107">Unique ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="10f7f-108">İçeri aktarmak için sıfır tabanlı kapsam.</span><span class="sxs-lookup"><span data-stu-id="10f7f-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="10f7f-109">Alan [Imetadataımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) kapsam için arabirim.</span><span class="sxs-lookup"><span data-stu-id="10f7f-109">Receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface for the scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="10f7f-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="10f7f-110">Return Value</span></span>  
 <span data-ttu-id="10f7f-111">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="10f7f-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10f7f-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="10f7f-112">Requirements</span></span>  
 <span data-ttu-id="10f7f-113">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="10f7f-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10f7f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10f7f-114">See also</span></span>
- [<span data-ttu-id="10f7f-115">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="10f7f-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="10f7f-116">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="10f7f-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="10f7f-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="10f7f-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
