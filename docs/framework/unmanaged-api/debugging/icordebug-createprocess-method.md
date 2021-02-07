---
description: ': ICorDebug:: CreateProcess yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: b504b5f7a60fd0fd4a8f8f1c5d8e3c3b8dcfd858
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712122"
---
# <a name="icordebugcreateprocess-method"></a><span data-ttu-id="e0920-103">ICorDebug::CreateProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e0920-103">ICorDebug::CreateProcess Method</span></span>

<span data-ttu-id="e0920-104">Hata ayıklayıcının denetimi altında bir işlem ve birincil iş parçacığını başlatır.</span><span class="sxs-lookup"><span data-stu-id="e0920-104">Launches a process and its primary thread under the control of the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0920-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e0920-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="e0920-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e0920-106">Parameters</span></span>  

 `lpApplicationName`  
 <span data-ttu-id="e0920-107">'ndaki Başlatılan işlem tarafından yürütülecek modülü belirten, null ile sonlandırılmış bir dize işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e0920-107">[in] Pointer to a null-terminated string that specifies the module to be executed by the launched process.</span></span> <span data-ttu-id="e0920-108">Modül, çağıran işlemin güvenlik bağlamında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="e0920-108">The module is executed in the security context of the calling process.</span></span>  
  
 `lpCommandLine`  
 <span data-ttu-id="e0920-109">'ndaki Başlatılan işlem tarafından yürütülecek komut satırını belirten, null ile sonlandırılmış bir dize işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e0920-109">[in] Pointer to a null-terminated string that specifies the command line to be executed by the launched process.</span></span> <span data-ttu-id="e0920-110">Uygulama adı (örneğin, "SomeApp.exe") ilk bağımsız değişken olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e0920-110">The application name (for example, "SomeApp.exe") must be the first argument.</span></span>  
  
 `lpProcessAttributes`  
 <span data-ttu-id="e0920-111">'ndaki `SECURITY_ATTRIBUTES` İşlemin güvenlik tanımlayıcısını belirten Win32 yapısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e0920-111">[in] Pointer to a Win32 `SECURITY_ATTRIBUTES` structure that specifies the security descriptor for the process.</span></span> <span data-ttu-id="e0920-112">`lpProcessAttributes`Null ise, işlem varsayılan bir güvenlik tanımlayıcısı alır.</span><span class="sxs-lookup"><span data-stu-id="e0920-112">If `lpProcessAttributes` is null, the process gets a default security descriptor.</span></span>  
  
 `lpThreadAttributes`  
 <span data-ttu-id="e0920-113">'ndaki `SECURITY_ATTRIBUTES` İşlemin birincil iş parçacığının güvenlik tanımlayıcısını belirten Win32 yapısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e0920-113">[in] Pointer to a Win32 `SECURITY_ATTRIBUTES` structure that specifies the security descriptor for the primary thread of the process.</span></span> <span data-ttu-id="e0920-114">`lpThreadAttributes`Null ise, iş parçacığı varsayılan bir güvenlik tanımlayıcısı alır.</span><span class="sxs-lookup"><span data-stu-id="e0920-114">If `lpThreadAttributes` is null, the thread gets a default security descriptor.</span></span>  
  
 `bInheritHandles`  
 <span data-ttu-id="e0920-115">'ndaki `true` Çağıran işlemdeki her bir devralınabilir tanıtıcının başlatılan işlem tarafından devralındığını veya tanıtıcıların devralınamayacağını belirtmek için olarak ayarlayın `false` .</span><span class="sxs-lookup"><span data-stu-id="e0920-115">[in] Set to `true` to indicate that each inheritable handle in the calling process is inherited by the launched process, or `false` to indicate that the handles are not inherited.</span></span> <span data-ttu-id="e0920-116">Devralınan tutamaçlar, özgün tanıtıcılarla aynı değere ve erişim haklarına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e0920-116">The inherited handles have the same value and access rights as the original handles.</span></span>  
  
 `dwCreationFlags`  
 <span data-ttu-id="e0920-117">'ndaki Öncelik sınıfını ve başlatılan işlemin davranışını denetleyen [Win32 Işlemi oluşturma bayraklarının](/windows/win32/procthread/process-creation-flags) bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="e0920-117">[in] A bitwise combination of the [Win32 Process Creation Flags](/windows/win32/procthread/process-creation-flags) that control the priority class and the behavior of the launched process.</span></span>  
  
 `lpEnvironment`  
 <span data-ttu-id="e0920-118">'ndaki Yeni işlem için ortam bloğunun işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e0920-118">[in] Pointer to an environment block for the new process.</span></span>  
  
 `lpCurrentDirectory`  
 <span data-ttu-id="e0920-119">'ndaki İşlem için geçerli dizinin tam yolunu belirten, null ile sonlandırılmış bir dize işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e0920-119">[in] Pointer to a null-terminated string that specifies the full path to the current directory for the process.</span></span> <span data-ttu-id="e0920-120">Bu parametre null ise, yeni işlem çağıran işlemle aynı geçerli sürücü ve dizine sahip olur.</span><span class="sxs-lookup"><span data-stu-id="e0920-120">If this parameter is null, the new process will have the same current drive and directory as the calling process.</span></span>  
  
 `lpStartupInfo`  
 <span data-ttu-id="e0920-121">'ndaki `STARTUPINFOW` Başlatılan işlemin ana penceresinin pencere istasyonunu, masaüstünü, standart tutamaçlarını ve görünümünü belirten bir Win32 yapısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e0920-121">[in] Pointer to a Win32 `STARTUPINFOW` structure that specifies the window station, desktop, standard handles, and appearance of the main window for the launched process.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="e0920-122">'ndaki `PROCESS_INFORMATION` Başlatılacak işlemle ilgili kimlik bilgilerini belirten Win32 yapısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e0920-122">[in] Pointer to a Win32 `PROCESS_INFORMATION` structure that specifies the identification information about the process to be launched.</span></span>  
  
 `debuggingFlags`  
 <span data-ttu-id="e0920-123">'ndaki Hata ayıklama seçeneklerini belirten CorDebugCreateProcessFlags numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="e0920-123">[in] A value of the CorDebugCreateProcessFlags enumeration that specifies the debugging options.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="e0920-124">dışı İşlemi temsil eden ICorDebugProcess nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e0920-124">[out] A pointer to the address of a ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0920-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e0920-125">Remarks</span></span>  

 <span data-ttu-id="e0920-126">Bu yöntemin parametreleri Win32 `CreateProcess` yöntemiyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="e0920-126">The parameters of this method are the same as those of the Win32 `CreateProcess` method.</span></span>  
  
 <span data-ttu-id="e0920-127">Yönetilmeyen karma mod hata ayıklamayı etkinleştirmek için `dwCreationFlags` DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e0920-127">To enable unmanaged mixed-mode debugging, set `dwCreationFlags` to DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS.</span></span> <span data-ttu-id="e0920-128">Yalnızca yönetilen hata ayıklamayı kullanmak istiyorsanız, bu bayrakları ayarlamayın.</span><span class="sxs-lookup"><span data-stu-id="e0920-128">If you want to use only managed debugging, do not set these flags.</span></span>  
  
 <span data-ttu-id="e0920-129">Hata ayıklayıcı ve hataları Ayıklanacak işlem (ekli işlem) tek bir konsolu paylaşıyorsa ve birlikte çalışma hata ayıklaması kullanılırsa, ekli işlemin konsol kilitlerini tutması ve hata ayıklama olayında durdurulması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="e0920-129">If the debugger and the process to be debugged (the attached process) share a single console, and if interop debugging is used, it is possible for the attached process to hold console locks and stop at a debug event.</span></span> <span data-ttu-id="e0920-130">Hata ayıklayıcı daha sonra konsolu kullanma denemesini engeller.</span><span class="sxs-lookup"><span data-stu-id="e0920-130">The debugger will then block any attempt to use the console.</span></span> <span data-ttu-id="e0920-131">Bu sorundan kaçınmak için, parametresindeki CREATE_NEW_CONSOLE bayrağını ayarlayın `dwCreationFlags` .</span><span class="sxs-lookup"><span data-stu-id="e0920-131">To avoid this problem, set the CREATE_NEW_CONSOLE flag in the `dwCreationFlags` parameter.</span></span>  
  
 <span data-ttu-id="e0920-132">Birlikte çalışabilirlik hata ayıklaması, IA-64 tabanlı ve AMD64 tabanlı platformlar gibi Win9x ve x86 olmayan platformlarda desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="e0920-132">Interop debugging is not supported on Win9x and non-x86 platforms such as IA-64-based and AMD64-based platforms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0920-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e0920-133">Requirements</span></span>  

 <span data-ttu-id="e0920-134">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0920-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0920-135">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e0920-135">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0920-136">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e0920-136">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0920-137">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0920-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0920-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0920-138">See also</span></span>

- [<span data-ttu-id="e0920-139">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e0920-139">ICorDebug Interface</span></span>](icordebug-interface.md)
