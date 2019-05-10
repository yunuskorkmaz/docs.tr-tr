---
title: Özellik veya yöntem çağrısı, bir özel nesneye bağımsız değişken ya da dönüş değeri olarak başvuru içeremez.
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 67b0b50ecd6d7933d2aeea4556a8e261632e297a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64646911"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a>Özellik veya yöntem çağrısı, bir özel nesneye bağımsız değişken ya da dönüş değeri olarak başvuru içeremez.
Bu hatanın olası nedenleri arasında:  
  
- Bir istemci bir özelliği veya yöntemi bir işlem dışı bileşeninin çağrılır ve bir özel nesneye bir başvuru bağımsız değişkenlerden biri geçirilecek çalıştı.  
  
- Bir işlem dışı bileşeni, bir geri arama yöntemi, istemci üzerinde çağrılır ve bir özel nesneye bir başvuruya çalışıldı.  
  
- Bir özel nesneye bir başvuru, yükseltme bir olayın bağımsız değişken olarak geçirmek bir işlem dışı bileşeni çalıştı.  
  
- Bir istemci bir özel nesneye başvuru atamayı denediniz bir `ByRef` işleme bir olayının bağımsız değişkeni.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Başvuruyu kaldırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Private](../../../visual-basic/language-reference/modifiers/private.md)
