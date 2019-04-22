---
title: "Nasıl yapılır: Visual Basic'te metin dosyalarına ekleme"
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], appending to files
- I/O [Visual Basic], My.Computer.FileSystem.WriteAllText method
- I/O [Visual Basic], WriteAllText method
ms.assetid: bbbd7fb5-f169-41a9-b53f-520ea9613913
ms.openlocfilehash: 83f34e9cb669e8d2e841b13875b5237626164dd9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819846"
---
# <a name="how-to-append-to-text-files-in-visual-basic"></a><span data-ttu-id="8d117-102">Nasıl yapılır: Visual Basic'te metin dosyalarına ekleme</span><span class="sxs-lookup"><span data-stu-id="8d117-102">How to: Append to Text Files in Visual Basic</span></span>
<span data-ttu-id="8d117-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> Belirterek bir metin dosyasına eklenecek yöntemi kullanılabilir `append` parametrenin ayarlanmış `True`.</span><span class="sxs-lookup"><span data-stu-id="8d117-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method can be used to append to a text file by specifying that the `append` parameter is set to `True`.</span></span>  
  
### <a name="to-append-to-a-text-file"></a><span data-ttu-id="8d117-104">Bir metin dosyasına eklemek için</span><span class="sxs-lookup"><span data-stu-id="8d117-104">To append to a text file</span></span>  
  
-   <span data-ttu-id="8d117-105">Kullanım `WriteAllText` yöntemi, eklenecek dizeyi ve hedef dosya belirtme ve ayarı `append` parametresi `True`.</span><span class="sxs-lookup"><span data-stu-id="8d117-105">Use the `WriteAllText` method, specifying the target file and string to be appended and setting the `append` parameter to `True`.</span></span>  
  
     <span data-ttu-id="8d117-106">Bu örnek bir dize Yazar `"This is a test string."` adlı dosyaya `Testfile.txt`.</span><span class="sxs-lookup"><span data-stu-id="8d117-106">This example writes the string `"This is a test string."` to the file named `Testfile.txt`.</span></span>  
  
     [!code-vb[VbFileIOWrite#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#6)]  
  
## <a name="robust-programming"></a><span data-ttu-id="8d117-107">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="8d117-107">Robust Programming</span></span>  
 <span data-ttu-id="8d117-108">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="8d117-108">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="8d117-109">Yol aşağıdaki nedenlerden biri için geçerli değildir: sıfır uzunluklu bir dize olan, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya cihaz yoludur (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="8d117-109">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="8d117-110">Çünkü bu yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="8d117-110">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="8d117-111">`File` mevcut olmayan bir yola işaret (<xref:System.IO.FileNotFoundException> veya <xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="8d117-111">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="8d117-112">Dosya başka bir işlem tarafından kullanılıyor veya bir g/ç hatası oluşuyor (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="8d117-112">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="8d117-113">Yolun sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="8d117-113">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="8d117-114">Yolda bir dosya veya dizin adı iki nokta üst üste (:) içeriyor veya biçimi geçersiz (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="8d117-114">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="8d117-115">Kullanıcı yolu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="8d117-115">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d117-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d117-116">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [<span data-ttu-id="8d117-117">Dosyalara Yazma</span><span class="sxs-lookup"><span data-stu-id="8d117-117">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
