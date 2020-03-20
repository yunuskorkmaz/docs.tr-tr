---
title: ISymUnmanagedSourceServerModule::GetSourceServerData Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSourceServerModule.GetSourceServerData
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData
helpviewer_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData method [.NET Framework debugging]
- GetSourceServerData method [.NET Framework debugging]
ms.assetid: 20bdf8ff-2d15-4c64-8950-6888f642d6c0
topic_type:
- apiref
ms.openlocfilehash: 6904271ed90cf733b9221178927bc680d76b58a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176584"
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a>ISymUnmanagedSourceServerModule::GetSourceServerData Metodu
Modülün kaynak sunucu verilerini verir. Arayan kişi kaynakları kullanarak `CoTaskMemFree`serbest etmelidir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pDataByteCount`  
 [çıkış] Kaynak sunucu `ULONG32` verilerinin bayt boyutunda alan bir işaretçi.  
  
 `ppData`  
 [çıkış] Döndürülen `pDataByteCount` değeriçin bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 yöntem başarılı olursa S_OK; aksi takdirde, E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Üstbilgi:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ISymUnmanagedSourceServerModule Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)
