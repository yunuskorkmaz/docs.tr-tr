---
description: 'Daha fazla bilgi edinin: Init yöntemi'
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
ms.openlocfilehash: 531e05a09cbecbfb67c8c004d1e4ba1deb7e59a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662565"
---
# <a name="init-method"></a><span data-ttu-id="c01c1-103">Init Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c01c1-103">Init Method</span></span>

<span data-ttu-id="c01c1-104">Kullanım için [IALink arabirimini](ialink-interface.md) uygulayan nesneleri hazırlar.</span><span class="sxs-lookup"><span data-stu-id="c01c1-104">Prepares objects implementing the [IALink Interface](ialink-interface.md) for use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c01c1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c01c1-105">Syntax</span></span>  
  
```cpp  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c01c1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c01c1-106">Parameters</span></span>  

 `pDispenser`  
 <span data-ttu-id="c01c1-107">Meta veri dağıtıcısının [ımetadatadağıtıserex arabirimi](../metadata/imetadatadispenserex-interface.md) işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c01c1-107">[IMetaDataDispenserEx Interface](../metadata/imetadatadispenserex-interface.md) pointer to the metadata dispenser.</span></span>  
  
 `pErrorHandler`  
 <span data-ttu-id="c01c1-108">[IMetaDataError arabirimi](../metadata/imetadataerror-interface.md) işaretçisi isteğe bağlı bir hata işleme arabirimine.</span><span class="sxs-lookup"><span data-stu-id="c01c1-108">[IMetaDataError Interface](../metadata/imetadataerror-interface.md) pointer to an optional error handling interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c01c1-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c01c1-109">Return Value</span></span>  

 <span data-ttu-id="c01c1-110">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="c01c1-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c01c1-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c01c1-111">Requirements</span></span>  

 <span data-ttu-id="c01c1-112">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="c01c1-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c01c1-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c01c1-113">See also</span></span>

- [<span data-ttu-id="c01c1-114">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c01c1-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="c01c1-115">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c01c1-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="c01c1-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="c01c1-116">ALink API</span></span>](index.md)
