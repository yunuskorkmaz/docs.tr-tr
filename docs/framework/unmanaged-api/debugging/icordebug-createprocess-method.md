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
ms.openlocfilehash: dfda61706af3e1043d271c0aa74264bd99a4076c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43386597"
---
# <a name="icordebugcreateprocess-method"></a>ICorDebug::CreateProcess Yöntemi
Bir işlem ve onun birincil iş parçacığı hata ayıklayıcının denetiminin altında başlatır.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
  
#### <a name="parameters"></a>Parametreler  
 `lpApplicationName`  
 [in] Başlatılan işlem tarafından yürütülecek modülü belirtiyorsa null ile sonlandırılmış bir dize işaretçisi. Modül çağırma işleminin bağlamında çalıştırılır.  
  
 `lpCommandLine`  
 [in] Başlatılan işlem tarafından yürütülecek komut satırı belirten bir null ile sonlandırılmış dize işaretçisi. Uygulama adı (örneğin, "SomeApp.exe"), ilk bağımsız değişken olmalıdır.  
  
 `lpProcessAttributes`  
 [in] Bir Win32 işaretçisine `SECURITY_ATTRIBUTES` işlemi için güvenlik tanımlayıcısı belirten yapısı. Varsa `lpProcessAttributes` olan null, işlem varsayılan güvenlik tanımlayıcısını alır.  
  
 `lpThreadAttributes`  
 [in] Bir Win32 işaretçisine `SECURITY_ATTRIBUTES` işlemin birincil iş parçacığı için güvenlik tanımlayıcısı belirten yapısı. Varsa `lpThreadAttributes` olan null, iş parçacığı bir varsayılan güvenlik tanımlayıcısını alır.  
  
 `bInheritHandles`  
 [in] Kümesine `true` çağırma işleminde devralınabilir her tutamacı başlatılan işlem tarafından devralınır belirtmek için veya `false` tutamaçları devralınmaz belirtmek için. Devralınan tutamaçları özgün tutamaçlarını aynı değeri ve erişim haklarına sahip.  
  
 `dwCreationFlags`  
 [in] Bitsel bir birleşimi [Win32 işlem oluşturma bayrak](https://go.microsoft.com/fwlink/?linkid=69981) öncelik sınıfı ve başlatılan işlemin davranışını kontrol eden.  
  
 `lpEnvironment`  
 [in] Yeni işlem için bir ortam bloğuna işaretçi.  
  
 `lpCurrentDirectory`  
 [in] İşlem için geçerli dizin tam yolunu belirtir null ile sonlandırılmış bir dize işaretçisi. Bu parametre null ise, yeni işlem çağırma işlemi aynı geçerli sürücü ve dizine sahip.  
  
 `lpStartupInfo`  
 [in] Bir Win32 işaretçisine `STARTUPINFOW` iş istasyonunda, masaüstü, standart tanıtıcıları ve başlatılan işlem için ana penceresinin görünümünü belirtir yapısı.  
  
 `lpProcessInformation`  
 [in] Bir Win32 işaretçisine `PROCESS_INFORMATION` yapısı başlatılacak işlemine ilişkin kimlik bilgilerini belirtir.  
  
 `debuggingFlags`  
 [in] Hata ayıklama seçenekleri belirten CorDebugCreateProcessFlags sabit listesi değeri.  
  
 `ppProcess`  
 [out] İşlemi temsil eden Icordebugprocess nesnesi adresi için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem parametrelerini Win32 aynıdır `CreateProcess` yöntemi.  
  
 Yönetilmeyen karışık mod hata ayıklamayı etkinleştirmek için ayarlanmış `dwCreationFlags` DEBUG_PROCESS için &#124; DEBUG_ONLY_THIS_PROCESS. Yalnızca yönetilen hata ayıklama kullanmak istiyorsanız, bu bayraklar ayarlamayın.  
  
 Hata ayıklayıcı ve işlem olacak şekilde (iliştirilmiş işlem) hata ayıklaması, tek bir konsol paylaşmak ve birlikte çalışma hata ayıklama kullanılıyorsa bir hata ayıklama etkinlikte durdurmak ve konsol için kilitler barındırmıyorsa iliştirilmiş işlem mümkündür. Hata ayıklayıcı, ardından konsolunu kullanmak için her türlü girişim engeller. Bu sorundan kaçınmak için CREATE_NEW_CONSOLE bayrağını ayarlayın `dwCreationFlags` parametresi.  
  
 IA-64 tabanlı ve AMD64 tabanlı platformları gibi Win9x ve x86 olmayan platformlarda birlikte çalışma hata ayıklama desteklenmiyor.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebug Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
