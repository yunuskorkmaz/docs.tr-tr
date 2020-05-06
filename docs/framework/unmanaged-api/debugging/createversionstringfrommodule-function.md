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
ms.openlocfilehash: 60b7d77542a5065fb1e09a98e659cac17fb093e9
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860856"
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
 'ndaki Boyut `pBuffer`.  
  
 `pdwLength`  
 dışı Tarafından `pBuffer`döndürülen sürüm dizesinin uzunluğu.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 Hedef CLR 'nin sürüm dizesi içinde `pBuffer`başarıyla döndürüldü.  
  
 E_INVALIDARG  
 `szModuleName`null veya ya da `pBuffer` `cchBuffer` null. `pBuffer`ve `cchBuffer` her ikisi de null ya da boş olmamalıdır.  
  
 HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT_BUFFER)  
 `pdwLength`Şundan `cchBuffer`büyüktür. Hem hem de `pBuffer` için null değeri geçirtiyse ve gereken arabellek boyutunu kullanarak `cchBuffer` `pdwLength`sorguladıysanız, bu beklenen bir sonuç olabilir.  
  
 HRESULT_FROM_WIN32 (ERROR_MOD_NOT_FOUND)  
 `szModuleName`Hedef işlemde geçerli bir CLR yolu içermiyor.  
  
 E_FAIL (veya diğer E_ dönüş kodları)  
 `pidDebuggee`geçerli bir işleme ya da başka bir hataya başvurmaz.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu işlev tarafından `pidDebuggee` tanımlanan bir clr işlemini ve tarafından `szModuleName`belirtilen bir dize yolunu kabul eder. Sürüm dizesi, işaret eden `pBuffer` arabellekte döndürülür. Bu dize, işlev kullanıcısının opaktır; Yani, sürüm dizesinde hiç iç anlamı yoktur. Yalnızca bu işlev bağlamında ve [CreateDebuggingInterfaceFromVersion İşlevi](createdebugginginterfacefromversion-function-for-silverlight.md)için kullanılır.  
  
 Bu işlev iki kez çağrılmalıdır. İlk kez çağırdığınızda, hem hem de `pBuffer` için null değeri geçirin. `cchBuffer` Bunu yaptığınızda, için `pBuffer` gereken arabelleğin boyutu ' de `pdwLength`döndürülür. Daha sonra işlevi ikinci bir kez çağırabilir ve içindeki arabelleği `pBuffer` ve boyutuna geçirebilirsiniz. `cchBuffer`  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** dbgshim. h  
  
 **Kitaplık:** dbgshim. dll  
  
 **.NET Framework sürümleri:** 3,5 SP1
