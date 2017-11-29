---
title: "Bir sınıfın örnek üyesine paylaştırılmış yöntem veya paylaştırılmış üye başlatıcıdan, sınıfın açık bir örneği olmadan başvurulamaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30369
- bc30369
helpviewer_keywords:
- Shared
- BC30369
ms.assetid: 39d9466b-c1f3-4406-91a5-3d6c52d23a3d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6a15d36c0b3a4d6b1657d583de0dc61621da960d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
 [Paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md)
