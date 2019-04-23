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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 795392bc50d4b7c5eeb82b98230a52156f273f15
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59187375"
---
# <a name="icordebugcreateprocess-method"></a><span data-ttu-id="3bc0c-102">ICorDebug::CreateProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3bc0c-102">ICorDebug::CreateProcess Method</span></span>
<span data-ttu-id="3bc0c-103">Bir işlem ve onun birincil iş parçacığı hata ayıklayıcının denetiminin altında başlatır.</span><span class="sxs-lookup"><span data-stu-id="3bc0c-103">Launches a process and its primary thread under the control of the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bc0c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3bc0c-104">Syntax</span></span>  
  
```  
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
  
## <a name="parameters"></a><span data-ttu-id="3bc0c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3bc0c-105">Parameters</span></span>  
 `lpApplicationName`  
 <span data-ttu-id="3bc0c-106">[in] Başlatılan işlem tarafından yürütülecek modülü belirtiyorsa null ile sonlandırılmış bir dize işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="3bc0c-106">[in] Pointer to a null-terminated string that specifies the module to be executed by the launched process.</span></span> <span data-ttu-id="3bc0c-107">Modül çağırma işleminin bağlamında çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="3bc0c-107">The module is executed in the security context of the calling process.</span></span>  
  
 `lpCommandLine`  
 <span data-ttu-id="3bc0c-108">[in] Başlatılan işlem tarafından yürütülecek komut satırı belirten bir null ile sonlandırılmış dize işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="3bc0c-108">[in] Pointer to a null-terminated string that specifies the command line to be executed by the launched process.</span></span> <span data-ttu-id="3bc0c-109">Uygulama adı (örneğin, "SomeApp.exe"), ilk bağımsız değişken olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3bc0c-109">The application name (for example, "SomeApp.exe") must be the first argument.</span></span>  
  
 `lpProcessAttributes`  
 <span data-ttu-id="3bc0c-110">[in] Bir Win32 işaretçisine `SECURITY_ATTRIBUTES` işlemi için güvenlik tanımlayıcısı belirten yapısı.</span><span class="sxs-lookup"><span data-stu-id="3bc0c-110">[in] Pointer to a Win32 `SECURITY_ATTRIBUTES` structure that specifies the security descriptor for the process.</span></span> <span data-ttu-id="3bc0c-111">Varsa `lpProcessAttributes` olan null, işlem varsayılan güvenlik tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="3bc0c-111">If `lpProcessAttributes` is null, the process gets a default security descriptor.</span></span>  
  
 `lpThreadAttributes`  
 <span data-ttu-id="3bc0c-112">[in] Bir Win32 işaretçisine `SECURITY_ATTRIBUTES` işlemin birincil iş parçacığı için güvenlik tanımlayıcısı belirten yapısı.</span><span class="sxs-lookup"><span data-stu-id="3bc0c-112">[in] Pointer to a Win32 `SECURITY_ATTRIBUTES` structure that specifies the security descriptor for the primary thread of the process.</span></span> <span data-ttu-id="3bc0c-113">Varsa `lpThreadAttributes` olan null, iş parçacığı bir varsayılan güvenlik tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="3bc0c-113">If `lpThreadAttributes` is null, the thread gets a default security descriptor.</span></span>  
  
 `bInheritHandles`  
 <span data-ttu-id="3bc0c-114">[in] Kümesine `true` çağırma işleminde devralınabilir her tutamacı başlatılan işlem tarafından devralınır belirtmek için veya `false` tutamaçları devralınmaz belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="3bc0c-114">[in] Set to `true` to indicate that each inheritable handle in the calling process is inherited by the launched process, or `false` to indicate that the handles are not inherited.</span></span> <span data-ttu-id="3bc0c-115">Devralınan tutamaçları özgün tutamaçlarını aynı değeri ve erişim haklarına sahip.</span><span class="sxs-lookup"><span data-stu-id="3bc0c-115">The inherited handles have the same value and access rights as the original handles.</span></span>  
  
 `dwCreationFlags`  
 <span data-ttu-id="3bc0c-116">[in] Bitsel bir birleşimi [Win32 işlem oluşturma bayrak](https://go.microsoft.com/fwlink/?linkid=69981) öncelik sınıfı ve başlatılan işlemin davranışını kontrol eden.</span><span class="sxs-lookup"><span data-stu-id="3bc0c-116">[in] A bitwise combination of the [Win32 Process Creation Flags](https://go.microsoft.com/fwlink/?linkid=69981) that control the priority class and the behavior of the launched process.</span></span>  
  
 `lpEnvironment`  
 <span data-ttu-id="3bc0c-117">[in] Yeni işlem için bir ortam bloğuna işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3bc0c-117">[in] Pointer to an environment block for the new process.</span></span>  
  
 `lpCurrentDirectory`  
 <span data-ttu-id="3bc0c-118">[in] İşlem için geçerli dizin tam yolunu belirtir null ile sonlandırılmış bir dize işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="3bc0c-118">[in] Pointer to a null-terminated string that specifies the full path to the current directory for the process.</span></span> <span data-ttu-id="3bc0c-119">Bu parametre null ise, yeni işlem çağırma işlemi aynı geçerli sürücü ve dizine sahip.</span><span class="sxs-lookup"><span data-stu-id="3bc0c-119">If this parameter is null, the new process will have the same current drive and directory as the calling process.</span></span>  
  
 `lpStartupInfo`  
 <span data-ttu-id="3bc0c-120">[in] Bir Win32 işaretçisine `STARTUPINFOW` iş istasyonunda, masaüstü, standart tanıtıcıları ve başlatılan işlem için ana penceresinin görünümünü belirtir yapısı.</span><span class="sxs-lookup"><span data-stu-id="3bc0c-120">[in] Pointer to a Win32 `STARTUPINFOW` structure that specifies the window station, desktop, standard handles, and appearance of the main window for the launched process.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="3bc0c-121">[in] Bir Win32 işaretçisine `PROCESS_INFORMATION` yapısı başlatılacak işlemine ilişkin kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3bc0c-121">[in] Pointer to a Win32 `PROCESS_INFORMATION` structure that specifies the identification information about the process to be launched.</span></span>  
  
 `debuggingFlags`  
 <span data-ttu-id="3bc0c-122">[in] Hata ayıklama seçenekleri belirten CorDebugCreateProcessFlags sabit listesi değeri.</span><span class="sxs-lookup"><span data-stu-id="3bc0c-122">[in] A value of the CorDebugCreateProcessFlags enumeration that specifies the debugging options.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="3bc0c-123">[out] İşlemi temsil eden Icordebugprocess nesnesi adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3bc0c-123">[out] A pointer to the address of a ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3bc0c-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3bc0c-124">Remarks</span></span>  
 <span data-ttu-id="3bc0c-125">Bu yöntem parametrelerini Win32 aynıdır `CreateProcess` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3bc0c-125">The parameters of this method are the same as those of the Win32 `CreateProcess` method.</span></span>  
  
 <span data-ttu-id="3bc0c-126">Yönetilmeyen karışık mod hata ayıklamayı etkinleştirmek için ayarlanmış `dwCreationFlags` DEBUG_PROCESS için &#124; DEBUG_ONLY_THIS_PROCESS.</span><span class="sxs-lookup"><span data-stu-id="3bc0c-126">To enable unmanaged mixed-mode debugging, set `dwCreationFlags` to DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS.</span></span> <span data-ttu-id="3bc0c-127">Yalnızca yönetilen hata ayıklama kullanmak istiyorsanız, bu bayraklar ayarlamayın.</span><span class="sxs-lookup"><span data-stu-id="3bc0c-127">If you want to use only managed debugging, do not set these flags.</span></span>  
  
 <span data-ttu-id="3bc0c-128">Hata ayıklayıcı ve işlem olacak şekilde (iliştirilmiş işlem) hata ayıklaması, tek bir konsol paylaşmak ve birlikte çalışma hata ayıklama kullanılıyorsa bir hata ayıklama etkinlikte durdurmak ve konsol için kilitler barındırmıyorsa iliştirilmiş işlem mümkündür.</span><span class="sxs-lookup"><span data-stu-id="3bc0c-128">If the debugger and the process to be debugged (the attached process) share a single console, and if interop debugging is used, it is possible for the attached process to hold console locks and stop at a debug event.</span></span> <span data-ttu-id="3bc0c-129">Hata ayıklayıcı, ardından konsolunu kullanmak için her türlü girişim engeller.</span><span class="sxs-lookup"><span data-stu-id="3bc0c-129">The debugger will then block any attempt to use the console.</span></span> <span data-ttu-id="3bc0c-130">Bu sorundan kaçınmak için CREATE_NEW_CONSOLE bayrağını ayarlayın `dwCreationFlags` parametresi.</span><span class="sxs-lookup"><span data-stu-id="3bc0c-130">To avoid this problem, set the CREATE_NEW_CONSOLE flag in the `dwCreationFlags` parameter.</span></span>  
  
 <span data-ttu-id="3bc0c-131">IA-64 tabanlı ve AMD64 tabanlı platformları gibi Win9x ve x86 olmayan platformlarda birlikte çalışma hata ayıklama desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="3bc0c-131">Interop debugging is not supported on Win9x and non-x86 platforms such as IA-64-based and AMD64-based platforms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bc0c-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3bc0c-132">Requirements</span></span>  
 <span data-ttu-id="3bc0c-133">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bc0c-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bc0c-134">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3bc0c-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3bc0c-135">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3bc0c-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3bc0c-136">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bc0c-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bc0c-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3bc0c-137">See also</span></span>

- [<span data-ttu-id="3bc0c-138">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3bc0c-138">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
