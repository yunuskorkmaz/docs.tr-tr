---
title: Özellik veya yöntem çağrısı, bir özel nesneye bağımsız değişken ya da dönüş değeri olarak başvuru içeremez.
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 1f36526eab1bc0964bf89398b6e0f3e74d09fdc6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583831"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a>Özellik veya yöntem çağrısı, bir özel nesneye bağımsız değişken ya da dönüş değeri olarak başvuru içeremez.
Bu hatanın olası nedenleri arasında şunlardır:  
  
-   Bir istemci bir özelliği veya yöntemi bir işlem dışı bileşen çağrılır ve özel bir nesneye başvuru bağımsız değişkenlerden biri geçirme girişiminde bulunuldu.  
  
-   Bir işlem dışı bileşen, istemci üzerinde geri arama yöntemi çağrılır ve özel bir nesneye başvuru geçirme girişiminde bulunuldu.  
  
-   Özel bir nesneye başvuru oluşturma bir olay bağımsız değişken olarak geçirmek bir işlem dışı bileşen çalıştı.  
  
-   Bir özel nesneye başvuru atamak bir istemci çalıştı bir `ByRef` işleme olayının bağımsız değişkeni.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Başvurusunu kaldırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Private](../../../visual-basic/language-reference/modifiers/private.md)
