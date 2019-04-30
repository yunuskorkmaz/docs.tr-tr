---
title: Activate işlevi (WPF yönetilmeyen API Başvurusu)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- Activate
api_location:
- PresentationHost_v0400.dll
ms.assetid: 1400329c-b598-465f-80f2-e3dabf044811
ms.openlocfilehash: ee231653815bd5ef75d58979034e3b3be9f5ba54
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777175"
---
# <a name="activate-function-wpf-unmanaged-api-reference"></a>Activate işlevi (WPF yönetilmeyen API Başvurusu)

Bu API Windows Presentation Foundation (WPF) altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.

Windows Presentation Foundation (WPF) altyapısı tarafından windows yönetimi için kullanılır.

## <a name="syntax"></a>Sözdizimi

```cpp
void Activate(
    const ActivateParameters* pParameters,
    __deref_out_ecount(1) LPUNKNOWN* ppInner,
    );
```

## <a name="parameters"></a>Parametreler

`pParameters`\
Pencerenin etkinleştirme parametresi için bir işaretçi.

`ppInner`\
Bir işaretçi içeren tek öğeli arabellek adresini bir işaretçiye bir <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> nesne.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz: [.NET Framework sistem gereksinimleri](../../get-started/system-requirements.md).

**DLL:**

.NET Framework 3.0 ve 3.5: PresentationHostDLL.dll

.NET Framework 4 ve üzeri: PresentationHost_v0400.dll

**.NET framework sürümü:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WPF Yönetilmeyen API Başvurusu](wpf-unmanaged-api-reference.md)
