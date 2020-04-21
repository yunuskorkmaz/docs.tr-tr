---
title: Kayıt İfadelerini Kopyalama ve Güncelleştirme
description: Varolan bir kaydı veya anonim kaydı kopyalayan, belirtilen alanları güncelleştiren ve güncelleştirilen kaydı veya anonim kaydı döndüren bir 'kopyalama ve güncelleştirme ifadesini' nasıl yazacağız öğrenin.
author: ChrSteinert
ms.date: 06/12/2019
ms.openlocfilehash: bec3e0ac2fb34e358b199c509c4599b55d7bf35e
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739281"
---
# <a name="copy-and-update-record-expressions"></a>Kayıt İfadelerini Kopyalama ve Güncelleştirme

*Kayıt ifadesini kopyala ve güncelleştir,* varolan bir kaydı kopyalayan, belirtilen alanları güncelleştiren ve güncelleştirilen kaydı döndüren bir ifadedir.

## <a name="syntax"></a>Sözdizimi

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a>Açıklamalar

Kayıtlar ve anonim kayıtlar varsayılan olarak değişmez olduğundan, varolan bir kaydı güncelleştirmek mümkün değildir. Güncelleştirilmiş bir kayıt oluşturmak için bir kaydın tüm alanlarının yeniden belirtilmesi gerekir. Bu görevi basitleştirmek için bir *kopyalama ve güncelleştirme ifadesi* kullanılabilir. Bu ifade varolan bir kaydı alır, ifade ve ifade tarafından belirtilen eksik alandan belirtilen alanları kullanarak aynı türde yeni bir tane oluşturur.

Bu, varolan bir kaydı kopyalamanız ve büyük olasılıkla bazı alan değerlerini değiştirmeniz gerektiğinde yararlı olabilir.

Örneğin yeni oluşturulan bir kaydı ele alalım.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Bu kayıtta yalnızca iki alanı güncelleştirmek için *kopyala ve güncelleştir kaydı ifadesini*kullanabilirsiniz:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Kayıtlar](records.md)
- [Anonim Kayıtlar](anonymous-records.md)
- [F# Dil Referansı](index.md)
