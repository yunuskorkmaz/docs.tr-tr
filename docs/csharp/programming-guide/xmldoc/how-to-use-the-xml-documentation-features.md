---
title: 'Nasıl yapılır: XML belgeleri özelliklerini (C# programlama Kılavuzu) kullanma'
ms.date: 06/01/2018
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: 48654968e5099164874bae8a00767d12c8fe4582
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45514452"
---
# <a name="how-to-use-the-xml-documentation-features"></a><span data-ttu-id="bfc4f-102">Nasıl yapılır: XML belgeleri özelliklerini kullanma</span><span class="sxs-lookup"><span data-stu-id="bfc4f-102">How to: Use the XML documentation features</span></span>

<span data-ttu-id="bfc4f-103">Aşağıdaki örnek, belgelenmiş bir türü temel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="bfc4f-103">The following sample provides a basic overview of a type that has been documented.</span></span>

## <a name="example"></a><span data-ttu-id="bfc4f-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="bfc4f-104">Example</span></span>

[!code-csharp[csProgGuideDocComments#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#15)]

<span data-ttu-id="bfc4f-105">Örneğin, aşağıdaki içeriğe sahip bir .xml dosyası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="bfc4f-105">The example generates an .xml file with the following contents:</span></span>

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

## <a name="compiling-the-code"></a><span data-ttu-id="bfc4f-106">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="bfc4f-106">Compiling the code</span></span>

<span data-ttu-id="bfc4f-107">Örneği derlemek için aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="bfc4f-107">To compile the example, type the following command line:</span></span>

`csc XMLsample.cs /doc:XMLsample.xml`

<span data-ttu-id="bfc4f-108">Bu komut XML dosyasını oluşturur *XMLsample.xml*, tarayıcınızda veya türü komutunu kullanarak görüntüleyebileceğiniz.</span><span class="sxs-lookup"><span data-stu-id="bfc4f-108">This command creates the XML file *XMLsample.xml*, which you can view in your browser or by using the TYPE command.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="bfc4f-109">Güçlü programlama</span><span class="sxs-lookup"><span data-stu-id="bfc4f-109">Robust programming</span></span>

<span data-ttu-id="bfc4f-110">XML belgeleri başlar: / / / ile.</span><span class="sxs-lookup"><span data-stu-id="bfc4f-110">XML documentation starts with ///.</span></span> <span data-ttu-id="bfc4f-111">Yeni bir proje oluşturduğunuzda, sihirbaz sizin için bazı başlangıç / / / satırları yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="bfc4f-111">When you create a new project, the wizards put some starter /// lines in for you.</span></span> <span data-ttu-id="bfc4f-112">Bu açıklamalar işlenmesini bazı kısıtlamalar mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="bfc4f-112">The processing of these comments has some restrictions:</span></span>

- <span data-ttu-id="bfc4f-113">Belgeler doğru biçimlendirilmiş XML.</span><span class="sxs-lookup"><span data-stu-id="bfc4f-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="bfc4f-114">Doğru biçimlendirilmiş XML değil, bir uyarı oluşturulur ve soubor dokumentace bir hatayla karşılaşıldı bildiren bir açıklama içerir.</span><span class="sxs-lookup"><span data-stu-id="bfc4f-114">If the XML is not well-formed, a warning is generated and the documentation file will contain a comment that says that an error was encountered.</span></span>

- <span data-ttu-id="bfc4f-115">Geliştiriciler kendi kümesi etiketleri oluşturmak ücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="bfc4f-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="bfc4f-116">Önerilen bir dizi etiketi yoktur (bkz [etiketleri belge açıklamaları için önerilen](recommended-tags-for-documentation-comments.md)).</span><span class="sxs-lookup"><span data-stu-id="bfc4f-116">There is a recommended set of tags (see [Recommended tags for documentation comments](recommended-tags-for-documentation-comments.md)).</span></span> <span data-ttu-id="bfc4f-117">Önerilen etiketler bazıları, özel anlamları vardır:</span><span class="sxs-lookup"><span data-stu-id="bfc4f-117">Some of the recommended tags have special meanings:</span></span>

  - <span data-ttu-id="bfc4f-118">\<Param > etiketi, parametreler tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bfc4f-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="bfc4f-119">Kullandıysanız, derleyici parametresi var olduğundan ve tüm parametreleri belgelerinde açıklanan doğrular.</span><span class="sxs-lookup"><span data-stu-id="bfc4f-119">If used, the compiler verifies that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="bfc4f-120">Doğrulama başarısızsa, derleyici bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="bfc4f-120">If the verification failed, the compiler issues a warning.</span></span>

  - <span data-ttu-id="bfc4f-121">`cref` Öznitelik, bir kod öğesi başvuru sağlamak için herhangi bir etiket eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="bfc4f-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="bfc4f-122">Derleyici, bu kod öğesi var olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="bfc4f-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="bfc4f-123">Doğrulama başarısızsa, derleyici bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="bfc4f-123">If the verification failed, the compiler issues a warning.</span></span> <span data-ttu-id="bfc4f-124">Tüm derleyici uyar `using` içinde tanımlanan bir tür için göründüğünde deyimleri `cref` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="bfc4f-124">The compiler respects any `using` statements when it looks for a type described in the `cref` attribute.</span></span>

  - <span data-ttu-id="bfc4f-125">\<Özet > etiketi IntelliSense Visual Studio içindeki bir tür veya üyeyle ilgili ek bilgileri görüntülemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bfc4f-125">The \<summary> tag is used by IntelliSense inside Visual Studio to display additional information about a type or member.</span></span>

    > [!NOTE]
    > <span data-ttu-id="bfc4f-126">XML dosyası, tür ve üyeler hakkında tam bilgi sağlamaz (örneğin, bunu herhangi bir tür bilgilerini içermiyor).</span><span class="sxs-lookup"><span data-stu-id="bfc4f-126">The XML file does not provide full information about the type and members (for example, it does not contain any type information).</span></span> <span data-ttu-id="bfc4f-127">Bir tür veya üyeyle ilgili eksiksiz bilgi almak için soubor dokumentace gerçek türe veya üyeye yansıma ile birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bfc4f-127">To get full information about a type or member, the documentation file must be used together with reflection on the actual type or member.</span></span>

## <a name="see-also"></a><span data-ttu-id="bfc4f-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bfc4f-128">See Also</span></span>

- [<span data-ttu-id="bfc4f-129">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="bfc4f-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="bfc4f-130">/ doc (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="bfc4f-130">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
- [<span data-ttu-id="bfc4f-131">XML Belge Açıklamaları</span><span class="sxs-lookup"><span data-stu-id="bfc4f-131">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)  
