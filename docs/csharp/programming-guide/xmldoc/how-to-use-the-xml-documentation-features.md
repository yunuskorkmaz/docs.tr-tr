---
title: XML dokümantasyon özellikleri nasıl kullanılır - C# programlama kılavuzu
ms.date: 06/01/2018
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: e279b13d9216120e25f454faa14dc71ad24c74ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157006"
---
# <a name="how-to-use-the-xml-documentation-features"></a>XML belge özelliklerini kullanma

Aşağıdaki örnek, belgelenmiş bir türün temel bir genel görünümünü sağlar.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#15)]

Örnek, aşağıdaki içeriği içeren bir *.xml* dosyası oluşturur.

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

Örneği derlemek için aşağıdaki komut satırını yazın:

`csc XMLsample.cs /doc:XMLsample.xml`

Bu komut, tarayıcınızda veya TYPE komutunu kullanarak görüntüleyebileceğiniz XML dosyasını *XMLsample.xml*oluşturur.

## <a name="robust-programming"></a>Sağlam programlama

XML belgeleri ile başlar /. Yeni bir proje oluşturduğunuzda, sihirbazlar sizin için bazı başlangıç / satırlar koyar. Bu yorumların işlenmesi bazı kısıtlamalar vardır:

- Belgeler iyi biçimlendirilmiş XML olmalıdır. XML iyi oluşturulmadıysa, bir uyarı oluşturulur ve belge dosyasında bir hatayla karşılaşıldığını belirten bir yorum bulunur.

- Geliştiriciler kendi etiket kümelerini oluşturmakta özgürler. Önerilen bir [etiket kümesi](recommended-tags-for-documentation-comments.md)vardır. Önerilen etiketlerden bazılarının özel anlamları vardır:

  - \<Param> etiketi parametreleri tanımlamak için kullanılır. Kullanılırsa, derleyici parametrenin var olduğunu ve tüm parametrelerin belgelerde açıklandığını doğrular. Doğrulama başarısız olduysa, derleyici bir uyarı yayınlar.

  - Öznitelik, `cref` bir kod öğesine başvuru sağlamak için herhangi bir etikete eklenebilir. Derleyici bu kod öğesinin var olduğunu doğrular. Doğrulama başarısız olduysa, derleyici bir uyarı yayınlar. Derleyici öznitelik `using` açıklanan `cref` bir tür arar zaman herhangi bir deyimler saygı duyar.

  - Özet \<> etiketi, Visual Studio içinde IntelliSense tarafından bir tür veya üye hakkında ek bilgi görüntülemek için kullanılır.

    > [!NOTE]
    > XML dosyası türü ve üyeleri hakkında tam bilgi sağlamaz (örneğin, herhangi bir tür bilgisi içermez). Bir tür veya üye hakkında tam bilgi almak için, belge dosyası gerçek tür veya üye yansıması ile birlikte kullanılmalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../index.md)
- [-doc (C# derleyici seçenekleri)](../../language-reference/compiler-options/doc-compiler-option.md)
- [XML belgeleri yorumları](./index.md)
- [DocFX dokümantasyon işlemcisi](https://dotnet.github.io/docfx/)
- [Sandcastle dokümantasyon işlemcisi](https://github.com/EWSoftware/SHFB)
