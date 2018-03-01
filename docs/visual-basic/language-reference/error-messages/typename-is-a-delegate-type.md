---
title: "&#39; &lt;typename&gt;&#39; bir temsilci türü"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9428f0ac321b90e36d4d987381ed69b6c968894c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="39lttypenamegt39-is-a-delegate-type"></a>&#39; &lt;typename&gt;&#39; bir temsilci türü
'\<typename >' temsilci türüdür. Temsilci yapım yalnızca tek bir AddressOf ifade bir değişken listesi olarak verir. Genellikle bir AddressOf ifade temsilci yapım yerine kullanılabilir.  
  
 A `New` yan tümcesi bir temsilci sınıfının bir örneğini oluşturma sağlayan bir temsilci Oluşturucu geçersiz bağımsız değişken listesi.  
  
 Yalnızca tek bir sağlayabilir `AddressOf` yeni bir temsilci örneği oluşturulurken ifade.  
  
 Bu hata, herhangi bir bağımsız değişken temsilci Oluşturucu için birden fazla bağımsız değişken geçirmek ya da tek bir bağımsız değişken geçirirseniz bir geçerli olmayan geçirmezseniz sonuçlanabilir `AddressOf` ifade.  
  
 **Hata Kimliği:** BC32008  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Tek kullanımlık `AddressOf` temsilci sınıfında için bağımsız değişken listesi ifadesinde `New` yan tümcesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [New işleci](../../../visual-basic/language-reference/operators/new-operator.md)  
 [AddressOf işleci](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Temsilciler](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Nasıl yapılır: temsilci yöntemi çağırma](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
