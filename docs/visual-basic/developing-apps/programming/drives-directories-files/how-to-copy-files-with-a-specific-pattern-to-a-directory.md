---
title: 'Nasıl Yapılır: Belirli Düzendeki Dosyaları Dizine Kopyalama'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: f205d2ad-bbe5-4d55-8a40-acda21aa82dd
ms.openlocfilehash: ee3951e967436a1b8aec09b8e42dc6d1b547bc02
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348848"
---
# <a name="how-to-copy-files-with-a-specific-pattern-to-a-directory-in-visual-basic"></a><span data-ttu-id="eab3a-102">Nasıl Yapılır: Visual Basic'te Belirli Düzendeki Dosyaları Dizine Kopyalama</span><span class="sxs-lookup"><span data-stu-id="eab3a-102">How to: Copy Files with a Specific Pattern to a Directory in Visual Basic</span></span>

<span data-ttu-id="eab3a-103"><xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> yöntemi, dosyaların yol adlarını temsil eden salt okunurdur bir dize koleksiyonu döndürür.</span><span class="sxs-lookup"><span data-stu-id="eab3a-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> method returns a read-only collection of strings representing the path names for the files.</span></span> <span data-ttu-id="eab3a-104">Belirli bir kalıbı belirtmek için `wildCards` parametresini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eab3a-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span>  
  
 <span data-ttu-id="eab3a-105">Eşleşen dosya bulunmazsa boş bir koleksiyon döndürülür.</span><span class="sxs-lookup"><span data-stu-id="eab3a-105">An empty collection is returned if no matching files are found.</span></span>  
  
 <span data-ttu-id="eab3a-106">Dosyaları bir dizine kopyalamak için <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eab3a-106">You can use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> method to copy the files to a directory.</span></span>  
  
### <a name="to-copy-files-with-a-specific-pattern-to-a-directory"></a><span data-ttu-id="eab3a-107">Belirli bir düzene sahip dosyaları dizine kopyalamak için</span><span class="sxs-lookup"><span data-stu-id="eab3a-107">To copy files with a specific pattern to a directory</span></span>  
  
1. <span data-ttu-id="eab3a-108">Dosya listesini döndürmek için `GetFiles` yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="eab3a-108">Use the `GetFiles` method to return the list of files.</span></span> <span data-ttu-id="eab3a-109">Bu örnek, belirtilen dizindeki tüm. rtf dosyalarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="eab3a-109">This example returns all .rtf files in the specified directory.</span></span>  
  
     [!code-vb[VbFileIOMisc#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#36)]  
  
2. <span data-ttu-id="eab3a-110">Dosyaları kopyalamak için `CopyFile` yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="eab3a-110">Use the `CopyFile` method to copy the files.</span></span> <span data-ttu-id="eab3a-111">Bu örnek, dosyaları `testdirectory`adlı dizine kopyalar.</span><span class="sxs-lookup"><span data-stu-id="eab3a-111">This example copies the files to the directory named `testdirectory`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#88)]  
  
3. <span data-ttu-id="eab3a-112">`Next` ifadesiyle `For` ifadesini kapatın.</span><span class="sxs-lookup"><span data-stu-id="eab3a-112">Close the `For` statement with a `Next` statement.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#89)]  
  
## <a name="example"></a><span data-ttu-id="eab3a-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="eab3a-113">Example</span></span>  

 <span data-ttu-id="eab3a-114">Aşağıdaki örnek, yukarıdaki kod parçacıklarını tamamlanmış bir biçimde sunar, belirtilen dizindeki tüm. rtf dosyalarını `testdirectory`adlı dizine kopyalar.</span><span class="sxs-lookup"><span data-stu-id="eab3a-114">The following example, which presents the above snippets in complete form, copies all .rtf files in the specified directory to the directory named `testdirectory`.</span></span>  
  
 [!code-vb[VbFileIOMisc#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#37)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="eab3a-115">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="eab3a-115">.NET Framework Security</span></span>  

 <span data-ttu-id="eab3a-116">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="eab3a-116">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="eab3a-117">Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (\\\\.\\) (<xref:System.ArgumentException>) ile başlar.</span><span class="sxs-lookup"><span data-stu-id="eab3a-117">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="eab3a-118">Yol `Nothing` (<xref:System.ArgumentNullException>) olduğundan geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="eab3a-118">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="eab3a-119">Dizin yok (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="eab3a-119">The directory does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="eab3a-120">Dizin, var olan bir dosyaya (<xref:System.IO.IOException>) işaret eder.</span><span class="sxs-lookup"><span data-stu-id="eab3a-120">The directory points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="eab3a-121">Yol, sistem tarafından tanımlanan uzunluk üst sınırını (<xref:System.IO.PathTooLongException>) aşıyor.</span><span class="sxs-lookup"><span data-stu-id="eab3a-121">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="eab3a-122">Yoldaki bir dosya veya dizin adı iki nokta içerir (:) ya da geçersiz bir biçimde (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="eab3a-122">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="eab3a-123">Kullanıcı, yolu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="eab3a-123">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span> <span data-ttu-id="eab3a-124">Kullanıcının gerekli izinleri yok (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="eab3a-124">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eab3a-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eab3a-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [<span data-ttu-id="eab3a-126">Nasıl Yapılır: Belirli bir Desendeki Alt Dizinleri Bulma</span><span class="sxs-lookup"><span data-stu-id="eab3a-126">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [<span data-ttu-id="eab3a-127">Sorun Giderme: Metin Dosyalarını Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="eab3a-127">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [<span data-ttu-id="eab3a-128">Nasıl Yapılır: Dizindeki Dosya Koleksiyonunu Alma</span><span class="sxs-lookup"><span data-stu-id="eab3a-128">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
