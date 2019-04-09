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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 68fe41afa1999295a32b930b779991e2bbddb19a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117332"
---
# <a name="imetadataerroronerror-method"></a><span data-ttu-id="75258-102">IMetaDataError::OnError Yöntemi</span><span class="sxs-lookup"><span data-stu-id="75258-102">IMetaDataError::OnError Method</span></span>
<span data-ttu-id="75258-103">Meta veri birleştirme sırasında oluşan hataları bildirir.</span><span class="sxs-lookup"><span data-stu-id="75258-103">Provides notification of errors that occur during the metadata merge.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75258-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="75258-104">Syntax</span></span>  
  
```  
HRESULT OnError (  
    [in] HRESULT   hrError,   
    [in] mdToken   token  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75258-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="75258-105">Parameters</span></span>  
 `hrError`  
 <span data-ttu-id="75258-106">[in] Çağıran Metoda döndürülen HRESULT hata değer.</span><span class="sxs-lookup"><span data-stu-id="75258-106">[in] The HRESULT error value returned to the calling method.</span></span>  
  
 `token`  
 <span data-ttu-id="75258-107">[in] Hata oluştuğunda, birleştirilen kod nesnesinin meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="75258-107">[in] The metadata token of the code object that was being merged when the error occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75258-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="75258-108">Requirements</span></span>  
 <span data-ttu-id="75258-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75258-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75258-110">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="75258-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="75258-111">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="75258-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="75258-112">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="75258-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="75258-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75258-113">See also</span></span>

- [<span data-ttu-id="75258-114">IMetaDataError Arabirimi</span><span class="sxs-lookup"><span data-stu-id="75258-114">IMetaDataError Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)
