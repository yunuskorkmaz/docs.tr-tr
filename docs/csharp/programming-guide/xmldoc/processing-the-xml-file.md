---
title: XML dosyasının işlenmesi - C# programlama kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- XML processing [C#]
- XML [C#], processing
ms.assetid: 60c71193-9dac-4cd3-98c5-100bd0edcc42
ms.openlocfilehash: bc72cade9ce6edddb88d741a3424405bba0a7ad8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793387"
---
# <a name="processing-the-xml-file-c-programming-guide"></a>XML dosyasını işleme (C# programlama kılavuzu)

Derleyici, kodunuzda belge oluşturmak için etiketlenen her yapı için bir kimlik dizesi oluşturur. (Kodunuzu nasıl etiketleyecekleriniz hakkında bilgi [için, Belge Yorumları için Önerilen Etiketler'e](./recommended-tags-for-documentation-comments.md)bakın.) Kimlik dizesi, yapıyı benzersiz olarak tanımlar. XML dosyasını işleyen programlar, belgelerin uygulandığı karşılık gelen .NET Framework meta veri/yansıtma öğesini tanımlamak için kimlik dizesini kullanabilir.

XML dosyası kodunuzu hiyerarşik bir gösterim değildir; her öğe için oluşturulmuş bir kimliği olan düz bir listedir.

Derleyici, kimlik dizelerini oluştururken aşağıdaki kuralları gözlemler:

- Dizede beyaz boşluk yok.

- Kimlik dizesinin ilk bölümü, tek bir karakter ve ardından bir üst üste gelen üye türünü tanımlar. Aşağıdaki üye türleri kullanılır:

    |Karakter|Açıklama|
    |---------------|-----------------|
    |N|ad alanı<br /><br /> Bir ad alanına belge açıklamaları ekleyemezsiniz, ancak desteklenen yerlerde bunlara cref başvuruları yapabilirsiniz.|
    |T|türü: sınıf, arayüz, struct, enum veya temsilci|
    |F|alan|
    |P|özelliği (dizin leyiciler veya diğer dizine eklenmiş özellikler dahil)|
    |M|yöntemi (yapıcılar, işleçler ve benzeri özel yöntemler dahil)|
    |E|event|
    |!|hata dizesi<br /><br /> Dize geri kalanı hata hakkında bilgi sağlar. C# derleyicisi çözülemeyen bağlantılar için hata bilgileri oluşturur.|

- Dize ikinci bölümü, ad alanının kökünden başlayarak öğenin tam nitelikli adıdır. Öğenin adı, çevreleyen türü(ler) ve ad alanı dönemlere göre ayrılır. Öğenin adının dönemleri varsa, bunlar karma işareti ('#') ile değiştirilir. Hiçbir öğenin doğrudan adına bir karma işareti olduğu varsayılır. Örneğin, String oluşturucutam nitelikli adı "System.String.#ctor" olacaktır.

- Özellikler ve yöntemler için, yönteme bağımsız değişkenler varsa, parantez içinde ekteki bağımsız değişken listesi aşağıdaki gibidir. Bağımsız değişken yoksa, parantez yok. Bağımsız değişkenler virgülle ayrılır. Her bağımsız değişkenin kodlanması doğrudan nasıl bir .NET Framework imzasında kodlanır aşağıdaki gibidir:

  - Taban türleri. Normal türler (ELEMENT_TYPE_CLASS veya ELEMENT_TYPE_VALUETYPE) türün tam nitelikli adı olarak temsil edilir.

  - İçsel türler (örneğin, ELEMENT_TYPE_I4, ELEMENT_TYPE_OBJECT, ELEMENT_TYPE_STRING, ELEMENT_TYPE_TYPEDBYREF ve ELEMENT_TYPE_VOID) ilgili tam türün tam nitelikli adı olarak temsil edilir. Örneğin, System.Int32 veya System.TypedReference.

  - ELEMENT_TYPE_PTR, değiştirilen türden\*sonra ' ' olarak temsil edilir.

  - ELEMENT_TYPE_BYREF, değiştirilen türden\@sonra ' ' olarak temsil edilir.

  - ELEMENT_TYPE_PINNED, değiştirilen türü izleyen bir '^' olarak temsil edilir. C# derleyicisi bunu asla üretmez.

  - ELEMENT_TYPE_CMOD_REQ, değiştirilen türü izleyen bir '&#124;' ve değiştirici sınıfın tam nitelikli adı olarak temsil edilir. C# derleyicisi bunu asla üretmez.

  - ELEMENT_TYPE_CMOD_OPT, değiştirilen türü izleyerek bir '!' ve değiştirici sınıfın tam nitelikli adı olarak temsil edilir.

  - ELEMENT_TYPE_SZARRAY, dizinin öğe türünü izleyen "[]" olarak temsil edilir.

  - ELEMENT_TYPE_GENERICARRAY, dizinin öğe türünü izleyen "[?]" olarak temsil edilir. C# derleyicisi bunu asla üretmez.

  - ELEMENT_TYPE_ARRAY , [*lowerbound*`size`: ,`size`*lowerbound*: ] virgül sayısının sıralama - 1 olduğu ve biliniyorsa her boyutun alt sınırları ve boyutuonda ondalık olarak temsil edilir. Daha düşük bir sınır veya boyut belirtilmemişse, yalnızca atlanır. Belirli bir boyutun alt sınırı ve boyutu atlanırsa, ':' de atlanır. Örneğin, alt sınırlar ve belirtilmemiş boyutlar olarak 1'li 2 boyutlu bir dizi [1:,1:]' dir.

  - ELEMENT_TYPE_FNPTR "=FUNC:`type`(*imza*)" olarak `type` temsil edilir, iade türü nerededir ve *imza* yöntemin bağımsız değişkenleridir. Bağımsız değişken yoksa, parantezler atlanır. C# derleyicisi bunu asla üretmez.

    Aşırı yüklenen yöntemleri ayırt etmek için hiçbir zaman kullanılmadığından, aşağıdaki imza bileşenleri temsil edilmez:

  - çağırma sözleşmesi

  - dönüş türü

  - ELEMENT_TYPE_SENTINEL

- Yalnızca dönüşüm işleçleri için (op_Implicit ve op_Explicit), yöntemin iade değeri yukarıda kodlanmış olarak '~' olarak kodlanır ve ardından iade türü kodlanır.

- Genel türler için, türün adı bir backtick ve ardından genel tür parametrelerinin sayısını gösteren bir sayı tarafından izlenir. Örnek:

     ``<member name="T:SampleClass`2">``olarak tanımlanan bir tür için `public class SampleClass<T, U>`etikettir.

     Genel türleri parametre olarak alan yöntemler için, genel tür parametreleri backticks \`\`(örneğin 0, 1) ile prefaced sayılar olarak belirtilir. Türün genel parametreleri için sıfır tabanlı dizi gösterimini temsil eden her sayı.

## <a name="examples"></a>Örnekler

Aşağıdaki örnekler, bir sınıfın kimlik dizelerinin ve üyelerinin nasıl oluşturulacağını gösterir:

[!code-csharp[csProgGuidePointers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#21)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../index.md)
- [-doc (C# derleyici seçenekleri)](../../language-reference/compiler-options/doc-compiler-option.md)
- [XML belgeleri yorumları](./index.md)
