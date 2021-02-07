---
description: 'Daha fazla bilgi edinin: ImportFileEx yöntemi'
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
ms.openlocfilehash: a8a7e5a142091bf7cc93f50a4ae20c59d800f3ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718024"
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
