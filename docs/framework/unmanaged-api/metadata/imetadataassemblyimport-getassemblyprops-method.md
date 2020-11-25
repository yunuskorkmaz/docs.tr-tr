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
ms.openlocfilehash: 1e1a86cdf55812197aae653dca256fb910a7f168
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733899"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a>IMetaDataAssemblyImport::GetAssemblyProps Yöntemi

Belirtilen meta veri imzasına sahip derleme için özellik kümesini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 [in]. `mdAssembly`Özelliklerinin alınacağı derlemeyi temsil eden meta veri belirteci.  
  
 `ppbPublicKey`  
 dışı Ortak anahtara veya meta veri belirtecine yönelik bir işaretçi.  
  
 `pcbPublicKey`  
 dışı Döndürülen ortak anahtardaki bayt sayısı.  
  
 `pulHashAlgId`  
 dışı Derlemedeki dosyaları karma hale almak için kullanılan algoritmanın işaretçisi.  
  
 `szName`  
 dışı Derlemenin basit adı.  
  
 `cchName`  
 'ndaki , Öğesinin geniş karakter cinsinden boyutu `szName` .  
  
 `pchName`  
 dışı Aslında ' de döndürülen geniş karakter sayısı `szName` .  
  
 `pMetaData`  
 dışı Derleme meta verilerini içeren bir ASSEMBLYMETADATA yapısına yönelik işaretçi.  
  
 `pdwAssemblyFlags`  
 dışı Bir derlemeye uygulanan meta verileri tanımlayan bayraklar. Bu değer bir veya daha fazla [CorAssemblyFlags](corassemblyflags-enumeration.md) değerinin birleşimidir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyImport Arabirimi](imetadataassemblyimport-interface.md)
