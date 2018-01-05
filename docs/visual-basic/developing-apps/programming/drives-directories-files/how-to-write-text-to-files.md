---
title: "Nasıl Yapılır: Visual Basic'te Dosyalara Metin Yazma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic]
- examples [Visual Basic], text files
ms.assetid: 304956eb-530d-4df7-b48f-9b4d1f2581a0
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4fbbe0ec007911460dc2bda8c681775da9a6cb91
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-write-text-to-files-in-visual-basic"></a><span data-ttu-id="978dd-102">Nasıl Yapılır: Visual Basic'te Dosyalara Metin Yazma</span><span class="sxs-lookup"><span data-stu-id="978dd-102">How to: Write Text to Files in Visual Basic</span></span>
<span data-ttu-id="978dd-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> Yöntemi, dosyalara metin yazma için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="978dd-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method can be used to write text to files.</span></span> <span data-ttu-id="978dd-104">Belirtilen dosya mevcut değilse oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="978dd-104">If the specified file does not exist, it is created.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="978dd-105">Yordam</span><span class="sxs-lookup"><span data-stu-id="978dd-105">Procedure</span></span>  
  
#### <a name="to-write-text-to-a-file"></a><span data-ttu-id="978dd-106">Bir dosyaya metin yazma</span><span class="sxs-lookup"><span data-stu-id="978dd-106">To write text to a file</span></span>  
  
-   <span data-ttu-id="978dd-107">Kullanım `WriteAllText` metin dosyasını ve yazılacak metnini belirten bir dosyaya yazmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="978dd-107">Use the `WriteAllText` method to write text to a file, specifying the file and text to be written.</span></span> <span data-ttu-id="978dd-108">Bu örnek satır Yazar `"This is new text."` adlı dosyaya `test.txt`, varolan herhangi bir metin dosyasındaki metni ekleme.</span><span class="sxs-lookup"><span data-stu-id="978dd-108">This example writes the line `"This is new text."` to the file named `test.txt`, appending the text to any existing text in the file.</span></span>  
  
     [!code-vb[VbFileIOWrite#3](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files_1.vb)]  
  
#### <a name="to-write-a-series-of-strings-to-a-file"></a><span data-ttu-id="978dd-109">Dizeleri bir dizi bir dosyaya yazmak için</span><span class="sxs-lookup"><span data-stu-id="978dd-109">To write a series of strings to a file</span></span>  
  
-   <span data-ttu-id="978dd-110">Dize toplulukta döngüsü.</span><span class="sxs-lookup"><span data-stu-id="978dd-110">Loop through the string collection.</span></span> <span data-ttu-id="978dd-111">Kullanım `WriteAllText` metni eklenecek dize ve hedef dosya belirten bir dosyaya yazmak için yöntem ve ayar `append` için `True`.</span><span class="sxs-lookup"><span data-stu-id="978dd-111">Use the `WriteAllText` method to write text to a file, specifying the target file and string to be added and setting `append` to `True`.</span></span>  
  
     <span data-ttu-id="978dd-112">Bu örnek, dosya adlarını Yazar `Documents and Settings` dizininden `FileList.txt`, satır ekleme dönüş her okunabilirliği arasında.</span><span class="sxs-lookup"><span data-stu-id="978dd-112">This example writes the names of the files in the `Documents and Settings` directory to `FileList.txt`, inserting a carriage return between each for better readability.</span></span>  
  
     [!code-vb[VbFileIOWrite#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files_2.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="978dd-113">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="978dd-113">Robust Programming</span></span>  
 <span data-ttu-id="978dd-114">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="978dd-114">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="978dd-115">Yolu şu nedenlerden biri için geçerli değil: sıfır uzunlukta bir dize değil, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir aygıt yol olduğundan (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="978dd-115">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="978dd-116">Çünkü yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="978dd-116">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="978dd-117">`File`var olmayan bir yola işaret eden (<xref:System.IO.FileNotFoundException> veya <xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="978dd-117">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="978dd-118">Dosya başka bir işlem tarafından kullanılıyor veya bir g/ç hatası oluştuğunda (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="978dd-118">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="978dd-119">Yolu sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="978dd-119">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="978dd-120">Yolda bir dosya veya dizin adı biçimi geçersiz veya iki nokta üst üste (:) içerir (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="978dd-120">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="978dd-121">Kullanıcı yolunu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="978dd-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="978dd-122">Tam ve çağrısı disktir `WriteAllText` başarısız (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="978dd-122">The disk is full, and the call to `WriteAllText` fails (<xref:System.IO.IOException>).</span></span>  
  
 <span data-ttu-id="978dd-123">Kısmi güven bağlamda çalıştırıyorsanız, kodu nedeniyle yeterli ayrıcalığa sahip bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="978dd-123">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="978dd-124">Daha fazla bilgi için bkz: [kod erişim güvenliği Temelleri](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="978dd-124">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="978dd-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="978dd-125">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>  
 [<span data-ttu-id="978dd-126">Nasıl yapılır: metin dosyalarını okuma</span><span class="sxs-lookup"><span data-stu-id="978dd-126">How to: Read from Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
