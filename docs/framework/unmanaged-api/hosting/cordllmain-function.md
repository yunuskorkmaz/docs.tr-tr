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
ms.openlocfilehash: 1b3ebcabc66ee7ca29245bb02d958be311bc65fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673702"
---
# <a name="_cordllmain-function"></a>\_CorDllMain Işlevi

Ortak dil çalışma zamanını (CLR) başlatır, DLL derlemesinin CLR üst bilgisinde yönetilen giriş noktasını bulur ve yürütmeyi başlatır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `hInst`  
 'ndaki Yüklenen modülün örnek tanıtıcısı.  
  
 `dwReason`  
 'ndaki DLL giriş noktası işlevinin neden çağrıldığını gösterir. Bu parametre aşağıdaki değerlerden biri olabilir: DLL \_ PROCESS_ATTACH, dll \_ iş parçacığı \_ iliştirme, dll \_ Iş parçacığı \_ iliştirme veya dll \_ işlem \_ ayırma. Bu değerlerin açıklamaları için `DllMain` Platform SDK 'sindeki belgelere bakın.  
  
 `lpReserved`  
 'ndaki Kullanılmayan.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Bu yöntem `true` başarı için döndürür ve `false` bir hata oluşursa.  
  
## <a name="remarks"></a>Açıklamalar  

 Bu işlev, DLL derlemeleri için işletim sistemi yükleyicisi tarafından çağırılır. Yürütülebilir derlemeler için yükleyici, bunun yerine [ \_ corexemain](corexemain-function.md) işlevini çağırır.  
  
 İşletim sistemi yükleyicisi, DLL dosyasında belirtilen giriş noktası ne olursa olsun bu yöntemi çağırır.  
  
`_CorDllMain`İşlevi, işletim sistemi yükleyicisi tarafından doğrudan çağrılır.
  
 Daha fazla bilgi için [ \_ corvalidateımage](corvalidateimage-function.md) konusunun açıklamalar bölümüne bakın.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Genel Statik İşlevleri](../metadata/metadata-global-static-functions.md)
