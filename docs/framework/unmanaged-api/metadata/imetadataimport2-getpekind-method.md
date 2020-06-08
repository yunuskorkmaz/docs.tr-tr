---
title: IMetaDataImport2::GetPEKind Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetPEKind
helpviewer_keywords:
- GetPEKind method [.NET Framework metadata]
- IMetaDataImport2::GetPEKind method [.NET Framework metadata]
ms.assetid: d91c3d89-8022-4a4c-a2a2-a8af2c387507
topic_type:
- apiref
ms.openlocfilehash: 3626998c456e23fb922ae45a68bedb0e45a7ccba
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490438"
---
# <a name="imetadataimport2getpekind-method"></a>IMetaDataImport2::GetPEKind Yöntemi
Taşınabilir yürütülebilir (PE) dosyasındaki, genellikle geçerli meta veri kapsamında tanımlanan bir DLL veya EXE dosyası olan kodun yapısını tanımlayan bir değer alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetPEKind (  
   [out] DWORD *pdwPEKind,  
   [out] DWORD *pdwMachine  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pdwPEKind`  
 dışı PE dosyasını tanımlayan bir [CorPEKind](corpekind-enumeration.md) numaralandırması değerine yönelik bir işaretçi.  
  
 `pdwMachine`  
 dışı Makinenin mimarisini tanımlayan bir değere yönelik bir işaretçi. Olası değerler için sonraki bölüme bakın.  
  
## <a name="remarks"></a>Açıklamalar  
 Parametresi tarafından başvurulan değer `pdwMachine` aşağıdakilerden biri olabilir.  
  
|Değer|Makine mimarisi|  
|-----------|--------------------------|  
|IMAGE_FILE_MACHINE_I386<br /><br /> 0x014C|x86|  
|IMAGE_FILE_MACHINE_IA64<br /><br /> 0x0200|Intel ıPF|  
|IMAGE_FILE_MACHINE_AMD64<br /><br /> 0x8664|x64|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [CorPEKind Numaralandırması](corpekind-enumeration.md)
