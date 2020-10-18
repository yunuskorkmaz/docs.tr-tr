---
title: Özellik veya yöntem çağrısı, bir özel nesneye bağımsız değişken ya da dönüş değeri olarak başvuru içeremez.
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 00237d795fb62fbae426e0015d8e64d5fabb4c32
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162680"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a>Özellik veya yöntem çağrısı, bir özel nesneye bağımsız değişken ya da dönüş değeri olarak başvuru içeremez.

Bu hatanın olası nedenleri arasında:

- İstemci bir işlem dışı bileşenin özelliğini veya yöntemini çağırdı ve bağımsız değişkenlerden biri olarak özel bir nesneye başvuru geçirmeye çalıştı.

- İşlem dışı bir bileşen, istemcisi üzerinde bir geri çağırma yöntemi çağırdı ve özel bir nesneye başvuru geçirmeye çalıştı.

- İşlem dışı bir bileşen, bir özel nesneye bir başvuruyu, oluşturduğu bir olayın bağımsız değişkeni olarak geçirmeye çalıştı.

- İstemci `ByRef` , işlediği bir olayın bağımsız değişkenine özel nesne başvurusu atamaya çalıştı.

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Başvuruyu kaldırın.

## <a name="see-also"></a>Ayrıca bkz.

- [Özelleştirme](../modifiers/private.md)
