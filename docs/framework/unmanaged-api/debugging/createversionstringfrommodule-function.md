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
ms.openlocfilehash: 1b944034251b34350057866b2a52e63e934d72d4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733353"
---
# <a name="createversionstringfrommodule-function"></a>CreateVersionStringFromModule İşlevi

Hedef işlemdeki ortak dil çalışma zamanı (CLR) yolundan bir sürüm dizesi oluşturur.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki Boyut `pBuffer` .  
  
 `pdwLength`  
 dışı Tarafından döndürülen sürüm dizesinin uzunluğu `pBuffer` .  
  
## <a name="return-value"></a>Dönüş Değeri  

 S_OK  
 Hedef CLR 'nin sürüm dizesi içinde başarıyla döndürüldü `pBuffer` .  
  
 E_INVALIDARG  
 `szModuleName` null veya ya da `pBuffer` `cchBuffer` null. `pBuffer` ve `cchBuffer` her ikisi de null ya da boş olmamalıdır.  
  
 HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT_BUFFER)  
 `pdwLength` Şundan büyüktür `cchBuffer` . Hem hem de için null değeri geçirtiyse `pBuffer` `cchBuffer` ve gereken arabellek boyutunu kullanarak sorguladıysanız, bu beklenen bir sonuç olabilir `pdwLength` .  
  
 HRESULT_FROM_WIN32 (ERROR_MOD_NOT_FOUND)  
 `szModuleName` Hedef işlemde geçerli bir CLR yolu içermiyor.  
  
 E_FAIL (veya diğer E_ dönüş kodları)  
 `pidDebuggee` geçerli bir işleme ya da başka bir hataya başvurmaz.  
  
## <a name="remarks"></a>Açıklamalar  

 Bu işlev tarafından tanımlanan bir CLR işlemini `pidDebuggee` ve tarafından belirtilen bir dize yolunu kabul eder `szModuleName` . Sürüm dizesi, işaret eden arabellekte döndürülür `pBuffer` . Bu dize, işlev kullanıcısının opaktır; Yani, sürüm dizesinde hiç iç anlamı yoktur. Yalnızca bu işlev bağlamında ve [CreateDebuggingInterfaceFromVersion İşlevi](createdebugginginterfacefromversion-function-for-silverlight.md)için kullanılır.  
  
 Bu işlev iki kez çağrılmalıdır. İlk kez çağırdığınızda, hem hem de için null değeri geçirin `pBuffer` `cchBuffer` . Bunu yaptığınızda, için gereken arabelleğin boyutu `pBuffer` ' de döndürülür `pdwLength` . Daha sonra işlevi ikinci bir kez çağırabilir ve içindeki arabelleği `pBuffer` ve boyutuna geçirebilirsiniz `cchBuffer` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** dbgshim. h  
  
 **Kitaplık:** dbgshim.dll  
  
 **.NET Framework sürümleri:** 3,5 SP1
