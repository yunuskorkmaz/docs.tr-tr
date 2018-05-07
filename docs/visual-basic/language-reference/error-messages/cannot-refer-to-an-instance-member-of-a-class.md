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
ms.openlocfilehash: 368539ed24d9819c8d1ddbbb9e3e0dff21d27c32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="cannot-refer-to-an-instance-member-of-a-class-from-within-a-shared-method-or-shared-member-initializer-without-an-explicit-instance-of-the-class"></a>Bir sınıfın örnek üyesine paylaştırılmış yöntem veya paylaştırılmış üye başlatıcıdan, sınıfın açık bir örneği olmadan başvurulamaz
Paylaşılan bir yordam aynı sınıfın paylaşılmayan üye başvurmak denediniz. Aşağıdaki örnek, böyle bir durum gösterir.  
  
```  
Class sample  
    Public x as Integer  
    Public Shared Sub setX()  
        x = 10  
    End Sub  
End Class  
```  
  
 Önceki örnekte, atama ifadesi `x = 10` bu hata iletisini oluşturur. Paylaşılan bir yordam bir örnek değişkeni erişmeye çalışıyor olmasıdır.  
  
 Değişkeni `x` olarak bildirilmedi örnek üyesine çünkü [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md). Her sınıf örneği `sample` kendi bağımsız değişken içeriyor `x`. Ne zaman bir örnek ayarlar veya değerini değiştirir `x`, değerini etkilemez `x` başka bir örnek.  
  
 Ancak, yordamı `setX` olan `Shared` sınıfın tüm örnekleri arasında `sample`. Başka bir deyişle, bir sınıfın örneklerini ile ilişkili değil, ancak bunun yerine tek tek örneklerini bağımsız olarak çalışır. Belirli bir örneği ile bağlantı içerdiğinden `setX` bir örnek değişkeni erişemiyor. Yalnızca üzerinde çalışmalıdır `Shared` değişkenleri. Zaman `setX` ayarlar veya yeni bir değer sınıfın tüm örnekleri için kullanılabilir paylaşılan bir değişkenin değerini değiştirir.  
  
 **Hata Kimliği:** BC30369  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Sınıfın tüm örnekleri arasında paylaşılabilir veya her örneği için tek tek tutulan üyesi isteyip istemediğinize karar verin.  
  
2.  Tüm örnekler arasında paylaşılacak üye tek bir kopyasını istiyorsanız ekleyin `Shared` üye bildirimi anahtar sözcük. Korumak `Shared` yordamı bildiriminde anahtar sözcüğü.  
  
3.  Her örnek üyesinin tek tek kendi kopyasına sahip istiyorsanız belirtmeyin `Shared` üye bildirimi için. Kaldırma `Shared` yordamı bildirimi anahtar sözcük.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
