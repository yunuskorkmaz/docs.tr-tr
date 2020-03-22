---
title: 'Nasıl Yapılır: Dosyalara Metin Yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic]
- examples [Visual Basic], text files
ms.assetid: 304956eb-530d-4df7-b48f-9b4d1f2581a0
ms.openlocfilehash: ce1ee59ba71af6bb13e05a5bce37a2f7eee37712
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334468"
---
# <a name="how-to-write-text-to-files-in-visual-basic"></a><span data-ttu-id="f35bb-102">Nasıl Yapılır: Visual Basic'te Dosyalara Metin Yazma</span><span class="sxs-lookup"><span data-stu-id="f35bb-102">How to: Write Text to Files in Visual Basic</span></span>

<span data-ttu-id="f35bb-103">Yöntem, <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> dosyalara metin yazmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f35bb-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method can be used to write text to files.</span></span> <span data-ttu-id="f35bb-104">Belirtilen dosya yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f35bb-104">If the specified file does not exist, it is created.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="f35bb-105">Yordam</span><span class="sxs-lookup"><span data-stu-id="f35bb-105">Procedure</span></span>  
  
#### <a name="to-write-text-to-a-file"></a><span data-ttu-id="f35bb-106">Dosyaya metin yazmak için</span><span class="sxs-lookup"><span data-stu-id="f35bb-106">To write text to a file</span></span>  
  
- <span data-ttu-id="f35bb-107">Dosyaya `WriteAllText` metin yazmak için, dosyayı ve yazılacak metni belirtmek için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="f35bb-107">Use the `WriteAllText` method to write text to a file, specifying the file and text to be written.</span></span> <span data-ttu-id="f35bb-108">Bu örnek, `"This is new text."` satırı dosyadaki `test.txt`varolan herhangi bir metne ekolarak, adlı dosyaya yazar.</span><span class="sxs-lookup"><span data-stu-id="f35bb-108">This example writes the line `"This is new text."` to the file named `test.txt`, appending the text to any existing text in the file.</span></span>  
  
     [!code-vb[VbFileIOWrite#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#3)]  
  
#### <a name="to-write-a-series-of-strings-to-a-file"></a><span data-ttu-id="f35bb-109">Bir dosyaya bir dizi dize yazmak için</span><span class="sxs-lookup"><span data-stu-id="f35bb-109">To write a series of strings to a file</span></span>  
  
- <span data-ttu-id="f35bb-110">Dize koleksiyonu üzerinden döngü.</span><span class="sxs-lookup"><span data-stu-id="f35bb-110">Loop through the string collection.</span></span> <span data-ttu-id="f35bb-111">Dosyaya `WriteAllText` metin yazmak, eklenecek hedef dosya ve dizeyi belirtmek `append` ve `True`''e ayar yapmak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="f35bb-111">Use the `WriteAllText` method to write text to a file, specifying the target file and string to be added and setting `append` to `True`.</span></span>  
  
     <span data-ttu-id="f35bb-112">Bu örnek, daha iyi okunabilirlik için `FileList.txt`her biri arasında bir satır başı eklemek için `Documents and Settings` dizindeki dosyaların adlarını yazar.</span><span class="sxs-lookup"><span data-stu-id="f35bb-112">This example writes the names of the files in the `Documents and Settings` directory to `FileList.txt`, inserting a carriage return between each for better readability.</span></span>  
  
     [!code-vb[VbFileIOWrite#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#4)]  
  
## <a name="robust-programming"></a><span data-ttu-id="f35bb-113">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="f35bb-113">Robust Programming</span></span>  

 <span data-ttu-id="f35bb-114">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="f35bb-114">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="f35bb-115">Yol aşağıdaki nedenlerden biri için geçerli değildir: bir sıfır uzunlukta dize, sadece beyaz boşluk içerir, geçersiz karakterler içerir, \\ \\ya\\da bir aygıt yolu (ile başlar . ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="f35bb-115">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="f35bb-116">Yol geçerli değildir, çünkü `Nothing` <xref:System.ArgumentNullException>( ).</span><span class="sxs-lookup"><span data-stu-id="f35bb-116">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="f35bb-117">`File`olmayan bir yola işaret eder<xref:System.IO.FileNotFoundException> <xref:System.IO.DirectoryNotFoundException>( veya ).</span><span class="sxs-lookup"><span data-stu-id="f35bb-117">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="f35bb-118">Dosya başka bir işlem tarafından kullanılıyor veya G/Ç<xref:System.IO.IOException>hatası oluşur ( ).</span><span class="sxs-lookup"><span data-stu-id="f35bb-118">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="f35bb-119">Yol, sistem tarafından tanımlanan maksimum<xref:System.IO.PathTooLongException>uzunluğu aşıyor ( ).</span><span class="sxs-lookup"><span data-stu-id="f35bb-119">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="f35bb-120">Yoldaki bir dosya veya dizin adı bir üst üste (:) veya geçersiz bir biçimde<xref:System.NotSupportedException>( ).</span><span class="sxs-lookup"><span data-stu-id="f35bb-120">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="f35bb-121">Kullanıcı yolu görüntülemek için gerekli izinlerden<xref:System.Security.SecurityException>yoksundur ( ).</span><span class="sxs-lookup"><span data-stu-id="f35bb-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="f35bb-122">Disk dolu ve çağrı `WriteAllText` başarısız olur<xref:System.IO.IOException>( ).</span><span class="sxs-lookup"><span data-stu-id="f35bb-122">The disk is full, and the call to `WriteAllText` fails (<xref:System.IO.IOException>).</span></span>  
  
 <span data-ttu-id="f35bb-123">Kısmi güven bağlamında çalışıyorsanız, kod yetersiz ayrıcalıklar nedeniyle bir özel durum atabilir.</span><span class="sxs-lookup"><span data-stu-id="f35bb-123">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="f35bb-124">Daha fazla bilgi için [Kod Erişim Güvenlik Temelleri'ne](../../../../framework/misc/code-access-security-basics.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="f35bb-124">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f35bb-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f35bb-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- [<span data-ttu-id="f35bb-126">Nasıl Yapılsın: Metin Dosyalarından Okuma</span><span class="sxs-lookup"><span data-stu-id="f35bb-126">How to: Read from Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
