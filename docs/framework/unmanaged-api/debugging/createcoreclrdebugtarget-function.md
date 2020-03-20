---
title: CreateCoreClrDebugTarget İşlevi
ms.date: 03/30/2017
api_name:
- CreateCorClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- Silverlight, remote debugging
- CreateCoreClrDebugTarget function
ms.assetid: 1cf4ca8e-d9bb-4633-9adf-5e24315bf87a
topic_type:
- apiref
ms.openlocfilehash: 0b210f105495fa3f5595adbcb0805e1d1fb62310
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179214"
---
# <a name="createcoreclrdebugtarget-function"></a>CreateCoreClrDebugTarget İşlevi
Uzak bir makinede çalışan bir hata ayıklayıcı proxy'ye bağlantı oluşturur ve uzak makinede çalışan işlemleri ve yüklü çalışma sürelerini sorgulamak için kullanılabilecek bir [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) nesnesi döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwAddress`  
 [içinde] Uzak bir hedef makinenin IPv4 adresi.  
  
 `ppTarget`  
 [çıkış] Oluşturulacak bir [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) nesnesine işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 İşlemdeki CLR sayısı başarıyla belirlendi ve karşılık gelen tutamaç ve yol dizileri düzgün şekilde dolduruldu.  
  
 E_outofmemory  
 `ppTarget`'ye yeterli bellek ayrılamıyor.  
  
 E_FAIL (veya diğer E_ iade kodları)  
 Diğer başarısızlıklar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Kütüphane:** mscordbi_macx86.dll  
  
 **.NET Çerçeve Sürümleri:** 3.5 SP1
