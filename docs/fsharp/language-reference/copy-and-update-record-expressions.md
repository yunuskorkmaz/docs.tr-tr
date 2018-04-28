---
title: 'Kopyalama ve güncelleştirme kayıt ifadeleri (F #)'
description: "'Varolan bir kaydı, güncelleştirmelerinin kopyalayan bir kopyalama ve güncelleştirme kayıt ifadesi' alanları belirtilen ve güncelleştirilmiş kaydı döndürür yazma öğrenin."
author: ChrSteinert
ms.author: phcart
ms.date: 06/04/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 98a515b5f053e9339588157185848e8315a580f4
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="copy-and-update-record-expressions"></a>Kopyalama ve güncelleştirme kayıt ifadeleri

A *kopyalama ve güncelleştirme kayıt ifade* varolan bir kaydı kopyalar, belirtilen alanları güncelleştirir ve güncelleştirilmiş kayıt döndüren bir ifadedir.


## <a name="syntax"></a>Sözdizimi

```fsharp
{ record-name with
    updated-member-definitions }
```

## <a name="remarks"></a>Açıklamalar
Yani hiçbir varolan bir kaydı güncelleştirmeye olası kayıtları varsayılan olarak, değişmez. Güncelleştirilmiş bir kaydı bir kaydın tüm alanları oluşturmak için yeniden belirtilmesi gerekir. Bu görev basitleştirmek için bir *kopyalama ve güncelleştirme kayıt ifade* kullanılabilir. Bu ifade varolan bir kaydı alır, ifade belirtilen alanları ve belirtilen ifade tarafından eksik alan kullanarak aynı türde yeni bir tane oluşturur.
Varolan bir kaydı kopyalayın ve büyük olasılıkla bazı alan değerlerini değiştirmek varsa, bu yararlı olabilir.

Örneği için yeni oluşturulan bir kayıt alın.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Yalnızca o kaydın kullanabileceğiniz alanında bulunan güncelleştirmek için olsaydı *kopyalama ve güncelleştirme kayıt ifade* aşağıdaki gibi:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a>Ayrıca Bkz.
[Kayıtlar](records.md)

[F# Dili Başvurusu](index.md)
