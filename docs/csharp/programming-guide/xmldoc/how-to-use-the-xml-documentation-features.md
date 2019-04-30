---
title: 'Nasıl yapılır: -XML belgeleri özelliklerini kullanma C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 06/01/2018
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: 893dc726f7b4ee2d2afa69f63d13d1f11a4692db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61708203"
---
# <a name="how-to-use-the-xml-documentation-features"></a>Nasıl yapılır: XML belgeleri özelliklerini kullanma

Aşağıdaki örnek, belgelenmiş bir türü temel bir bakış sağlar.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#15)]

Örneğin, aşağıdaki içeriğe sahip bir .xml dosyası oluşturur:

```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>xmlsample</name>
    </assembly>
    <members>
        <member name="T:TestClass">
            <summary>
            Class level summary documentation goes here.
            </summary>
            <remarks>
            Longer comments can be associated with a type or member through
            the remarks tag.
            </remarks>
        </member>
        <member name="F:TestClass._name">
            <summary>
            Store for the Name property.
            </summary>
        </member>
        <member name="M:TestClass.#ctor">
            <summary>
            The class constructor.
            </summary>
        </member>
        <member name="P:TestClass.Name">
            <summary>
            Name property.
            </summary>
            <value>
            A value tag is used to describe the property value.
            </value>
        </member>
        <member name="M:TestClass.SomeMethod(System.String)">
            <summary>
            Description for SomeMethod.
            </summary>
            <param name="s"> Parameter description for s goes here.</param>
            <seealso cref="T:System.String">
            You can use the cref attribute on any tag to reference a type or member 
            and the compiler will check that the reference exists.
            </seealso>
        </member>
        <member name="M:TestClass.SomeOtherMethod">
            <summary>
            Some other method.
            </summary>
            <returns>
            Return values are described through the returns tag.
            </returns>
            <seealso cref="M:TestClass.SomeMethod(System.String)">
            Notice the use of the cref attribute to reference a specific method.
            </seealso>
        </member>
        <member name="M:TestClass.Main(System.String[])">
            <summary>
            The entry point for the application.
            </summary>
            <param name="args"> A list of command line arguments.</param>
        </member>
        <member name="T:TestInterface">
            <summary>
            Documentation that describes the interface goes here.
            </summary>
            <remarks>
            Details about the interface go here.
            </remarks>
        </member>
        <member name="M:TestInterface.InterfaceMethod(System.Int32)">
            <summary>
            Documentation that describes the method goes here.
            </summary>
            <param name="n">
            Parameter n requires an integer argument.
            </param>
            <returns>
            The method returns an integer.
            </returns>
        </member>
    </members>
</doc>
```

## <a name="compiling-the-code"></a>Kod derleme

Örneği derlemek için aşağıdaki komutu yazın:

`csc XMLsample.cs /doc:XMLsample.xml`

Bu komut XML dosyasını oluşturur *XMLsample.xml*, tarayıcınızda veya türü komutunu kullanarak görüntüleyebileceğiniz.

## <a name="robust-programming"></a>Güçlü programlama

XML belgeleri başlar: / / / ile. Yeni bir proje oluşturduğunuzda, sihirbaz sizin için bazı başlangıç / / / satırları yerleştirin. Bu açıklamalar işlenmesini bazı kısıtlamalar mevcuttur:

- Belgeler doğru biçimlendirilmiş XML. Doğru biçimlendirilmiş XML değil, bir uyarı oluşturulur ve soubor dokumentace bir hatayla karşılaşıldı bildiren bir açıklama içerir.

- Geliştiriciler kendi kümesi etiketleri oluşturmak ücretsizdir. Önerilen bir dizi etiketi yoktur (bkz [etiketleri belge açıklamaları için önerilen](recommended-tags-for-documentation-comments.md)). Önerilen etiketler bazıları, özel anlamları vardır:

  - \<Param > etiketi, parametreler tanımlamak için kullanılır. Kullandıysanız, derleyici parametresi var olduğundan ve tüm parametreleri belgelerinde açıklanan doğrular. Doğrulama başarısızsa, derleyici bir uyarı verir.

  - `cref` Öznitelik, bir kod öğesi başvuru sağlamak için herhangi bir etiket eklenebilir. Derleyici, bu kod öğesi var olduğunu doğrular. Doğrulama başarısızsa, derleyici bir uyarı verir. Tüm derleyici uyar `using` içinde tanımlanan bir tür için göründüğünde deyimleri `cref` özniteliği.

  - \<Özet > etiketi IntelliSense Visual Studio içindeki bir tür veya üyeyle ilgili ek bilgileri görüntülemek için kullanılır.

    > [!NOTE]
    > XML dosyası, tür ve üyeler hakkında tam bilgi sağlamaz (örneğin, bunu herhangi bir tür bilgilerini içermiyor). Bir tür veya üyeyle ilgili eksiksiz bilgi almak için soubor dokumentace gerçek türe veya üyeye yansıma ile birlikte kullanılmalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [/ doc (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)
- [XML Belge Açıklamaları](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
