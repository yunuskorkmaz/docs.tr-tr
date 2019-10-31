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
ms.openlocfilehash: 1571ff796a10c5ddcd85cc2ce130e62eab2ed8f2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132078"
---
# <a name="createversionstringfrommodule-function"></a>CreateVersionStringFromModule İşlevi
Hedef işlemdeki ortak dil çalışma zamanı (CLR) yolundan bir sürüm dizesi oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
 'ndaki Hedef CLR 'nin yüklendiği işlemin tanımlayıcısı.  
  
 `szModuleName`  
 'ndaki İşlemde yüklü olan hedef CLR 'ye tam veya göreli yol.  
  
 `pBuffer`  
 dışı Hedef CLR için sürüm dizesini depolamak için dönüş arabelleği.  
  
 `cchBuffer`  
 'ndaki `pBuffer`boyutu.  
  
 `pdwLength`  
 dışı `pBuffer`tarafından döndürülen sürüm dizesinin uzunluğu.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 Hedef CLR 'nin sürüm dizesi `pBuffer`başarıyla döndürüldü.  
  
 E_INVALIDARG  
 `szModuleName` null veya `pBuffer` ya da `cchBuffer` null. `pBuffer` ve `cchBuffer` her ikisi de null veya null olmamalıdır.  
  
 HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)  
 `pdwLength`, `cchBuffer`daha büyük. Hem `pBuffer` hem de `cchBuffer`için null değer geçirtiyse ve `pdwLength`kullanarak gerekli arabellek boyutunu sorguladıysanız bu beklenen bir sonuç olabilir.  
  
 HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)  
 `szModuleName` hedef işlemde geçerli bir CLR yolu içermiyor.  
  
 E_FAıL (veya diğer E_ dönüş kodları)  
 `pidDebuggee` geçerli bir işleme ya da başka bir hataya başvurmuyor.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu işlev, `pidDebuggee` tarafından tanımlanan bir CLR işlemini ve `szModuleName`tarafından belirtilen bir dize yolunu kabul eder. Sürüm dizesi, `pBuffer` gösterdiği arabellekte döndürülür. Bu dize, işlev kullanıcısının opaktır; Yani, sürüm dizesinde hiç iç anlamı yoktur. Yalnızca bu işlev bağlamında ve [CreateDebuggingInterfaceFromVersion İşlevi](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md)için kullanılır.  
  
 Bu işlev iki kez çağrılmalıdır. İlk kez çağırdığınızda, hem `pBuffer` hem de `cchBuffer`için null değeri geçirin. Bunu yaptığınızda, `pBuffer` için gereken arabelleğin boyutu `pdwLength`döndürülür. Daha sonra işlevi ikinci bir kez çağırabilir ve arabelleği `pBuffer` ve boyutunu `cchBuffer`olarak geçirebilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** dbgshim. h  
  
 **Kitaplık:** dbgshim. dll  
  
 **.NET Framework sürümleri:** 3,5 SP1
