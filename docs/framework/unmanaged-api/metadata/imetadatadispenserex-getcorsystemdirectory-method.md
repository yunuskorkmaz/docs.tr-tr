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
ms.openlocfilehash: fb673666543bea3df44005ee3b20d311524f51d0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175921"
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a><span data-ttu-id="11898-102">IMetaDataDispenserEx::GetCORSystemDirectory Metodu</span><span class="sxs-lookup"><span data-stu-id="11898-102">IMetaDataDispenserEx::GetCORSystemDirectory Method</span></span>
<span data-ttu-id="11898-103">Geçerli ortak dil çalışma saatini (CLR) tutan dizini alır.</span><span class="sxs-lookup"><span data-stu-id="11898-103">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="11898-104">Bu yöntem yalnızca işlem dışı hata ayıklayıcılar tarafından kullanılmak üzere desteklenir.</span><span class="sxs-lookup"><span data-stu-id="11898-104">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="11898-105">Başka bir bileşenden çağrılırsa, E_NOTIMPL döndürecek.</span><span class="sxs-lookup"><span data-stu-id="11898-105">If called from another component, it will return E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11898-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="11898-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,
    [in]  DWORD       cchBuffer,
    [out] DWORD*      pchBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11898-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="11898-107">Parameters</span></span>  
 `szBuffer`  
 <span data-ttu-id="11898-108">[çıkış] Dizin adını almak için arabellek.</span><span class="sxs-lookup"><span data-stu-id="11898-108">[out] The buffer to receive the directory name.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="11898-109">[içinde] Boyutu, bayt, ve. `szBuffer`</span><span class="sxs-lookup"><span data-stu-id="11898-109">[in] The size, in bytes, of `szBuffer`.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="11898-110">[çıkış] Bayt sayısı aslında `szBuffer`döndü.</span><span class="sxs-lookup"><span data-stu-id="11898-110">[out] The number of bytes actually returned in `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11898-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="11898-111">Requirements</span></span>  
 <span data-ttu-id="11898-112">**Platform:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11898-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11898-113">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="11898-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="11898-114">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="11898-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="11898-115">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11898-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11898-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11898-116">See also</span></span>

- [<span data-ttu-id="11898-117">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="11898-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="11898-118">IMetaDataDispenser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="11898-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
