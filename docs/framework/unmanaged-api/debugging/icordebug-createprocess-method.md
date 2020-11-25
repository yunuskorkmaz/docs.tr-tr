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
ms.openlocfilehash: aeb39782c4c0624501a0e2a71960f5d16ab3c03e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723486"
---
# <a name="icordebugcreateprocess-method"></a>ICorDebug::CreateProcess Yöntemi

Hata ayıklayıcının denetimi altında bir işlem ve birincil iş parçacığını başlatır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
  
## <a name="parameters"></a>Parametreler  

 `lpApplicationName`  
 'ndaki Başlatılan işlem tarafından yürütülecek modülü belirten, null ile sonlandırılmış bir dize işaretçisi. Modül, çağıran işlemin güvenlik bağlamında yürütülür.  
  
 `lpCommandLine`  
 'ndaki Başlatılan işlem tarafından yürütülecek komut satırını belirten, null ile sonlandırılmış bir dize işaretçisi. Uygulama adı (örneğin, "SomeApp.exe") ilk bağımsız değişken olmalıdır.  
  
 `lpProcessAttributes`  
 'ndaki `SECURITY_ATTRIBUTES` İşlemin güvenlik tanımlayıcısını belirten Win32 yapısına yönelik işaretçi. `lpProcessAttributes`Null ise, işlem varsayılan bir güvenlik tanımlayıcısı alır.  
  
 `lpThreadAttributes`  
 'ndaki `SECURITY_ATTRIBUTES` İşlemin birincil iş parçacığının güvenlik tanımlayıcısını belirten Win32 yapısına yönelik işaretçi. `lpThreadAttributes`Null ise, iş parçacığı varsayılan bir güvenlik tanımlayıcısı alır.  
  
 `bInheritHandles`  
 'ndaki `true` Çağıran işlemdeki her bir devralınabilir tanıtıcının başlatılan işlem tarafından devralındığını veya tanıtıcıların devralınamayacağını belirtmek için olarak ayarlayın `false` . Devralınan tutamaçlar, özgün tanıtıcılarla aynı değere ve erişim haklarına sahiptir.  
  
 `dwCreationFlags`  
 'ndaki Öncelik sınıfını ve başlatılan işlemin davranışını denetleyen [Win32 Işlemi oluşturma bayraklarının](/windows/win32/procthread/process-creation-flags) bit düzeyinde birleşimi.  
  
 `lpEnvironment`  
 'ndaki Yeni işlem için ortam bloğunun işaretçisi.  
  
 `lpCurrentDirectory`  
 'ndaki İşlem için geçerli dizinin tam yolunu belirten, null ile sonlandırılmış bir dize işaretçisi. Bu parametre null ise, yeni işlem çağıran işlemle aynı geçerli sürücü ve dizine sahip olur.  
  
 `lpStartupInfo`  
 'ndaki `STARTUPINFOW` Başlatılan işlemin ana penceresinin pencere istasyonunu, masaüstünü, standart tutamaçlarını ve görünümünü belirten bir Win32 yapısına yönelik işaretçi.  
  
 `lpProcessInformation`  
 'ndaki `PROCESS_INFORMATION` Başlatılacak işlemle ilgili kimlik bilgilerini belirten Win32 yapısına yönelik işaretçi.  
  
 `debuggingFlags`  
 'ndaki Hata ayıklama seçeneklerini belirten CorDebugCreateProcessFlags numaralandırması değeri.  
  
 `ppProcess`  
 dışı İşlemi temsil eden ICorDebugProcess nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Bu yöntemin parametreleri Win32 `CreateProcess` yöntemiyle aynıdır.  
  
 Yönetilmeyen karma mod hata ayıklamayı etkinleştirmek için `dwCreationFlags` DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS olarak ayarlayın. Yalnızca yönetilen hata ayıklamayı kullanmak istiyorsanız, bu bayrakları ayarlamayın.  
  
 Hata ayıklayıcı ve hataları Ayıklanacak işlem (ekli işlem) tek bir konsolu paylaşıyorsa ve birlikte çalışma hata ayıklaması kullanılırsa, ekli işlemin konsol kilitlerini tutması ve hata ayıklama olayında durdurulması mümkündür. Hata ayıklayıcı daha sonra konsolu kullanma denemesini engeller. Bu sorundan kaçınmak için, parametresindeki CREATE_NEW_CONSOLE bayrağını ayarlayın `dwCreationFlags` .  
  
 Birlikte çalışabilirlik hata ayıklaması, IA-64 tabanlı ve AMD64 tabanlı platformlar gibi Win9x ve x86 olmayan platformlarda desteklenmez.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebug Arabirimi](icordebug-interface.md)
