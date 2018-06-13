---
title: CreateVersionStringFromModule İşlevi
ms.date: 03/30/2017
api_name:
- CreateVersionStringFromModule
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- CreateVersionStringFromModule
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CreateVersionStringFromModule function
ms.assetid: 3d2fe9bd-75ef-4364-84a6-da1e1994ac1a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0988b2c4471cb5449f7c7fac82c6e94bcd537b7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33409286"
---
# <a name="createversionstringfrommodule-function"></a>CreateVersionStringFromModule İşlevi
Ortak dil çalışma zamanı (CLR) yolu bir hedef işlemde bir sürüm dizesi oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateVersionStringFromModule (  
    [in]  DWORD      pidDebuggee,  
    [in]  LPCWSTR    szModuleName,  
    [out, size_is(cchBuffer),  
          length_is(*pdwLength)] LPWSTR Buffer,  
    [in]  DWORD      cchBuffer,  
    [out] DWORD*     pdwLength  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pidDebuggee`  
 [in] CLR hedef yüklendiği işlem tanıtıcısı.  
  
 `szModuleName`  
 [in] İşlemde yüklü CLR hedef tam veya göreli yolu.  
  
 `pBuffer`  
 [out] Hedef CLR sürüm dizesi depolamak için arabellek döndür.  
  
 `cchBuffer`  
 [in] Boyutunu `pBuffer`.  
  
 `pdwLength`  
 [out] Tarafından döndürülen sürüm dizesi `pBuffer`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 Hedef CLR sürüm dizesi başarıyla döndürüldü `pBuffer`.  
  
 E_INVALIDARG  
 `szModuleName` olan null ya da `pBuffer` veya `cchBuffer` null. `pBuffer` ve `cchBuffer` her ikisi de null veya boş olmayan olmalıdır.  
  
 HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)  
 `pdwLength` Daha fazla `cchBuffer`. Her ikisi için null geçtiğinde, bu beklenen bir sonucu olabilir `pBuffer` ve `cchBuffer`ve gerekli arabellek boyutu kullanarak sorgulanan `pdwLength`.  
  
 HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)  
 `szModuleName` Hedef işlemin geçerli bir CLR yoluna sahip değil.  
  
 E_FAIL (veya diğer E_ dönüş kodları)  
 `pidDebuggee` Geçerli bir işlem veya diğer hata başvurmuyor.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu işlev tarafından tanımlanan bir CLR işlem kabul `pidDebuggee` tarafından belirtilen bir dize yol `szModuleName`. Sürüm dizesi arabellekte döndürülür, `pBuffer` işaret eder. Bu dize işlevi kullanıcıya donuk; diğer bir deyişle, sürüm dizesindeki iç hiçbir anlamı yoktur. Yalnızca bu işlev bağlamda kullanılır ve [Createdebuggingınterfacefromversion işlevi](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md).  
  
 Bu işlev iki kez çağrılmalıdır. İlk kez çağırdığınızda, her ikisi için null geçirmeniz `pBuffer` ve `cchBuffer`. Bunu yaptığınızda, gerekli arabellek boyutu `pBuffer` içinde döndürülen `pdwLength`. Ardından, ikinci kez işlevini çağırın ve arabellekte geçirin `pBuffer` ve boyutunda `cchBuffer`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** dbgshim.h  
  
 **Kitaplığı:** dbgshim.dll  
  
 **.NET framework sürümleri:** 3.5 SP1
