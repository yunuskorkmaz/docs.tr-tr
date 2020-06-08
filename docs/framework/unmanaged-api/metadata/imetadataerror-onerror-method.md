---
title: IMetaDataError::OnError Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataError.OnError
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataError::OnError
helpviewer_keywords:
- IMetaDataError::OnError method [.NET Framework metadata]
- OnError method, IMetaDataError interface [.NET Framework metadata]
ms.assetid: c1e744b8-a6fb-4d9c-a971-8babc875d8f0
topic_type:
- apiref
ms.openlocfilehash: d2252f58af1a319d953fb320a99fad1cfec3dca0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492726"
---
# <a name="imetadataerroronerror-method"></a><span data-ttu-id="cd0ad-102">IMetaDataError::OnError Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cd0ad-102">IMetaDataError::OnError Method</span></span>
<span data-ttu-id="cd0ad-103">Meta veri birleştirme sırasında oluşan hataların bildirimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="cd0ad-103">Provides notification of errors that occur during the metadata merge.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd0ad-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="cd0ad-104">Syntax</span></span>  
  
```cpp  
HRESULT OnError (  
    [in] HRESULT   hrError,
    [in] mdToken   token  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd0ad-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cd0ad-105">Parameters</span></span>  
 `hrError`  
 <span data-ttu-id="cd0ad-106">'ndaki Çağırma yöntemine döndürülen HRESULT hata değeri.</span><span class="sxs-lookup"><span data-stu-id="cd0ad-106">[in] The HRESULT error value returned to the calling method.</span></span>  
  
 `token`  
 <span data-ttu-id="cd0ad-107">'ndaki Hata oluştuğunda birleştirilmekte olan kod nesnesinin meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="cd0ad-107">[in] The metadata token of the code object that was being merged when the error occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd0ad-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cd0ad-108">Requirements</span></span>  
 <span data-ttu-id="cd0ad-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd0ad-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd0ad-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="cd0ad-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cd0ad-111">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="cd0ad-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cd0ad-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd0ad-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd0ad-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd0ad-113">See also</span></span>

- [<span data-ttu-id="cd0ad-114">IMetaDataError Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cd0ad-114">IMetaDataError Interface</span></span>](imetadataerror-interface.md)
