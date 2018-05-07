---
title: Nesne değişkeni veya With bloğu değişkeni ayarlanmamış
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: b2bd1be83f57dbdc7a64b407dc1052074e19c74b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="object-variable-or-with-block-variable-not-set"></a>Nesne değişkeni veya With bloğu değişkeni ayarlanmamış
Geçersiz nesne değişkeni başvuruluyor.   Bu hata, çeşitli nedenlerle oluşabilir:  
  
-   Bir değişken türü belirtmeden bildirildi. Bir değişken türü belirtmeden bildirilirse türü için varsayılan `Object`.  
  
     Örneğin, ile bildirilen bir değişken `Dim x` türü olacaktır `Object;` ile bildirilen bir değişken `Dim x As String` türü olacaktır `String`.  
  
    > [!TIP]
    >  `Option Strict` Deyimi izin vermez sonuçlanır örtük yazarak bir `Object` türü. Türü atlarsanız, derleme zamanı hatası meydana gelir. Bkz: [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
-   Ayarlanmış bir nesneye başvurmak çalışıyorsunuz `Nothing`  
  
     biçimindeki telefon numarasıdır.  
  
-   Bir öğe düzgün bildirilen değildi bir dizi değişkeni erişmeye çalışıyorsunuz.  
  
     Örneğin, bir dizi olarak bildirilen `products() As String` dizinin bir öğeye başvuru denerseniz hata tetikleyecek `products(3) = "Widget"`. Dizi öğe var ve bir nesne olarak kabul edilir.  
  
-   Erişim kodu içinde çalıştığınız bir `With...End With` blok başlatıldı önce engeller.   A `With...End With` blok yürüterek başlatılmalı `With` deyimi giriş noktası.  
  
> [!NOTE]
>  Visual Basic veya VBA önceki sürümlerinde bu hata ayrıca kullanmadan bir değişkene bir değer atayarak tetiklendi `Set` anahtar sözcüğü (`x = "name"` yerine `Set x = "name"`). `Set` Anahtar sözcüğü artık Visual Basic .net içinde geçerli değil.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Ayarlama `Option Strict` için `On` dosyanın başına aşağıdaki kodu ekleyerek:  
  
```vb  
Option Strict On  
```  

     When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.  
  
2.  Etkinleştirmek istemiyorsanız, `Option Strict`, kodunuzu olmadan türü belirtilmiş herhangi bir değişkeni için arama (`Dim x` yerine `Dim x As String`) ve amaçlanan türü bildirimini ekleyin.  
  
3.  Ayarlanmış olan bir nesne değişkeni için başvuran olmayan emin `Nothing`.  Kodunuz için anahtar sözcüğü arama `Nothing`ve nesne ayarlanmamış kodunuzu düzeltmeniz `Nothing` sonra gösterdiğiniz kadar.  
  
4.  Bunlara erişim önce herhangi bir dizi değişkeni dimensioned emin olun. Dizinin ilk oluşturduğunuzda, bir boyut ya da atayabilirsiniz (`Dim x(5) As String` yerine `Dim x() As String`), veya `ReDim` ilk erişebilmesi dizi boyutları ayarlamak için anahtar sözcüğü.  
  
5.  Emin olun, `With` blok yürüterek başlatılır `With` deyimi giriş noktası.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nesne Değişken Bildirimi](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [ReDim Deyimi](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [With...End With Deyimi](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
