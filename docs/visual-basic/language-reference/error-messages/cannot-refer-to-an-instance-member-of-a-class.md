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
ms.openlocfilehash: a2a5ab99ff68e6dce783a2fd986ee6e8c15ae858
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701171"
---
# <a name="cannot-refer-to-an-instance-member-of-a-class-from-within-a-shared-method-or-shared-member-initializer-without-an-explicit-instance-of-the-class"></a>Bir sınıfın örnek üyesine paylaştırılmış yöntem veya paylaştırılmış üye başlatıcıdan, sınıfın açık bir örneği olmadan başvurulamaz
Paylaşılan bir yordamın içinden bir sınıfın paylaşılmayan üyesine başvurmaya çalıştınız. Aşağıdaki örnekte böyle bir durum gösterilmektedir.  
  
```vb  
Class sample  
    Public x as Integer  
    Public Shared Sub setX()  
        x = 10  
    End Sub  
End Class  
```  
  
 Yukarıdaki örnekte, `x = 10` atama ifadesinde bu hata iletisi oluşturulur. Bunun nedeni, paylaşılan bir yordamın bir örnek değişkenine erişmeye çalışıyor olması.  
  
 @No__t-0 değişkeni, [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md)olarak bildirildiği için bir örnek üyesidir. @No__t-0 sınıfının her örneği kendi bağımsız değişkenini içerir `x`. Bir örnek `x` değerini ayarladığında veya değiştirdiğinde, başka bir örnekteki `x` değerini etkilemez.  
  
 Ancak, `setX` yordamı, `sample` sınıfının tüm örnekleri arasında `Shared` ' dir. Bu, sınıfın herhangi bir örneğiyle ilişkilendirilmediği, ancak tek tek örneklerden bağımsız olarak çalışan bir anlamına gelir. Belirli bir örneğe sahip hiçbir bağlantısı olmadığından, `setX` bir örnek değişkenine erişemez. Yalnızca `Shared` değişkenlerinde çalışması gerekir. @No__t-0, paylaşılan bir değişkenin değerini ayarladığında veya değiştirdiğinde, bu yeni değer sınıfının tüm örnekleri için kullanılabilir.  
  
 **Hata kimliği:** BC30369  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Üyenin sınıfın tüm örnekleri arasında paylaşılmasını mi yoksa her örnek için bir bireyin mı saklanacağını belirleyin.  
  
2. Üyenin tek bir kopyasının tüm örnekler arasında paylaşılmasını istiyorsanız üye bildirimine `Shared` anahtar sözcüğünü ekleyin. Yordam bildiriminde `Shared` anahtar sözcüğünü koruyun.  
  
3. Her bir örneğin üyenin tek bir kopyasına sahip olmasını istiyorsanız, üye bildirimi için `Shared` belirtmeyin. Yordam bildiriminden `Shared` anahtar sözcüğünü kaldırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
