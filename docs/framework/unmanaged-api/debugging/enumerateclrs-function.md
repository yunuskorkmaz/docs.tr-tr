---
title: EnumerateCLRs İşlevi
ms.date: 03/30/2017
api_name:
- EnumerateCLRs
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- EnumerateCLRs
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- EnumerateCLRs function
ms.assetid: f8d50cb3-ec4f-4529-8fe3-bd61fd28e13c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e7532218728aead72186b5156da87db6d3bc0a8c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469345"
---
# <a name="enumerateclrs-function"></a>EnumerateCLRs İşlevi
Bir işlemde CLRs numaralandırmak için bir mekanizma sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumerateCLRs (  
    [in]  DWORD      debuggeePID,  
    [out] HANDLE**   ppHandleArrayOut,  
    [out] LPWSTR**   ppStringArrayOut,  
    [out] DWORD*     pdwArrayLengthOut  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `debuggeePID`  
 [in] Yüklenen CLRs Numaralandırılacak işleminin işlem tanıtıcısı.  
  
 `ppHandleArrayOut`  
 [out] CLR başlangıç devam etmek için kullanılan olay tanıtıcıları içeren bir dizi için işaretçi. Dizideki her tutamacı geçerli olması garanti edilmez. Geçerli tanıtıcı devam başlangıç olayı olarak aynı dizinde bulunan karşılık gelen çalışma zamanı için kullanılmak üzere olup olmadığını `ppStringArrayOut`.  
  
 `ppStringArrayOut`  
 [out] Tam yolları CLRs belirten bir dize dizisi işaretçisine işlemde yüklü.  
  
 `pdwArrayLengthOut`  
 [out] İşaretçisine eşit boyutlu uzunluğunu içeren bir DWORD `ppHandleArrayOut` ve `pdwArrayLengthOut`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 İşlem CLRs sayısında başarıyla belirlendi ve karşılık gelen tanıtıcısı ve yol diziler düzgün doldurulmuş.  
  
 E_INVALIDARG  
 Ya da `ppHandleArrayOut` veya `ppStringArrayOut` null ise veya `pdwArrayLengthOut` null.  
  
 E_OUTOFMEMORY  
 İşlev tanıtıcısı ve yol diziler için yeterli bellek ayıramadı.  
  
 E_FAIL (veya diğer E_ dönüş kodları)  
 Yüklenen CLRs numaralandırılamadı.  
  
## <a name="remarks"></a>Açıklamalar  
 Tarafından tanımlanan bir hedef işlemi `debuggeePID`, işlev yolları, bir dizi döndürür `ppStringArrayOut`, işlemde yüklü CLRs; bir dizi olay işleyicilerini `ppHandleArrayOut`, hangi içerebilir devam başlangıç olay için aynı dizindeki; CLR ve dizi boyutu `pdwArrayLengthOut`, yüklenen CLRs sayısını belirtir.  
  
 Windows işletim sisteminde `debuggeePID` eşlemeleri bir işletim sistemi için işlem tanımlayıcısı.  
  
 Bellek için `ppHandleArrayOut` ve `ppStringArrayOut` bu işlev tarafından ayrılır. Ayrılan bellek boşaltmak için çağırmalısınız [CloseCLREnumeration işlevi](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md).  
  
 Bu işlev, her iki dizi parametrelerle hedef işlemde CLRs sayısını döndürmek için null olarak çağrılabilir. Bu sayıdan, bir çağıranın oluşturulacak arabellek boyutu çıkarabilir: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** dbgshim.h  
  
 **Kitaplığı:** dbgshim.dll  
  
 **.NET framework sürümleri:** 3.5 SP1
