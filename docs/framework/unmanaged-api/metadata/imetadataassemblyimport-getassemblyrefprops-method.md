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
ms.openlocfilehash: 9aef471c1155070af0e9bcca14975a65bc5dc763
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175973"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a>IMetaDataAssemblyImport::GetAssemblyRefProps Yöntemi
Belirtilen meta veri imzasıyla derleme başvurusu için özellik kümesini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 [içinde] Özellikleri `mdAssemblyRef` almak için derleme başvurutemsil meta veri belirteci.  
  
 `ppbPublicKeyOrToken`  
 [çıkış] Ortak anahtarveya meta veri belirteci için bir işaretçi.  
  
 `pcbPublicKeyOrToken`  
 [çıkış] Döndürülen ortak anahtar veya belirteçteki bayt sayısı.  
  
 `szName`  
 [çıkış] Derlemenin basit adı.  
  
 `cchName`  
 [içinde] Boyutu, geniş chars, `szName`ve .  
  
 `pchName`  
 [çıkış] Geniş karakter sayısına işaretçi aslında `szName`döndürülür.  
  
 `pMetaData`  
 [çıkış] Derleme meta verilerini içeren bir ASSEMBLYMETADATA yapısına işaretçi.  
  
 `ppbHashValue`  
 [çıkış] Karma değeri için bir işaretçi. Bu, Sha-1 algoritmasını kullanarak, `PublicKey` [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) numaralandırmasının arfFullOriginator bayrağı ayarlanmadığı sürece, başvurulan derleme özelliğinin karmadır.  
  
 `pcbHashValue`  
 [çıkış] Döndürülen karma değerdeki geniş karakter sayısı.  
  
 `pdwAssemblyRefFlags`  
 [çıkış] Bir derlemeye uygulanan meta verileri açıklayan bayraklar için bir işaretçi. Bayrak değeri, bir veya daha fazla [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) değerinin bir leşimidir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem başarılı olursa S_OK döndürür; aksi takdirde, Winerror.h üstbilgi dosyasında tanımlanan hata kodlarından birini döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
