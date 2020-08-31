---
title: <include> -C# Programlama Kılavuzu
description: XML hakkında bilgi edinin <include> Etiket. Bu etiket, kaynak kodunuzda türleri ve üyeleri tanımlayan başka bir dosyadaki açıklamalara başvurmanıza olanak sağlar.
ms.date: 07/20/2015
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
ms.openlocfilehash: d2de8fea17850685668766bc4ec6e64b1be77cce
ms.sourcegitcommit: 2560a355c76b0a04cba0d34da870df9ad94ceca3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2020
ms.locfileid: "89053197"
---
# <a name="include-c-programming-guide"></a><span data-ttu-id="56cba-105">\<include> (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="56cba-105">\<include> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="56cba-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="56cba-106">Syntax</span></span>

```xml
<include file='filename' path='tagpath[@name="id"]' />
```

## <a name="parameters"></a><span data-ttu-id="56cba-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="56cba-107">Parameters</span></span>

- `filename`

  <span data-ttu-id="56cba-108">Belgeleri içeren XML dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="56cba-108">The name of the XML file containing the documentation.</span></span> <span data-ttu-id="56cba-109">Dosya adı, kaynak kodu dosyası ile ilişkili bir yol ile nitelenme yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="56cba-109">The file name can be qualified with a path relative to the source code file.</span></span> <span data-ttu-id="56cba-110">`filename`Tek tırnak işaretleri (' ') içine alın.</span><span class="sxs-lookup"><span data-stu-id="56cba-110">Enclose `filename` in single quotation marks (' ').</span></span>

- `tagpath`

  <span data-ttu-id="56cba-111">İçindeki etiketlerin yolu, etikete yol `filename` açar `name` .</span><span class="sxs-lookup"><span data-stu-id="56cba-111">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="56cba-112">Yolu tek tırnak işaretleri (' ') içine alın.</span><span class="sxs-lookup"><span data-stu-id="56cba-112">Enclose the path in single quotation marks (' ').</span></span>

- `name`

  <span data-ttu-id="56cba-113">Yorumlarla önce gelen etiketteki ad Belirleyicisi; `name` , olur `id` .</span><span class="sxs-lookup"><span data-stu-id="56cba-113">The name specifier in the tag that precedes the comments; `name` will have an `id`.</span></span>

- `id`

  <span data-ttu-id="56cba-114">Açıklamaların önündeki etiketin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="56cba-114">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="56cba-115">KIMLIĞI çift tırnak işareti ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="56cba-115">Enclose the ID in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="56cba-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="56cba-116">Remarks</span></span>

<span data-ttu-id="56cba-117">`<include>`Etiketi, kaynak kodunuzda türleri ve üyeleri tanımlayan başka bir dosyadaki açıklamalara başvurmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="56cba-117">The `<include>` tag lets you refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="56cba-118">Bu, belge açıklamalarını doğrudan kaynak kodu dosyanıza yerleştirmeye alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="56cba-118">This is an alternative to placing documentation comments directly in your source code file.</span></span> <span data-ttu-id="56cba-119">Belgeler ayrı bir dosyaya yerleştirilerek, kaynak denetimini belgelere kaynak koddan ayrı olarak uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56cba-119">By putting the documentation in a separate file, you can apply source control to the documentation separately from the source code.</span></span> <span data-ttu-id="56cba-120">Bir kişinin kaynak kodu dosyası kullanıma alınmış olabilir ve başka birisinin belge dosyası kullanıma alınmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="56cba-120">One person can have the source code file checked out and someone else can have the documentation file checked out.</span></span>

<span data-ttu-id="56cba-121">`<include>`Etiketi, XML XPath söz dizimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="56cba-121">The `<include>` tag uses the XML XPath syntax.</span></span> <span data-ttu-id="56cba-122">Kullanımı özelleştirmenin yolları için XPath belgelerine başvurun `<include>` .</span><span class="sxs-lookup"><span data-stu-id="56cba-122">Refer to XPath documentation for ways to customize your `<include>` use.</span></span>

## <a name="example"></a><span data-ttu-id="56cba-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="56cba-123">Example</span></span>

<span data-ttu-id="56cba-124">Bu çok dosyalı bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="56cba-124">This is a multifile example.</span></span> <span data-ttu-id="56cba-125">Tarafından kullanılan ilk dosya aşağıda verilmiştir `<include>` .</span><span class="sxs-lookup"><span data-stu-id="56cba-125">The following is the first file, which uses `<include>`.</span></span>

[!code-csharp[csProgGuideDocComments#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#5)]

<span data-ttu-id="56cba-126">İkinci dosya *xml_include_tag.doc*, aşağıdaki belge açıklamalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="56cba-126">The second file, *xml_include_tag.doc*, contains the following documentation comments.</span></span>

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

## <a name="program-output"></a><span data-ttu-id="56cba-127">Program çıktısı</span><span class="sxs-lookup"><span data-stu-id="56cba-127">Program output</span></span>

<span data-ttu-id="56cba-128">Aşağıdaki komut satırı ile test ve test2 sınıflarını derlerken aşağıdaki çıktı oluşturulur: `-doc:DocFileName.xml.` Visual Studio 'da, proje Tasarımcısı 'Nın derleme BÖLMESINDE XML belgesi açıklamaları seçeneğini belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56cba-128">The following output is generated when you compile the Test and Test2 classes with the following command line: `-doc:DocFileName.xml.` In Visual Studio, you specify the XML doc comments option in the Build pane of the Project Designer.</span></span> <span data-ttu-id="56cba-129">C# derleyicisi `<include>` etiketini gördüğünde, geçerli kaynak dosya yerine *xml_include_tag.doc* belge açıklamalarını arar.</span><span class="sxs-lookup"><span data-stu-id="56cba-129">When the C# compiler sees the `<include>` tag, it searches for documentation comments in *xml_include_tag.doc* instead of the current source file.</span></span> <span data-ttu-id="56cba-130">Derleyici daha sonra *DocFileName.xml*oluşturur ve bu, son belgeleri oluşturmak Için [sandrole](https://github.com/EWSoftware/SHFB) gibi belge araçları tarafından tüketilen dosyadır.</span><span class="sxs-lookup"><span data-stu-id="56cba-130">The compiler then generates *DocFileName.xml*, and this is the file that is consumed by documentation tools such as [Sandcastle](https://github.com/EWSoftware/SHFB) to produce the final documentation.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="56cba-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56cba-131">See also</span></span>

- [<span data-ttu-id="56cba-132">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="56cba-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="56cba-133">Belge açıklamaları için önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="56cba-133">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
