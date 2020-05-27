---
title: IMetaDataEmit::SetMethodImplFlags Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetMethodImplFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodImplFlags
helpviewer_keywords:
- IMetaDataEmit::SetMethodImplFlags method [.NET Framework metadata]
- SetMethodImpFlags method [.NET Framework metadata]
ms.assetid: 4bc82d9b-9544-4be3-ba51-a2d4d806158a
topic_type:
- apiref
ms.openlocfilehash: a02456393680169ce33369ee5914f6c5216081c6
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009229"
---
# <a name="imetadataemitsetmethodimplflags-method"></a><span data-ttu-id="a2fb1-102">IMetaDataEmit::SetMethodImplFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a2fb1-102">IMetaDataEmit::SetMethodImplFlags Method</span></span>
<span data-ttu-id="a2fb1-103">Belirtilen belirteç tarafından başvurulan devralınmış Yöntem uygulamasının meta veri imzasını ayarlar veya güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="a2fb1-103">Sets or updates the metadata signature of the inherited method implementation that is referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2fb1-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a2fb1-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodImplFlags (
    [in]  mdMethodDef   md,
    [in]  DWORD         dwImplFlags
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2fb1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a2fb1-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="a2fb1-106">'ndaki Değiştirilecek metodun belirteci.</span><span class="sxs-lookup"><span data-stu-id="a2fb1-106">[in] The token for the method to be changed.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="a2fb1-107">'ndaki Yöntem uygulama özelliklerini belirten [CorMethodImpl](cormethodimpl-enumeration.md) numaralandırması değerlerinin birleşimi.</span><span class="sxs-lookup"><span data-stu-id="a2fb1-107">[in] A combination of the values of the [CorMethodImpl](cormethodimpl-enumeration.md) enumeration that specifies the method implementation features.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2fb1-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a2fb1-108">Requirements</span></span>  
 <span data-ttu-id="a2fb1-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2fb1-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2fb1-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a2fb1-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a2fb1-111">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="a2fb1-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a2fb1-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2fb1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2fb1-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2fb1-113">See also</span></span>

- [<span data-ttu-id="a2fb1-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a2fb1-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="a2fb1-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a2fb1-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
