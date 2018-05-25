---
title: 'Nasıl yapılır: XML Belgeleri Özelliklerini Kullanma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: d7f1f51040033cf25f7f1aefb04d249e6e028ca3
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2018
---
# <a name="how-to-use-the-xml-documentation-features-c-programming-guide"></a><span data-ttu-id="dfcb3-102">Nasıl yapılır: XML Belgeleri Özelliklerini Kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="dfcb3-102">How to: Use the XML Documentation Features (C# Programming Guide)</span></span>
<span data-ttu-id="dfcb3-103">Aşağıdaki örnek belgelenmiştir bir tür temel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="dfcb3-103">The following sample provides a basic overview of a type that has been documented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfcb3-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="dfcb3-104">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#15](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/how-to-use-the-xml-documentation-features_1.cs)]  

<span data-ttu-id="dfcb3-105">Örneğin, aşağıdaki içeriğe sahip bir .xml dosyası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="dfcb3-105">The example generates an .xml file with the following contents:</span></span>

```xml  
<?xml version="1.0"?>  
<doc>  
 <assembly>  
 <name>xmlsample</name>  
 </assembly>  
 <members>  
 <member name="T:SomeClass">  
 <summary>  
 Class level summary documentation goes here.</summary>  
 <remarks>  
 Longer comments can be associated with a type or member  
 through the remarks tag</remarks>  
 </member>  
 <member name="F:SomeClass.m_Name">  
 <summary>  
 Store for the name property</summary>  
 </member>  
 <member name="M:SomeClass.#ctor">  
 <summary>The class constructor.</summary>  
 </member>  
 <member name="M:SomeClass.SomeMethod(System.String)">  
 <summary>  
 Description for SomeMethod.</summary>  
 <param name="s"> Parameter description for s goes here</param>  
 <seealso cref="T:System.String">  
 You can use the cref attribute on any tag to reference a type or member  
 and the compiler will check that the reference exists. </seealso>  
 </member>  
 <member name="M:SomeClass.SomeOtherMethod">  
 <summary>  
 Some other method. </summary>  
 <returns>  
 Return results are described through the returns tag.</returns>  
 <seealso cref="M:SomeClass.SomeMethod(System.String)">  
 Notice the use of the cref attribute to reference a specific method </seealso>  
 </member>  
 <member name="M:SomeClass.Main(System.String[])">  
 <summary>  
 The entry point for the application.  
 </summary>  
 <param name="args"> A list of command line arguments</param>  
 </member>  
 <member name="P:SomeClass.Name">  
 <summary>  
 Name property </summary>  
 <value>A value tag is used to describe the property value</value>  
 </member>  
 </members>  
</doc>   
```

## <a name="compiling-the-code"></a><span data-ttu-id="dfcb3-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="dfcb3-106">Compiling the Code</span></span>  
 <span data-ttu-id="dfcb3-107">Örnek derlemek için aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="dfcb3-107">To compile the example, type the following command line:</span></span>  
  
 `csc XMLsample.cs /doc:XMLsample.xml`  
  
 <span data-ttu-id="dfcb3-108">Bu TYPE komutunu kullanarak veya tarayıcınızda görüntüleyebilirsiniz XMLsample.xml XML dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dfcb3-108">This will create the XML file XMLsample.xml, which you can view in your browser or by using the TYPE command.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="dfcb3-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="dfcb3-109">Robust Programming</span></span>  
 <span data-ttu-id="dfcb3-110">XML belgeleri başlatır: / / / ile.</span><span class="sxs-lookup"><span data-stu-id="dfcb3-110">XML documentation starts with ///.</span></span> <span data-ttu-id="dfcb3-111">Yeni bir proje oluşturduğunuzda, sihirbazda bazı starter / / / satırları yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="dfcb3-111">When you create a new project, the wizards put some starter /// lines in for you.</span></span> <span data-ttu-id="dfcb3-112">Bu açıklamalar işlenmesini bazı kısıtlamaları vardır:</span><span class="sxs-lookup"><span data-stu-id="dfcb3-112">The processing of these comments has some restrictions:</span></span>  
  
