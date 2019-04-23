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
ms.openlocfilehash: 60602462376543fe934bb3c58bc4988fa8ab34bf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119372"
---
# <a name="init-method"></a><span data-ttu-id="f2da5-102">Init Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f2da5-102">Init Method</span></span>
<span data-ttu-id="f2da5-103">Uygulama nesneleri hazırlar [Ialink arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md) kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="f2da5-103">Prepares objects implementing the [IALink Interface](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md) for use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2da5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2da5-104">Syntax</span></span>  
  
```  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2da5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f2da5-105">Parameters</span></span>  
 `pDispenser`  
 <span data-ttu-id="f2da5-106">[Imetadatadispenserex arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md) meta verileri dağıtıcısı için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f2da5-106">[IMetaDataDispenserEx Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md) pointer to the metadata dispenser.</span></span>  
  
 `pErrorHandler`  
 <span data-ttu-id="f2da5-107">[Imetadataerror arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) işleme arabirimini hatayla isteğe bağlı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="f2da5-107">[IMetaDataError Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) pointer to an optional error handling interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f2da5-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f2da5-108">Return Value</span></span>  
 <span data-ttu-id="f2da5-109">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="f2da5-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2da5-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f2da5-110">Requirements</span></span>  
 <span data-ttu-id="f2da5-111">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="f2da5-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2da5-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2da5-112">See also</span></span>

- [<span data-ttu-id="f2da5-113">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f2da5-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="f2da5-114">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f2da5-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="f2da5-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="f2da5-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
