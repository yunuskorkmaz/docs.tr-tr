---
title: LINQ ve dizeler (C#)
ms.date: 07/20/2015
ms.assetid: dbe2d657-b3f3-487e-b645-21fb2d71cd7b
ms.openlocfilehash: b805bc7318b8c5fe70ab1c060d1058a6bbc4f177
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635541"
---
# <a name="linq-and-strings-c"></a><span data-ttu-id="a92ec-102">LINQ ve dizeler (C#)</span><span class="sxs-lookup"><span data-stu-id="a92ec-102">LINQ and strings (C#)</span></span>

<span data-ttu-id="a92ec-103">LINQ, dizeleri ve dize koleksiyonlarını sorgulamak ve dönüştürmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a92ec-103">LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="a92ec-104">Bu, özellikle metin dosyalarındaki yarı yapılandırılmış verilerle yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="a92ec-104">It can be especially useful with semi-structured data in text files.</span></span> <span data-ttu-id="a92ec-105">LINQ sorguları, geleneksel dize işlevleri ve normal ifadelerle birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a92ec-105">LINQ queries can be combined with traditional string functions and regular expressions.</span></span> <span data-ttu-id="a92ec-106">Örneğin, LINQ kullanarak sorgulayabilmeniz veya değiştiremeyeceğiniz bir dize dizisi oluşturmak için <xref:System.String.Split%2A?displayProperty=nameWithType> veya <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a92ec-106">For example, you can use the <xref:System.String.Split%2A?displayProperty=nameWithType> or <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method to create an array of strings that you can then query or modify by using LINQ.</span></span> <span data-ttu-id="a92ec-107">Bir LINQ sorgusunun `where` yan tümcesinde <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a92ec-107">You can use the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> method in the `where` clause of a LINQ query.</span></span> <span data-ttu-id="a92ec-108">Aynı şekilde, bir normal ifade tarafından döndürülen <xref:System.Text.RegularExpressions.MatchCollection> sonuçlarını sorgulamak veya değiştirmek için LINQ kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a92ec-108">And you can use LINQ to query or modify the <xref:System.Text.RegularExpressions.MatchCollection> results returned by a regular expression.</span></span>

<span data-ttu-id="a92ec-109">Yarı yapılandırılmış metin verilerini XML 'e dönüştürmek için bu bölümde açıklanan teknikleri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a92ec-109">You can also use the techniques described in this section to transform semi-structured text data to XML.</span></span> <span data-ttu-id="a92ec-110">Daha fazla bilgi için bkz. [CSV DOSYALARıNDAN XML oluşturma](how-to-generate-xml-from-csv-files.md).</span><span class="sxs-lookup"><span data-stu-id="a92ec-110">For more information, see [How to generate XML from CSV files](how-to-generate-xml-from-csv-files.md).</span></span>

<span data-ttu-id="a92ec-111">Bu bölümdeki örnekler iki kategoriye ayrılır:</span><span class="sxs-lookup"><span data-stu-id="a92ec-111">The examples in this section fall into two categories:</span></span>

## <a name="querying-a-block-of-text"></a><span data-ttu-id="a92ec-112">Metin bloğunu sorgulama</span><span class="sxs-lookup"><span data-stu-id="a92ec-112">Querying a block of text</span></span>

<span data-ttu-id="a92ec-113"><xref:System.String.Split%2A?displayProperty=nameWithType> yöntemini veya <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> yöntemini kullanarak bunları bir daha küçük dizeler dizisine bölerek metin bloklarını sorgulayabilir, çözümleyebilir ve değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a92ec-113">You can query, analyze, and modify text blocks by splitting them into a queryable array of smaller strings by using the <xref:System.String.Split%2A?displayProperty=nameWithType> method or the <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a92ec-114">Kaynak metni sözcükler, cümleler, paragraflar, sayfalar veya diğer ölçütlere bölebilir ve ardından sorgunuzda gerekliyse ek bölmeler gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a92ec-114">You can split the source text into words, sentences, paragraphs, pages, or any other criteria, and then perform additional splits if they are required in your query.</span></span>

- [<span data-ttu-id="a92ec-115">Dizedeki bir sözcüğün tekrarlamalarını sayma (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a92ec-115">How to count occurrences of a word in a string (LINQ) (C#)</span></span>](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
  <span data-ttu-id="a92ec-116">Metin üzerinde basit sorgulama için LINQ 'ın nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a92ec-116">Shows how to use LINQ for simple querying over text.</span></span>

- [<span data-ttu-id="a92ec-117">Belirli bir sözcük kümesini (LINQ) içeren cümleleri sorgulama (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a92ec-117">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

  <span data-ttu-id="a92ec-118">Metin dosyalarının rastgele sınırlarda nasıl bölüneceği ve her parçaya yönelik sorguların nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a92ec-118">Shows how to split text files on arbitrary boundaries and how to perform queries against each part.</span></span>

- [<span data-ttu-id="a92ec-119">Dizedeki karakterleri sorgulama (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a92ec-119">How to query for characters in a string (LINQ) (C#)</span></span>](how-to-query-for-characters-in-a-string-linq.md)

  <span data-ttu-id="a92ec-120">Bir dizenin sorgulanabilir bir tür olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a92ec-120">Demonstrates that a string is a queryable type.</span></span>

- [<span data-ttu-id="a92ec-121">LINQ sorgularını normal ifadelerle birleştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="a92ec-121">How to combine LINQ queries with regular expressions (C#)</span></span>](how-to-combine-linq-queries-with-regular-expressions.md)

  <span data-ttu-id="a92ec-122">Filtrelenmiş sorgu sonuçlarında karmaşık model eşleştirmesi için LINQ sorgularında normal ifadelerin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a92ec-122">Shows how to use regular expressions in LINQ queries for complex pattern matching on filtered query results.</span></span>

## <a name="querying-semi-structured-data-in-text-format"></a><span data-ttu-id="a92ec-123">Yarı yapılandırılmış verileri metin biçiminde sorgulama</span><span class="sxs-lookup"><span data-stu-id="a92ec-123">Querying semi-structured data in text format</span></span>

<span data-ttu-id="a92ec-124">Birçok farklı metin dosyası türü, genellikle sekme veya virgülle ayrılmış dosyalar ya da sabit uzunluklu çizgiler gibi benzer biçimlendirmeler içeren bir dizi satırdan oluşur.</span><span class="sxs-lookup"><span data-stu-id="a92ec-124">Many different types of text files consist of a series of lines, often with similar formatting, such as tab- or comma-delimited files or fixed-length lines.</span></span> <span data-ttu-id="a92ec-125">Bu tür bir metin dosyasını belleğe okuduktan sonra, satırları sorgulamak ve/veya değiştirmek için LINQ kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a92ec-125">After you read such a text file into memory, you can use LINQ to query and/or modify the lines.</span></span> <span data-ttu-id="a92ec-126">LINQ sorguları Ayrıca birden çok kaynaktan veri birleştirme görevini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="a92ec-126">LINQ queries also simplify the task of combining data from multiple sources.</span></span>

- [<span data-ttu-id="a92ec-127">İki liste arasında küme farkını bulma (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a92ec-127">How to find the set difference between two lists (LINQ) (C#)</span></span>](how-to-find-the-set-difference-between-two-lists-linq.md)

  <span data-ttu-id="a92ec-128">Bir listede bulunan ancak diğeri olmayan tüm dizelerin nasıl bulunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a92ec-128">Shows how to find all the strings that are present in one list but not the other.</span></span>

- [<span data-ttu-id="a92ec-129">Her kelime veya alana göre metin verilerini sıralama veya filtreleme (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a92ec-129">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

  <span data-ttu-id="a92ec-130">Metin çizgilerinin herhangi bir sözcük veya alana göre nasıl sıralanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a92ec-130">Shows how to sort text lines based on any word or field.</span></span>

- [<span data-ttu-id="a92ec-131">Ayrılmış bir dosyanın (LINQ) alanlarını yeniden sıralama (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a92ec-131">How to reorder the fields of a delimited file (LINQ) (C#)</span></span>](how-to-reorder-the-fields-of-a-delimited-file-linq.md)

  <span data-ttu-id="a92ec-132">Bir. csv dosyasındaki bir satırdaki alanların nasıl yeniden oluşturulduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a92ec-132">Shows how to reorder fields in a line in a .csv file.</span></span>

- [<span data-ttu-id="a92ec-133">Dize koleksiyonlarını birleştirme ve karşılaştırma (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a92ec-133">How to combine and compare string collections (LINQ) (C#)</span></span>](how-to-combine-and-compare-string-collections-linq.md)

  <span data-ttu-id="a92ec-134">Dize listelerinin çeşitli yollarla nasıl birleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a92ec-134">Shows how to combine string lists in various ways.</span></span>

- [<span data-ttu-id="a92ec-135">Birden çok kaynaktan nesne koleksiyonları doldurma (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a92ec-135">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](how-to-populate-object-collections-from-multiple-sources-linq.md)

  <span data-ttu-id="a92ec-136">Birden çok metin dosyasını veri kaynağı olarak kullanarak nasıl nesne koleksiyonları oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a92ec-136">Shows how to create object collections by using multiple text files as data sources.</span></span>

- [<span data-ttu-id="a92ec-137">Benzer olmayan dosyalardaki (LINQ) (C#) içerik ekleme</span><span class="sxs-lookup"><span data-stu-id="a92ec-137">How to join content from dissimilar files (LINQ) (C#)</span></span>](how-to-join-content-from-dissimilar-files-linq.md)
  
  <span data-ttu-id="a92ec-138">İki listedeki dizelerin, eşleşen bir anahtar kullanılarak tek bir dize içinde nasıl birleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a92ec-138">Shows how to combine strings in two lists into a single string by using a matching key.</span></span>

- [<span data-ttu-id="a92ec-139">Grupları (LINQ) kullanarak bir dosyayı birden çok dosyaya bölme (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a92ec-139">How to split a file into many files by using groups (LINQ) (C#)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
  
  <span data-ttu-id="a92ec-140">Veri kaynağı olarak tek bir dosya kullanarak yeni dosyaların nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a92ec-140">Shows how to create new files by using a single file as a data source.</span></span>

- [<span data-ttu-id="a92ec-141">CSV metin dosyasında (LINQ) sütun değerlerini hesaplama (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a92ec-141">How to compute column values in a CSV text file (LINQ) (C#)</span></span>](how-to-compute-column-values-in-a-csv-text-file-linq.md)
  
  <span data-ttu-id="a92ec-142">. Csv dosyalarındaki metin verilerinde matematiksel hesaplamaların nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a92ec-142">Shows how to perform mathematical computations on text data in .csv files.</span></span>

## <a name="see-also"></a><span data-ttu-id="a92ec-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a92ec-143">See also</span></span>

- [<span data-ttu-id="a92ec-144">Dil ile tümleşik sorgu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a92ec-144">Language-Integrated Query (LINQ) (C#)</span></span>](index.md)
- [<span data-ttu-id="a92ec-145">CSV dosyalarından XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="a92ec-145">How to generate XML from CSV files</span></span>](how-to-generate-xml-from-csv-files.md)
