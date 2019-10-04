---
title: 'Nasıl yapılır: XML belgeleri özelliklerini kullanma- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 06/01/2018
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: 06b0c3b7877337d8a5703403af98dbacdf3ea93c
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834170"
---
# <a name="how-to-use-the-xml-documentation-features"></a><span data-ttu-id="a6fb8-102">Nasıl yapılır: XML belgeleri özelliklerini kullanma</span><span class="sxs-lookup"><span data-stu-id="a6fb8-102">How to: Use the XML documentation features</span></span>

<span data-ttu-id="a6fb8-103">Aşağıdaki örnek, belgelenen bir türe temel bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6fb8-103">The following sample provides a basic overview of a type that has been documented.</span></span>

## <a name="example"></a><span data-ttu-id="a6fb8-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a6fb8-104">Example</span></span>

[!code-csharp[csProgGuideDocComments#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#15)]

<span data-ttu-id="a6fb8-105">Örnek, aşağıdaki içeriklerle bir. xml dosyası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="a6fb8-105">The example generates an .xml file with the following contents:</span></span>

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

## <a name="compiling-the-code"></a><span data-ttu-id="a6fb8-106">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="a6fb8-106">Compiling the code</span></span>

<span data-ttu-id="a6fb8-107">Örneği derlemek için aşağıdaki komut satırını yazın:</span><span class="sxs-lookup"><span data-stu-id="a6fb8-107">To compile the example, type the following command line:</span></span>

`csc XMLsample.cs /doc:XMLsample.xml`

<span data-ttu-id="a6fb8-108">Bu komut, tarayıcınızda görüntüleyebileceğiniz veya TYPE komutunu kullanarak *XMLsample. XML*XML dosyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a6fb8-108">This command creates the XML file *XMLsample.xml*, which you can view in your browser or by using the TYPE command.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="a6fb8-109">Güçlü programlama</span><span class="sxs-lookup"><span data-stu-id="a6fb8-109">Robust programming</span></span>

<span data-ttu-id="a6fb8-110">XML belgeleri///ile başlar.</span><span class="sxs-lookup"><span data-stu-id="a6fb8-110">XML documentation starts with ///.</span></span> <span data-ttu-id="a6fb8-111">Yeni bir proje oluşturduğunuzda, sihirbazlar sizin için bazı başlangıç//satır satırları koyar.</span><span class="sxs-lookup"><span data-stu-id="a6fb8-111">When you create a new project, the wizards put some starter /// lines in for you.</span></span> <span data-ttu-id="a6fb8-112">Bu yorumların işlenmesinde bazı kısıtlamalar vardır:</span><span class="sxs-lookup"><span data-stu-id="a6fb8-112">The processing of these comments has some restrictions:</span></span>

- <span data-ttu-id="a6fb8-113">Belgeler düzgün biçimlendirilmiş XML olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a6fb8-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="a6fb8-114">XML doğru biçimlendirilmediyse bir uyarı oluşturulur ve belge dosyası bir hata ile karşılaşıldığını bildiren bir açıklama içerir.</span><span class="sxs-lookup"><span data-stu-id="a6fb8-114">If the XML is not well-formed, a warning is generated and the documentation file will contain a comment that says that an error was encountered.</span></span>

- <span data-ttu-id="a6fb8-115">Geliştiriciler kendi etiket kümesini oluşturmak ücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="a6fb8-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="a6fb8-116">Önerilen bir etiket kümesi vardır ( [belge açıklamaları Için önerilen etiketlere](recommended-tags-for-documentation-comments.md)bakın).</span><span class="sxs-lookup"><span data-stu-id="a6fb8-116">There is a recommended set of tags (see [Recommended tags for documentation comments](recommended-tags-for-documentation-comments.md)).</span></span> <span data-ttu-id="a6fb8-117">Önerilen etiketlerden bazılarının özel anlamları vardır:</span><span class="sxs-lookup"><span data-stu-id="a6fb8-117">Some of the recommended tags have special meanings:</span></span>

  - <span data-ttu-id="a6fb8-118">@No__t-0param > etiketi parametreleri tanımlamakta kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a6fb8-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="a6fb8-119">Kullanıldıysa, derleyici parametrenin var olduğunu ve tüm parametrelerin belgelerde açıklandığını doğrular.</span><span class="sxs-lookup"><span data-stu-id="a6fb8-119">If used, the compiler verifies that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="a6fb8-120">Doğrulama başarısız olursa, derleyici bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="a6fb8-120">If the verification failed, the compiler issues a warning.</span></span>

  - <span data-ttu-id="a6fb8-121">@No__t-0 özniteliği, bir kod öğesine başvuru sağlamak için herhangi bir etikete iliştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a6fb8-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="a6fb8-122">Derleyici bu kod öğesinin varolduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="a6fb8-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="a6fb8-123">Doğrulama başarısız olursa, derleyici bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="a6fb8-123">If the verification failed, the compiler issues a warning.</span></span> <span data-ttu-id="a6fb8-124">Derleyici, `cref` özniteliğinde açıklanan bir türü ararken her bir `using` deyimi uyar.</span><span class="sxs-lookup"><span data-stu-id="a6fb8-124">The compiler respects any `using` statements when it looks for a type described in the `cref` attribute.</span></span>

  - <span data-ttu-id="a6fb8-125">@No__t-0summary > etiketi, Visual Studio içinde IntelliSense tarafından bir tür veya üyeyle ilgili ek bilgileri göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a6fb8-125">The \<summary> tag is used by IntelliSense inside Visual Studio to display additional information about a type or member.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a6fb8-126">XML dosyası, tür ve Üyeler hakkında tam bilgi sağlamaz (örneğin, herhangi bir tür bilgisi içermez).</span><span class="sxs-lookup"><span data-stu-id="a6fb8-126">The XML file does not provide full information about the type and members (for example, it does not contain any type information).</span></span> <span data-ttu-id="a6fb8-127">Bir tür veya üye hakkında tam bilgi almak için, belge dosyasının gerçek tür veya üye üzerinde yansıma ile birlikte kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a6fb8-127">To get full information about a type or member, the documentation file must be used together with reflection on the actual type or member.</span></span>

## <a name="see-also"></a><span data-ttu-id="a6fb8-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6fb8-128">See also</span></span>

- [<span data-ttu-id="a6fb8-129">C#Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a6fb8-129">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a6fb8-130">/Doc (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="a6fb8-130">/doc (C# Compiler Options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="a6fb8-131">XML belge açıklamaları</span><span class="sxs-lookup"><span data-stu-id="a6fb8-131">XML Documentation Comments</span></span>](./index.md)
- [<span data-ttu-id="a6fb8-132">DocFX belge işlemcisi</span><span class="sxs-lookup"><span data-stu-id="a6fb8-132">DocFX documentation processor</span></span>](https://dotnet.github.io/docfx/)
- [<span data-ttu-id="a6fb8-133">Sandrole belge işlemcisi</span><span class="sxs-lookup"><span data-stu-id="a6fb8-133">Sandcastle documentation processor</span></span>](https://github.com/EWSoftware/SHFB)
