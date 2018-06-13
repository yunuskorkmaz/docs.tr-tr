---
title: '&#39;&lt;TypeName&gt; &#39; bir temsilci türü'
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: c6d4244ce72dedee50b65ba19978149ce86b9e87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595654"
---
# <a name="39lttypenamegt39-is-a-delegate-type"></a>&#39;&lt;TypeName&gt; &#39; bir temsilci türü
'\<typename >' temsilci türüdür. Temsilci yapım yalnızca tek bir AddressOf ifade bir değişken listesi olarak verir. Genellikle bir AddressOf ifade temsilci yapım yerine kullanılabilir.  
  
 A `New` yan tümcesi bir temsilci sınıfının bir örneğini oluşturma sağlayan bir temsilci Oluşturucu geçersiz bağımsız değişken listesi.  
  
 Yalnızca tek bir sağlayabilir `AddressOf` yeni bir temsilci örneği oluşturulurken ifade.  
  
 Bu hata, herhangi bir bağımsız değişken temsilci Oluşturucu için birden fazla bağımsız değişken geçirmek ya da tek bir bağımsız değişken geçirirseniz bir geçerli olmayan geçirmezseniz sonuçlanabilir `AddressOf` ifade.  
  
 **Hata Kimliği:** BC32008  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Tek kullanımlık `AddressOf` temsilci sınıfında için bağımsız değişken listesi ifadesinde `New` yan tümcesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [New İşleci](../../../visual-basic/language-reference/operators/new-operator.md)  
 [AddressOf İşleci](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Temsilciler](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Nasıl yapılır: Temsilci Yöntemi Çağırma](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
