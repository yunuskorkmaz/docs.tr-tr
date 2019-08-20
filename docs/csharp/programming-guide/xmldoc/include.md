---
title: <include> - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
ms.openlocfilehash: 26241dab70a3b6a0cf80b374868fa759647cd8d9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588000"
---
# <a name="include-c-programming-guide"></a><span data-ttu-id="1473e-102">\<> dahil etC# (Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="1473e-102">\<include> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="1473e-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1473e-103">Syntax</span></span>  
  
```xml  
<include file='filename' path='tagpath[@name="id"]' />  
```  
  
## <a name="parameters"></a><span data-ttu-id="1473e-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1473e-104">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="1473e-105">Belgeleri içeren XML dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="1473e-105">The name of the XML file containing the documentation.</span></span> <span data-ttu-id="1473e-106">Dosya adı, kaynak kodu dosyası ile ilişkili bir yol ile nitelenme yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="1473e-106">The file name can be qualified with a path relative to the source code file.</span></span> <span data-ttu-id="1473e-107">Tek `filename` tırnak işaretleri (' ') içine alın.</span><span class="sxs-lookup"><span data-stu-id="1473e-107">Enclose `filename` in single quotation marks (' ').</span></span>  
  
 `tagpath`  
 <span data-ttu-id="1473e-108">İçindeki `filename` etiketlerin yolu, etikete `name`yol açar.</span><span class="sxs-lookup"><span data-stu-id="1473e-108">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="1473e-109">Yolu tek tırnak işaretleri (' ') içine alın.</span><span class="sxs-lookup"><span data-stu-id="1473e-109">Enclose the path in single quotation marks (' ').</span></span>  
  
 `name`  
 <span data-ttu-id="1473e-110">Yorumlarla önce gelen etiketteki ad Belirleyicisi; `name` ,`id`olur.</span><span class="sxs-lookup"><span data-stu-id="1473e-110">The name specifier in the tag that precedes the comments; `name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="1473e-111">Açıklamaların önündeki etiketin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="1473e-111">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="1473e-112">KIMLIĞI çift tırnak işareti ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="1473e-112">Enclose the ID in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1473e-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1473e-113">Remarks</span></span>  
 <span data-ttu-id="1473e-114">\<İçerme > etiketi, kaynak kodunuzda türleri ve üyeleri tanımlayan başka bir dosyadaki açıklamalara başvurmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="1473e-114">The \<include> tag lets you refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="1473e-115">Bu, belge açıklamalarını doğrudan kaynak kodu dosyanıza yerleştirmeye alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="1473e-115">This is an alternative to placing documentation comments directly in your source code file.</span></span> <span data-ttu-id="1473e-116">Belgeler ayrı bir dosyaya yerleştirilerek, kaynak denetimini belgelere kaynak koddan ayrı olarak uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1473e-116">By putting the documentation in a separate file, you can apply source control to the documentation separately from the source code.</span></span> <span data-ttu-id="1473e-117">Bir kişinin kaynak kodu dosyası kullanıma alınmış olabilir ve başka birisinin belge dosyası kullanıma alınmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="1473e-117">One person can have the source code file checked out and someone else can have the documentation file checked out.</span></span>  
  
 <span data-ttu-id="1473e-118">\<İçerme > etiketi XML XPath söz dizimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1473e-118">The \<include> tag uses the XML XPath syntax.</span></span> <span data-ttu-id="1473e-119">\<İçerme > kullanımını özelleştirmenin yolları için XPath belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="1473e-119">Refer to XPath documentation for ways to customize your \<include> use.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1473e-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="1473e-120">Example</span></span>  
 <span data-ttu-id="1473e-121">Bu çok dosyalı bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="1473e-121">This is a multifile example.</span></span> <span data-ttu-id="1473e-122">> \<İçeren ilk dosya aşağıda listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="1473e-122">The first file, which uses \<include>, is listed below:</span></span>  
  
 [!code-csharp[csProgGuideDocComments#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#5)]  
  
 <span data-ttu-id="1473e-123">İkinci dosya olan xml_include_tag. doc, aşağıdaki belge açıklamalarını içerir:</span><span class="sxs-lookup"><span data-stu-id="1473e-123">The second file, xml_include_tag.doc, contains the following documentation comments:</span></span>  
  
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
  
## <a name="program-output"></a><span data-ttu-id="1473e-124">Program çıktısı</span><span class="sxs-lookup"><span data-stu-id="1473e-124">Program Output</span></span>  
 <span data-ttu-id="1473e-125">Aşağıdaki komut satırı ile test ve test2 sınıflarını derlerken aşağıdaki çıktı oluşturulur: `/doc:DocFileName.xml.`Visual Studio 'da, proje Tasarımcısı ' nın Yapı bölmesinde XML belgesi açıklamaları seçeneğini belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1473e-125">The following output is generated when you compile the Test and Test2 classes with the following command line: `/doc:DocFileName.xml.` In Visual Studio, you specify the XML doc comments option in the Build pane of the Project Designer.</span></span> <span data-ttu-id="1473e-126">C# Derleyici \<içerme > etiketini gördüğünde, geçerli kaynak dosya yerine xml_include_tag. doc içinde belge açıklamalarını arar.</span><span class="sxs-lookup"><span data-stu-id="1473e-126">When the C# compiler sees the \<include> tag, it will search for documentation comments in xml_include_tag.doc instead of the current source file.</span></span> <span data-ttu-id="1473e-127">Daha sonra derleyici DocFileName. xml oluşturur ve bu, son belgeleri oluşturmak için [Docfx](https://dotnet.github.io/docfx/) ve [sandrole](https://github.com/EWSoftware/SHFB) gibi belge araçları tarafından tüketilen dosyadır.</span><span class="sxs-lookup"><span data-stu-id="1473e-127">The compiler then generates DocFileName.xml, and this is the file that is consumed by documentation tools such as [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to produce the final documentation.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1473e-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1473e-128">See also</span></span>

- [<span data-ttu-id="1473e-129">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1473e-129">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1473e-130">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="1473e-130">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
