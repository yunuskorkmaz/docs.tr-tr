---
title: 'Nasıl yapılır: Belirli Düzendeki Dosyaları Dizine Kopyalama'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: f205d2ad-bbe5-4d55-8a40-acda21aa82dd
ms.openlocfilehash: 7e263e2c9035db54dbb58c6c78c0647d5442504e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401712"
---
# <a name="how-to-copy-files-with-a-specific-pattern-to-a-directory-in-visual-basic"></a><span data-ttu-id="56c9e-102">Nasıl Yapılır: Visual Basic'te Belirli Düzendeki Dosyaları Dizine Kopyalama</span><span class="sxs-lookup"><span data-stu-id="56c9e-102">How to: Copy Files with a Specific Pattern to a Directory in Visual Basic</span></span>

<span data-ttu-id="56c9e-103"><xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>Yöntemi, dosyaların yol adlarını temsil eden salt okunurdur bir dize koleksiyonu döndürür.</span><span class="sxs-lookup"><span data-stu-id="56c9e-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> method returns a read-only collection of strings representing the path names for the files.</span></span> <span data-ttu-id="56c9e-104">`wildCards`Belirli bir kalıbı belirtmek için parametresini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56c9e-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span>  
  
 <span data-ttu-id="56c9e-105">Eşleşen dosya bulunmazsa boş bir koleksiyon döndürülür.</span><span class="sxs-lookup"><span data-stu-id="56c9e-105">An empty collection is returned if no matching files are found.</span></span>  
  
 <span data-ttu-id="56c9e-106"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>Dosyaları bir dizine kopyalamak için yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56c9e-106">You can use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> method to copy the files to a directory.</span></span>  
  
### <a name="to-copy-files-with-a-specific-pattern-to-a-directory"></a><span data-ttu-id="56c9e-107">Belirli bir düzene sahip dosyaları dizine kopyalamak için</span><span class="sxs-lookup"><span data-stu-id="56c9e-107">To copy files with a specific pattern to a directory</span></span>  
  
1. <span data-ttu-id="56c9e-108">`GetFiles`Dosya listesini döndürmek için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="56c9e-108">Use the `GetFiles` method to return the list of files.</span></span> <span data-ttu-id="56c9e-109">Bu örnek, belirtilen dizindeki tüm. rtf dosyalarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="56c9e-109">This example returns all .rtf files in the specified directory.</span></span>  
  
     [!code-vb[VbFileIOMisc#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#36)]  
  
2. <span data-ttu-id="56c9e-110">`CopyFile`Dosyaları kopyalamak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="56c9e-110">Use the `CopyFile` method to copy the files.</span></span> <span data-ttu-id="56c9e-111">Bu örnek, dosyalarını adlı dizine kopyalar `testdirectory` .</span><span class="sxs-lookup"><span data-stu-id="56c9e-111">This example copies the files to the directory named `testdirectory`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#88)]  
  
3. <span data-ttu-id="56c9e-112">İfadesini `For` bir `Next` ifadesiyle kapatın.</span><span class="sxs-lookup"><span data-stu-id="56c9e-112">Close the `For` statement with a `Next` statement.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#89)]  
  
## <a name="example"></a><span data-ttu-id="56c9e-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="56c9e-113">Example</span></span>  

 <span data-ttu-id="56c9e-114">Aşağıdaki örnek, yukarıdaki kod parçacıklarını tüm biçimde gösterir, belirtilen dizindeki tüm. rtf dosyalarını adlı dizine kopyalar `testdirectory` .</span><span class="sxs-lookup"><span data-stu-id="56c9e-114">The following example, which presents the above snippets in complete form, copies all .rtf files in the specified directory to the directory named `testdirectory`.</span></span>  
  
 [!code-vb[VbFileIOMisc#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#37)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="56c9e-115">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="56c9e-115">.NET Framework Security</span></span>  

 <span data-ttu-id="56c9e-116">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="56c9e-116">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="56c9e-117">Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (ile başlar \\ \\ . \\ ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="56c9e-117">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="56c9e-118">Yol () olduğu için geçerli değil `Nothing` <xref:System.ArgumentNullException> .</span><span class="sxs-lookup"><span data-stu-id="56c9e-118">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="56c9e-119">Dizin yok ( <xref:System.IO.DirectoryNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="56c9e-119">The directory does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="56c9e-120">Dizin, var olan bir dosyaya () işaret eder <xref:System.IO.IOException> .</span><span class="sxs-lookup"><span data-stu-id="56c9e-120">The directory points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="56c9e-121">Yol, sistem tarafından tanımlanan uzunluk üst sınırını ( <xref:System.IO.PathTooLongException> ) aşıyor.</span><span class="sxs-lookup"><span data-stu-id="56c9e-121">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="56c9e-122">Yoldaki bir dosya veya dizin adı iki nokta içerir (:) ya da geçersiz bir biçimde ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="56c9e-122">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="56c9e-123">Kullanıcı, () yolunu görüntülemek için gerekli izinlere sahip değil <xref:System.Security.SecurityException> .</span><span class="sxs-lookup"><span data-stu-id="56c9e-123">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span> <span data-ttu-id="56c9e-124">Kullanıcının gerekli izinleri () yok <xref:System.UnauthorizedAccessException> .</span><span class="sxs-lookup"><span data-stu-id="56c9e-124">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56c9e-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56c9e-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [<span data-ttu-id="56c9e-126">Nasıl yapılır: Belirli bir Desendeki Alt Dizinleri Bulma</span><span class="sxs-lookup"><span data-stu-id="56c9e-126">How to: Find Subdirectories with a Specific Pattern</span></span>](how-to-find-subdirectories-with-a-specific-pattern.md)
- [<span data-ttu-id="56c9e-127">Sorun Giderme: Metin Dosyalarını Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="56c9e-127">Troubleshooting: Reading from and Writing to Text Files</span></span>](troubleshooting-reading-from-and-writing-to-text-files.md)
- [<span data-ttu-id="56c9e-128">Nasıl yapılır: Dizindeki Dosya Koleksiyonunu Alma</span><span class="sxs-lookup"><span data-stu-id="56c9e-128">How to: Get the Collection of Files in a Directory</span></span>](how-to-get-the-collection-of-files-in-a-directory.md)
