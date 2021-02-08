---
description: 'Hakkında daha fazla bilgi edinin: bir özellik veya yöntem çağrısı, bir özel nesneye bağımsız değişken olarak veya dönüş değeri olarak başvuru içeremez'
title: Özellik veya yöntem çağrısı, bir özel nesneye bağımsız değişken ya da dönüş değeri olarak başvuru içeremez.
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 8fe570c9ed789a5bac36aafa9b1ec2f507a55d51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797204"
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

- [Özel](../modifiers/private.md)
