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
ms.openlocfilehash: 986ae69e7ebb8f607be5d37fab426bcc787abb26
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445646"
---
# <a name="init-method"></a><span data-ttu-id="d0b55-102">Init Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d0b55-102">Init Method</span></span>
<span data-ttu-id="d0b55-103">Prepares objects implementing the [IALink Interface](ialink-interface.md) for use.</span><span class="sxs-lookup"><span data-stu-id="d0b55-103">Prepares objects implementing the [IALink Interface](ialink-interface.md) for use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0b55-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0b55-104">Syntax</span></span>  
  
```cpp  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0b55-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d0b55-105">Parameters</span></span>  
 `pDispenser`  
 <span data-ttu-id="d0b55-106">[IMetaDataDispenserEx Interface](../metadata/imetadatadispenserex-interface.md) pointer to the metadata dispenser.</span><span class="sxs-lookup"><span data-stu-id="d0b55-106">[IMetaDataDispenserEx Interface](../metadata/imetadatadispenserex-interface.md) pointer to the metadata dispenser.</span></span>  
  
 `pErrorHandler`  
 <span data-ttu-id="d0b55-107">[IMetaDataError Interface](../metadata/imetadataerror-interface.md) pointer to an optional error handling interface.</span><span class="sxs-lookup"><span data-stu-id="d0b55-107">[IMetaDataError Interface](../metadata/imetadataerror-interface.md) pointer to an optional error handling interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0b55-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d0b55-108">Return Value</span></span>  
 <span data-ttu-id="d0b55-109">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="d0b55-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0b55-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0b55-110">Requirements</span></span>  
 <span data-ttu-id="d0b55-111">Requires alink.h</span><span class="sxs-lookup"><span data-stu-id="d0b55-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0b55-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0b55-112">See also</span></span>

- [<span data-ttu-id="d0b55-113">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d0b55-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="d0b55-114">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d0b55-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="d0b55-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="d0b55-115">ALink API</span></span>](index.md)
