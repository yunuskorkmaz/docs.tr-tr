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
ms.openlocfilehash: cf0aa035b78b582ede76f288443734c25e92a02c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466537"
---
# <a name="loadlibraryshim-function"></a><span data-ttu-id="774ea-102">LoadLibraryShim İşlevi</span><span class="sxs-lookup"><span data-stu-id="774ea-102">LoadLibraryShim Function</span></span>
<span data-ttu-id="774ea-103">Belirtilen .NET Framework yeniden dağıtılabilir pakette bulunan bir DLL sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="774ea-103">Loads a specified version of a DLL that is included in the .NET Framework redistributable package.</span></span>  
  
 <span data-ttu-id="774ea-104">Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="774ea-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="774ea-105">Kullanım [Iclrruntimeınfo::LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="774ea-105">Use the [ICLRRuntimeInfo::LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="774ea-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="774ea-106">Syntax</span></span>  
  
```  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="774ea-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="774ea-107">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="774ea-108">[in] .NET Framework Kitaplığı'ndan yüklenecek DLL adını temsil eden sıfır ile sonlandırılmış dize.</span><span class="sxs-lookup"><span data-stu-id="774ea-108">[in] A zero-terminated string that represents the name of the DLL to be loaded from the .NET Framework library.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="774ea-109">[in] Yüklenecek DLL sürümünü temsil eden sıfır ile sonlandırılmış dize.</span><span class="sxs-lookup"><span data-stu-id="774ea-109">[in] A zero-terminated string that represents the version of the DLL to be loaded.</span></span> <span data-ttu-id="774ea-110">Varsa `szVersion` null, 4 sürümünden küçük belirtilen DLL'yi en son sürümünü yükleme için seçilen sürüm olduğu.</span><span class="sxs-lookup"><span data-stu-id="774ea-110">If `szVersion` is null, the version selected for loading is the latest version of the specified DLL that is less than version 4.</span></span> <span data-ttu-id="774ea-111">Diğer bir deyişle, tüm sürümler sürüm 4'değerinden büyük veya eşit sayılır `szVersion` null ise, sürüm 4 değerinden hiçbir sürüm yüklüyse, DLL yüklenecek başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="774ea-111">That is, all versions equal to or greater than version 4 are ignored if `szVersion` is null, and if no version less than version 4 is installed, the DLL fails to load.</span></span> <span data-ttu-id="774ea-112">Bu yüklemesi sağlamaktır [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] önceden mevcut olan uygulamaları veya bileşenleri etkilemez.</span><span class="sxs-lookup"><span data-stu-id="774ea-112">This is to ensure that installation of the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] does not affect pre-existing applications or components.</span></span> <span data-ttu-id="774ea-113">Girdisine bakın [In-Proc SxS ve geçiş Hızlı Başlangıç](https://go.microsoft.com/fwlink/?LinkId=200329) CLR Ekibi blogunda.</span><span class="sxs-lookup"><span data-stu-id="774ea-113">See the entry [In-Proc SxS and Migration Quick Start](https://go.microsoft.com/fwlink/?LinkId=200329) in the CLR team blog.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="774ea-114">Daha sonraki kullanımlar için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="774ea-114">Reserved for future use.</span></span>  
  
 `phModDll`  
 <span data-ttu-id="774ea-115">[out] Modül tanıtıcısını işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="774ea-115">[out] A pointer to the handle of the module.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="774ea-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="774ea-116">Return Value</span></span>  
 <span data-ttu-id="774ea-117">Bu yöntem standart Bileşen Nesne Modeli (COM) hata kodları, ek olarak aşağıdaki değerleri Wınerror içinde tanımlanan döndürür.</span><span class="sxs-lookup"><span data-stu-id="774ea-117">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="774ea-118">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="774ea-118">Return code</span></span>|<span data-ttu-id="774ea-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="774ea-119">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="774ea-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="774ea-120">S_OK</span></span>|<span data-ttu-id="774ea-121">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="774ea-121">The method completed successfully.</span></span>|  
|<span data-ttu-id="774ea-122">CLR_E_SHIM_RUNTIMELOAD</span><span class="sxs-lookup"><span data-stu-id="774ea-122">CLR_E_SHIM_RUNTIMELOAD</span></span>|<span data-ttu-id="774ea-123">Yükleme `szDllName` ortak dil çalışma zamanı (CLR) ve CLR'nin gereken sürümü yüklenemiyor yüklenmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="774ea-123">Loading `szDllName` requires loading the common language runtime (CLR), and the necessary version of the CLR cannot be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="774ea-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="774ea-124">Remarks</span></span>  
 <span data-ttu-id="774ea-125">Bu işlev, .NET Framework yeniden dağıtılabilir paketine dahil edilen DLL'lerini yüklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="774ea-125">This function is used to load DLLs that are included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="774ea-126">Kullanıcı tarafından oluşturulan DLL'leri yüklenmez.</span><span class="sxs-lookup"><span data-stu-id="774ea-126">It does not load user-generated DLLs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="774ea-127">.NET Framework sürüm 2.0 ile başlayarak, Fusion.dll yüklenirken yüklenecek CLR neden olur.</span><span class="sxs-lookup"><span data-stu-id="774ea-127">Beginning with the .NET Framework version 2.0, loading Fusion.dll causes the CLR to be loaded.</span></span> <span data-ttu-id="774ea-128">Fusion.dll işlevler çalışma zamanı tarafından sağlanan uygulamaları sarmalayıcıları sunulmuştur olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="774ea-128">This is because the functions in Fusion.dll are now wrappers whose implementations are provided by the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="774ea-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="774ea-129">Requirements</span></span>  
 <span data-ttu-id="774ea-130">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="774ea-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="774ea-131">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="774ea-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="774ea-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="774ea-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="774ea-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="774ea-133">See also</span></span>
- [<span data-ttu-id="774ea-134">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="774ea-134">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
