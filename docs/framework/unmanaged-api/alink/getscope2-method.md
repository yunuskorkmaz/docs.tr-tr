---
title: GetScope2 Metodu
ms.date: 03/30/2017
api_name:
- IALink2.GetScope2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope2
helpviewer_keywords:
- GetScope2 method
ms.assetid: 49435665-6f5a-4acd-9034-8c9244a04a63
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0c0abc63610f3f1ed6e8a556c44ee15edc1ea20b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741833"
---
# <a name="getscope2-method"></a><span data-ttu-id="357a5-102">GetScope2 Metodu</span><span class="sxs-lookup"><span data-stu-id="357a5-102">GetScope2 Method</span></span>
<span data-ttu-id="357a5-103">Bir içeri aktarma kapsamı alır.</span><span class="sxs-lookup"><span data-stu-id="357a5-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="357a5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="357a5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="357a5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="357a5-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="357a5-106">Hedef derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="357a5-106">ID of target assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="357a5-107">Alınacağı dosya kimliği.</span><span class="sxs-lookup"><span data-stu-id="357a5-107">ID of file from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="357a5-108">İçeri aktarmak için sıfır tabanlı kapsam.</span><span class="sxs-lookup"><span data-stu-id="357a5-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="357a5-109">İşaretçi alır [Imetadataımport2 arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) Belirtilen kapsam için arabirim.</span><span class="sxs-lookup"><span data-stu-id="357a5-109">Receives pointer to [IMetaDataImport2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface for indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="357a5-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="357a5-110">Return Value</span></span>  
 <span data-ttu-id="357a5-111">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="357a5-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="357a5-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="357a5-112">Requirements</span></span>  
 <span data-ttu-id="357a5-113">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="357a5-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="357a5-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="357a5-114">See also</span></span>

- [<span data-ttu-id="357a5-115">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="357a5-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="357a5-116">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="357a5-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="357a5-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="357a5-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
