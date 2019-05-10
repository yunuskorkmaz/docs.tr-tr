---
title: "'<typename>' bir temsilci türü değil"
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: 45dc0403468fa40888a6c5e6bdfe6ca782e98325
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664179"
---
# <a name="typename-is-a-delegate-type"></a>'\<typename >' bir temsilci türü
'\<typename >' temsilci türüdür. Temsilci oluşturma yalnızca tek bir AddressOf ifade bir bağımsız değişken listesi olarak izin verir. Genellikle bir AddressOf ifadesi, bir temsilci oluşturma yerine kullanılabilir.  
  
 A `New` yan tümcesi bir temsilci sınıfı örneğini oluşturma temsilci Oluşturucu için geçersiz bağımsız değişken listesi sağlar.  
  
 Yalnızca tek bir sağladığınız `AddressOf` yeni bir temsilci örneğini oluştururken ifade.  
  
 Bu hata, herhangi bir bağımsız değişken temsilci Oluşturucu için birden fazla bağımsız değişken geçirmeniz ya da tek bir bağımsız değişken geçirirseniz, geçerli değil geçirmezseniz sonuçlanabilir `AddressOf` ifade.  
  
 **Hata Kimliği:** BC32008  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Tek kullanımlık `AddressOf` ifade'temsilci sınıfında bağımsız değişken listesinde `New` yan tümcesi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [New İşleci](../../../visual-basic/language-reference/operators/new-operator.md)
- [AddressOf İşleci](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Temsilciler](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Nasıl yapılır: Bir temsilci yöntemi çağırma](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
