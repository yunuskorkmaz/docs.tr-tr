---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataError:: Hata1 yöntemi'
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
ms.openlocfilehash: 9556f1bd7758755d9160e3a2e91a1fe5786aa562
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99670976"
---
# <a name="imetadataerroronerror-method"></a><span data-ttu-id="88fb7-103">IMetaDataError::OnError Yöntemi</span><span class="sxs-lookup"><span data-stu-id="88fb7-103">IMetaDataError::OnError Method</span></span>

<span data-ttu-id="88fb7-104">Meta veri birleştirme sırasında oluşan hataların bildirimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="88fb7-104">Provides notification of errors that occur during the metadata merge.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88fb7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="88fb7-105">Syntax</span></span>  
  
```cpp  
HRESULT OnError (  
    [in] HRESULT   hrError,
    [in] mdToken   token  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88fb7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="88fb7-106">Parameters</span></span>  

 `hrError`  
 <span data-ttu-id="88fb7-107">'ndaki Çağırma yöntemine döndürülen HRESULT hata değeri.</span><span class="sxs-lookup"><span data-stu-id="88fb7-107">[in] The HRESULT error value returned to the calling method.</span></span>  
  
 `token`  
 <span data-ttu-id="88fb7-108">'ndaki Hata oluştuğunda birleştirilmekte olan kod nesnesinin meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="88fb7-108">[in] The metadata token of the code object that was being merged when the error occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88fb7-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="88fb7-109">Requirements</span></span>  

 <span data-ttu-id="88fb7-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88fb7-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88fb7-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="88fb7-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="88fb7-112">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="88fb7-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="88fb7-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88fb7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88fb7-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88fb7-114">See also</span></span>

- [<span data-ttu-id="88fb7-115">IMetaDataError Arabirimi</span><span class="sxs-lookup"><span data-stu-id="88fb7-115">IMetaDataError Interface</span></span>](imetadataerror-interface.md)
