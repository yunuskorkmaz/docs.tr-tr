---
title: Kayıt İfadelerini Kopyalama ve Güncelleştirme
description: Varolan bir kaydı veya anonim kaydı kopyalayan, belirtilen alanları güncelleştiren ve güncelleştirilmiş kaydı veya anonim kaydı döndüren ' kopyalama ve güncelleştirme ifadesi ' yazmayı öğrenin.
author: ChrSteinert
ms.date: 06/12/2019
ms.openlocfilehash: dfb20a6ff8282ae5988772cc0f0841db23aad942
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630385"
---
# <a name="copy-and-update-record-expressions"></a>Kayıt İfadelerini Kopyalama ve Güncelleştirme

Bir *kopyalama ve güncelleştirme kaydı ifadesi* , var olan bir kaydı kopyalayan, belirtilen alanları güncelleştiren ve güncelleştirilmiş kaydı döndüren bir ifadedir.

## <a name="syntax"></a>Sözdizimi

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a>Açıklamalar

Kayıtlar ve anonim kayıtlar varsayılan olarak sabittir, böylece var olan bir kayda yönelik bir güncelleştirme yoktur. Güncelleştirilmiş bir kayıt oluşturmak için bir kaydın tüm alanlarının yeniden belirtilmesi gerekir. Bu görevi basitleştirmek için, bir *kopyalama ve güncelleştirme ifadesi* kullanılabilir. Bu ifade mevcut bir kaydı alır, ifadeden belirtilen alanları ve ifade tarafından belirtilen eksik alanı kullanarak aynı türden yeni bir tane oluşturur.

Bu, var olan bir kaydı kopyalamanız ve muhtemelen alan değerlerinden bazılarını değiştirmeniz gerektiğinde yararlı olabilir.

Yeni oluşturulan bir kayıt örneğini alın.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Yalnızca söz konusu kayıt alanında güncelleştirme yaptıysanız, aşağıdaki gibi *kopyalama ve güncelleştirme kayıt ifadesini* kullanabilirsiniz:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Kayıtlar](records.md)
- [Anonim kayıtlar](anonymous-records.md)
- [F# Dili Başvurusu](index.md)
