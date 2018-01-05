---
title: IMetaDataDispenserEx::GetCORSystemDirectory Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx.GetCORSystemDirectory
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx::GetCORSystemDirectory
helpviewer_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory method [.NET Framework metadata]
- GetCORSystemDirectory method [.NET Framework metadata]
ms.assetid: d9e0f3b6-e106-4820-bada-5bfba34ce360
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e93f544e504949b496881369c15905ef43a0d2f6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a><span data-ttu-id="757fd-102">IMetaDataDispenserEx::GetCORSystemDirectory Metodu</span><span class="sxs-lookup"><span data-stu-id="757fd-102">IMetaDataDispenserEx::GetCORSystemDirectory Method</span></span>
<span data-ttu-id="757fd-103">Geçerli ortak dil çalışma zamanı (CLR) tutan dizinin alır.</span><span class="sxs-lookup"><span data-stu-id="757fd-103">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="757fd-104">Bu yöntem yalnızca kullanım için işlem dışı hata ayıklayıcıları tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="757fd-104">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="757fd-105">Başka bir bileşen tarafından çağrılan olursa E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="757fd-105">If called from another component, it will return E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="757fd-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="757fd-106">Syntax</span></span>  
  
```  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,   
    [in]  DWORD       cchBuffer,   
    [out] DWORD*      pchBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="757fd-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="757fd-107">Parameters</span></span>  
 `szBuffer`  
 <span data-ttu-id="757fd-108">[out] Dizin adı almak için bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="757fd-108">[out] The buffer to receive the directory name.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="757fd-109">[in] Bayt olarak boyutu, `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="757fd-109">[in] The size, in bytes, of `szBuffer`.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="757fd-110">[out] Gerçekte döndürülen bayt sayısı `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="757fd-110">[out] The number of bytes actually returned in `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="757fd-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="757fd-111">Requirements</span></span>  
 <span data-ttu-id="757fd-112">**Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="757fd-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="757fd-113">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="757fd-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="757fd-114">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="757fd-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="757fd-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="757fd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="757fd-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="757fd-116">See Also</span></span>  
 [<span data-ttu-id="757fd-117">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="757fd-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="757fd-118">IMetaDataDispenser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="757fd-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
