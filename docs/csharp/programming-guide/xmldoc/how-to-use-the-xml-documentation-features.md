---
title: XML belgeleri özelliklerini kullanma- C# Programlama Kılavuzu
ms.date: 06/01/2018
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: 57034fb835d4c82b5bf658e61ec78ef226c2551e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789779"
---
# <a name="how-to-use-the-xml-documentation-features"></a>XML belge özelliklerini kullanma

Aşağıdaki örnek, belgelenen bir türe temel bir genel bakış sağlar.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#15)]

Örnek, aşağıdaki içeriklerle bir *. xml* dosyası oluşturur.

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

## <a name="compiling-the-code"></a>Kodu derleme

Örneği derlemek için aşağıdaki komut satırını yazın:

`csc XMLsample.cs /doc:XMLsample.xml`

Bu komut, tarayıcınızda görüntüleyebileceğiniz veya TYPE komutunu kullanarak *XMLsample. XML*XML dosyasını oluşturur.

## <a name="robust-programming"></a>Güçlü programlama

XML belgeleri///ile başlar. Yeni bir proje oluşturduğunuzda, sihirbazlar sizin için bazı başlangıç//satır satırları koyar. Bu yorumların işlenmesinde bazı kısıtlamalar vardır:

- Belgeler düzgün biçimlendirilmiş XML olmalıdır. XML doğru biçimlendirilmediyse bir uyarı oluşturulur ve belge dosyası bir hata ile karşılaşıldığını bildiren bir açıklama içerir.

- Geliştiriciler kendi etiket kümesini oluşturmak ücretsizdir. [Önerilen bir etiket kümesi](recommended-tags-for-documentation-comments.md)vardır. Önerilen etiketlerden bazılarının özel anlamları vardır:

  - Parametreleri anlatmak için \<param > etiketi kullanılır. Kullanıldıysa, derleyici parametrenin var olduğunu ve tüm parametrelerin belgelerde açıklandığını doğrular. Doğrulama başarısız olursa, derleyici bir uyarı verir.

  - `cref` özniteliği, bir kod öğesine başvuru sağlamak için herhangi bir etikete iliştirilebilir. Derleyici bu kod öğesinin varolduğunu doğrular. Doğrulama başarısız olursa, derleyici bir uyarı verir. Derleyici, `cref` özniteliğinde açıklanan bir türü ararken tüm `using` deyimlerini uyar.

  - \<Summary > etiketi, Visual Studio içinde IntelliSense tarafından bir tür veya üyeyle ilgili ek bilgileri göstermek için kullanılır.

    > [!NOTE]
    > XML dosyası, tür ve Üyeler hakkında tam bilgi sağlamaz (örneğin, herhangi bir tür bilgisi içermez). Bir tür veya üye hakkında tam bilgi almak için, belge dosyasının gerçek tür veya üye üzerinde yansıma ile birlikte kullanılması gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [C#Programlama Kılavuzu](../index.md)
- [-Doc (C# derleyici seçenekleri)](../../language-reference/compiler-options/doc-compiler-option.md)
- [XML belge açıklamaları](./index.md)
- [DocFX belge işlemcisi](https://dotnet.github.io/docfx/)
- [Sandrole belge işlemcisi](https://github.com/EWSoftware/SHFB)
