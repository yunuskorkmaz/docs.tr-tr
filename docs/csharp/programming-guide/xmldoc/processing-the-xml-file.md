---
title: XML dosyası işleme-C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- XML processing [C#]
- XML [C#], processing
ms.assetid: 60c71193-9dac-4cd3-98c5-100bd0edcc42
ms.openlocfilehash: 1e3d96f9398f2c08ed715111f01987e2d1948439
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287265"
---
# <a name="process-the-xml-file-c-programming-guide"></a>XML dosyasını işleme (C# Programlama Kılavuzu)

Derleyici, kodunuzda belge oluşturmak için etiketlenmiş her yapı için bir KIMLIK dizesi oluşturur. (Kodunuzu etiketleme hakkında daha fazla bilgi için bkz. [belge açıklamaları Için önerilen Etiketler](./recommended-tags-for-documentation-comments.md).) KIMLIK dizesi yapıyı benzersiz bir şekilde tanımlar. XML dosyasını işleyen programlar, belgenin uygulandığı ilgili .NET meta verilerini veya yansıma öğesini tanımlamak için KIMLIK dizesini kullanabilir.

## <a name="id-strings"></a>KIMLIK dizeleri

XML dosyası, kodunuzun hiyerarşik bir temsili değildir. Her öğe için oluşturulmuş KIMLIĞI olan düz bir liste.

Derleyici, KIMLIK dizelerini oluşturduğunda aşağıdaki kuralları sunar:

- Dizede boşluk yok.

- Dizenin ilk bölümü, tek bir karakter kullanarak ve sonra iki nokta üst üste gelen üye türünü tanımlar. Aşağıdaki üye türleri kullanılır:

    |Karakter|Üye türü|Notlar|
    |---------------|-----------------|-|
    |N|ad alanı|Bir ad alanına belge açıklamaları ekleyemezsiniz, ancak bu kişilere, desteklenmiş olduğu durumlarda bu başvuruları yapabilirsiniz.|
    |T|tür|Bir tür sınıf, arabirim, yapı, sabit listesi veya temsilci olabilir.|
    |F|alan|
    |P|özellik|Dizin oluşturucular veya diğer dizinli özellikler içerir.|
    |M|method|Oluşturucular ve işleçler gibi özel yöntemleri içerir.|
    |E|event|
    |!|hata dizesi|Dizenin geri kalanı hata hakkında bilgi sağlar. C# derleyicisi, çözümlenemeyen bağlantılar için hata bilgileri oluşturur.|

- Dizenin ikinci bölümü, ad alanının köküden başlayarak öğenin tam nitelikli adıdır. Öğenin adı, kapsayan tür (ler) ve ad alanı noktalarla ayrılır. Öğenin adında nokta varsa, bunlar karma işareti (' # ') ile değiştirilmiştir. Hiçbir öğenin doğrudan adında bir karma işareti olmadığı varsayılır. Örneğin, dize oluşturucusunun tam adı "System. String. #ctor" dir.

- Özellikler ve yöntemler için parantez içine alınmış parametre listesi aşağıda verilmiştir. Hiçbir parametre yoksa, hiçbir parantez yok. Parametreler virgülle ayrılır. Her parametrenin kodlaması, .NET imzasında nasıl kodlandığını doğrudan izler:

  - Temel türler. Normal türler (ELEMENT_TYPE_CLASS veya ELEMENT_TYPE_VALUETYPE), türün tam adı olarak gösterilir.

  - İç türler (örneğin, ELEMENT_TYPE_I4, ELEMENT_TYPE_OBJECT, ELEMENT_TYPE_STRING, ELEMENT_TYPE_TYPEDBYREF ve ELEMENT_TYPE_VOID) karşılık gelen tam türün tam adı olarak gösterilir. Örneğin, System. Int32 veya System. TypedReference.

  - ELEMENT_TYPE_PTR, \* değiştirilen türden sonra ' ' olarak gösterilir.

  - ELEMENT_TYPE_BYREF, \@ değiştirilen türden sonra ' ' olarak gösterilir.

  - ELEMENT_TYPE_PINNED, değiştirilen türden sonra bir ' ^ ' olarak temsil edilir. C# derleyicisi hiçbir şekilde bunu oluşturmaz.

  - ELEMENT_TYPE_CMOD_REQ, değiştirilen türü takip eden bir ' &#124; ' ve değiştirici sınıfının tam adı olarak temsil edilir. C# derleyicisi hiçbir şekilde bunu oluşturmaz.

  - ELEMENT_TYPE_CMOD_OPT, değiştirilen türü takip eden bir '! ' ve değiştirici sınıfının tam adı olarak temsil edilir.

  - ELEMENT_TYPE_SZARRAY, dizinin öğe türü takip eden "[]" olarak temsil edilir.

  - ELEMENT_TYPE_GENERICARRAY, dizinin öğe türü takip eden "[?]" olarak temsil edilir. C# derleyicisi hiçbir şekilde bunu oluşturmaz.

  - Element_type_array,*lowerbound* `size` virgül sayısının derece-1 olduğu ve bilindiğinde her boyutun alt sınırları ve boyutunun ondalık olarak temsil edildiği [küçük harfe göre:, küçük*harf sınırı*:] olarak temsil edilir `size` . Daha düşük bir sınır veya boyut belirtilmemişse, bu atlanır. Belirli bir boyutun alt sınırı ve boyutu atlanırsa, ': ' de atlanır. Örneğin, alt sınır olarak 1 olan 2 boyutlu bir dizi ve belirtilmemiş boyutlar [1:, 1:].

  - ELEMENT_TYPE_FNPTR, `type` *signature* `type` dönüş türü olduğu ve *imza* YÖNTEMIN bağımsız değişkenlerinin olduğu "= Func: (Signature)" olarak temsil edilir. Bağımsız değişken yoksa, parantezler atlanır. C# derleyicisi hiçbir şekilde bunu oluşturmaz.

  Aşağıdaki imza bileşenleri, aşırı yüklenmiş yöntemleri ayırt etmek için kullanılmadığından gösterilmemektedir:

  - çağırma kuralı

  - dönüş türü

  - ELEMENT_TYPE_SENTINEL

- Yalnızca dönüştürme işleçleri için ( `op_Implicit` ve `op_Explicit` ), yöntemin dönüş değeri ' ~ ' ve ardından dönüş türü olarak kodlanır.

- Genel türler için, türün adının ardından bir geri değer ve ardından genel tür parametrelerinin sayısını belirten bir sayı gelmelidir. Örneğin:

     ``<member name="T:SampleClass`2">``, olarak tanımlanan bir türün etikettir `public class SampleClass<T, U>` .

     Genel tür parametreleri parametre olarak alan yöntemler için, (örneğin \` , 0, 1), genel tür parametreleri birlikte bulunan sayılar olarak belirtilir \` . Her sayı, türün genel parametreleri için sıfır tabanlı dizi gösterimini temsil eder.

## <a name="examples"></a>Örnekler

Aşağıdaki örneklerde bir sınıf ve üyeleri için KIMLIK dizelerinin nasıl oluşturulduğu gösterilmektedir:

[!code-csharp[csProgGuidePointers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#21)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../index.md)
- [-Doc (C# derleyici seçenekleri)](../../language-reference/compiler-options/doc-compiler-option.md)
- [XML belgeleri yorumları](./index.md)
