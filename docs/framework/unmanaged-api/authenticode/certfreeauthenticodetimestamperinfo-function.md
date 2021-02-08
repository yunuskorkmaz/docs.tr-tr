---
description: 'Daha fazla bilgi edinin: CertFreeAuthenticodeTimestamperInfo Işlevi'
title: CertFreeAuthenticodeTimestamperInfo İşlevi
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeTimestamperInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 3eb14c49-68c2-4516-ac89-e5bd7473831c
topic_type:
- apiref
ms.openlocfilehash: 5234a90ea1d0272a7409b1b0b4def2160b77a513
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772945"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="32602-103">CertFreeAuthenticodeTimestamperInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="32602-103">CertFreeAuthenticodeTimestamperInfo Function</span></span>

<span data-ttu-id="32602-104">[AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) yapısı için ayrılan kaynakları boşaltır.</span><span class="sxs-lookup"><span data-stu-id="32602-104">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>

## <a name="syntax"></a><span data-ttu-id="32602-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32602-105">Syntax</span></span>

```cpp
HRESULT CertFreeAuthenticodeTimestamperInfo (
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo
);
```

## <a name="parameters"></a><span data-ttu-id="32602-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="32602-106">Parameters</span></span>

 `pTimestamperInfo`\
 <span data-ttu-id="32602-107">[in, out] Yayımlanacak zaman bilgileri.</span><span class="sxs-lookup"><span data-stu-id="32602-107">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="32602-108">[AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) yapısına bakın.</span><span class="sxs-lookup"><span data-stu-id="32602-108">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>

## <a name="return-value"></a><span data-ttu-id="32602-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="32602-109">Return Value</span></span>

 <span data-ttu-id="32602-110">`S_OK` işlev başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="32602-110">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="32602-111">Aksi takdirde, bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="32602-111">Otherwise, returns an error code.</span></span>

## <a name="requirements"></a><span data-ttu-id="32602-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="32602-112">Requirements</span></span>

<span data-ttu-id="32602-113">**Bütünleştirilmiş kod**: clr.dll</span><span class="sxs-lookup"><span data-stu-id="32602-113">**Assembly**: clr.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="32602-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32602-114">See also</span></span>

- [<span data-ttu-id="32602-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="32602-115">Authenticode</span></span>](index.md)
