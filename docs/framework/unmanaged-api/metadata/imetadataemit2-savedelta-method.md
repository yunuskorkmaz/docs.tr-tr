---
description: 'Daha fazla bilgi edinin: IMetaDataEmit2:: SaveDelta yöntemi'
title: IMetaDataEmit2::SaveDelta Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDelta
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDelta
helpviewer_keywords:
- IMetaDataEmit2::SaveDelta method [.NET Framework metadata]
- SaveDelta method [.NET Framework metadata]
ms.assetid: b95739fe-d2fa-4776-ae0d-31d9707ef799
topic_type:
- apiref
ms.openlocfilehash: 6e7a7527125869fea041f407da056db3eea88cbe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771775"
---
# <a name="imetadataemit2savedelta-method"></a><span data-ttu-id="12aa9-103">IMetaDataEmit2::SaveDelta Yöntemi</span><span class="sxs-lookup"><span data-stu-id="12aa9-103">IMetaDataEmit2::SaveDelta Method</span></span>

<span data-ttu-id="12aa9-104">Değişiklikleri geçerli Düzenle ve devam et oturumundan belirtilen dosyaya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="12aa9-104">Saves changes from the current edit-and-continue session to the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12aa9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="12aa9-105">Syntax</span></span>  
  
```cpp  
HRESULT SaveDelta (  
    [in] LPCWSTR     szFile,
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12aa9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="12aa9-106">Parameters</span></span>  

 `szFile`  
 <span data-ttu-id="12aa9-107">'ndaki Değişikliklerin kaydedileceği dosya adı.</span><span class="sxs-lookup"><span data-stu-id="12aa9-107">[in] The file name under which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="12aa9-108">'ndaki Ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="12aa9-108">[in] Reserved.</span></span> <span data-ttu-id="12aa9-109">Sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="12aa9-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12aa9-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="12aa9-110">Requirements</span></span>  

 <span data-ttu-id="12aa9-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12aa9-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12aa9-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="12aa9-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="12aa9-113">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="12aa9-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="12aa9-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12aa9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12aa9-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12aa9-115">See also</span></span>

- [<span data-ttu-id="12aa9-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="12aa9-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="12aa9-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="12aa9-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
