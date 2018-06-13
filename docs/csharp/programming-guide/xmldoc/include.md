---
title: '&lt;dahil&gt; (C# programlama Kılavuzu)'
ms.date: 07/20/2015
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
ms.openlocfilehash: a681a2fcbb874d67b82c8bda73d92dd993928bbc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334515"
---
# <a name="ltincludegt-c-programming-guide"></a><span data-ttu-id="da7a8-102">&lt;dahil&gt; (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="da7a8-102">&lt;include&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="da7a8-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="da7a8-103">Syntax</span></span>  
  
```xml  
<include file='filename' path='tagpath[@name="id"]' />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="da7a8-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="da7a8-104">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="da7a8-105">Belgeleri içeren XML dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="da7a8-105">The name of the XML file containing the documentation.</span></span> <span data-ttu-id="da7a8-106">Dosya adı nitelenmiş bir yol olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="da7a8-106">The file name can be qualified with a path.</span></span> <span data-ttu-id="da7a8-107">İçine `filename` tek tırnak işareti (' ').</span><span class="sxs-lookup"><span data-stu-id="da7a8-107">Enclose `filename` in single quotation marks (' ').</span></span>  
  
 `tagpath`  
 <span data-ttu-id="da7a8-108">Etiketleri yolunu `filename` etikete müşteri adayları `name`.</span><span class="sxs-lookup"><span data-stu-id="da7a8-108">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="da7a8-109">Yolun tek tırnak işaretleri içine alın (' ').</span><span class="sxs-lookup"><span data-stu-id="da7a8-109">Enclose the path in single quotation marks (' ').</span></span>  
  
 `name`  
 <span data-ttu-id="da7a8-110">Ad belirticisi açıklamaları önündeki etiketinde; `name` sahip bir `id`.</span><span class="sxs-lookup"><span data-stu-id="da7a8-110">The name specifier in the tag that precedes the comments; `name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="da7a8-111">Açıklamaları önündeki etiket kimliği.</span><span class="sxs-lookup"><span data-stu-id="da7a8-111">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="da7a8-112">Kimliği çift tırnak işaretleri içine alın ("").</span><span class="sxs-lookup"><span data-stu-id="da7a8-112">Enclose the ID in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da7a8-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="da7a8-113">Remarks</span></span>  
 <span data-ttu-id="da7a8-114">\<Dahil > etiketi, başka bir dosya türlerini tanımlamak açıklamaları ve kaynak kodunuzu üyelerinde bakın sağlar.</span><span class="sxs-lookup"><span data-stu-id="da7a8-114">The \<include> tag lets you refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="da7a8-115">Bu belge açıklamaları doğrudan, kaynak kodu dosyasına yerleştirerek alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="da7a8-115">This is an alternative to placing documentation comments directly in your source code file.</span></span> <span data-ttu-id="da7a8-116">Ayrı bir dosyaya belgelere koyarak, kaynak denetimi belgelere ayrı ayrı kaynak kodundan uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da7a8-116">By putting the documentation in a separate file, you can apply source control to the documentation separately from the source code.</span></span> <span data-ttu-id="da7a8-117">Bir kişi kullanıma kaynak kodu dosyasına sahip olabilir ve başka birinin kullanıma belge dosyası olabilir.</span><span class="sxs-lookup"><span data-stu-id="da7a8-117">One person can have the source code file checked out and someone else can have the documentation file checked out.</span></span>  
  
 <span data-ttu-id="da7a8-118">\<Dahil > etiketi XML XPath sözdizimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="da7a8-118">The \<include> tag uses the XML XPath syntax.</span></span> <span data-ttu-id="da7a8-119">Özelleştirme yolları XPath belgelere bakın, \<dahil > kullanın.</span><span class="sxs-lookup"><span data-stu-id="da7a8-119">Refer to XPath documentation for ways to customize your \<include> use.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da7a8-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="da7a8-120">Example</span></span>  
 <span data-ttu-id="da7a8-121">Bu birden çok dosya bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="da7a8-121">This is a multifile example.</span></span> <span data-ttu-id="da7a8-122">Kullanan ilk dosya \<dahil >, aşağıda listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="da7a8-122">The first file, which uses \<include>, is listed below:</span></span>  
  
 [!code-csharp[csProgGuideDocComments#5](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/include_1.cs)]  
  
 <span data-ttu-id="da7a8-123">İkinci dosya, xml_include_tag.doc, aşağıdaki belge açıklamaları içerir:</span><span class="sxs-lookup"><span data-stu-id="da7a8-123">The second file, xml_include_tag.doc, contains the following documentation comments:</span></span>  
  
```xml  
<MyDocs>  
  
<MyMembers name="test">  
<summary>  
The summary for this type.  
</summary>  
</MyMembers>  
  
<MyMembers name="test2">  
<summary>  
The summary for this other type.  
</summary>  
</MyMembers>  
  
</MyDocs>  
```  
  
## <a name="program-output"></a><span data-ttu-id="da7a8-124">Program çıktısı</span><span class="sxs-lookup"><span data-stu-id="da7a8-124">Program Output</span></span>  
 <span data-ttu-id="da7a8-125">Aşağıdaki komut satırı Test ve Test2 sınıflarıyla derleme yaparken aşağıdaki çıkış oluşturulur: `/doc:DocFileName.xml.` Visual Studio'da, belirttiğiniz XML belge açıklamaları seçeneği Proje Tasarımcısı'nın Yapı bölmesinde.</span><span class="sxs-lookup"><span data-stu-id="da7a8-125">The following output is generated when you compile the Test and Test2 classes with the following command line: `/doc:DocFileName.xml.` In Visual Studio, you specify the XML doc comments option in the Build pane of the Project Designer.</span></span> <span data-ttu-id="da7a8-126">C# Derleyici gördüğünde \<dahil > etiketi, bu da arayacaktır geçerli kaynak dosyası yerine xml_include_tag.doc belge açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="da7a8-126">When the C# compiler sees the \<include> tag, it will search for documentation comments in xml_include_tag.doc instead of the current source file.</span></span> <span data-ttu-id="da7a8-127">Derleyici sonra DocFileName.xml oluşturur ve bu belgeleri araçları tarafından gibi tüketilen dosyası [Sandcastle](https://github.com/EWSoftware/SHFB) son belgeleri oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="da7a8-127">The compiler then generates DocFileName.xml, and this is the file that is consumed by documentation tools such as [Sandcastle](https://github.com/EWSoftware/SHFB) to produce the final documentation.</span></span>  
  
```xml  
<?xml version="1.0"?>   
<doc>   
    <assembly>   
        <name>xml_include_tag</name>   
    </assembly>   
    <members>   
        <member name="T:Test">   
            <summary>   
The summary for this type.   
</summary>   
        </member>   
        <member name="T:Test2">   
            <summary>   
The summary for this other type.   
</summary>   
        </member>   
    </members>   
</doc>   
```  
  
## <a name="see-also"></a><span data-ttu-id="da7a8-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="da7a8-128">See Also</span></span>  
 [<span data-ttu-id="da7a8-129">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="da7a8-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="da7a8-130">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="da7a8-130">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
