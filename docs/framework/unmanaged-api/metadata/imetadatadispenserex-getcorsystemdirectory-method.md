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
ms.openlocfilehash: ea0e6f96028afc201f498119976eb87aa762a6eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681697"
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a><span data-ttu-id="ea737-102">IMetaDataDispenserEx::GetCORSystemDirectory Metodu</span><span class="sxs-lookup"><span data-stu-id="ea737-102">IMetaDataDispenserEx::GetCORSystemDirectory Method</span></span>

<span data-ttu-id="ea737-103">Geçerli ortak dil çalışma zamanını (CLR) tutan dizini alır.</span><span class="sxs-lookup"><span data-stu-id="ea737-103">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="ea737-104">Bu yöntem yalnızca işlem dışı hata ayıklayıcıları tarafından kullanılmak üzere desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ea737-104">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="ea737-105">Başka bir bileşenden çağrılırsa E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="ea737-105">If called from another component, it will return E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea737-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ea737-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,
    [in]  DWORD       cchBuffer,
    [out] DWORD*      pchBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea737-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ea737-107">Parameters</span></span>  

 `szBuffer`  
 <span data-ttu-id="ea737-108">dışı Dizin adını almak için arabellek.</span><span class="sxs-lookup"><span data-stu-id="ea737-108">[out] The buffer to receive the directory name.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="ea737-109">'ndaki Bayt cinsinden boyutu `szBuffer` .</span><span class="sxs-lookup"><span data-stu-id="ea737-109">[in] The size, in bytes, of `szBuffer`.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="ea737-110">dışı Aslında ' de döndürülen bayt sayısı `szBuffer` .</span><span class="sxs-lookup"><span data-stu-id="ea737-110">[out] The number of bytes actually returned in `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea737-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ea737-111">Requirements</span></span>  

 <span data-ttu-id="ea737-112">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea737-112">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea737-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ea737-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ea737-114">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="ea737-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ea737-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea737-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea737-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea737-116">See also</span></span>

- [<span data-ttu-id="ea737-117">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ea737-117">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="ea737-118">IMetaDataDispenser Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ea737-118">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
