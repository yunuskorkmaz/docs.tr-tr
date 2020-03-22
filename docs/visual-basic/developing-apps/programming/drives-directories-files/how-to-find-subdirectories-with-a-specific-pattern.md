---
title: 'Nasıl Yapılır: Belirli bir Desendeki Alt Dizinleri Bulma'
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: c8e13598080139cafabffb2e17d0a3b99c37dc5d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348768"
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a><span data-ttu-id="75862-102">Nasıl Yapılır: Visual Basic'te Belirli bir Desendeki Alt Dizinleri Bulma</span><span class="sxs-lookup"><span data-stu-id="75862-102">How to: Find Subdirectories with a Specific Pattern in Visual Basic</span></span>

<span data-ttu-id="75862-103">Yöntem, <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> bir dizindeki alt dizinlerin yol adlarını temsil eden salt okunur dizeler koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="75862-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> method returns a read-only collection of strings representing the path names for the subdirectories in a directory.</span></span> <span data-ttu-id="75862-104">`wildCards` Belirli bir desen belirtmek için parametrekullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="75862-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span> <span data-ttu-id="75862-105">Alt dizinlerin içeriğini aramaya eklemek isterseniz, parametreyi `searchType` ' `SearchOption.SearchAllSubDirectories`ye göre ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="75862-105">If you would like to include the contents of subdirectories in the search, set the `searchType` parameter to `SearchOption.SearchAllSubDirectories`.</span></span>

<span data-ttu-id="75862-106">Belirtilen desenle eşleşen dizinler bulunmazsa boş bir koleksiyon döndürülür.</span><span class="sxs-lookup"><span data-stu-id="75862-106">An empty collection is returned if no directories matching the specified pattern are found.</span></span>

## <a name="to-find-subdirectories-with-a-specific-pattern"></a><span data-ttu-id="75862-107">Belirli bir desene sahip alt dizinleri bulmak için</span><span class="sxs-lookup"><span data-stu-id="75862-107">To find subdirectories with a specific pattern</span></span>

<span data-ttu-id="75862-108">Aramak `GetDirectories` istediğiniz dizinin adını ve yolunu sağlayarak yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="75862-108">Use the `GetDirectories` method, supplying the name and path of the directory you want to search.</span></span> <span data-ttu-id="75862-109">Aşağıdaki örnek, dizin yapısında kendi adlarında "Günlükler" sözcüğünü içeren tüm `ListBox1`dizinleri döndürür ve bunları .</span><span class="sxs-lookup"><span data-stu-id="75862-109">The following example returns all the directories in the directory structure that contain the word "Logs" in their name, and adds them to `ListBox1`.</span></span>

[!code-vb[VbVbcnFileAccess#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnFileAccess/VB/Class1.vb#1)]

## <a name="robust-programming"></a><span data-ttu-id="75862-110">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="75862-110">Robust Programming</span></span>

<span data-ttu-id="75862-111">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="75862-111">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="75862-112">Yol aşağıdaki nedenlerden biri için geçerli değildir: bir sıfır uzunlukta dize, sadece beyaz boşluk içerir, geçersiz karakterler içerir, \\ \\ya\\da bir aygıt yolu (ile başlar . ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="75862-112">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="75862-113">Yol geçerli değildir, çünkü `Nothing` <xref:System.ArgumentNullException>( ).</span><span class="sxs-lookup"><span data-stu-id="75862-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="75862-114">Belirtilen joker karakterlerden biri veya `Nothing`birkaçı boş bir dizedir<xref:System.ArgumentNullException>veya yalnızca boşluk içerir ( ).</span><span class="sxs-lookup"><span data-stu-id="75862-114">One or more of the specified wildcard characters is `Nothing`, an empty string, or contains only spaces (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="75862-115">`directory`yok (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="75862-115">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>

- <span data-ttu-id="75862-116">`directory`varolan bir dosyaya işaret eder (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="75862-116">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="75862-117">Yol, sistem tarafından tanımlanan maksimum<xref:System.IO.PathTooLongException>uzunluğu aşıyor ( ).</span><span class="sxs-lookup"><span data-stu-id="75862-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>

- <span data-ttu-id="75862-118">Yoldaki bir dosya veya klasör adı bir üst üste içerir (:) veya geçersiz bir biçimde<xref:System.NotSupportedException>( ).</span><span class="sxs-lookup"><span data-stu-id="75862-118">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="75862-119">Kullanıcı yolu görüntülemek için gerekli izinlerden<xref:System.Security.SecurityException>yoksundur ( ).</span><span class="sxs-lookup"><span data-stu-id="75862-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="75862-120">Kullanıcı gerekli izinleri yoksun<xref:System.UnauthorizedAccessException>( ).</span><span class="sxs-lookup"><span data-stu-id="75862-120">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="75862-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75862-121">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [<span data-ttu-id="75862-122">Nasıl Yapılır: Belirli bir Düzendeki Dosyaları Bulma</span><span class="sxs-lookup"><span data-stu-id="75862-122">How to: Find Files with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
