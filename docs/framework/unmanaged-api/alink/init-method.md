---
title: Init Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.Init
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- Init
helpviewer_keywords:
- Init method
ms.assetid: e48b5c64-049f-4f93-ad87-d07ae9cd5845
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 606809533010f458272cd6fbbad6234217bddea2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741622"
---
# <a name="init-method"></a><span data-ttu-id="57c38-102">Init Yöntemi</span><span class="sxs-lookup"><span data-stu-id="57c38-102">Init Method</span></span>
<span data-ttu-id="57c38-103">Uygulama nesneleri hazırlar [Ialink arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md) kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="57c38-103">Prepares objects implementing the [IALink Interface](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md) for use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57c38-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="57c38-104">Syntax</span></span>  
  
```cpp  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="57c38-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="57c38-105">Parameters</span></span>  
 `pDispenser`  
 <span data-ttu-id="57c38-106">[Imetadatadispenserex arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md) meta verileri dağıtıcısı için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="57c38-106">[IMetaDataDispenserEx Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md) pointer to the metadata dispenser.</span></span>  
  
 `pErrorHandler`  
 <span data-ttu-id="57c38-107">[Imetadataerror arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) işleme arabirimini hatayla isteğe bağlı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="57c38-107">[IMetaDataError Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) pointer to an optional error handling interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57c38-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="57c38-108">Return Value</span></span>  
 <span data-ttu-id="57c38-109">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="57c38-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57c38-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="57c38-110">Requirements</span></span>  
 <span data-ttu-id="57c38-111">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="57c38-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57c38-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57c38-112">See also</span></span>

- [<span data-ttu-id="57c38-113">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="57c38-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="57c38-114">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="57c38-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="57c38-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="57c38-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
