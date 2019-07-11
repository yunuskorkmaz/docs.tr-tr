---
title: IMetaDataDispenserEx::GetCORSystemDirectory Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.GetCORSystemDirectory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory
helpviewer_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory method [.NET Framework metadata]
- GetCORSystemDirectory method [.NET Framework metadata]
ms.assetid: d9e0f3b6-e106-4820-bada-5bfba34ce360
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f03a2dfa60f2fbdce317d96a9e5b23c6f017dc3d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777748"
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a><span data-ttu-id="198ef-102">IMetaDataDispenserEx::GetCORSystemDirectory Metodu</span><span class="sxs-lookup"><span data-stu-id="198ef-102">IMetaDataDispenserEx::GetCORSystemDirectory Method</span></span>
<span data-ttu-id="198ef-103">Geçerli ortak dil çalışma zamanının (CLR) tutan dizinin alır.</span><span class="sxs-lookup"><span data-stu-id="198ef-103">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="198ef-104">Bu yöntemi kullanmak için yalnızca işlem dışı hata ayıklayıcıları tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="198ef-104">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="198ef-105">Başka bir bileşenden çağrılırsa E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="198ef-105">If called from another component, it will return E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="198ef-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="198ef-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,   
    [in]  DWORD       cchBuffer,   
    [out] DWORD*      pchBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="198ef-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="198ef-107">Parameters</span></span>  
 `szBuffer`  
 <span data-ttu-id="198ef-108">[out] Dizin adını almak için arabellek.</span><span class="sxs-lookup"><span data-stu-id="198ef-108">[out] The buffer to receive the directory name.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="198ef-109">[in] Bayt cinsinden boyutu, `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="198ef-109">[in] The size, in bytes, of `szBuffer`.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="198ef-110">[out] Gerçekte döndürülen bayt sayısı `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="198ef-110">[out] The number of bytes actually returned in `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="198ef-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="198ef-111">Requirements</span></span>  
 <span data-ttu-id="198ef-112">**Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="198ef-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="198ef-113">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="198ef-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="198ef-114">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="198ef-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="198ef-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="198ef-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="198ef-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="198ef-116">See also</span></span>

- [<span data-ttu-id="198ef-117">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="198ef-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="198ef-118">IMetaDataDispenser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="198ef-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
