---
title: IAssemblyCacheItem::CreateStream Yöntemi
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem.CreateStream
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::CreateStream
helpviewer_keywords:
- CreateStream method [.NET Framework fusion]
- IAssemblyCacheItem::CreateStream method [.NET Framework fusion]
ms.assetid: 697ab0f4-470c-4baa-a415-4a975c42d0d5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 380e248c8c4e3407fff868cdd9a5c63b63e50c69
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353913"
---
# <a name="iassemblycacheitemcreatestream-method"></a>IAssemblyCacheItem::CreateStream Yöntemi

Belirtilen ada ve biçimi bir akış oluşturur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT CreateStream (
    [in]  DWORD dwFlags,
    [in]  LPCWSTR pszStreamName,
    [in]  DWORD dwFormat,
    [in]  DWORD dwFormatFlags,
    [out] IStream **ppIStream,
    [in, optional] ULARGE_INTEGER *puliMaxSize
);
```

## <a name="parameters"></a>Parametreler

`dwFlags`\
[in] Fusion.idl içinde tanımlanan bayraklar.

`pszStreamName`\
[in] Oluşturulacak Akış adı.

`dwFormat`\
[in] Akışla için dosya biçimi.

`dwFormatFlags`\
[in] Fusion.idl içinde tanımlanan özel biçim bayrakları.

`ppIStream`\
[out] Döndürülen adresini bir işaretçiye [IStream](/windows/desktop/api/objidl/nn-objidl-istream) örneği.

`puliMaxSize`\
[, isteğe bağlı] En büyük boyutu tarafından başvuruda bulunulan akışın `ppIStream`.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

**Üst bilgi:** Fusion.h

**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [IAssemblyCacheItem Arabirimi](iassemblycacheitem-interface.md)