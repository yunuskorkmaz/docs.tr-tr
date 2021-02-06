---
description: ': Imetadatayayma:: SetMethodImplFlags yöntemi hakkında daha fazla bilgi'
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
ms.openlocfilehash: ea7f3122a21c8651014e60de3629db87eeaf6260
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657844"
---
# <a name="imetadataemitsetmethodimplflags-method"></a><span data-ttu-id="31049-103">IMetaDataEmit::SetMethodImplFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="31049-103">IMetaDataEmit::SetMethodImplFlags Method</span></span>

<span data-ttu-id="31049-104">Belirtilen belirteç tarafından başvurulan devralınmış Yöntem uygulamasının meta veri imzasını ayarlar veya güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="31049-104">Sets or updates the metadata signature of the inherited method implementation that is referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31049-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="31049-105">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodImplFlags (
    [in]  mdMethodDef   md,
    [in]  DWORD         dwImplFlags
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31049-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="31049-106">Parameters</span></span>  

 `md`  
 <span data-ttu-id="31049-107">'ndaki Değiştirilecek metodun belirteci.</span><span class="sxs-lookup"><span data-stu-id="31049-107">[in] The token for the method to be changed.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="31049-108">'ndaki Yöntem uygulama özelliklerini belirten [CorMethodImpl](cormethodimpl-enumeration.md) numaralandırması değerlerinin birleşimi.</span><span class="sxs-lookup"><span data-stu-id="31049-108">[in] A combination of the values of the [CorMethodImpl](cormethodimpl-enumeration.md) enumeration that specifies the method implementation features.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31049-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="31049-109">Requirements</span></span>  

 <span data-ttu-id="31049-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31049-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31049-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="31049-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="31049-112">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="31049-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="31049-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31049-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31049-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31049-114">See also</span></span>

- [<span data-ttu-id="31049-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31049-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="31049-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31049-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
