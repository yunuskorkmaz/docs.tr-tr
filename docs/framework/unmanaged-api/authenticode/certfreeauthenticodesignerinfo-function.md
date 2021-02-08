---
description: 'Daha fazla bilgi edinin: CertFreeAuthenticodeSignerInfo Işlevi'
title: CertFreeAuthenticodeSignerInfo İşlevi
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeSignerInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 8029633c-b6e4-4665-a7c2-89607c3247ef
topic_type:
- apiref
ms.openlocfilehash: 6e8a97e8fee37d885c7d32102ed8cc7654992223
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772984"
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="aa48f-103">CertFreeAuthenticodeSignerInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="aa48f-103">CertFreeAuthenticodeSignerInfo Function</span></span>

<span data-ttu-id="aa48f-104">[AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) yapısı için ayrılan kaynakları boşaltır.</span><span class="sxs-lookup"><span data-stu-id="aa48f-104">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) structure.</span></span>

## <a name="syntax"></a><span data-ttu-id="aa48f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aa48f-105">Syntax</span></span>

```cpp
HRESULT CertFreeAuthenticodeSignerInfo (
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);
```

## <a name="parameters"></a><span data-ttu-id="aa48f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aa48f-106">Parameters</span></span>

 `pSignerInfo`\
 <span data-ttu-id="aa48f-107">[in, out] Yayımlanacak imzalayan bilgileri.</span><span class="sxs-lookup"><span data-stu-id="aa48f-107">[in, out] Signer information to be released.</span></span> <span data-ttu-id="aa48f-108">[AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) yapısına bakın.</span><span class="sxs-lookup"><span data-stu-id="aa48f-108">See the [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) structure.</span></span>

## <a name="return-value"></a><span data-ttu-id="aa48f-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="aa48f-109">Return Value</span></span>

 <span data-ttu-id="aa48f-110">`S_OK` işlev başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="aa48f-110">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="aa48f-111">Aksi takdirde, bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="aa48f-111">Otherwise, returns an error code.</span></span>

## <a name="requirements"></a><span data-ttu-id="aa48f-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aa48f-112">Requirements</span></span>

<span data-ttu-id="aa48f-113">**Bütünleştirilmiş kod**: clr.dll</span><span class="sxs-lookup"><span data-stu-id="aa48f-113">**Assembly**: clr.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="aa48f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa48f-114">See also</span></span>

- [<span data-ttu-id="aa48f-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="aa48f-115">Authenticode</span></span>](index.md)
