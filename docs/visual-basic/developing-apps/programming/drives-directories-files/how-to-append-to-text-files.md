---
title: 'Nasıl Yapılır: Metin Dosyalarına Ekleme'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], appending to files
- I/O [Visual Basic], My.Computer.FileSystem.WriteAllText method
- I/O [Visual Basic], WriteAllText method
ms.assetid: bbbd7fb5-f169-41a9-b53f-520ea9613913
ms.openlocfilehash: 97bcb5c511452e418df010f12d4b63f04251d021
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348879"
---
# <a name="how-to-append-to-text-files-in-visual-basic"></a><span data-ttu-id="d4bb5-102">Nasıl Yapılır: Visual Basic'te Metin Dosyalarına Ekleme</span><span class="sxs-lookup"><span data-stu-id="d4bb5-102">How to: Append to Text Files in Visual Basic</span></span>

<span data-ttu-id="d4bb5-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> yöntemi, `append` parametresinin `True`olarak ayarlandığını belirterek bir metin dosyasına eklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d4bb5-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method can be used to append to a text file by specifying that the `append` parameter is set to `True`.</span></span>  
  
### <a name="to-append-to-a-text-file"></a><span data-ttu-id="d4bb5-104">Bir metin dosyasına eklemek için</span><span class="sxs-lookup"><span data-stu-id="d4bb5-104">To append to a text file</span></span>  
  
- <span data-ttu-id="d4bb5-105">Eklenecek hedef dosyayı ve dizeyi belirterek `WriteAllText` yöntemini kullanın ve `append` parametresini `True`olarak ayarlamayı yapın.</span><span class="sxs-lookup"><span data-stu-id="d4bb5-105">Use the `WriteAllText` method, specifying the target file and string to be appended and setting the `append` parameter to `True`.</span></span>  
  
     <span data-ttu-id="d4bb5-106">Bu örnek `"This is a test string."` dize `Testfile.txt`adlı dosyaya yazar.</span><span class="sxs-lookup"><span data-stu-id="d4bb5-106">This example writes the string `"This is a test string."` to the file named `Testfile.txt`.</span></span>  
  
     [!code-vb[VbFileIOWrite#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#6)]  
  
## <a name="robust-programming"></a><span data-ttu-id="d4bb5-107">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="d4bb5-107">Robust Programming</span></span>  

 <span data-ttu-id="d4bb5-108">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="d4bb5-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="d4bb5-109">Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (\\\\.\\) (<xref:System.ArgumentException>) ile başlar.</span><span class="sxs-lookup"><span data-stu-id="d4bb5-109">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="d4bb5-110">Yol `Nothing` (<xref:System.ArgumentNullException>) olduğundan geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="d4bb5-110">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="d4bb5-111">`File`, varolmayan bir yola işaret eder (<xref:System.IO.FileNotFoundException> veya <xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="d4bb5-111">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="d4bb5-112">Dosya başka bir işlem tarafından kullanılıyor veya bir g/ç hatası oluştu (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="d4bb5-112">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="d4bb5-113">Yol, sistem tarafından tanımlanan uzunluk üst sınırını (<xref:System.IO.PathTooLongException>) aşıyor.</span><span class="sxs-lookup"><span data-stu-id="d4bb5-113">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="d4bb5-114">Yoldaki bir dosya veya dizin adı iki nokta içerir (:) ya da geçersiz bir biçimde (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="d4bb5-114">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="d4bb5-115">Kullanıcı, yolu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="d4bb5-115">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4bb5-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4bb5-116">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [<span data-ttu-id="d4bb5-117">Dosyalara Yazma</span><span class="sxs-lookup"><span data-stu-id="d4bb5-117">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
