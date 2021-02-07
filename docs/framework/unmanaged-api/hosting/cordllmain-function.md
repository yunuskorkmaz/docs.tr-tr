---
description: 'Hakkında daha fazla bilgi edinin: _CorDllMain Işlevi'
title: _CorDllMain İşlevi
ms.date: 03/30/2017
api_name:
- _CorDllMain
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorDllMain
helpviewer_keywords:
- _CorDllMain function [.NET Framework hosting]
ms.assetid: bc7b51cf-39d3-48ec-a5cb-2f179fbefff8
topic_type:
- apiref
ms.openlocfilehash: 442afae3a627eb684a86c02fbc6e546aa804b7a5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717159"
---
# <a name="_cordllmain-function"></a><span data-ttu-id="78723-103">\_CorDllMain Işlevi</span><span class="sxs-lookup"><span data-stu-id="78723-103">\_CorDllMain Function</span></span>

<span data-ttu-id="78723-104">Ortak dil çalışma zamanını (CLR) başlatır, DLL derlemesinin CLR üst bilgisinde yönetilen giriş noktasını bulur ve yürütmeyi başlatır.</span><span class="sxs-lookup"><span data-stu-id="78723-104">Initializes the common language runtime (CLR), locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78723-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="78723-105">Syntax</span></span>  
  
```cpp  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78723-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="78723-106">Parameters</span></span>  

 `hInst`  
 <span data-ttu-id="78723-107">'ndaki Yüklenen modülün örnek tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="78723-107">[in] The instance handle of the loaded module.</span></span>  
  
 `dwReason`  
 <span data-ttu-id="78723-108">'ndaki DLL giriş noktası işlevinin neden çağrıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="78723-108">[in]Indicates why the DLL entry-point function is being called.</span></span> <span data-ttu-id="78723-109">Bu parametre aşağıdaki değerlerden biri olabilir: DLL \_ PROCESS_ATTACH, dll \_ iş parçacığı \_ iliştirme, dll \_ Iş parçacığı \_ iliştirme veya dll \_ işlem \_ ayırma.</span><span class="sxs-lookup"><span data-stu-id="78723-109">This parameter can be one of the following values: DLL\_PROCESS_ATTACH, DLL\_THREAD\_ATTACH, DLL\_THREAD\_ATTACH, or DLL\_PROCESS\_DETACH.</span></span> <span data-ttu-id="78723-110">Bu değerlerin açıklamaları için `DllMain` Platform SDK 'sindeki belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="78723-110">For descriptions of these values, see the `DllMain` documentation in the Platform SDK.</span></span>  
  
 `lpReserved`  
 <span data-ttu-id="78723-111">'ndaki Kullanılmayan.</span><span class="sxs-lookup"><span data-stu-id="78723-111">[in] Unused.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78723-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="78723-112">Return Value</span></span>  

 <span data-ttu-id="78723-113">Bu yöntem `true` başarı için döndürür ve `false` bir hata oluşursa.</span><span class="sxs-lookup"><span data-stu-id="78723-113">This method returns `true` for success and `false` if an error occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78723-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="78723-114">Remarks</span></span>  

 <span data-ttu-id="78723-115">Bu işlev, DLL derlemeleri için işletim sistemi yükleyicisi tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="78723-115">This function is called by the operating system loader for DLL assemblies.</span></span> <span data-ttu-id="78723-116">Yürütülebilir derlemeler için yükleyici, bunun yerine [ \_ corexemain](corexemain-function.md) işlevini çağırır.</span><span class="sxs-lookup"><span data-stu-id="78723-116">For executable assemblies, the loader calls the [\_CorExeMain](corexemain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="78723-117">İşletim sistemi yükleyicisi, DLL dosyasında belirtilen giriş noktası ne olursa olsun bu yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="78723-117">The operating system loader calls this method regardless of the entry point specified in the DLL file.</span></span>  
  
<span data-ttu-id="78723-118">`_CorDllMain`İşlevi, işletim sistemi yükleyicisi tarafından doğrudan çağrılır.</span><span class="sxs-lookup"><span data-stu-id="78723-118">The `_CorDllMain` function is called directly by the operating system loader.</span></span>
  
 <span data-ttu-id="78723-119">Daha fazla bilgi için [ \_ corvalidateımage](corvalidateimage-function.md) konusunun açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="78723-119">For additional information, see the Remarks section in the [\_CorValidateImage](corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78723-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="78723-120">Requirements</span></span>  

 <span data-ttu-id="78723-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78723-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78723-122">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="78723-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="78723-123">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="78723-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="78723-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78723-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78723-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78723-125">See also</span></span>

- [<span data-ttu-id="78723-126">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="78723-126">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
