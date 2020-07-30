---
title: XML belge özelliklerini kullanma-C# Programlama Kılavuzu
description: XML belge özelliklerini kullanmayı öğrenin. Kod örneklerine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 06/01/2018
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: 9ad2cfe62c70174eec9020ad4c8ce11608aca36d
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380676"
---
# <a name="how-to-use-the-xml-documentation-features"></a><span data-ttu-id="dfa86-104">XML belge özelliklerini kullanma</span><span class="sxs-lookup"><span data-stu-id="dfa86-104">How to use the XML documentation features</span></span>

<span data-ttu-id="dfa86-105">Aşağıdaki örnek, belgelenen bir türe temel bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="dfa86-105">The following sample provides a basic overview of a type that has been documented.</span></span>

## <a name="example"></a><span data-ttu-id="dfa86-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="dfa86-106">Example</span></span>

[!code-csharp[csProgGuideDocComments#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#15)]

<span data-ttu-id="dfa86-107">Örnek, aşağıdaki içeriklerle bir *. xml* dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dfa86-107">The example generates an *.xml* file with the following contents.</span></span>

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

## <a name="compiling-the-code"></a><span data-ttu-id="dfa86-108">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="dfa86-108">Compiling the code</span></span>

<span data-ttu-id="dfa86-109">Örneği derlemek için aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="dfa86-109">To compile the example, enter the following command:</span></span>

`csc XMLsample.cs /doc:XMLsample.xml`

<span data-ttu-id="dfa86-110">Bu komut, tarayıcınızda görüntüleyebileceğiniz veya komutunu kullanarak *XMLsample.xml*XML dosyası oluşturur `TYPE` .</span><span class="sxs-lookup"><span data-stu-id="dfa86-110">This command creates the XML file *XMLsample.xml*, which you can view in your browser or by using the `TYPE` command.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="dfa86-111">Güçlü programlama</span><span class="sxs-lookup"><span data-stu-id="dfa86-111">Robust programming</span></span>

<span data-ttu-id="dfa86-112">XML belgeleri ile başlar `///` .</span><span class="sxs-lookup"><span data-stu-id="dfa86-112">XML documentation starts with `///`.</span></span> <span data-ttu-id="dfa86-113">Yeni bir proje oluşturduğunuzda, sihirbazlar sizin için bazı başlangıç satırları koyar `///` .</span><span class="sxs-lookup"><span data-stu-id="dfa86-113">When you create a new project, the wizards put some starter `///` lines in for you.</span></span> <span data-ttu-id="dfa86-114">Bu yorumların işlenmesinde bazı kısıtlamalar vardır:</span><span class="sxs-lookup"><span data-stu-id="dfa86-114">The processing of these comments has some restrictions:</span></span>

- <span data-ttu-id="dfa86-115">Belgeler düzgün biçimlendirilmiş XML olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dfa86-115">The documentation must be well-formed XML.</span></span> <span data-ttu-id="dfa86-116">XML doğru biçimlendirilmediyse bir uyarı oluşturulur ve belge dosyası bir hata ile karşılaşıldığını bildiren bir açıklama içerir.</span><span class="sxs-lookup"><span data-stu-id="dfa86-116">If the XML is not well-formed, a warning is generated and the documentation file will contain a comment that says that an error was encountered.</span></span>

- <span data-ttu-id="dfa86-117">Geliştiriciler kendi etiket kümesini oluşturmak ücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="dfa86-117">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="dfa86-118">[Önerilen bir etiket kümesi](recommended-tags-for-documentation-comments.md)vardır.</span><span class="sxs-lookup"><span data-stu-id="dfa86-118">There is a [recommended set of tags](recommended-tags-for-documentation-comments.md).</span></span> <span data-ttu-id="dfa86-119">Önerilen etiketlerden bazılarının özel anlamları vardır:</span><span class="sxs-lookup"><span data-stu-id="dfa86-119">Some of the recommended tags have special meanings:</span></span>

  - <span data-ttu-id="dfa86-120">`<param>`Etiketi, parametreleri tanımlamakta kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dfa86-120">The `<param>` tag is used to describe parameters.</span></span> <span data-ttu-id="dfa86-121">Kullanıldıysa, derleyici parametrenin var olduğunu ve tüm parametrelerin belgelerde açıklandığını doğrular.</span><span class="sxs-lookup"><span data-stu-id="dfa86-121">If used, the compiler verifies that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="dfa86-122">Doğrulama başarısız olursa, derleyici bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="dfa86-122">If the verification fails, the compiler issues a warning.</span></span>

  - <span data-ttu-id="dfa86-123">`cref`Özniteliği bir kod öğesine başvurmak için herhangi bir etikete iliştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="dfa86-123">The `cref` attribute can be attached to any tag to reference a code element.</span></span> <span data-ttu-id="dfa86-124">Derleyici bu kod öğesinin varolduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="dfa86-124">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="dfa86-125">Doğrulama başarısız olursa, derleyici bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="dfa86-125">If the verification fails, the compiler issues a warning.</span></span> <span data-ttu-id="dfa86-126">Derleyici, `using` özniteliğinde açıklanan bir türü ararken tüm deyimlere uyar `cref` .</span><span class="sxs-lookup"><span data-stu-id="dfa86-126">The compiler respects any `using` statements when it looks for a type described in the `cref` attribute.</span></span>

  - <span data-ttu-id="dfa86-127">`<summary>`Etiketi, Visual Studio Içinde IntelliSense tarafından bir tür veya üyeyle ilgili ek bilgileri göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dfa86-127">The `<summary>` tag is used by IntelliSense inside Visual Studio to display additional information about a type or member.</span></span>

    > [!NOTE]
    > <span data-ttu-id="dfa86-128">XML dosyası, tür ve Üyeler hakkında tam bilgi sağlamaz (örneğin, herhangi bir tür bilgisi içermez).</span><span class="sxs-lookup"><span data-stu-id="dfa86-128">The XML file does not provide full information about the type and members (for example, it does not contain any type information).</span></span> <span data-ttu-id="dfa86-129">Bir tür veya üye hakkında tam bilgi almak için, gerçek tür veya üyede yansıma ile birlikte belge dosyasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="dfa86-129">To get full information about a type or member, use the documentation file together with reflection on the actual type or member.</span></span>

## <a name="see-also"></a><span data-ttu-id="dfa86-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dfa86-130">See also</span></span>

- [<span data-ttu-id="dfa86-131">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="dfa86-131">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="dfa86-132">-Doc (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="dfa86-132">-doc (C# compiler options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="dfa86-133">XML belgeleri yorumları</span><span class="sxs-lookup"><span data-stu-id="dfa86-133">XML documentation comments</span></span>](./index.md)
- [<span data-ttu-id="dfa86-134">DocFX belge işlemcisi</span><span class="sxs-lookup"><span data-stu-id="dfa86-134">DocFX documentation processor</span></span>](https://dotnet.github.io/docfx/)
- [<span data-ttu-id="dfa86-135">Sandrole belge işlemcisi</span><span class="sxs-lookup"><span data-stu-id="dfa86-135">Sandcastle documentation processor</span></span>](https://github.com/EWSoftware/SHFB)
