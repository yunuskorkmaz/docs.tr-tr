---
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
ms.openlocfilehash: 3b2322f708afed08172f87e843c225aa9c60d9d3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616612"
---
# <a name="_cordllmain-function"></a><span data-ttu-id="0dde8-102">\_CorDllMain Işlevi</span><span class="sxs-lookup"><span data-stu-id="0dde8-102">\_CorDllMain Function</span></span>

<span data-ttu-id="0dde8-103">Ortak dil çalışma zamanını (CLR) başlatır, DLL derlemesinin CLR üst bilgisinde yönetilen giriş noktasını bulur ve yürütmeyi başlatır.</span><span class="sxs-lookup"><span data-stu-id="0dde8-103">Initializes the common language runtime (CLR), locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dde8-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0dde8-104">Syntax</span></span>  
  
```cpp  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0dde8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0dde8-105">Parameters</span></span>  
 `hInst`  
 <span data-ttu-id="0dde8-106">'ndaki Yüklenen modülün örnek tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="0dde8-106">[in] The instance handle of the loaded module.</span></span>  
  
 `dwReason`  
 <span data-ttu-id="0dde8-107">'ndaki DLL giriş noktası işlevinin neden çağrıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0dde8-107">[in]Indicates why the DLL entry-point function is being called.</span></span> <span data-ttu-id="0dde8-108">Bu parametre aşağıdaki değerlerden biri olabilir: DLL \_ PROCESS_ATTACH, dll \_ iş parçacığı \_ iliştirme, dll \_ Iş parçacığı \_ iliştirme veya dll \_ işlem \_ ayırma.</span><span class="sxs-lookup"><span data-stu-id="0dde8-108">This parameter can be one of the following values: DLL\_PROCESS_ATTACH, DLL\_THREAD\_ATTACH, DLL\_THREAD\_ATTACH, or DLL\_PROCESS\_DETACH.</span></span> <span data-ttu-id="0dde8-109">Bu değerlerin açıklamaları için `DllMain` Platform SDK 'sindeki belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="0dde8-109">For descriptions of these values, see the `DllMain` documentation in the Platform SDK.</span></span>  
  
 `lpReserved`  
 <span data-ttu-id="0dde8-110">'ndaki Kullanılmayan.</span><span class="sxs-lookup"><span data-stu-id="0dde8-110">[in] Unused.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0dde8-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0dde8-111">Return Value</span></span>  
 <span data-ttu-id="0dde8-112">Bu yöntem `true` başarı için döndürür ve `false` bir hata oluşursa.</span><span class="sxs-lookup"><span data-stu-id="0dde8-112">This method returns `true` for success and `false` if an error occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0dde8-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0dde8-113">Remarks</span></span>  
 <span data-ttu-id="0dde8-114">Bu işlev, DLL derlemeleri için işletim sistemi yükleyicisi tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="0dde8-114">This function is called by the operating system loader for DLL assemblies.</span></span> <span data-ttu-id="0dde8-115">Yürütülebilir derlemeler için yükleyici, bunun yerine [ \_ corexemain](corexemain-function.md) işlevini çağırır.</span><span class="sxs-lookup"><span data-stu-id="0dde8-115">For executable assemblies, the loader calls the [\_CorExeMain](corexemain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="0dde8-116">İşletim sistemi yükleyicisi, DLL dosyasında belirtilen giriş noktası ne olursa olsun bu yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="0dde8-116">The operating system loader calls this method regardless of the entry point specified in the DLL file.</span></span>  
  
<span data-ttu-id="0dde8-117">`_CorDllMain`İşlevi, işletim sistemi yükleyicisi tarafından doğrudan çağrılır.</span><span class="sxs-lookup"><span data-stu-id="0dde8-117">The `_CorDllMain` function is called directly by the operating system loader.</span></span>
  
 <span data-ttu-id="0dde8-118">Daha fazla bilgi için [ \_ corvalidateımage](corvalidateimage-function.md) konusunun açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0dde8-118">For additional information, see the Remarks section in the [\_CorValidateImage](corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0dde8-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0dde8-119">Requirements</span></span>  

 <span data-ttu-id="0dde8-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0dde8-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0dde8-121">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0dde8-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0dde8-122">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="0dde8-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0dde8-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0dde8-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dde8-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0dde8-124">See also</span></span>

- [<span data-ttu-id="0dde8-125">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="0dde8-125">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
