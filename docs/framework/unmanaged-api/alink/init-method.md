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
ms.openlocfilehash: b512389078ab022208c4b163edc8501a900669ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400370"
---
# <a name="init-method"></a><span data-ttu-id="7aa2a-102">Init Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7aa2a-102">Init Method</span></span>
<span data-ttu-id="7aa2a-103">Uygulama nesneleri hazırlar [Ialink arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md) kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="7aa2a-103">Prepares objects implementing the [IALink Interface](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md) for use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7aa2a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7aa2a-104">Syntax</span></span>  
  
```  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7aa2a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7aa2a-105">Parameters</span></span>  
 `pDispenser`  
 <span data-ttu-id="7aa2a-106">[Imetadatadispenserex arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md) meta verileri dağıtıcısının işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7aa2a-106">[IMetaDataDispenserEx Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md) pointer to the metadata dispenser.</span></span>  
  
 `pErrorHandler`  
 <span data-ttu-id="7aa2a-107">[Imetadataerror arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) isteğe bağlı bir hata arabirimi işleme işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7aa2a-107">[IMetaDataError Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) pointer to an optional error handling interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7aa2a-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7aa2a-108">Return Value</span></span>  
 <span data-ttu-id="7aa2a-109">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="7aa2a-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7aa2a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7aa2a-110">Requirements</span></span>  
 <span data-ttu-id="7aa2a-111">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="7aa2a-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7aa2a-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7aa2a-112">See Also</span></span>  
 [<span data-ttu-id="7aa2a-113">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7aa2a-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="7aa2a-114">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7aa2a-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="7aa2a-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="7aa2a-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
