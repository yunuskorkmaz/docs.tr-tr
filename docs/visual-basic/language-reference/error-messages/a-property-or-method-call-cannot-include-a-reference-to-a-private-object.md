---
title: Özellik veya yöntem çağrısı, bir özel nesneye bağımsız değişken ya da dönüş değeri olarak başvuru içeremez.
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 36c71cdb345d0fdc0da2b58865a1f11956bcb944
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409978"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a>Özellik veya yöntem çağrısı, bir özel nesneye bağımsız değişken ya da dönüş değeri olarak başvuru içeremez.

Bu hatanın olası nedenleri arasında:  
  
- İstemci bir işlem dışı bileşenin özelliğini veya yöntemini çağırdı ve bağımsız değişkenlerden biri olarak özel bir nesneye başvuru geçirmeye çalıştı.  
  
- İşlem dışı bir bileşen, istemcisi üzerinde bir geri çağırma yöntemi çağırdı ve özel bir nesneye başvuru geçirmeye çalıştı.  
  
- İşlem dışı bir bileşen, bir özel nesneye bir başvuruyu, oluşturduğu bir olayın bağımsız değişkeni olarak geçirmeye çalıştı.  
  
- İstemci `ByRef` , işlediği bir olayın bağımsız değişkenine özel nesne başvurusu atamaya çalıştı.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Başvuruyu kaldırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özelleştirme](../modifiers/private.md)
