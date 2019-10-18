---
title: XML dosyası- C# programlama kılavuzunu işleme
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML processing [C#]
- XML [C#], processing
ms.assetid: 60c71193-9dac-4cd3-98c5-100bd0edcc42
ms.openlocfilehash: bb713fbc5ddd3737cb629c5c09c25ff2980c73dc
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523382"
---
# <a name="processing-the-xml-file-c-programming-guide"></a>XML Dosyasını İşleme (C# Programlama Kılavuzu)

Derleyici, kodunuzda belge oluşturmak için etiketlenmiş her yapı için bir KIMLIK dizesi oluşturur. (Kodunuzu etiketleme hakkında daha fazla bilgi için bkz. [belge açıklamaları Için önerilen Etiketler](./recommended-tags-for-documentation-comments.md).) KIMLIK dizesi yapıyı benzersiz bir şekilde tanımlar. XML dosyasını işleyen programlar, belgelerin uygulandığı karşılık gelen .NET Framework meta veri/yansıma öğesini tanımlamak için KIMLIK dizesini kullanabilir.

 XML dosyası, kodunuzun hiyerarşik bir temsili değildir; her öğe için oluşturulmuş KIMLIĞI olan düz bir liste.

 Derleyici, KIMLIK dizelerini oluşturduğunda aşağıdaki kuralları sunar:

- Dizede boşluk yok.

- KIMLIK dizesinin ilk bölümü, tanımlanmakta olan üyenin türünü, tek bir karakter ve iki nokta üst üste ile belirler. Aşağıdaki üye türleri kullanılır:

    |Karakter|Açıklama|
    |---------------|-----------------|
    |N|ad alanı<br /><br /> Bir ad alanına belge açıklamaları ekleyemezsiniz, ancak bu kişilere, desteklenmiş olduğu durumlarda bu başvuruları yapabilirsiniz.|
    |T|Tür: Class, Interface, struct, Enum, Delegate|
    |F|alan|
    |P|Özellik (Dizin oluşturucular veya diğer dizinli özellikler dahil)|
    |M|Yöntem (oluşturucular, işleçler ve benzeri özel yöntemler dahil)|
    |E|olay|
    |!|Hata dizesi<br /><br /> Dizenin geri kalanı hata hakkında bilgi sağlar. Derleyici C# , çözümlenemeyen bağlantılar için hata bilgileri oluşturur.|

- Dizenin ikinci bölümü, ad alanının köküden başlayarak öğenin tam nitelikli adıdır. Öğenin adı, kapsayan tür (ler) ve ad alanı noktalarla ayrılır. Öğenin adında nokta varsa, bunlar karma işareti (' # ') ile değiştirilmiştir. Hiçbir öğenin doğrudan adında bir karma işareti olmadığı varsayılır. Örneğin, dize oluşturucusunun tam adı "System. String. #ctor" olacaktır.

- Özellikler ve yöntemler için, yöntem için bağımsız değişkenler varsa, parantez içine alınmış bağımsız değişken listesi aşağıda verilmiştir. Bağımsız değişken yoksa, parantezler yok. Bağımsız değişkenler virgülle ayrılır. Her bağımsız değişkenin kodlaması, .NET Framework imzasında nasıl kodlandığını doğrudan izler:

  - Temel türler. Normal türler (ELEMENT_TYPE_CLASS veya ELEMENT_TYPE_VALUETYPE), türün tam nitelikli adı olarak gösterilir.

  - İç türler (örneğin, ELEMENT_TYPE_I4, ELEMENT_TYPE_OBJECT, ELEMENT_TYPE_STRING, ELEMENT_TYPE_TYPEDBYREF. ve ELEMENT_TYPE_VOID) karşılık gelen tam türün tam adı olarak gösterilir. Örneğin, System. Int32 veya System. TypedReference.

  - ELEMENT_TYPE_PTR, değiştirilen türden sonra bir ' \* ' olarak temsil edilir.

  - ELEMENT_TYPE_BYREF, değiştirilen türden sonra bir ' \@ ' olarak temsil edilir.

  - ELEMENT_TYPE_PINNED, değiştirilen türden sonra bir ' ^ ' olarak temsil edilir. C# Derleyici bunu hiçbir şekilde oluşturmaz.

  - ELEMENT_TYPE_CMOD_REQ, değiştirilen türü takip eden&#124;bir ' ' ve değiştirici sınıfının tam adı olarak temsil edilir. C# Derleyici bunu hiçbir şekilde oluşturmaz.

  - ELEMENT_TYPE_CMOD_OPT, değiştirilen türden sonra bir '! ' ve değiştirici sınıfının tam adı olarak temsil edilir.

  - ELEMENT_TYPE_SZARRAY, dizinin öğe türü takip eden "[]" olarak temsil edilir.

  - ELEMENT_TYPE_GENERICARRAY, dizinin öğe türü takip eden "[?]" olarak temsil edilir. C# Derleyici bunu hiçbir şekilde oluşturmaz.

  - ELEMENT_TYPE_ARRAY, virgül sayısının derece-1 olduğu ve bilinen her boyutun alt sınırları ve boyutunun ondalık olarak temsil edildiği [küçük*harfe*göre: `size`, küçük*harfe*göre: `size`] olarak gösterilir. Daha düşük bir sınır veya boyut belirtilmemişse, bu yalnızca atlanır. Belirli bir boyutun alt sınırı ve boyutu atlanırsa, ': ' de atlanır. Örneğin, alt sınır olarak 1 olan 2 boyutlu bir dizi ve belirtilmemiş boyutlar [1:, 1:].

  - ELEMENT_TYPE_FNPTR, dönüş türü olan ve *imza* yöntemin bağımsız değişkenlerinin olduğu "= FUNC: `type` (*Signature*) `type`" olarak temsil edilir. Bağımsız değişken yoksa, parantezler atlanır. C# Derleyici bunu hiçbir şekilde oluşturmaz.

    Aşağıdaki imza bileşenleri, aşırı yüklenmiş yöntemlerin farklılaştırmaları hiçbir şekilde kullanıldıklarından temsil edilmez:

  - çağırma kuralı

  - Dönüş türü

  - ELEMENT_TYPE_SENTINEL

- Yalnızca dönüştürme işleçleri (op_Implicit ve op_Explicit) için, metodun dönüş değeri, yukarıda kodlanan bir ' ~ ' ve ardından dönüş türü tarafından kodlanır.

- Genel türler için, türün adının ardından bir geri değer ve ardından genel tür parametrelerinin sayısını belirten bir sayı gelmelidir. Örneğin:

     ``<member name="T:SampleClass`2">``, `public class SampleClass<T, U>` olarak tanımlanan bir türün etikettir.

     Genel türleri parametre olarak alan yöntemler için, genel tür parametreleri, geri işaretleri (örneğin \`0, \`1) ile önceden ortaya çıkacak sayılar olarak belirtilir. Türün genel parametreleri için sıfır tabanlı dizi gösterimini temsil eden her bir sayı.

## <a name="examples"></a>Örnekler

Aşağıdaki örneklerde, bir sınıfa ve üyelerine ait KIMLIK dizelerinin nasıl oluşturulacağı gösterilmektedir:

[!code-csharp[csProgGuidePointers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#21)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [-Doc (C# derleyici seçenekleri)](../../language-reference/compiler-options/doc-compiler-option.md)
- [XML Belge Açıklamaları](./index.md)
