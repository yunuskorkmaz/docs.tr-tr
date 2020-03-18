---
title: LINQ ve dizeleri (C#)
ms.date: 07/20/2015
ms.assetid: dbe2d657-b3f3-487e-b645-21fb2d71cd7b
ms.openlocfilehash: b805bc7318b8c5fe70ab1c060d1058a6bbc4f177
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635541"
---
# <a name="linq-and-strings-c"></a><span data-ttu-id="d5527-102">LINQ ve dizeleri (C#)</span><span class="sxs-lookup"><span data-stu-id="d5527-102">LINQ and strings (C#)</span></span>

<span data-ttu-id="d5527-103">LINQ, dizeleri ve dizeleri koleksiyonlarını sorgulamak ve dönüştürmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d5527-103">LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="d5527-104">Özellikle metin dosyalarındaki yarı yapılandırılmış verilerle yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="d5527-104">It can be especially useful with semi-structured data in text files.</span></span> <span data-ttu-id="d5527-105">LINQ sorguları geleneksel dize işlevleri ve normal ifadelerle birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d5527-105">LINQ queries can be combined with traditional string functions and regular expressions.</span></span> <span data-ttu-id="d5527-106">Örneğin, LINQ kullanarak <xref:System.String.Split%2A?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> sorgulayabildiğiniz veya değiştirebileceğiniz bir dizi dize oluşturmak için veya yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5527-106">For example, you can use the <xref:System.String.Split%2A?displayProperty=nameWithType> or <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method to create an array of strings that you can then query or modify by using LINQ.</span></span> <span data-ttu-id="d5527-107"><xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> Yöntemi LINQ sorgusunun `where` yan tümcesinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5527-107">You can use the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> method in the `where` clause of a LINQ query.</span></span> <span data-ttu-id="d5527-108">Ayrıca, düzenli bir ifadeyle döndürülen <xref:System.Text.RegularExpressions.MatchCollection> sonuçları sorgulamak veya değiştirmek için LINQ'yi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5527-108">And you can use LINQ to query or modify the <xref:System.Text.RegularExpressions.MatchCollection> results returned by a regular expression.</span></span>

<span data-ttu-id="d5527-109">Yarı yapılandırılmış metin verilerini XML'e dönüştürmek için bu bölümde açıklanan teknikleri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5527-109">You can also use the techniques described in this section to transform semi-structured text data to XML.</span></span> <span data-ttu-id="d5527-110">Daha fazla bilgi için [CSV dosyalarından XML nasıl oluşturacağıkonusunda](how-to-generate-xml-from-csv-files.md)bilgi alabiliyorum.</span><span class="sxs-lookup"><span data-stu-id="d5527-110">For more information, see [How to generate XML from CSV files](how-to-generate-xml-from-csv-files.md).</span></span>

<span data-ttu-id="d5527-111">Bu bölümdeki örnekler iki kategoriye ayrılır:</span><span class="sxs-lookup"><span data-stu-id="d5527-111">The examples in this section fall into two categories:</span></span>

## <a name="querying-a-block-of-text"></a><span data-ttu-id="d5527-112">Metin bloğunu sorgulama</span><span class="sxs-lookup"><span data-stu-id="d5527-112">Querying a block of text</span></span>

<span data-ttu-id="d5527-113"><xref:System.String.Split%2A?displayProperty=nameWithType> Yöntem veya <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> yöntemi kullanarak metin bloklarını sorgulanabilir küçük dizeleri diziye bölerek sorgulayabilir, çözümleyebilir ve değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5527-113">You can query, analyze, and modify text blocks by splitting them into a queryable array of smaller strings by using the <xref:System.String.Split%2A?displayProperty=nameWithType> method or the <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d5527-114">Kaynak metni sözcüklere, cümlelere, paragraflara, sayfalara veya diğer ölçütlere bölebilir ve sorgunuzda gerekirse ek bölmeler gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5527-114">You can split the source text into words, sentences, paragraphs, pages, or any other criteria, and then perform additional splits if they are required in your query.</span></span>

- [<span data-ttu-id="d5527-115">Bir dizedeki bir sözcüğün oluşumları nasıl sayilir (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d5527-115">How to count occurrences of a word in a string (LINQ) (C#)</span></span>](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
  <span data-ttu-id="d5527-116">Metin üzerinden basit sorgulama için LINQ'nin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5527-116">Shows how to use LINQ for simple querying over text.</span></span>

- [<span data-ttu-id="d5527-117">Belirli bir sözcük kümesi (LINQ) (C#) içeren cümleler için sorgulama</span><span class="sxs-lookup"><span data-stu-id="d5527-117">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

  <span data-ttu-id="d5527-118">Metin dosyalarını rasgele sınırlarda nasıl bölerve her bölüme karşı sorguların nasıl gerçekleştirilişini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5527-118">Shows how to split text files on arbitrary boundaries and how to perform queries against each part.</span></span>

- [<span data-ttu-id="d5527-119">Dizedeki karakterler (LINQ) (C#) karakterleri sorgulama</span><span class="sxs-lookup"><span data-stu-id="d5527-119">How to query for characters in a string (LINQ) (C#)</span></span>](how-to-query-for-characters-in-a-string-linq.md)

  <span data-ttu-id="d5527-120">Bir dize sorgulanabilir bir tür olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5527-120">Demonstrates that a string is a queryable type.</span></span>

- [<span data-ttu-id="d5527-121">LINQ sorgularını normal ifadelerle birleştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="d5527-121">How to combine LINQ queries with regular expressions (C#)</span></span>](how-to-combine-linq-queries-with-regular-expressions.md)

  <span data-ttu-id="d5527-122">Filtre uygulanmış sorgu sonuçlarında karmaşık desen eşleştirmesi için LINQ sorgularında normal ifadelerin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5527-122">Shows how to use regular expressions in LINQ queries for complex pattern matching on filtered query results.</span></span>

## <a name="querying-semi-structured-data-in-text-format"></a><span data-ttu-id="d5527-123">Yarı yapılandırılmış verileri metin biçiminde sorgulama</span><span class="sxs-lookup"><span data-stu-id="d5527-123">Querying semi-structured data in text format</span></span>

<span data-ttu-id="d5527-124">Birçok farklı metin dosyası türü, genellikle sekme veya virgülle sınırlandırılmış dosyalar veya sabit uzunluktaki satırlar gibi benzer biçimlendirmeye sahip bir dizi satırdan oluşur.</span><span class="sxs-lookup"><span data-stu-id="d5527-124">Many different types of text files consist of a series of lines, often with similar formatting, such as tab- or comma-delimited files or fixed-length lines.</span></span> <span data-ttu-id="d5527-125">Böyle bir metin dosyasını belleğe okuduktan sonra, satırları sorgulamak ve/veya değiştirmek için LINQ'yu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5527-125">After you read such a text file into memory, you can use LINQ to query and/or modify the lines.</span></span> <span data-ttu-id="d5527-126">LINQ sorguları, birden çok kaynaktan gelen verileri birleştirme görevini de basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="d5527-126">LINQ queries also simplify the task of combining data from multiple sources.</span></span>

- [<span data-ttu-id="d5527-127">İki liste (LINQ) (C#) arasındaki küme farkı nasıl bulabilirim?</span><span class="sxs-lookup"><span data-stu-id="d5527-127">How to find the set difference between two lists (LINQ) (C#)</span></span>](how-to-find-the-set-difference-between-two-lists-linq.md)

  <span data-ttu-id="d5527-128">Bir listede bulunan ancak diğerinde bulunmayan tüm dizeleri nasıl bulacağımı gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5527-128">Shows how to find all the strings that are present in one list but not the other.</span></span>

- [<span data-ttu-id="d5527-129">Metin verilerini herhangi bir sözcüğe veya alana göre sıralama veya filtreleme (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d5527-129">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

  <span data-ttu-id="d5527-130">Metin çizgilerini herhangi bir sözcük veya alana göre nasıl sıralanır gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5527-130">Shows how to sort text lines based on any word or field.</span></span>

- [<span data-ttu-id="d5527-131">Sınırlandırılmış bir dosyanın (LINQ) (C#) alanlarını yeniden sıralama</span><span class="sxs-lookup"><span data-stu-id="d5527-131">How to reorder the fields of a delimited file (LINQ) (C#)</span></span>](how-to-reorder-the-fields-of-a-delimited-file-linq.md)

  <span data-ttu-id="d5527-132">.csv dosyasındaki bir satırdaki alanların nasıl yeniden sıralanın gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5527-132">Shows how to reorder fields in a line in a .csv file.</span></span>

- [<span data-ttu-id="d5527-133">Dize koleksiyonlarını birleştirme ve karşılaştırma (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d5527-133">How to combine and compare string collections (LINQ) (C#)</span></span>](how-to-combine-and-compare-string-collections-linq.md)

  <span data-ttu-id="d5527-134">Dize listelerini çeşitli şekillerde nasıl birleştirin.</span><span class="sxs-lookup"><span data-stu-id="d5527-134">Shows how to combine string lists in various ways.</span></span>

- [<span data-ttu-id="d5527-135">Nesne koleksiyonları birden çok kaynaktan (LINQ) (C#) doldurma</span><span class="sxs-lookup"><span data-stu-id="d5527-135">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](how-to-populate-object-collections-from-multiple-sources-linq.md)

  <span data-ttu-id="d5527-136">Veri kaynağı olarak birden çok metin dosyasını kullanarak nesne koleksiyonlarının nasıl oluşturulurulur gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5527-136">Shows how to create object collections by using multiple text files as data sources.</span></span>

- [<span data-ttu-id="d5527-137">Farklı dosyalardan (LINQ) (C#) içerik birleştirme</span><span class="sxs-lookup"><span data-stu-id="d5527-137">How to join content from dissimilar files (LINQ) (C#)</span></span>](how-to-join-content-from-dissimilar-files-linq.md)
  
  <span data-ttu-id="d5527-138">Eşleşen bir tuşu kullanarak iki listedeki dizeleri tek bir dize halinde nasıl birleştirin.</span><span class="sxs-lookup"><span data-stu-id="d5527-138">Shows how to combine strings in two lists into a single string by using a matching key.</span></span>

- [<span data-ttu-id="d5527-139">Grupları kullanarak bir dosyayı birçok dosyaya bölme (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d5527-139">How to split a file into many files by using groups (LINQ) (C#)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
  
  <span data-ttu-id="d5527-140">Veri kaynağı olarak tek bir dosya kullanarak yeni dosyaların nasıl oluşturularak oluşturulabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5527-140">Shows how to create new files by using a single file as a data source.</span></span>

- [<span data-ttu-id="d5527-141">CSV metin dosyasındaki sütun değerlerini nasıl hesaplar (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d5527-141">How to compute column values in a CSV text file (LINQ) (C#)</span></span>](how-to-compute-column-values-in-a-csv-text-file-linq.md)
  
  <span data-ttu-id="d5527-142">.csv dosyalarındaki metin verilerinde matematiksel hesaplamaların nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5527-142">Shows how to perform mathematical computations on text data in .csv files.</span></span>

## <a name="see-also"></a><span data-ttu-id="d5527-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5527-143">See also</span></span>

- [<span data-ttu-id="d5527-144">Dil-Tümleşik Sorgu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d5527-144">Language-Integrated Query (LINQ) (C#)</span></span>](index.md)
- [<span data-ttu-id="d5527-145">CSV dosyalarından XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="d5527-145">How to generate XML from CSV files</span></span>](how-to-generate-xml-from-csv-files.md)
