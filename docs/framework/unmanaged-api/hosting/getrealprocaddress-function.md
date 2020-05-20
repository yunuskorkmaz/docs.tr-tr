---
title: GetRealProcAddress İşlevi
ms.date: 03/30/2017
api_name:
- GetRealProcAddress
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetRealProcAddress
helpviewer_keywords:
- GetRealProcAddress function [.NET Framework hosting]
ms.assetid: f1f2fab1-400b-488f-95f2-d49c4fca3556
topic_type:
- apiref
ms.openlocfilehash: 6bbf8366054c58543444a4b710a687198f365e6e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617210"
---
# <a name="getrealprocaddress-function"></a><span data-ttu-id="70e63-102">GetRealProcAddress İşlevi</span><span class="sxs-lookup"><span data-stu-id="70e63-102">GetRealProcAddress Function</span></span>
<span data-ttu-id="70e63-103">Ortak dil çalışma zamanının (CLR) en son yüklenen sürümünden aktarılmış olan belirtilen işlevin adresini alır.</span><span class="sxs-lookup"><span data-stu-id="70e63-103">Gets the address of the specified function that is exported from the latest installed version of the common language runtime (CLR).</span></span>  
  
 <span data-ttu-id="70e63-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="70e63-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70e63-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="70e63-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRealProcAddress (  
    [in]  LPCSTR  pwszProcName,
    [out] VOID  **ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70e63-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="70e63-106">Parameters</span></span>  
 `pwszProcName`  
 <span data-ttu-id="70e63-107">'ndaki İşlevin adı.</span><span class="sxs-lookup"><span data-stu-id="70e63-107">[in] The name of the function.</span></span>  
  
 `ppv`  
 <span data-ttu-id="70e63-108">dışı İşlevin adresine bir işaretçi alan konum.</span><span class="sxs-lookup"><span data-stu-id="70e63-108">[out] The location that receives a pointer to the address of the function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="70e63-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="70e63-109">Return Value</span></span>  
 <span data-ttu-id="70e63-110">Bu yöntem, CorError. h içinde tanımlanan aşağıdaki değerlere ek olarak, WinError. h içinde tanımlanan standart bileşen nesne modeli (COM) hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="70e63-110">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values defined in CorError.h.</span></span>  
  
|<span data-ttu-id="70e63-111">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="70e63-111">Return code</span></span>|<span data-ttu-id="70e63-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70e63-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="70e63-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="70e63-113">S_OK</span></span>|<span data-ttu-id="70e63-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="70e63-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="70e63-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="70e63-115">E_POINTER</span></span>|<span data-ttu-id="70e63-116">`ppv`geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="70e63-116">`ppv` is not valid.</span></span>|  
|<span data-ttu-id="70e63-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="70e63-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="70e63-118">İşlev çalışma zamanından dışarıya aktarılmamış.</span><span class="sxs-lookup"><span data-stu-id="70e63-118">The function is not exported from the runtime.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="70e63-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="70e63-119">Requirements</span></span>  
 <span data-ttu-id="70e63-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70e63-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70e63-121">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="70e63-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="70e63-122">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="70e63-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="70e63-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70e63-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70e63-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70e63-124">See also</span></span>

- [<span data-ttu-id="70e63-125">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="70e63-125">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
