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
ms.openlocfilehash: 489fa217744e41ccb5d27d088790131c15e1ee52
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177392"
---
# <a name="imetadataerroronerror-method"></a><span data-ttu-id="f0e13-102">IMetaDataError::OnError Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0e13-102">IMetaDataError::OnError Method</span></span>
<span data-ttu-id="f0e13-103">Meta veri birleştirme sırasında oluşan hataların bildirimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0e13-103">Provides notification of errors that occur during the metadata merge.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0e13-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0e13-104">Syntax</span></span>  
  
```cpp  
HRESULT OnError (  
    [in] HRESULT   hrError,
    [in] mdToken   token  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0e13-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f0e13-105">Parameters</span></span>  
 `hrError`  
 <span data-ttu-id="f0e13-106">[içinde] HRESULT hata değeri arama yöntemine döndürülür.</span><span class="sxs-lookup"><span data-stu-id="f0e13-106">[in] The HRESULT error value returned to the calling method.</span></span>  
  
 `token`  
 <span data-ttu-id="f0e13-107">[içinde] Hata oluştuğunda birleştirilen kod nesnesinin meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="f0e13-107">[in] The metadata token of the code object that was being merged when the error occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0e13-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0e13-108">Requirements</span></span>  
 <span data-ttu-id="f0e13-109">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0e13-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0e13-110">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f0e13-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f0e13-111">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="f0e13-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f0e13-112">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0e13-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0e13-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0e13-113">See also</span></span>

- [<span data-ttu-id="f0e13-114">IMetaDataError Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f0e13-114">IMetaDataError Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)
