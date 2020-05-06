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
ms.openlocfilehash: 1f33fb98712939d1e687798547b784819f164d63
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860729"
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
 dışı CLR başlatmaya devam etmek için kullanılan olay tutamaçlarını içeren bir diziye yönelik işaretçi. Dizideki her tanıtıcının geçerli olması garanti edilmez. Geçerliyse, tanıtıcı aynı dizininde bulunan ilgili çalışma zamanı için devam-başlatma olayı olarak kullanılır `ppStringArrayOut`.  
  
 `ppStringArrayOut`  
 dışı İşlemde yüklü olan tüm CLRs yollarını belirten dizeler dizisine yönelik işaretçi.  
  
 `pdwArrayLengthOut`  
 dışı Eşit büyüklükte boyut `ppHandleArrayOut` ve `pdwArrayLengthOut`uzunluğu içeren bir DWORD işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 İşlemdeki CLRs sayısı başarıyla belirlendi ve karşılık gelen tanıtıcı ve yol dizileri doğru şekilde dolduruldu.  
  
 E_INVALIDARG  
 `ppStringArrayOut` Ya `ppHandleArrayOut` da null `pdwArrayLengthOut` ya da null.  
  
 E_OUTOFMEMORY  
 İşlev, tanıtıcı ve yol dizileri için yeterli bellek ayıramadı.  
  
 E_FAIL (veya diğer E_ dönüş kodları)  
 Yüklenen CLRs numaralandırılamıyor.  
  
## <a name="remarks"></a>Açıklamalar  
 Tarafından `debuggeePID`tanımlanan bir hedef işlem için işlev, işlem Içinde yüklenen CLRs 'ye bir yol `ppStringArrayOut`dizisi döndürür; CLR için aynı dizinde devam- `ppHandleArrayOut`başlatma olayı içerebilen olay tanıtıcısı dizisi; ve, yüklenen CLRs sayısını belirten `pdwArrayLengthOut`dizilerin boyutudur.  
  
 Windows işletim sisteminde bir IŞLETIM sistemi `debuggeePID` işlem tanımlayıcısına eşlenir.  
  
 Ve `ppHandleArrayOut` `ppStringArrayOut` için bellek bu işlev tarafından ayrılır. Ayrılan belleği serbest bırakmak için [CloseCLREnumeration işlevini](closeclrenumeration-function.md)çağırmanız gerekir.  
  
 Bu işlev, hedef işlemdeki CLRs sayısını döndürmek için her iki dizi parametresi null olarak ayarlanmış şekilde çağrılabilir. Bu saydan bir arayan, oluşturulacak arabelleğin boyutunu çıkarabilir: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** dbgshim. h  
  
 **Kitaplık:** dbgshim. dll  
  
 **.NET Framework sürümleri:** 3,5 SP1
