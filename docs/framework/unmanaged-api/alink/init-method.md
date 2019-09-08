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
ms.openlocfilehash: bf96770dd58c9b84596c082a615f626ec723cc6c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787239"
---
# <a name="init-method"></a><span data-ttu-id="cc03b-102">Init Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cc03b-102">Init Method</span></span>
<span data-ttu-id="cc03b-103">Kullanım için [IALink arabirimini](ialink-interface.md) uygulayan nesneleri hazırlar.</span><span class="sxs-lookup"><span data-stu-id="cc03b-103">Prepares objects implementing the [IALink Interface](ialink-interface.md) for use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc03b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cc03b-104">Syntax</span></span>  
  
```cpp  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc03b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cc03b-105">Parameters</span></span>  
 `pDispenser`  
 <span data-ttu-id="cc03b-106">Meta veri dağıtıcısının [ımetadatadağıtıserex arabirimi](../metadata/imetadatadispenserex-interface.md) işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="cc03b-106">[IMetaDataDispenserEx Interface](../metadata/imetadatadispenserex-interface.md) pointer to the metadata dispenser.</span></span>  
  
 `pErrorHandler`  
 <span data-ttu-id="cc03b-107">[IMetaDataError arabirimi](../metadata/imetadataerror-interface.md) işaretçisi isteğe bağlı bir hata işleme arabirimine.</span><span class="sxs-lookup"><span data-stu-id="cc03b-107">[IMetaDataError Interface](../metadata/imetadataerror-interface.md) pointer to an optional error handling interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cc03b-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cc03b-108">Return Value</span></span>  
 <span data-ttu-id="cc03b-109">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="cc03b-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc03b-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cc03b-110">Requirements</span></span>  
 <span data-ttu-id="cc03b-111">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="cc03b-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc03b-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc03b-112">See also</span></span>

- [<span data-ttu-id="cc03b-113">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cc03b-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="cc03b-114">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cc03b-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="cc03b-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="cc03b-115">ALink API</span></span>](index.md)
