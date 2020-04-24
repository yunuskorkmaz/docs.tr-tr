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
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a><span data-ttu-id="fd9fb-102">Nasıl Yapılır: Visual Basic'te Belirli bir Desendeki Alt Dizinleri Bulma</span><span class="sxs-lookup"><span data-stu-id="fd9fb-102">How to: Find Subdirectories with a Specific Pattern in Visual Basic</span></span>

<span data-ttu-id="fd9fb-103">Yöntemi <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> , bir dizindeki alt dizinlerin yol adlarını temsil eden salt okunurdur bir dize koleksiyonu döndürür.</span><span class="sxs-lookup"><span data-stu-id="fd9fb-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> method returns a read-only collection of strings representing the path names for the subdirectories in a directory.</span></span> <span data-ttu-id="fd9fb-104">Belirli bir kalıbı belirtmek `wildCards` için parametresini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd9fb-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span> <span data-ttu-id="fd9fb-105">Aramada alt dizinlerin içeriğini eklemek istiyorsanız, `searchType` parametresini olarak `SearchOption.SearchAllSubDirectories`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fd9fb-105">If you would like to include the contents of subdirectories in the search, set the `searchType` parameter to `SearchOption.SearchAllSubDirectories`.</span></span>

<span data-ttu-id="fd9fb-106">Belirtilen Düzenle eşleşen hiçbir dizin bulunamazsa boş bir koleksiyon döndürülür.</span><span class="sxs-lookup"><span data-stu-id="fd9fb-106">An empty collection is returned if no directories matching the specified pattern are found.</span></span>

## <a name="to-find-subdirectories-with-a-specific-pattern"></a><span data-ttu-id="fd9fb-107">Belirli bir düzene sahip alt dizinleri bulmak için</span><span class="sxs-lookup"><span data-stu-id="fd9fb-107">To find subdirectories with a specific pattern</span></span>

<span data-ttu-id="fd9fb-108">Arama yapmak `GetDirectories` istediğiniz dizinin adını ve yolunu sağlayarak yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="fd9fb-108">Use the `GetDirectories` method, supplying the name and path of the directory you want to search.</span></span> <span data-ttu-id="fd9fb-109">Aşağıdaki örnek, dizin yapısındaki, adında "Logs" sözcüğünü içeren tüm dizinleri döndürür ve içine ekler `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="fd9fb-109">The following example returns all the directories in the directory structure that contain the word "Logs" in their name, and adds them to `ListBox1`.</span></span>

[!code-vb[VbVbcnFileAccess#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnFileAccess/VB/Class1.vb#1)]

## <a name="robust-programming"></a><span data-ttu-id="fd9fb-110">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="fd9fb-110">Robust Programming</span></span>

<span data-ttu-id="fd9fb-111">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="fd9fb-111">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="fd9fb-112">Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (ile \\ \\başlar.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="fd9fb-112">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="fd9fb-113">Yol `Nothing` (<xref:System.ArgumentNullException>) olduğu için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="fd9fb-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="fd9fb-114">Belirtilen Joker karakterlerden biri veya birkaçı `Nothing`, boş bir dize veya yalnızca boşluk (<xref:System.ArgumentNullException>) içeriyor.</span><span class="sxs-lookup"><span data-stu-id="fd9fb-114">One or more of the specified wildcard characters is `Nothing`, an empty string, or contains only spaces (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="fd9fb-115">`directory`yok (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="fd9fb-115">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>

- <span data-ttu-id="fd9fb-116">`directory`var olan bir dosyaya (<xref:System.IO.IOException>) işaret eder.</span><span class="sxs-lookup"><span data-stu-id="fd9fb-116">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="fd9fb-117">Yol, sistem tarafından tanımlanan uzunluk üst sınırını (<xref:System.IO.PathTooLongException>) aşıyor.</span><span class="sxs-lookup"><span data-stu-id="fd9fb-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>

- <span data-ttu-id="fd9fb-118">Yoldaki bir dosya veya klasör adı iki nokta içerir (:) ya da geçersiz bir biçimde (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="fd9fb-118">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="fd9fb-119">Kullanıcı, (<xref:System.Security.SecurityException>) yolunu görüntülemek için gerekli izinlere sahip değil.</span><span class="sxs-lookup"><span data-stu-id="fd9fb-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="fd9fb-120">Kullanıcının gerekli izinleri (<xref:System.UnauthorizedAccessException>) yok.</span><span class="sxs-lookup"><span data-stu-id="fd9fb-120">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="fd9fb-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd9fb-121">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [<span data-ttu-id="fd9fb-122">Nasıl Yapılır: Belirli bir Düzendeki Dosyaları Bulma</span><span class="sxs-lookup"><span data-stu-id="fd9fb-122">How to: Find Files with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
