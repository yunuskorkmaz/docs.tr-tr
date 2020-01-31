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
ms.openlocfilehash: cdf88ef193df71a638fff43add1a9648d8631731
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789123"
---
# <a name="enumerateclrs-function"></a>EnumerateCLRs İşlevi
Bir işlemdeki CLRs 'yi listelemek için bir mekanizma sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumerateCLRs (  
    [in]  DWORD      debuggeePID,  
    [out] HANDLE**   ppHandleArrayOut,  
    [out] LPWSTR**   ppStringArrayOut,  
    [out] DWORD*     pdwArrayLengthOut  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `debuggeePID`  
 'ndaki Yüklenen CLRs 'nin numaralandıralınacağı işlemin işlem tanımlayıcısı.  
  
 `ppHandleArrayOut`  
 dışı CLR başlatmaya devam etmek için kullanılan olay tutamaçlarını içeren bir diziye yönelik işaretçi. Dizideki her tanıtıcının geçerli olması garanti edilmez. Geçerliyse, tanıtıcı aynı `ppStringArrayOut`dizininde bulunan ilgili çalışma zamanı için devam-başlatma olayı olarak kullanılır.  
  
 `ppStringArrayOut`  
 dışı İşlemde yüklü olan tüm CLRs yollarını belirten dizeler dizisine yönelik işaretçi.  
  
 `pdwArrayLengthOut`  
 dışı Eşit ölçekli `ppHandleArrayOut` ve `pdwArrayLengthOut`uzunluğunu içeren bir DWORD işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 İşlemdeki CLRs sayısı başarıyla belirlendi ve karşılık gelen tanıtıcı ve yol dizileri doğru şekilde dolduruldu.  
  
 E_INVALIDARG  
 `ppHandleArrayOut` veya `ppStringArrayOut` null ya da `pdwArrayLengthOut` null.  
  
 E_OUTOFMEMORY  
 İşlev, tanıtıcı ve yol dizileri için yeterli bellek ayıramadı.  
  
 E_FAIL (veya diğer E_ dönüş kodları)  
 Yüklenen CLRs numaralandırılamıyor.  
  
## <a name="remarks"></a>Açıklamalar  
 `debuggeePID`tarafından tanımlanan bir hedef işlem için işlev, `ppStringArrayOut`, işlem içinde yüklenmiş bir yol dizisi döndürür; aynı dizinde CLR için devam-başlatma olayı içerebilen `ppHandleArrayOut`olay tanıtıcı dizisi; ve dizi boyutu, yüklenen CLRs sayısını belirten `pdwArrayLengthOut`.  
  
 Windows işletim sisteminde `debuggeePID` bir IŞLETIM sistemi işlem tanımlayıcısına eşlenir.  
  
 `ppHandleArrayOut` ve `ppStringArrayOut` bellek bu işlev tarafından ayrılır. Ayrılan belleği serbest bırakmak için [CloseCLREnumeration işlevini](closeclrenumeration-function.md)çağırmanız gerekir.  
  
 Bu işlev, hedef işlemdeki CLRs sayısını döndürmek için her iki dizi parametresi null olarak ayarlanmış şekilde çağrılabilir. Bu sayımla, bir arayan, oluşturulacak arabelleğin boyutunu çıkarabilir: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** dbgshim. h  
  
 **Kitaplık:** dbgshim. dll  
  
 **.NET Framework sürümleri:** 3,5 SP1
