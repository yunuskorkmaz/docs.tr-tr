---
description: ': Imetadatadağıtıserex:: GetCORSystemDirectory metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 3ceda653e50ba5ad7de5548b78781f48cda41624
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753568"
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a><span data-ttu-id="ab059-103">IMetaDataDispenserEx::GetCORSystemDirectory Metodu</span><span class="sxs-lookup"><span data-stu-id="ab059-103">IMetaDataDispenserEx::GetCORSystemDirectory Method</span></span>

<span data-ttu-id="ab059-104">Geçerli ortak dil çalışma zamanını (CLR) tutan dizini alır.</span><span class="sxs-lookup"><span data-stu-id="ab059-104">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="ab059-105">Bu yöntem yalnızca işlem dışı hata ayıklayıcıları tarafından kullanılmak üzere desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ab059-105">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="ab059-106">Başka bir bileşenden çağrılırsa E_NOTIMPL döndürür.</span><span class="sxs-lookup"><span data-stu-id="ab059-106">If called from another component, it will return E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab059-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ab059-107">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,
    [in]  DWORD       cchBuffer,
    [out] DWORD*      pchBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab059-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ab059-108">Parameters</span></span>  

 `szBuffer`  
 <span data-ttu-id="ab059-109">dışı Dizin adını almak için arabellek.</span><span class="sxs-lookup"><span data-stu-id="ab059-109">[out] The buffer to receive the directory name.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="ab059-110">'ndaki Bayt cinsinden boyutu `szBuffer` .</span><span class="sxs-lookup"><span data-stu-id="ab059-110">[in] The size, in bytes, of `szBuffer`.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="ab059-111">dışı Aslında ' de döndürülen bayt sayısı `szBuffer` .</span><span class="sxs-lookup"><span data-stu-id="ab059-111">[out] The number of bytes actually returned in `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab059-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ab059-112">Requirements</span></span>  

 <span data-ttu-id="ab059-113">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab059-113">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab059-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ab059-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ab059-115">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="ab059-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ab059-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab059-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab059-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab059-117">See also</span></span>

- [<span data-ttu-id="ab059-118">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ab059-118">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="ab059-119">IMetaDataDispenser Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ab059-119">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
