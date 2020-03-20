---
title: IMetaDataAssemblyImport::GetAssemblyProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyProps
helpviewer_keywords:
- GetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetAssemblyProps method [.NET Framework metadata]
ms.assetid: 0eaa4aa9-9441-444a-920c-e4b2a2db899e
topic_type:
- apiref
ms.openlocfilehash: dfa900e2184a8c415d75f5702c572b14c4018749
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177784"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a>IMetaDataAssemblyImport::GetAssemblyProps Yöntemi
Belirtilen meta veri imzasıyla derleme için özellik kümesini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetAssemblyProps (  
    [in]  mdAssembly          mda,  
    [out] const void          **ppbPublicKey,
    [out] ULONG               *pcbPublicKey,  
    [out] ULONG               *pulHashAlgId,  
    [out] LPWSTR              szName,  
    [in] ULONG                cchName,  
    [out] ULONG               *pchName,  
    [out] ASSEMBLYMETADATA    *pMetaData,  
    [out] DWORD               *pdwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `mda`  
 [içinde]. Özellikleri `mdAssembly` almak için derlemeyi temsil eden meta veri belirteci.  
  
 `ppbPublicKey`  
 [çıkış] Ortak anahtarveya meta veri belirteci için bir işaretçi.  
  
 `pcbPublicKey`  
 [çıkış] Döndürülen ortak anahtardaki bayt sayısı.  
  
 `pulHashAlgId`  
 [çıkış] Derlemedeki dosyaları karmalamak için kullanılan algoritmaya işaretçi.  
  
 `szName`  
 [çıkış] Derlemenin basit adı.  
  
 `cchName`  
 [içinde] Boyutu, geniş chars, `szName`ve .  
  
 `pchName`  
 [çıkış] Geniş karakter sayısı aslında döndü `szName`.  
  
 `pMetaData`  
 [çıkış] Derleme meta verilerini içeren bir ASSEMBLYMETADATA yapısına işaretçi.  
  
 `pdwAssemblyFlags`  
 [çıkış] Derlemeye uygulanan meta verileri açıklayan bayraklar. Bu değer, bir veya daha fazla [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) değerinin bir leşimidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
