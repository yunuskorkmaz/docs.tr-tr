---
title: ICorDebug::CreateProcess Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebug.CreateProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CreateProcess
helpviewer_keywords:
- ICorDebug::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: b6128694-11ed-46e7-bd4e-49ea1914c46a
topic_type:
- apiref
ms.openlocfilehash: cb16bae2dfe151d04c40269a8e6872ecb49b4269
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789008"
---
# <a name="icordebugcreateprocess-method"></a><span data-ttu-id="07ab6-102">ICorDebug::CreateProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="07ab6-102">ICorDebug::CreateProcess Method</span></span>
<span data-ttu-id="07ab6-103">Hata ayıklayıcının denetimi altında bir işlem ve birincil iş parçacığını başlatır.</span><span class="sxs-lookup"><span data-stu-id="07ab6-103">Launches a process and its primary thread under the control of the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07ab6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="07ab6-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateProcess (  
    [in]  LPCWSTR                     lpApplicationName,  
    [in]  LPWSTR                      lpCommandLine,  
    [in]  LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
    [in]  LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
    [in]  BOOL                        bInheritHandles,  
    [in]  DWORD                       dwCreationFlags,  
    [in]  PVOID                       lpEnvironment,  
    [in]  LPCWSTR                     lpCurrentDirectory,  
    [in]  LPSTARTUPINFOW              lpStartupInfo,  
    [in]  LPPROCESS_INFORMATION       lpProcessInformation,  
    [in]  CorDebugCreateProcessFlags  debuggingFlags,  
    [out] ICorDebugProcess            **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07ab6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="07ab6-105">Parameters</span></span>  
 `lpApplicationName`  
 <span data-ttu-id="07ab6-106">'ndaki Başlatılan işlem tarafından yürütülecek modülü belirten, null ile sonlandırılmış bir dize işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="07ab6-106">[in] Pointer to a null-terminated string that specifies the module to be executed by the launched process.</span></span> <span data-ttu-id="07ab6-107">Modül, çağıran işlemin güvenlik bağlamında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="07ab6-107">The module is executed in the security context of the calling process.</span></span>  
  
 `lpCommandLine`  
 <span data-ttu-id="07ab6-108">'ndaki Başlatılan işlem tarafından yürütülecek komut satırını belirten, null ile sonlandırılmış bir dize işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="07ab6-108">[in] Pointer to a null-terminated string that specifies the command line to be executed by the launched process.</span></span> <span data-ttu-id="07ab6-109">Uygulama adı (örneğin, "SomeApp. exe") ilk bağımsız değişken olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="07ab6-109">The application name (for example, "SomeApp.exe") must be the first argument.</span></span>  
  
 `lpProcessAttributes`  
 <span data-ttu-id="07ab6-110">'ndaki İşlemin güvenlik tanımlayıcısını belirten bir Win32 `SECURITY_ATTRIBUTES` yapısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="07ab6-110">[in] Pointer to a Win32 `SECURITY_ATTRIBUTES` structure that specifies the security descriptor for the process.</span></span> <span data-ttu-id="07ab6-111">`lpProcessAttributes` null ise, işlem varsayılan bir güvenlik tanımlayıcısı alır.</span><span class="sxs-lookup"><span data-stu-id="07ab6-111">If `lpProcessAttributes` is null, the process gets a default security descriptor.</span></span>  
  
 `lpThreadAttributes`  
 <span data-ttu-id="07ab6-112">'ndaki İşlemin birincil iş parçacığının güvenlik tanımlayıcısını belirten bir Win32 `SECURITY_ATTRIBUTES` yapısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="07ab6-112">[in] Pointer to a Win32 `SECURITY_ATTRIBUTES` structure that specifies the security descriptor for the primary thread of the process.</span></span> <span data-ttu-id="07ab6-113">`lpThreadAttributes` null ise, iş parçacığı varsayılan bir güvenlik tanımlayıcısı alır.</span><span class="sxs-lookup"><span data-stu-id="07ab6-113">If `lpThreadAttributes` is null, the thread gets a default security descriptor.</span></span>  
  
 `bInheritHandles`  
 <span data-ttu-id="07ab6-114">'ndaki Çağıran işlemdeki her bir devralınabilir tanıtıcının başlatılan işlem tarafından devralındığını veya tanıtıcıların devralınamayacağını belirtmek için `false` `true` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="07ab6-114">[in] Set to `true` to indicate that each inheritable handle in the calling process is inherited by the launched process, or `false` to indicate that the handles are not inherited.</span></span> <span data-ttu-id="07ab6-115">Devralınan tutamaçlar, özgün tanıtıcılarla aynı değere ve erişim haklarına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="07ab6-115">The inherited handles have the same value and access rights as the original handles.</span></span>  
  
 `dwCreationFlags`  
 <span data-ttu-id="07ab6-116">'ndaki Öncelik sınıfını ve başlatılan işlemin davranışını denetleyen [Win32 Işlemi oluşturma bayraklarının](/windows/win32/procthread/process-creation-flags) bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="07ab6-116">[in] A bitwise combination of the [Win32 Process Creation Flags](/windows/win32/procthread/process-creation-flags) that control the priority class and the behavior of the launched process.</span></span>  
  
 `lpEnvironment`  
 <span data-ttu-id="07ab6-117">'ndaki Yeni işlem için ortam bloğunun işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="07ab6-117">[in] Pointer to an environment block for the new process.</span></span>  
  
 `lpCurrentDirectory`  
 <span data-ttu-id="07ab6-118">'ndaki İşlem için geçerli dizinin tam yolunu belirten, null ile sonlandırılmış bir dize işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="07ab6-118">[in] Pointer to a null-terminated string that specifies the full path to the current directory for the process.</span></span> <span data-ttu-id="07ab6-119">Bu parametre null ise, yeni işlem çağıran işlemle aynı geçerli sürücü ve dizine sahip olur.</span><span class="sxs-lookup"><span data-stu-id="07ab6-119">If this parameter is null, the new process will have the same current drive and directory as the calling process.</span></span>  
  
 `lpStartupInfo`  
 <span data-ttu-id="07ab6-120">'ndaki Başlatılan işlemin ana penceresinin pencere istasyonunu, masaüstünü, standart tutamaçlarını ve görünümünü belirten bir Win32 `STARTUPINFOW` yapısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="07ab6-120">[in] Pointer to a Win32 `STARTUPINFOW` structure that specifies the window station, desktop, standard handles, and appearance of the main window for the launched process.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="07ab6-121">'ndaki Başlatılacak işlemle ilgili kimlik bilgilerini belirten bir Win32 `PROCESS_INFORMATION` yapısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="07ab6-121">[in] Pointer to a Win32 `PROCESS_INFORMATION` structure that specifies the identification information about the process to be launched.</span></span>  
  
 `debuggingFlags`  
 <span data-ttu-id="07ab6-122">'ndaki Hata ayıklama seçeneklerini belirten CorDebugCreateProcessFlags numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="07ab6-122">[in] A value of the CorDebugCreateProcessFlags enumeration that specifies the debugging options.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="07ab6-123">dışı İşlemi temsil eden ICorDebugProcess nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="07ab6-123">[out] A pointer to the address of a ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07ab6-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07ab6-124">Remarks</span></span>  
 <span data-ttu-id="07ab6-125">Bu yöntemin parametreleri, Win32 `CreateProcess` yöntemi ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="07ab6-125">The parameters of this method are the same as those of the Win32 `CreateProcess` method.</span></span>  
  
 <span data-ttu-id="07ab6-126">Yönetilmeyen karma mod hata ayıklamayı etkinleştirmek için `dwCreationFlags` DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="07ab6-126">To enable unmanaged mixed-mode debugging, set `dwCreationFlags` to DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS.</span></span> <span data-ttu-id="07ab6-127">Yalnızca yönetilen hata ayıklamayı kullanmak istiyorsanız, bu bayrakları ayarlamayın.</span><span class="sxs-lookup"><span data-stu-id="07ab6-127">If you want to use only managed debugging, do not set these flags.</span></span>  
  
 <span data-ttu-id="07ab6-128">Hata ayıklayıcı ve hataları Ayıklanacak işlem (ekli işlem) tek bir konsolu paylaşıyorsa ve birlikte çalışma hata ayıklaması kullanılırsa, ekli işlemin konsol kilitlerini tutması ve hata ayıklama olayında durdurulması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="07ab6-128">If the debugger and the process to be debugged (the attached process) share a single console, and if interop debugging is used, it is possible for the attached process to hold console locks and stop at a debug event.</span></span> <span data-ttu-id="07ab6-129">Hata ayıklayıcı daha sonra konsolu kullanma denemesini engeller.</span><span class="sxs-lookup"><span data-stu-id="07ab6-129">The debugger will then block any attempt to use the console.</span></span> <span data-ttu-id="07ab6-130">Bu sorundan kaçınmak için `dwCreationFlags` parametresindeki CREATE_NEW_CONSOLE bayrağını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="07ab6-130">To avoid this problem, set the CREATE_NEW_CONSOLE flag in the `dwCreationFlags` parameter.</span></span>  
  
 <span data-ttu-id="07ab6-131">Birlikte çalışabilirlik hata ayıklaması, IA-64 tabanlı ve AMD64 tabanlı platformlar gibi Win9x ve x86 olmayan platformlarda desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="07ab6-131">Interop debugging is not supported on Win9x and non-x86 platforms such as IA-64-based and AMD64-based platforms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07ab6-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="07ab6-132">Requirements</span></span>  
 <span data-ttu-id="07ab6-133">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07ab6-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07ab6-134">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="07ab6-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="07ab6-135">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="07ab6-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07ab6-136">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07ab6-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07ab6-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07ab6-137">See also</span></span>

- [<span data-ttu-id="07ab6-138">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="07ab6-138">ICorDebug Interface</span></span>](icordebug-interface.md)
