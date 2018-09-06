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
ms.openlocfilehash: 854c8b61fa8164bccfc9451f2f163dab4a56388f
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44038285"
---
# <a name="ltincludegt-c-programming-guide"></a><span data-ttu-id="409d7-102">&lt;dahil&gt; (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="409d7-102">&lt;include&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="409d7-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="409d7-103">Syntax</span></span>  
  
```xml  
<include file='filename' path='tagpath[@name="id"]' />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="409d7-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="409d7-104">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="409d7-105">Belgeleri içeren XML dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="409d7-105">The name of the XML file containing the documentation.</span></span> <span data-ttu-id="409d7-106">Dosya adı, kaynak kodu dosyasının göreli bir yol ile nitelenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="409d7-106">The file name can be qualified with a path relative to the source code file.</span></span> <span data-ttu-id="409d7-107">İçine `filename` tek tırnak işareti (' ').</span><span class="sxs-lookup"><span data-stu-id="409d7-107">Enclose `filename` in single quotation marks (' ').</span></span>  
  
 `tagpath`  
 <span data-ttu-id="409d7-108">Etiketleri yolunu `filename` etikete müşteri adayları `name`.</span><span class="sxs-lookup"><span data-stu-id="409d7-108">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="409d7-109">Yolu, tek tırnak işaretleri içine alın (' ').</span><span class="sxs-lookup"><span data-stu-id="409d7-109">Enclose the path in single quotation marks (' ').</span></span>  
  
 `name`  
 <span data-ttu-id="409d7-110">Yorumları önündeki etiketinde ad tanımlayıcısı; `name` sahip bir `id`.</span><span class="sxs-lookup"><span data-stu-id="409d7-110">The name specifier in the tag that precedes the comments; `name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="409d7-111">Yorumları önünde etiket kimliği.</span><span class="sxs-lookup"><span data-stu-id="409d7-111">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="409d7-112">Kimliği çift tırnak içine alın ("").</span><span class="sxs-lookup"><span data-stu-id="409d7-112">Enclose the ID in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="409d7-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="409d7-113">Remarks</span></span>  
 <span data-ttu-id="409d7-114">\<Dahil > etiket türleri açıklayan yorumlar başka bir dosyaya ve üyeleri, kaynak kodunuzdaki bakın olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="409d7-114">The \<include> tag lets you refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="409d7-115">Bu belge açıklamaları doğrudan, kaynak kodu dosyasında yerleştirme için bir alternatifidir.</span><span class="sxs-lookup"><span data-stu-id="409d7-115">This is an alternative to placing documentation comments directly in your source code file.</span></span> <span data-ttu-id="409d7-116">Ayrı bir dosyada belgeleri koyarak, kaynak denetimi belgeleri için ayrı ayrı kaynak koddan uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="409d7-116">By putting the documentation in a separate file, you can apply source control to the documentation separately from the source code.</span></span> <span data-ttu-id="409d7-117">Bir kişi kaynak kod dosyasını kullanıma alınmış olabilir ve başka birisi kullanıma belge dosyası olabilir.</span><span class="sxs-lookup"><span data-stu-id="409d7-117">One person can have the source code file checked out and someone else can have the documentation file checked out.</span></span>  
  
 <span data-ttu-id="409d7-118">\<Dahil > etiketini XML XPath sözdizimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="409d7-118">The \<include> tag uses the XML XPath syntax.</span></span> <span data-ttu-id="409d7-119">Özelleştirme yolları için XPath belgelerine bakın, \<dahil > kullanın.</span><span class="sxs-lookup"><span data-stu-id="409d7-119">Refer to XPath documentation for ways to customize your \<include> use.</span></span>  
  
## <a name="example"></a><span data-ttu-id="409d7-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="409d7-120">Example</span></span>  
 <span data-ttu-id="409d7-121">Bu çok dosyalı bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="409d7-121">This is a multifile example.</span></span> <span data-ttu-id="409d7-122">Kullanan ilk dosya \<dahil >, aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="409d7-122">The first file, which uses \<include>, is listed below:</span></span>  
  
 [!code-csharp[csProgGuideDocComments#5](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/include_1.cs)]  
  
 <span data-ttu-id="409d7-123">İkinci bir dosya, xml_include_tag.doc, aşağıdaki belgeleri açıklamaları içerir:</span><span class="sxs-lookup"><span data-stu-id="409d7-123">The second file, xml_include_tag.doc, contains the following documentation comments:</span></span>  
  
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
  
## <a name="program-output"></a><span data-ttu-id="409d7-124">Program çıktısı</span><span class="sxs-lookup"><span data-stu-id="409d7-124">Program Output</span></span>  
 <span data-ttu-id="409d7-125">Test ve Test2 sınıfları aşağıdaki komut satırı ile derleme yaparken aşağıdaki çıktı oluşturulur: `/doc:DocFileName.xml.` Visual Studio'da, belirttiğiniz XML belge açıklamaları seçeneği Proje Tasarımcısı'nın derleme bölmesinde.</span><span class="sxs-lookup"><span data-stu-id="409d7-125">The following output is generated when you compile the Test and Test2 classes with the following command line: `/doc:DocFileName.xml.` In Visual Studio, you specify the XML doc comments option in the Build pane of the Project Designer.</span></span> <span data-ttu-id="409d7-126">C# derleyicisi gördüğünde \<dahil > etiketi, arama yapacağı xml_include_tag.doc geçerli kaynak dosyanın yerine, belge açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="409d7-126">When the C# compiler sees the \<include> tag, it will search for documentation comments in xml_include_tag.doc instead of the current source file.</span></span> <span data-ttu-id="409d7-127">Derleyici, ardından DocFileName.xml oluşturur ve bu belgeleri araçları tarafından gibi kullanılan dosya [Sandcastle](https://github.com/EWSoftware/SHFB) son belgeleri oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="409d7-127">The compiler then generates DocFileName.xml, and this is the file that is consumed by documentation tools such as [Sandcastle](https://github.com/EWSoftware/SHFB) to produce the final documentation.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="409d7-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="409d7-128">See Also</span></span>

- [<span data-ttu-id="409d7-129">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="409d7-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="409d7-130">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="409d7-130">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
