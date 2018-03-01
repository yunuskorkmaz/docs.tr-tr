---
title: "Özellik veya yöntem çağrısı, bir özel nesneye bağımsız değişken ya da dönüş değeri olarak başvuru içeremez."
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cce2bc67beb7e4ac0664b5b7240f5eb3ea0204f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
 [Özel](../../../visual-basic/language-reference/modifiers/private.md)
