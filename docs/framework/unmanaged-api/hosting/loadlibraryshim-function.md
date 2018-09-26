---
title: LoadLibraryShim İşlevi
ms.date: 03/30/2017
api_name:
- LoadLibraryShim
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LoadLibraryShim
helpviewer_keywords:
- LoadLibraryShim function [.NET Framework hosting]
ms.assetid: 30931874-4d0e-4df1-b3d1-e425b50655d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5fe1ba15f8a9f8ee79582158209049c1e502a61d
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47199880"
---
# <a name="loadlibraryshim-function"></a><span data-ttu-id="c0fc6-102">LoadLibraryShim İşlevi</span><span class="sxs-lookup"><span data-stu-id="c0fc6-102">LoadLibraryShim Function</span></span>
<span data-ttu-id="c0fc6-103">Belirtilen .NET Framework yeniden dağıtılabilir pakette bulunan bir DLL sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="c0fc6-103">Loads a specified version of a DLL that is included in the .NET Framework redistributable package.</span></span>  
  
 <span data-ttu-id="c0fc6-104">Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c0fc6-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="c0fc6-105">Kullanım [Iclrruntimeınfo::LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="c0fc6-105">Use the [ICLRRuntimeInfo::LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0fc6-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c0fc6-106">Syntax</span></span>  
  
```  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c0fc6-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c0fc6-107">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="c0fc6-108">[in] .NET Framework Kitaplığı'ndan yüklenecek DLL adını temsil eden sıfır ile sonlandırılmış dize.</span><span class="sxs-lookup"><span data-stu-id="c0fc6-108">[in] A zero-terminated string that represents the name of the DLL to be loaded from the .NET Framework library.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="c0fc6-109">[in] Yüklenecek DLL sürümünü temsil eden sıfır ile sonlandırılmış dize.</span><span class="sxs-lookup"><span data-stu-id="c0fc6-109">[in] A zero-terminated string that represents the version of the DLL to be loaded.</span></span> <span data-ttu-id="c0fc6-110">Varsa `szVersion` null, 4 sürümünden küçük belirtilen DLL'yi en son sürümünü yükleme için seçilen sürüm olduğu.</span><span class="sxs-lookup"><span data-stu-id="c0fc6-110">If `szVersion` is null, the version selected for loading is the latest version of the specified DLL that is less than version 4.</span></span> <span data-ttu-id="c0fc6-111">Diğer bir deyişle, tüm sürümler sürüm 4'değerinden büyük veya eşit sayılır `szVersion` null ise, sürüm 4 değerinden hiçbir sürüm yüklüyse, DLL yüklenecek başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="c0fc6-111">That is, all versions equal to or greater than version 4 are ignored if `szVersion` is null, and if no version less than version 4 is installed, the DLL fails to load.</span></span> <span data-ttu-id="c0fc6-112">Bu yüklemesi sağlamaktır [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] önceden mevcut olan uygulamaları veya bileşenleri etkilemez.</span><span class="sxs-lookup"><span data-stu-id="c0fc6-112">This is to ensure that installation of the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] does not affect pre-existing applications or components.</span></span> <span data-ttu-id="c0fc6-113">Girdisine bakın [In-Proc SxS ve geçiş Hızlı Başlangıç](https://go.microsoft.com/fwlink/?LinkId=200329) CLR Ekibi blogunda.</span><span class="sxs-lookup"><span data-stu-id="c0fc6-113">See the entry [In-Proc SxS and Migration Quick Start](https://go.microsoft.com/fwlink/?LinkId=200329) in the CLR team blog.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="c0fc6-114">Daha sonraki kullanımlar için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="c0fc6-114">Reserved for future use.</span></span>  
  
 `phModDll`  
 <span data-ttu-id="c0fc6-115">[out] Modül tanıtıcısını işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c0fc6-115">[out] A pointer to the handle of the module.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c0fc6-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c0fc6-116">Return Value</span></span>  
 <span data-ttu-id="c0fc6-117">Bu yöntem standart Bileşen Nesne Modeli (COM) hata kodları, ek olarak aşağıdaki değerleri Wınerror içinde tanımlanan döndürür.</span><span class="sxs-lookup"><span data-stu-id="c0fc6-117">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="c0fc6-118">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="c0fc6-118">Return code</span></span>|<span data-ttu-id="c0fc6-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c0fc6-119">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="c0fc6-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="c0fc6-120">S_OK</span></span>|<span data-ttu-id="c0fc6-121">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="c0fc6-121">The method completed successfully.</span></span>|  
|<span data-ttu-id="c0fc6-122">CLR_E_SHIM_RUNTIMELOAD</span><span class="sxs-lookup"><span data-stu-id="c0fc6-122">CLR_E_SHIM_RUNTIMELOAD</span></span>|<span data-ttu-id="c0fc6-123">Yükleme `szDllName` ortak dil çalışma zamanı (CLR) ve CLR'nin gereken sürümü yüklenemiyor yüklenmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c0fc6-123">Loading `szDllName` requires loading the common language runtime (CLR), and the necessary version of the CLR cannot be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0fc6-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c0fc6-124">Remarks</span></span>  
 <span data-ttu-id="c0fc6-125">Bu işlev, .NET Framework yeniden dağıtılabilir paketine dahil edilen DLL'lerini yüklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c0fc6-125">This function is used to load DLLs that are included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="c0fc6-126">Kullanıcı tarafından oluşturulan DLL'leri yüklenmez.</span><span class="sxs-lookup"><span data-stu-id="c0fc6-126">It does not load user-generated DLLs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c0fc6-127">.NET Framework sürüm 2.0 ile başlayarak, Fusion.dll yüklenirken yüklenecek CLR neden olur.</span><span class="sxs-lookup"><span data-stu-id="c0fc6-127">Beginning with the .NET Framework version 2.0, loading Fusion.dll causes the CLR to be loaded.</span></span> <span data-ttu-id="c0fc6-128">Fusion.dll işlevler çalışma zamanı tarafından sağlanan uygulamaları sarmalayıcıları sunulmuştur olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="c0fc6-128">This is because the functions in Fusion.dll are now wrappers whose implementations are provided by the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0fc6-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c0fc6-129">Requirements</span></span>  
 <span data-ttu-id="c0fc6-130">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0fc6-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0fc6-131">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c0fc6-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c0fc6-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0fc6-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0fc6-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c0fc6-133">See Also</span></span>  
 [<span data-ttu-id="c0fc6-134">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="c0fc6-134">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
