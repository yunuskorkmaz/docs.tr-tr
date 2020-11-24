---
title: IMetaDataAssemblyEmit::DefineAssemblyRef Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssemblyRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssemblyRef
helpviewer_keywords:
- DefineAssemblyRef method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineAssemblyRef method [.NET Framework metadata]
ms.assetid: 0b284b18-0084-4b3a-912a-5ebe9f29c88b
topic_type:
- apiref
ms.openlocfilehash: ba53ff30f0b6d0ae7fed7db422b7c0a242204a2c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689439"
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a>IMetaDataAssemblyEmit::DefineAssemblyRef Yöntemi

`AssemblyRef`Bu derlemenin başvurduğu derleme için meta veriler içeren bir yapı oluşturur ve ilişkili meta veri belirtecini döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT DefineAssemblyRef (  
    [in]  void                *pbPublicKeyOrToken,  
    [in]  ULONG               cbPublicKeyOrToken,  
    [in]  LPCWSTR             szName,  
    [in]  ASSEMBLYMETADATA    pMetaData,  
    [in]  void                *pbHashValue,  
    [in]  ULONG               cbHashValue,  
    [in]  DWORD               dwAssemblyRefFlags,  
    [out] mdAssemblyRef       *pmdar  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pbPublicKeyOrToken`  
 'ndaki Başvurulan derlemenin yayımcısının ortak anahtarı. [StrongNameTokenFromAssembly](../strong-naming/strongnametokenfromassembly-function.md) yardımcı işlevi, bu parametre olarak geçirilecek ortak anahtarın karmasını almak için kullanılabilir.  
  
 `cbPublicKeyOrToken`  
 'ndaki Bayt cinsinden boyut `pbPublicKeyOrToken` .  
  
 `szName`  
 'ndaki Derlemenin insanların okunabilir metin adı. Bu değerin 1024 karakteri aşmaması gerekir.  
  
 `pMetaData`  
 'ndaki Başvurulan derlemenin sürümünü, platformunu ve yerel ayar bilgilerini içeren bir ASSEMBLYMETADATA örneği.  
  
 `pbHashValue`  
 'ndaki Başvurulan derlemeyle ilişkili karma verileri. İsteğe bağlı.  
  
 `cbHashValue`  
 'ndaki Bayt cinsinden boyut `pbHashValue` .  
  
 `dwAssemblyRefFlags`  
 'ndaki Yürütme altyapısının davranışını etkileyen, [CorAssemblyFlags](corassemblyflags-enumeration.md) değerlerinin bit düzeyinde birleşimi.  
  
 `pmdar`  
 dışı Döndürülen `AssemblyRef` meta veri belirtecine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 `AssemblyRef`Bu derlemenin başvurduğu her derleme için bir meta veri yapısının tanımlanması gerekir.  
  
 Çalışma zamanında, başvurulan bir derlemenin ayrıntıları, derleme çözümleyiciye "yerleşik olarak" bilgi olarak temsil ettikleri bir bildirim ile geçirilir. Derleme çözümleyici ilke uygular.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataAssemblyEmit Arabirimi](imetadataassemblyemit-interface.md)