-   <span data-ttu-id="dfcb3-113">Belge doğru biçimlendirilmiş XML.</span><span class="sxs-lookup"><span data-stu-id="dfcb3-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="dfcb3-114">Doğru biçimlendirilmiş XML değil, bir uyarı oluşturulur ve belge dosyası bir hatayla karşılaşıldı belirten bir açıklama içerir.</span><span class="sxs-lookup"><span data-stu-id="dfcb3-114">If the XML is not well-formed, a warning is generated and the documentation file will contain a comment that says that an error was encountered.</span></span>  
  
-   <span data-ttu-id="dfcb3-115">Geliştiriciler kendi etiketleri kümesi oluşturmak boş.</span><span class="sxs-lookup"><span data-stu-id="dfcb3-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="dfcb3-116">Önerilen etiketler birtakım yoktur (bkz [etiketleri belge açıklamaları için önerilen](recommended-tags-for-documentation-comments.md)).</span><span class="sxs-lookup"><span data-stu-id="dfcb3-116">There is a recommended set of tags (see [Recommended tags for documentation comments](recommended-tags-for-documentation-comments.md)).</span></span> <span data-ttu-id="dfcb3-117">Önerilen etiketler bazıları özel anlamlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="dfcb3-117">Some of the recommended tags have special meanings:</span></span>  
  
    -   <span data-ttu-id="dfcb3-118">\<Param > etiketi parametrelerini tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dfcb3-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="dfcb3-119">Kullandıysanız, derleyici parametresi var olduğundan ve tüm parametreleri belgelerinde açıklanan doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="dfcb3-119">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="dfcb3-120">Doğrulama başarısız olursa derleyici bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="dfcb3-120">If the verification failed, the compiler issues a warning.</span></span>  
  
    -   <span data-ttu-id="dfcb3-121">`cref` Öznitelik, bir başvuru code öğesi sağlamak için herhangi bir etiket için eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="dfcb3-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="dfcb3-122">Derleyici, bu kod öğesi var olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="dfcb3-122">The compiler will verify that this code element exists.</span></span> <span data-ttu-id="dfcb3-123">Doğrulama başarısız olursa derleyici bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="dfcb3-123">If the verification failed, the compiler issues a warning.</span></span> <span data-ttu-id="dfcb3-124">Derleyici herhangi uyar `using` açıklandığı bir tür için göründüğünde deyimleri `cref` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="dfcb3-124">The compiler respects any `using` statements when it looks for a type described in the `cref` attribute.</span></span>  
  
    -   <span data-ttu-id="dfcb3-125">\<Özet > etiketi IntelliSense Visual Studio içinde bir tür veya üye hakkındaki ek bilgileri görüntülemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dfcb3-125">The \<summary> tag is used by IntelliSense inside Visual Studio to display additional information about a type or member.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="dfcb3-126">XML dosyası türü ve üyeleri hakkında tam bilgi sağlamaz (örneğin, bunu herhangi bir tür bilgi içermiyor).</span><span class="sxs-lookup"><span data-stu-id="dfcb3-126">The XML file does not provide full information about the type and members (for example, it does not contain any type information).</span></span> <span data-ttu-id="dfcb3-127">Bir tür veya üye hakkında tam bilgi almak için belge dosyası gerçek tür veya üye yansıma ile birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dfcb3-127">To get full information about a type or member, the documentation file must be used together with reflection on the actual type or member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfcb3-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dfcb3-128">See Also</span></span>  
 [<span data-ttu-id="dfcb3-129">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="dfcb3-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="dfcb3-130">/ doc (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="dfcb3-130">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [<span data-ttu-id="dfcb3-131">XML Belge Açıklamaları</span><span class="sxs-lookup"><span data-stu-id="dfcb3-131">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
