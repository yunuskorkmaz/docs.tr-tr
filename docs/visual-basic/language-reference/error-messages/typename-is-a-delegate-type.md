---
title: "'<typename>' bir temsilci türü değil"
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: 4cc0a1221dcf65aa2a16fd7d82568c8544f27fdb
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875078"
---
# <a name="typename-is-a-delegate-type"></a>'\<typename>' bir temsilci türü değil

' \<typename> ' bir temsilci türüdür. Temsilci oluşturma, bağımsız değişken listesi olarak yalnızca tek bir AddressOf ifadesine izin veriyor. Genellikle bir AddressOf ifadesi, temsilci oluşturma yerine kullanılabilir.  
  
 `New`Temsilci sınıfının bir örneğini oluşturan yan tümce, temsilci oluşturucusuna geçersiz bir bağımsız değişken listesi sağlar.  
  
 `AddressOf`Yeni bir temsilci örneği oluştururken yalnızca tek bir ifade sağlayabilirsiniz.  
  
 Bu hata, birden fazla bağımsız değişken geçirirseniz veya geçerli bir ifade olmayan tek bir bağımsız değişken geçirirseniz, temsilci oluşturucusuna herhangi bir bağımsız değişken geçirmezseniz oluşabilir `AddressOf` .  
  
 **Hata kimliği:** BC32008  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- `AddressOf`Yan tümcesindeki Delegate sınıfı için bağımsız değişken listesinde tek bir ifade kullanın `New` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [New Işleci](../operators/new-operator.md)
- [AddressOf İşleci](../operators/addressof-operator.md)
- [Temsilciler](../../programming-guide/language-features/delegates/index.md)
- [Nasıl yapılır: Temsilci Yöntemi Çağırma](../../programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
