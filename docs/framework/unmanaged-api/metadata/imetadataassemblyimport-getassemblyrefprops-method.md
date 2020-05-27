---
title: IMetaDataAssemblyImport::GetAssemblyRefProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps method [.NET Framework metadata]
- GetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 5c6b7fb4-cbca-4479-b650-ab9a99732ea0
topic_type:
- apiref
ms.openlocfilehash: 2858e924ab6effe192955ce53dad9d333d2d244d
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009073"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a>IMetaDataAssemblyImport::GetAssemblyRefProps Yöntemi
Belirtilen meta veri imzasıyla derleme başvurusunun özellik kümesini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetAssemblyRefProps (  
    [in]  mdAssemblyRef        mdar,
    [out] const void          **ppbPublicKeyOrToken,
    [out] ULONG                *pcbPublicKeyOrToken,
    [out] LPWSTR               szName,
    [in]  ULONG                cchName,
    [out] ULONG                *pchName,
    [out] ASSEMBLYMETADATA     *pMetaData,
    [out] const void           **ppbHashValue,
    [out] ULONG                *pcbHashValue,
    [out] DWORD                *pdwAssemblyRefFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `mdar`  
 'ndaki `mdAssemblyRef`Özelliklerinin alınacağı derleme başvurusunu temsil eden meta veri belirteci.  
  
 `ppbPublicKeyOrToken`  
 dışı Ortak anahtara veya meta veri belirtecine yönelik bir işaretçi.  
  
 `pcbPublicKeyOrToken`  
 dışı Döndürülen ortak anahtar veya belirteçteki bayt sayısı.  
  
 `szName`  
 dışı Derlemenin basit adı.  
  
 `cchName`  
 'ndaki , Öğesinin geniş karakter cinsinden boyutu `szName` .  
  
 `pchName`  
 dışı Aslında ' de döndürülen geniş karakter sayısının bir işaretçisi `szName` .  
  
 `pMetaData`  
 dışı Derleme meta verilerini içeren bir ASSEMBLYMETADATA yapısına yönelik işaretçi.  
  
 `ppbHashValue`  
 dışı Karma değere yönelik bir işaretçi. Bu, `PublicKey` [AssemblyRefFlags](assemblyrefflags-enumeration.md) numaralandırması Için arfFullOriginator bayrağı ayarlanmadığı takdirde, başvurulan derlemenin özelliğinin SHA-1 algoritmasını kullanan karmadır.  
  
 `pcbHashValue`  
 dışı Döndürülen karma değerindeki geniş karakter sayısı.  
  
 `pdwAssemblyRefFlags`  
 dışı Bir derlemeye uygulanan meta verileri tanımlayan bayrakların işaretçisi. Flags değeri bir veya daha fazla [CorAssemblyFlags](corassemblyflags-enumeration.md) değeri birleşimidir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem başarılı olursa S_OK döndürür; Aksi takdirde, Winerror. h üstbilgi dosyasında tanımlanan hata kodlarından birini döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyImport Arabirimi](imetadataassemblyimport-interface.md)
