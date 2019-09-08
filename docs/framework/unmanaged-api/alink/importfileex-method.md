---
title: ImportFileEx Yöntemi
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx
helpviewer_keywords:
- ImportFileEx method
ms.assetid: ad276f3f-b303-46ac-97e0-66a377adaa4f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bd138d0418bb9667a86419d719bf0b95a4bb1b12
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777119"
---
# <a name="importfileex-method"></a>ImportFileEx Yöntemi
Belirtilen derleme veya ilişkisiz modül içeri aktarır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ImportFileEx(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a>Parametreler  
 `pszFilename`  
 İçinden içeri aktarılacak dosyanın tam adı.  
  
 `pszTargetName`  
 Hedef dosyanın isteğe bağlı adı.  
  
 `fSmartImport`  
 TRUE ise ImportTypes kullanılır, aksi takdirde içeri aktarma işlemi el ile gerçekleştirilmelidir.  
  
 `dwOpenFlags`  
 [OpenScope metoduna](../metadata/imetadatadispenser-openscope-method.md)geçirilecek bayraklar.  
  
 `pImportToken`  
 İçeri aktarılmakta olan dosyanın KIMLIĞINI alır.  
  
 `ppAssemblyScope`  
 Derleme içeri aktarma kapsamı [IMetaDataAssemblyImport Arabirimi](../metadata/imetadataassemblyimport-interface.md) arabirimini alır. Dosya bir derleme değilse NULL olarak ayarlanır.  
  
 `pdwCountOfScopes`  
 İçeri aktarılan dosya ve/veya kapsamların sayısını alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 ALink. h gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IALink2 Arabirimi](ialink2-interface.md)
- [IALink Arabirimi](ialink-interface.md)
- [ALink API](index.md)
