---
title: Kayıt İfadelerini Kopyalama ve Güncelleştirme
description: "', Mevcut bir kayıt veya anonim kaydı, güncelleştirmeleri kopyalayan bir kopyalama ve güncelleştirme expression' alanları belirtilen ve güncelleştirilmiş kayıt veya anonim bir kayıt döndürür yazmayı öğrenin."
author: ChrSteinert
ms.date: 06/12/2019
ms.openlocfilehash: d16f5ca337047ab2eecc8828b21d8a423bf39a1f
ms.sourcegitcommit: c4dfe37032c64a1fba2cc3d5947550d79f95e3b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/13/2019
ms.locfileid: "67041734"
---
# <a name="copy-and-update-record-expressions"></a>Kayıt İfadelerini Kopyalama ve Güncelleştirme

A *kopyalama ve güncelleştirme kayıt ifade* varolan bir kaydı kopyalar, belirtilen alanlarını güncelleştirir ve güncelleştirilen kaydı döndüren bir ifadedir.

## <a name="syntax"></a>Sözdizimi

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a>Açıklamalar

Böylece için varolan bir kaydı güncelleştirme olası, varsayılan olarak ve anonim kayıtlarını sabittir. Bir kaydın tüm alanlarını güncelleştirilen bir kaydı oluşturmak için yeniden belirtilmesi gerekir. Bu görevi kolaylaştırmak amacıyla bir *kopyalama ve güncelleştirme ifade* kullanılabilir. Bu ifade, varolan bir kaydı alır, ifade belirtilen alanları ve ifade tarafından belirtilen eksik alan kullanarak aynı türde yeni bir tane oluşturur.

Kayıtlardan kopyalayabilir ve büyük olasılıkla bazı alan değerleri değiştirmek varsa, bu yararlı olabilir.

Örneği için yeni oluşturulan bir kaydı alır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Yalnızca kullanabilirsiniz, kayıt alanı üzerinde güncelleştirmek için olsaydı *kopyalama ve güncelleştirme kayıt ifade* aşağıdaki gibidir:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Kayıtlar](records.md)
- [Anonim kayıtları](anonymous-records.md)
- [F# Dili Başvurusu](index.md)
