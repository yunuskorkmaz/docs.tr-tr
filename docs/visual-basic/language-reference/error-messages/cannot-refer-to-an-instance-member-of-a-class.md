---
title: Bir sınıfın örnek üyesine paylaştırılmış yöntem veya paylaştırılmış üye başlatıcıdan, sınıfın açık bir örneği olmadan başvurulamaz
ms.date: 07/20/2015
f1_keywords:
- vbc30369
- bc30369
helpviewer_keywords:
- Shared
- BC30369
ms.assetid: 39d9466b-c1f3-4406-91a5-3d6c52d23a3d
ms.openlocfilehash: aad068b5857eb956ded63fa2a57cb163d3cf5c58
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59322699"
---
# <a name="cannot-refer-to-an-instance-member-of-a-class-from-within-a-shared-method-or-shared-member-initializer-without-an-explicit-instance-of-the-class"></a>Bir sınıfın örnek üyesine paylaştırılmış yöntem veya paylaştırılmış üye başlatıcıdan, sınıfın açık bir örneği olmadan başvurulamaz
Paylaşılan bir yordam içinde bir sınıftan paylaşılmayan üyesi başvurmak çalıştınız. Aşağıdaki örnekte, böyle bir durum gösterilmektedir.  
  
```  
Class sample  
    Public x as Integer  
    Public Shared Sub setX()  
        x = 10  
    End Sub  
End Class  
```  
  
 Yukarıdaki örnekte, atama ifadesi `x = 10` bu hata iletisini oluşturur. Paylaşılan bir yordam örneği bir değişkene erişmeye çalışıyor olmasıdır.  
  
 Değişken `x` olarak bildirilmediğinden, bir örnek üyesi olduğu [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md). Sınıfın her örneğini `sample` kendi bağımsız değişkenini içeren `x`. Ne zaman bir örneği ayarlar veya değerini değiştirir `x`, değerini etkilemez `x` herhangi bir örneğindeki.  
  
 Ancak, yordamın `setX` olduğu `Shared` sınıfın tüm örnekleri arasında `sample`. Başka bir deyişle, herhangi bir sınıf örneği ile ilişkili değildir, ancak bunun yerine tek tek örnekleri bağımsız olarak çalışır. Belirli bir örneği ile bağlantı olduğundan `setX` bir örnek değişkeni erişemez. Yalnızca çalışmalıdır `Shared` değişkenleri. Zaman `setX` ayarlar veya yeni değeri sınıfın tüm örnekleri için kullanılabilir, paylaşılan bir değişkenin değerini değiştirir.  
  
 **Hata Kimliği:** BC30369  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Sınıfın tüm örnekleri arasında paylaşılan veya her örneği için tek tek tutulan üyesi için istediğinize karar verin.  
  
2. Üyenin tüm örnekleri arasında paylaşılması için tek bir kopyasını istiyorsanız ekleyin `Shared` üye bildirimi için anahtar sözcüğü. Korumak `Shared` yordamı bildirimindeki anahtar sözcüğü.  
  
3. Her örnek kendi ayrı üye kopyasına sahip istiyorsanız belirtmeyin `Shared` üye bildirimi için. Kaldırma `Shared` yordam bildirimi from anahtar sözcüğü.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
