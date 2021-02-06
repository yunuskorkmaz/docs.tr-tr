---
description: ': EnumerateCLRs Işlevi hakkında daha fazla bilgi'
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
ms.openlocfilehash: 75124ef1e1e8588cb3d709161c3c1119e960be9e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637793"
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
 dışı CLR başlatmaya devam etmek için kullanılan olay tutamaçlarını içeren bir diziye yönelik işaretçi. Dizideki her tanıtıcının geçerli olması garanti edilmez. Geçerliyse, tanıtıcı aynı dizininde bulunan ilgili çalışma zamanı için devam-başlatma olayı olarak kullanılır `ppStringArrayOut` .  
  
 `ppStringArrayOut`  
 dışı İşlemde yüklü olan tüm CLRs yollarını belirten dizeler dizisine yönelik işaretçi.  
  
 `pdwArrayLengthOut`  
 dışı Eşit büyüklükte boyut ve uzunluğu içeren bir DWORD işaretçisi `ppHandleArrayOut` `pdwArrayLengthOut` .  
  
## <a name="return-value"></a>Dönüş Değeri  

 S_OK  
 İşlemdeki CLRs sayısı başarıyla belirlendi ve karşılık gelen tanıtıcı ve yol dizileri doğru şekilde dolduruldu.  
  
 E_INVALIDARG  
 Ya da null ya da `ppHandleArrayOut` `ppStringArrayOut` `pdwArrayLengthOut` null.  
  
 E_OUTOFMEMORY  
 İşlev, tanıtıcı ve yol dizileri için yeterli bellek ayıramadı.  
  
 E_FAIL (veya diğer E_ dönüş kodları)  
 Yüklenen CLRs numaralandırılamıyor.  
  
## <a name="remarks"></a>Açıklamalar  

 Tarafından tanımlanan bir hedef işlem için işlev, `debuggeePID` `ppStringArrayOut` işlem Içinde yüklenen CLRs 'ye bir yol dizisi döndürür; bu, `ppHandleArrayOut` clr için aynı dizinde devam eden bir başlatma olayı içerebilen olay tanıtıcısı dizisi ve `pdwArrayLengthOut` yüklenen CLRs sayısını belirten dizilerin boyutu.  
  
 Windows işletim sisteminde `debuggeePID` BIR işletim sistemi işlem tanımlayıcısına eşlenir.  
  
 Ve için bellek `ppHandleArrayOut` `ppStringArrayOut` Bu işlev tarafından ayrılır. Ayrılan belleği serbest bırakmak için [CloseCLREnumeration işlevini](closeclrenumeration-function.md)çağırmanız gerekir.  
  
 Bu işlev, hedef işlemdeki CLRs sayısını döndürmek için her iki dizi parametresi null olarak ayarlanmış şekilde çağrılabilir. Bu saydan bir arayan, oluşturulacak arabelleğin boyutunu çıkarabilir: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** dbgshim. h  
  
 **Kitaplık:** dbgshim.dll  
  
 **.NET Framework sürümleri:** 3,5 SP1
