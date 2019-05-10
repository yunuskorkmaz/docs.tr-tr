---
title: Nesne değişkeni veya With bloğu değişkeni ayarlanmamış
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: 766b95163f164ec76135b964115069b6855ceebf
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64750681"
---
# <a name="object-variable-or-with-block-variable-not-set"></a>Nesne değişkeni veya With bloğu değişkeni ayarlanmamış
Geçersiz nesne değişkeni başvuruda bulunuyor.   Bu hata, çeşitli nedenlerle oluşabilir:

- Bir tür belirtmeden bir değişken bildirildi. Bir tür belirtmeden bildirilen bir değişken, yazmak için varsayılanları `Object`.

    Örneğin, bildirilen bir değişken `Dim x` türünde olur `Object;` ile bildirilen bir değişken `Dim x As String` türünde olur `String`.

    > [!TIP]
    >  `Option Strict` Deyimi izin vermiyor sonuçlanır örtülü yazma bir `Object` türü. Türü atlarsanız, bir derleme zamanı hatası oluşur. Bkz: [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md).

- Olarak ayarlanan bir nesne başvurmayı denediğiniz `Nothing`.

- Doğru değildi bildirilen bir dizi değişkenini öğesi erişmeye çalışıyorsunuz.

    Örneğin, bir dizi olarak bildirilen `products() As String` dizinin bir öğesine başvurmak denerseniz hata tetikleyecek `products(3) = "Widget"`. Dizinin öğe yok ve bir nesne olarak kabul edilir.

- Erişim kodu içinde çalıştığınız bir `With...End With` blok başlatılmadan önce engelleyin.   A `With...End With` blok yürüterek başlatılmalı `With` deyimi giriş noktası.

> [!NOTE]
> Visual Basic veya VBA önceki sürümlerinde bu hata ayrıca kullanmadan bir değeri bir değişkene atayarak tetiklendi `Set` anahtar sözcüğü (`x = "name"` yerine `Set x = "name"`). `Set` Anahtar sözcüğü artık Visual Basic. NET'te geçerli değil.

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. Ayarlama `Option Strict` için `On` dosyasının başına aşağıdaki kodu ekleyerek:

    ```vb
    Option Strict On
    ```

    Projeyi çalıştırdığınızda, bir derleyici hatası görünür **hata listesi** olmadan bir türü belirtilmiş herhangi bir değişken için.

2. Etkinleştirmek istemiyorsanız `Option Strict`, olmadan bir türü belirtilmiş tüm değişkenler için kodunuzu arama (`Dim x` yerine `Dim x As String`) ve amaçlanan türü bildirimini ekleyin.

3. Olarak ayarlanan bir nesne değişkenine başvuran olmayan emin `Nothing`.  Kodunuz için bir anahtar sözcük arama `Nothing`ve böylece nesnenin belirlendiğinden, kodunuzu gözden geçirme `Nothing` sonra başvurduğunuz kadar.

4. Bunları erişmeden önce herhangi bir dizi değişkeni dimensioned emin olun. Dizinin ilk oluşturduğunuzda, bir boyut ya da atayabilirsiniz (`Dim x(5) As String` yerine `Dim x() As String`), veya `ReDim` ilk erişmeden önce dizinin boyut sayısını ayarlamak için anahtar sözcüğü.

5. Emin olun, `With` blok yürüterek başlatılan `With` deyimi giriş noktası.

## <a name="see-also"></a>Ayrıca bkz.

- [Nesne Değişken Bildirimi](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [ReDim Deyimi](../../../visual-basic/language-reference/statements/redim-statement.md)
- [With...End With Deyimi](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
