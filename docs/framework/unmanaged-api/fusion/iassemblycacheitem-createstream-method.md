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
ms.openlocfilehash: 0660621f465f2ba3610e06bd1df38baa1bc5c907
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134478"
---
# <a name="iassemblycacheitemcreatestream-method"></a>IAssemblyCacheItem::CreateStream Yöntemi

Belirtilen ad ve biçimle bir akış oluşturur.

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
'ndaki Fusion. IDL içinde tanımlanan bayraklar.

`pszStreamName`\
'ndaki Oluşturulacak akışın adı.

`dwFormat`\
'ndaki Akışa eklenecek dosyanın biçimi.

`dwFormatFlags`\
'ndaki Fusion. IDL içinde tanımlı formata özgü bayraklar.

`ppIStream`\
dışı Döndürülen [IStream](/windows/desktop/api/objidl/nn-objidl-istream) örneğinin adresine yönelik bir işaretçi.

`puliMaxSize`\
[ın, isteğe bağlı] `ppIStream`başvurduğu akışın en büyük boyutu.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** Fusion. h

**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [IAssemblyCacheItem Arabirimi](iassemblycacheitem-interface.md)
