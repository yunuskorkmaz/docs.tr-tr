---
title: CreateAssemblyNameObject İşlevi
ms.date: 03/30/2017
api_name:
- CreateAssemblyNameObject
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyNameObject
helpviewer_keywords:
- CreateAssemblyNameObject function [.NET Framework fusion]
ms.assetid: 55c8b41e-fbe4-4ae0-aa29-68fbb2311691
topic_type:
- apiref
ms.openlocfilehash: 995f1064c2f40005c4a19ef034d7edfd668b5d51
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704168"
---
# <a name="createassemblynameobject-function"></a>CreateAssemblyNameObject İşlevi

Belirtilen ada sahip derlemenin benzersiz kimliğini temsil eden bir [IAssemblyName](iassemblyname-interface.md) örneğine yönelik bir arabirim işaretçisi alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT CreateAssemblyNameObject (  
    [out] LPASSEMBLYNAME  *ppAssemblyNameObj,  
    [in]  LPCWSTR         szAssemblyName,  
    [in]  DWORD           dwFlags,  
    [in]  LPVOID          pvReserved  
 );  
```  
  
## <a name="parameters"></a>Parametreler  

 `ppAssemblyNameObj`  
 dışı Döndürülen `IAssemblyName` .  
  
 `szAssemblyName`  
 'ndaki Yeni örneğin oluşturulacağı derlemenin adı `IAssemblyName` .  
  
 `dwFlags`  
 'ndaki Nesne oluşturucusuna geçirilecek bayraklar.  
  
 `pvReserved`  
 'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır. `pvReserved` null bir başvuru olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IAssemblyName Arabirimi](iassemblyname-interface.md)
- [Fusion Genel Statik İşlevleri](fusion-global-static-functions.md)
