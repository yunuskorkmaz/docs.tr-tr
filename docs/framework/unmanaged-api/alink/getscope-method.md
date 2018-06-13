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
ms.openlocfilehash: e2746073fbc6adfd7090aa9b3cc38e46c4411744
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400191"
---
# <a name="getscope-method1"></a><span data-ttu-id="d10a3-102">GetScope Method1</span><span class="sxs-lookup"><span data-stu-id="d10a3-102">GetScope Method1</span></span>
<span data-ttu-id="d10a3-103">Bir alma kapsamı alır.</span><span class="sxs-lookup"><span data-stu-id="d10a3-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d10a3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d10a3-104">Syntax</span></span>  
  
```  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d10a3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d10a3-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="d10a3-106">Derleme almak için benzersiz kimliği.</span><span class="sxs-lookup"><span data-stu-id="d10a3-106">Unique ID of assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="d10a3-107">Alınacak benzersiz kimliği dosyasının.</span><span class="sxs-lookup"><span data-stu-id="d10a3-107">Unique ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="d10a3-108">İçeri aktarmak için sıfır tabanlı kapsamı.</span><span class="sxs-lookup"><span data-stu-id="d10a3-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="d10a3-109">Alan [Imetadataımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) kapsam için arabirim.</span><span class="sxs-lookup"><span data-stu-id="d10a3-109">Receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface for the scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d10a3-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d10a3-110">Return Value</span></span>  
 <span data-ttu-id="d10a3-111">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="d10a3-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d10a3-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d10a3-112">Requirements</span></span>  
 <span data-ttu-id="d10a3-113">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="d10a3-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d10a3-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d10a3-114">See Also</span></span>  
 [<span data-ttu-id="d10a3-115">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d10a3-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="d10a3-116">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d10a3-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="d10a3-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="d10a3-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
