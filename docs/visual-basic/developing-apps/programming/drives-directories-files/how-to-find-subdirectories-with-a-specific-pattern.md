---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Visual Basic belirli bir düzene sahip alt dizinleri bulma'
title: 'Nasıl yapılır: Belirli bir Desendeki Alt Dizinleri Bulma'
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: aaf1fe0e844c6a3db2b011289613a80dbd1b43fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797555"
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a><span data-ttu-id="0323f-103">Nasıl Yapılır: Visual Basic'te Belirli bir Desendeki Alt Dizinleri Bulma</span><span class="sxs-lookup"><span data-stu-id="0323f-103">How to: Find Subdirectories with a Specific Pattern in Visual Basic</span></span>

<span data-ttu-id="0323f-104"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>Yöntemi, bir dizindeki alt dizinlerin yol adlarını temsil eden salt okunurdur bir dize koleksiyonu döndürür.</span><span class="sxs-lookup"><span data-stu-id="0323f-104">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> method returns a read-only collection of strings representing the path names for the subdirectories in a directory.</span></span> <span data-ttu-id="0323f-105">`wildCards`Belirli bir kalıbı belirtmek için parametresini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0323f-105">You can use the `wildCards` parameter to specify a specific pattern.</span></span> <span data-ttu-id="0323f-106">Aramada alt dizinlerin içeriğini eklemek istiyorsanız, `searchType` parametresini olarak ayarlayın `SearchOption.SearchAllSubDirectories` .</span><span class="sxs-lookup"><span data-stu-id="0323f-106">If you would like to include the contents of subdirectories in the search, set the `searchType` parameter to `SearchOption.SearchAllSubDirectories`.</span></span>

<span data-ttu-id="0323f-107">Belirtilen Düzenle eşleşen hiçbir dizin bulunamazsa boş bir koleksiyon döndürülür.</span><span class="sxs-lookup"><span data-stu-id="0323f-107">An empty collection is returned if no directories matching the specified pattern are found.</span></span>

## <a name="to-find-subdirectories-with-a-specific-pattern"></a><span data-ttu-id="0323f-108">Belirli bir düzene sahip alt dizinleri bulmak için</span><span class="sxs-lookup"><span data-stu-id="0323f-108">To find subdirectories with a specific pattern</span></span>

<span data-ttu-id="0323f-109">`GetDirectories`Arama yapmak istediğiniz dizinin adını ve yolunu sağlayarak yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0323f-109">Use the `GetDirectories` method, supplying the name and path of the directory you want to search.</span></span> <span data-ttu-id="0323f-110">Aşağıdaki örnek, dizin yapısındaki, adında "Logs" sözcüğünü içeren tüm dizinleri döndürür ve içine ekler `ListBox1` .</span><span class="sxs-lookup"><span data-stu-id="0323f-110">The following example returns all the directories in the directory structure that contain the word "Logs" in their name, and adds them to `ListBox1`.</span></span>

[!code-vb[VbVbcnFileAccess#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnFileAccess/VB/Class1.vb#1)]

## <a name="robust-programming"></a><span data-ttu-id="0323f-111">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="0323f-111">Robust Programming</span></span>

<span data-ttu-id="0323f-112">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="0323f-112">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="0323f-113">Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (ile başlar \\ \\ . \\ ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="0323f-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="0323f-114">Yol () olduğu için geçerli değil `Nothing` <xref:System.ArgumentNullException> .</span><span class="sxs-lookup"><span data-stu-id="0323f-114">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="0323f-115">Belirtilen Joker karakterlerden biri veya birkaçı `Nothing` , boş bir dize veya yalnızca boşluk ( <xref:System.ArgumentNullException> ) içeriyor.</span><span class="sxs-lookup"><span data-stu-id="0323f-115">One or more of the specified wildcard characters is `Nothing`, an empty string, or contains only spaces (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="0323f-116">`directory` yok ( <xref:System.IO.DirectoryNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="0323f-116">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>

- <span data-ttu-id="0323f-117">`directory` var olan bir dosyaya () işaret eder <xref:System.IO.IOException> .</span><span class="sxs-lookup"><span data-stu-id="0323f-117">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="0323f-118">Yol, sistem tarafından tanımlanan uzunluk üst sınırını ( <xref:System.IO.PathTooLongException> ) aşıyor.</span><span class="sxs-lookup"><span data-stu-id="0323f-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>

- <span data-ttu-id="0323f-119">Yoldaki bir dosya veya klasör adı iki nokta içerir (:) ya da geçersiz bir biçimde ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="0323f-119">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="0323f-120">Kullanıcı, () yolunu görüntülemek için gerekli izinlere sahip değil <xref:System.Security.SecurityException> .</span><span class="sxs-lookup"><span data-stu-id="0323f-120">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="0323f-121">Kullanıcının gerekli izinleri () yok <xref:System.UnauthorizedAccessException> .</span><span class="sxs-lookup"><span data-stu-id="0323f-121">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="0323f-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0323f-122">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [<span data-ttu-id="0323f-123">Nasıl yapılır: Belirli bir Düzendeki Dosyaları Bulma</span><span class="sxs-lookup"><span data-stu-id="0323f-123">How to: Find Files with a Specific Pattern</span></span>](how-to-find-files-with-a-specific-pattern.md)
