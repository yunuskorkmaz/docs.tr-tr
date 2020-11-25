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
ms.openlocfilehash: d5e9ba0023b6516eb6190f32bc65b2b8b6af79f9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727568"
---
# <a name="loadlibraryshim-function"></a><span data-ttu-id="ccdc9-102">LoadLibraryShim İşlevi</span><span class="sxs-lookup"><span data-stu-id="ccdc9-102">LoadLibraryShim Function</span></span>

<span data-ttu-id="ccdc9-103">Yeniden dağıtılabilir .NET Framework paketinde bulunan bir DLL 'nin belirtilen sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="ccdc9-103">Loads a specified version of a DLL that is included in the .NET Framework redistributable package.</span></span>  
  
 <span data-ttu-id="ccdc9-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="ccdc9-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="ccdc9-105">Bunun yerine [ICLRRuntimeInfo:: LoadLibrary](iclrruntimeinfo-loadlibrary-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ccdc9-105">Use the [ICLRRuntimeInfo::LoadLibrary](iclrruntimeinfo-loadlibrary-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccdc9-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ccdc9-106">Syntax</span></span>  
  
```cpp  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ccdc9-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ccdc9-107">Parameters</span></span>  

 `szDllName`  
 <span data-ttu-id="ccdc9-108">'ndaki .NET Framework kitaplığından yüklenecek DLL 'nin adını temsil eden sıfır ile sonlandırılmış bir dize.</span><span class="sxs-lookup"><span data-stu-id="ccdc9-108">[in] A zero-terminated string that represents the name of the DLL to be loaded from the .NET Framework library.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="ccdc9-109">'ndaki Yüklenecek DLL sürümünü temsil eden sıfır ile sonlandırılmış bir dize.</span><span class="sxs-lookup"><span data-stu-id="ccdc9-109">[in] A zero-terminated string that represents the version of the DLL to be loaded.</span></span> <span data-ttu-id="ccdc9-110">`szVersion`Null ise, yükleme için seçilen sürüm, BELIRTILEN dll 'nin sürüm 4 ' ten küçük olan en son sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="ccdc9-110">If `szVersion` is null, the version selected for loading is the latest version of the specified DLL that is less than version 4.</span></span> <span data-ttu-id="ccdc9-111">Yani, sürüm 4 ' ten büyük veya bundan büyük olan tüm sürümler yok sayılır `szVersion` ve sürüm 4 ' ten küçük bir sürüm yüklü değilse, dll yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="ccdc9-111">That is, all versions equal to or greater than version 4 are ignored if `szVersion` is null, and if no version less than version 4 is installed, the DLL fails to load.</span></span> <span data-ttu-id="ccdc9-112">Bu, .NET Framework 4 yüklemesinin önceden var olan uygulamaları veya bileşenleri etkilememesini sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="ccdc9-112">This is to ensure that installation of the .NET Framework 4 does not affect pre-existing applications or components.</span></span> <span data-ttu-id="ccdc9-113">CLR ekibi bloguna [-proc sxs ve geçiş hızlı başlangıç](https://devblogs.microsoft.com/dotnet/in-proc-sxs-and-migration-quick-start/) girdisine bakın.</span><span class="sxs-lookup"><span data-stu-id="ccdc9-113">See the entry [In-Proc SxS and Migration Quick Start](https://devblogs.microsoft.com/dotnet/in-proc-sxs-and-migration-quick-start/) in the CLR team blog.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="ccdc9-114">Daha sonraki kullanımlar için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="ccdc9-114">Reserved for future use.</span></span>  
  
 `phModDll`  
 <span data-ttu-id="ccdc9-115">dışı Modülün tanıtıcısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ccdc9-115">[out] A pointer to the handle of the module.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ccdc9-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ccdc9-116">Return Value</span></span>  

 <span data-ttu-id="ccdc9-117">Bu yöntem, aşağıdaki değerlere ek olarak, WinError. h içinde tanımlanan standart bileşen nesne modeli (COM) hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="ccdc9-117">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="ccdc9-118">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="ccdc9-118">Return code</span></span>|<span data-ttu-id="ccdc9-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ccdc9-119">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="ccdc9-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="ccdc9-120">S_OK</span></span>|<span data-ttu-id="ccdc9-121">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="ccdc9-121">The method completed successfully.</span></span>|  
|<span data-ttu-id="ccdc9-122">CLR_E_SHIM_RUNTIMELOAD</span><span class="sxs-lookup"><span data-stu-id="ccdc9-122">CLR_E_SHIM_RUNTIMELOAD</span></span>|<span data-ttu-id="ccdc9-123">Yükleme, `szDllName` ortak dil çalışma zamanının (CLR) yüklenmesini gerektirir ve clr 'nin gerekli sürümü yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="ccdc9-123">Loading `szDllName` requires loading the common language runtime (CLR), and the necessary version of the CLR cannot be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ccdc9-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ccdc9-124">Remarks</span></span>  

 <span data-ttu-id="ccdc9-125">Bu işlev, .NET Framework yeniden dağıtılabilir pakette bulunan dll 'Leri yüklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ccdc9-125">This function is used to load DLLs that are included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="ccdc9-126">Kullanıcı tarafından oluşturulan dll 'Leri yüklemez.</span><span class="sxs-lookup"><span data-stu-id="ccdc9-126">It does not load user-generated DLLs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ccdc9-127">.NET Framework sürüm 2,0 ' den başlayarak, yükleme Fusion.dll CLR 'nin yüklenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="ccdc9-127">Beginning with the .NET Framework version 2.0, loading Fusion.dll causes the CLR to be loaded.</span></span> <span data-ttu-id="ccdc9-128">Bunun nedeni, Fusion.dll içindeki işlevlerin artık uygulamaları çalışma zamanı tarafından sağlandığı sarmalayıcılardır.</span><span class="sxs-lookup"><span data-stu-id="ccdc9-128">This is because the functions in Fusion.dll are now wrappers whose implementations are provided by the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccdc9-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ccdc9-129">Requirements</span></span>  

 <span data-ttu-id="ccdc9-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccdc9-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccdc9-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ccdc9-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ccdc9-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccdc9-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccdc9-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ccdc9-133">See also</span></span>

- [<span data-ttu-id="ccdc9-134">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="ccdc9-134">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
