---
title: 'Nasıl yapılır: Metin Dosyalarına Ekleme'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], appending to files
- I/O [Visual Basic], My.Computer.FileSystem.WriteAllText method
- I/O [Visual Basic], WriteAllText method
ms.assetid: bbbd7fb5-f169-41a9-b53f-520ea9613913
ms.openlocfilehash: 53b2e4c9030e9d1dd81a4121ad3f92aad796e3e1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359961"
---
# <a name="how-to-append-to-text-files-in-visual-basic"></a><span data-ttu-id="2a766-102">Nasıl Yapılır: Visual Basic'te Metin Dosyalarına Ekleme</span><span class="sxs-lookup"><span data-stu-id="2a766-102">How to: Append to Text Files in Visual Basic</span></span>

<span data-ttu-id="2a766-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>Yöntemi, parametresinin olarak ayarlandığını belirterek bir metin dosyasına eklemek için kullanılabilir `append` `True` .</span><span class="sxs-lookup"><span data-stu-id="2a766-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method can be used to append to a text file by specifying that the `append` parameter is set to `True`.</span></span>  
  
### <a name="to-append-to-a-text-file"></a><span data-ttu-id="2a766-104">Bir metin dosyasına eklemek için</span><span class="sxs-lookup"><span data-stu-id="2a766-104">To append to a text file</span></span>  
  
- <span data-ttu-id="2a766-105">`WriteAllText`Eklenecek hedef dosyayı ve dizeyi belirterek ve parametresini olarak ayarlamak için yöntemini kullanın `append` `True` .</span><span class="sxs-lookup"><span data-stu-id="2a766-105">Use the `WriteAllText` method, specifying the target file and string to be appended and setting the `append` parameter to `True`.</span></span>  
  
     <span data-ttu-id="2a766-106">Bu örnek, dizeyi `"This is a test string."` adlı dosyaya yazar `Testfile.txt` .</span><span class="sxs-lookup"><span data-stu-id="2a766-106">This example writes the string `"This is a test string."` to the file named `Testfile.txt`.</span></span>  
  
     [!code-vb[VbFileIOWrite#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#6)]  
  
## <a name="robust-programming"></a><span data-ttu-id="2a766-107">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="2a766-107">Robust Programming</span></span>  

 <span data-ttu-id="2a766-108">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="2a766-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="2a766-109">Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (ile başlar \\ \\ . \\ ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="2a766-109">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="2a766-110">Yol () olduğu için geçerli değil `Nothing` <xref:System.ArgumentNullException> .</span><span class="sxs-lookup"><span data-stu-id="2a766-110">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="2a766-111">`File`varolmayan bir yola işaret eder ( <xref:System.IO.FileNotFoundException> veya <xref:System.IO.DirectoryNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="2a766-111">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="2a766-112">Dosya başka bir işlem tarafından kullanılıyor veya bir g/ç hatası oluştu ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="2a766-112">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="2a766-113">Yol, sistem tarafından tanımlanan uzunluk üst sınırını ( <xref:System.IO.PathTooLongException> ) aşıyor.</span><span class="sxs-lookup"><span data-stu-id="2a766-113">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="2a766-114">Yoldaki bir dosya veya dizin adı iki nokta içerir (:) ya da geçersiz bir biçimde ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="2a766-114">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="2a766-115">Kullanıcı, () yolunu görüntülemek için gerekli izinlere sahip değil <xref:System.Security.SecurityException> .</span><span class="sxs-lookup"><span data-stu-id="2a766-115">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a766-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a766-116">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [<span data-ttu-id="2a766-117">Dosyalara Yazma</span><span class="sxs-lookup"><span data-stu-id="2a766-117">Writing to Files</span></span>](writing-to-files.md)
