---
title: IXCLRDataModule::Request yöntemi
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::Request Method
helpviewer.keywords:
- IXCLRDataModule::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 755063ca6da29a2e4733dd653306192ac0434ec0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775459"
---
# <a name="ixclrdatamodulerequest-method"></a>IXCLRDataModule::Request yöntemi

Modülün verilerle verilen arabelleği doldurmak için istek sayısı.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Request([in] ULONG32 reqCode,
    [in] ULONG32 inBufferSize,
    [in, size_is(inBufferSize)] BYTE* inBuffer,
    [in] ULONG32 outBufferSize,
    [out, size_is(outBufferSize)] BYTE* outBuffer);
```

## <a name="parameters"></a>Parametreler

`reqCode`\
[in] İstek gönderilmesine izin türü.

`inBufferSize`\
[in] geçirilmesi giriş arabellek boyutu.

`inBuffer`\
[size_is(inBufferSize)] İstekte gönderilmek üzere ham verileri arabellek işaretçisi.

`outBufferSize`\
[in] Çıkış arabelleği boyutu.

`outBuffer`\
[out, size_is(outBufferSize)] İstek yanıt depolamak için kullanılan arabellek işaretçisi.

## <a name="remarks"></a>Açıklamalar

Sağlanan yöntem parçasıdır `IXCLRDataModule` arabirim ve sanal yöntem tablosunu 36th yuvaya karşılık gelir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).
**Üst bilgi:** Hiçbiri **kitaplığı:** Hiçbiri **.NET Framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama](index.md)
- [IXCLRDataModule arabirimi](ixclrdatamodule-interface.md)