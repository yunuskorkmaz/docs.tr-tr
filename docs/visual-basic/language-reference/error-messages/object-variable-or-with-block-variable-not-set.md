---
title: Nesne değişkeni veya With bloğu değişkeni ayarlanmamış
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: 07c215d373e4ac1cbadf82a48b8cb3d90efdbdb4
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040554"
---
# <a name="object-variable-or-with-block-variable-not-set"></a>Nesne değişkeni veya With bloğu değişkeni ayarlanmamış
Geçersiz bir nesne değişkenine başvuruluyor.   Bu hata, birkaç nedenden dolayı oluşabilir:

- Bir değişken, bir tür belirtilmeden bildirildi. Bir değişken bir tür belirtilmeden bildirilirse, varsayılan olarak yazın `Object`.

    Örneğin `Dim x` , ile `Object;` tanımlanan bir değişken, `String`ile `Dim x As String` tanımlanan bir değişken türünde olacaktır.

    > [!TIP]
    > İfade `Option Strict` , bir `Object` tür ile sonuçlanan örtük yazmaya izin vermez. Türü atlarsanız, bir derleme zamanı hatası oluşur. Bkz. [Option Strict deyimdir](../../../visual-basic/language-reference/statements/option-strict-statement.md).

- Olarak `Nothing`ayarlanmış bir nesneye başvurmaya çalışıyorsunuz.

- Düzgün şekilde bildirilmeyen bir dizi değişkeninin öğesine erişmeye çalışıyorsunuz.

    Örneğin, dizi `products(3) = "Widget"`öğesine başvuru yapmayı denerseniz `products() As String` , olarak tanımlanan bir dizi hatayı tetikler. Dizide hiç öğe yok ve bir nesne olarak değerlendirildi.

- Blok başlatılmadan önce bir `With...End With` blok içindeki koda erişmeye çalışıyorsunuz.   Bir `With...End With` blok, `With` ifade giriş noktası yürütülerek başlatılmalıdır.

> [!NOTE]
> Visual Basic veya VBA 'nın önceki sürümlerinde bu hata, `Set` anahtar sözcüğü kullanılmadan bir değişkene bir değer atanarak da tetikleniyor (`x = "name"` yerine `Set x = "name"`). `Set` Anahtar sözcüğü artık Visual Basic .NET içinde geçerli değildir.

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. Aşağıdaki `Option Strict` kodu `On` dosyanın başlangıcına ekleyerek olarak ayarlayın:

    ```vb
    Option Strict On
    ```

    Projeyi çalıştırdığınızda, bir tür olmadan belirtilen herhangi bir değişken için **hata listesi** bir derleyici hatası görüntülenir.

2. Etkinleştirmek `Option Strict`istemiyorsanız, kodunuzda bir tür olmadan belirtilen herhangi bir değişken (`Dim x` yerine `Dim x As String`) arayın ve hedeflenen türü bildirime ekleyin.

3. Olarak `Nothing`ayarlanmış bir nesne değişkenine başvurmadığından emin olun.  Anahtar sözcüğü `Nothing`için kodunuzda arama yapın ve bu nesnenin, başvurulduktan sonra olarak ayarlanmaması için `Nothing` kodunuzu düzeltin.

4. Herhangi bir dizi değişkeninin, erişmeden önce boyutlanır olduğundan emin olun. İlk olarak diziyi oluştururken bir boyut atayabilir (`Dim x(5) As String` `Dim x() As String`yerine `ReDim` ) veya ilk kez erişmeden önce dizinin boyutlarını ayarlamak için anahtar sözcüğünü kullanabilirsiniz.

5. `With` Deyiminizin `With` giriş noktasını yürüterek blobunun başlatıldığından emin olun.

## <a name="see-also"></a>Ayrıca bkz.

- [Nesne Değişken Bildirimi](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [ReDim Deyimi](../../../visual-basic/language-reference/statements/redim-statement.md)
- [With...End With Deyimi](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
