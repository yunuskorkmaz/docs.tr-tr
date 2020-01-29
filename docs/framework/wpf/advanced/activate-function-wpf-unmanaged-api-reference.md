---
title: Activate Işlevi-WPF yönetilmeyen API başvurusu
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- Activate
api_location:
- PresentationHost_v0400.dll
ms.assetid: 1400329c-b598-465f-80f2-e3dabf044811
ms.openlocfilehash: 9c0a235e8b94294ab82da88e43f7446c29739c12
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734505"
---
# <a name="activate-function-wpf-unmanaged-api-reference"></a>Activate Işlevi (WPF yönetilmeyen API Başvurusu)

Bu API Windows Presentation Foundation (WPF) altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.

Windows yönetimi için Windows Presentation Foundation (WPF) altyapısı tarafından kullanılır.

## <a name="syntax"></a>Sözdizimi

```cpp
void Activate(
    const ActivateParameters* pParameters,
    __deref_out_ecount(1) LPUNKNOWN* ppInner,
    );
```

## <a name="parameters"></a>Parametreler

`pParameters`\
Pencerenin etkinleştirme parametrelerine yönelik bir işaretçi.

`ppInner`\
<xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> nesnesine yönelik bir işaretçi içeren tek öğeli arabelleğin adresine yönelik bir işaretçi.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [.NET Framework sistem gereksinimleri](../../get-started/system-requirements.md).

**DOSYASıNı**

.NET Framework 3,0 ve 3,5: PresentationHostDLL. dll

.NET Framework 4 ve üzeri: PresentationHost_v0400. dll

**.NET Framework sürümü:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WPF Yönetilmeyen API Başvurusu](wpf-unmanaged-api-reference.md)
