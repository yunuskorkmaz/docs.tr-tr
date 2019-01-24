---
title: '&#39;&lt;TypeName&gt; &#39; temsilci türü'
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: 6676328d0c1ea459f5934b5f9e2cb66580adad40
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737208"
---
# <a name="39lttypenamegt39-is-a-delegate-type"></a>&#39;&lt;TypeName&gt; &#39; temsilci türü
'\<typename >' temsilci türüdür. Temsilci oluşturma yalnızca tek bir AddressOf ifade bir bağımsız değişken listesi olarak izin verir. Genellikle bir AddressOf ifadesi, bir temsilci oluşturma yerine kullanılabilir.  
  
 A `New` yan tümcesi bir temsilci sınıfı örneğini oluşturma temsilci Oluşturucu için geçersiz bağımsız değişken listesi sağlar.  
  
 Yalnızca tek bir sağladığınız `AddressOf` yeni bir temsilci örneğini oluştururken ifade.  
  
 Bu hata, herhangi bir bağımsız değişken temsilci Oluşturucu için birden fazla bağımsız değişken geçirmeniz ya da tek bir bağımsız değişken geçirirseniz, geçerli değil geçirmezseniz sonuçlanabilir `AddressOf` ifade.  
  
 **Hata Kimliği:** BC32008  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Tek kullanımlık `AddressOf` ifade'temsilci sınıfında bağımsız değişken listesinde `New` yan tümcesi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [New İşleci](../../../visual-basic/language-reference/operators/new-operator.md)
- [AddressOf İşleci](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Temsilciler](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Nasıl yapılır: Bir temsilci yöntemi çağırma](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
