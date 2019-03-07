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
ms.openlocfilehash: 3ed8b85475dc7327c1aac6f920aba627215e27c7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492029"
---
# <a name="createversionstringfrommodule-function"></a>CreateVersionStringFromModule İşlevi
Hedef işlemdeki ortak dil çalışma zamanı (CLR) yoldan bir sürüm dizesi oluşturur.  
  
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
  
## <a name="parameters"></a>Parametreler  
 `pidDebuggee`  
 [in] Hedef CLR yüklendiği işlem tanımlayıcısı.  
  
 `szModuleName`  
 [in] ' % S'hedef işlemde yüklü CLR tam veya göreli yolu.  
  
 `pBuffer`  
 [out] Hedef CLR sürümü dizesi depolamak için dönüş arabelleği.  
  
 `cchBuffer`  
 [in] Boyutu `pBuffer`.  
  
 `pdwLength`  
 [out] Tarafından döndürülen sürüm dizesinin uzunluğunu `pBuffer`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 Hedef CLR sürümü dizesi başarıyla döndürüldü `pBuffer`.  
  
 E_INVALIDARG  
 `szModuleName` olan null ya da `pBuffer` veya `cchBuffer` null. `pBuffer` ve `cchBuffer` her ikisi de null veya boş olmayan olmalıdır.  
  
 HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)  
 `pdwLength` büyüktür `cchBuffer`. Her ikisi için null geçtiğinde bu beklenen bir sonucu olabilir `pBuffer` ve `cchBuffer`ve gerekli arabellek boyutu kullanılarak sorgulanabilir `pdwLength`.  
  
 HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)  
 `szModuleName` Hedef işlemin içinde geçerli bir CLR yolu içermiyor.  
  
 E_FAIL (veya diğer E_ dönüş kodları)  
 `pidDebuggee` Geçerli bir işlem veya diğer hata başvurmuyor.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu işlev tarafından tanımlanan bir CLR işlemi kabul `pidDebuggee` ve tarafından belirtilen bir dize yol `szModuleName`. Sürüm dizesi arabellekteki döndürülür, `pBuffer` işaret eder. Bu dize işlevi kullanıcı için donuktur; diğer bir deyişle, sürüm dizesindeki iç anlamı yoktur. Bu işlev yalnızca bağlamında kullanılır ve [Createdebuggingınterfacefromversion işlevi](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md).  
  
 Bu işlevin iki kez çağrılması. İlk kez çağırdığınızda, her ikisi için null değeri geçirmeye `pBuffer` ve `cchBuffer`. Bunu yaptığınızda, gerekli arabellek boyutu `pBuffer` içinde döndürülen `pdwLength`. Ardından, ikinci kez işlevini çağırın ve arabellekteki geçirin `pBuffer` ve boyutunda `cchBuffer`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** dbgshim.h  
  
 **Kitaplığı:** dbgshim.dll  
  
 **.NET framework sürümleri:** 3.5 SP1
