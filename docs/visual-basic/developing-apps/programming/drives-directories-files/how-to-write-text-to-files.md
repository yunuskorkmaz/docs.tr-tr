---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Visual Basic dosyalara metin yazma'
title: 'Nasıl yapılır: Dosyalara Metin Yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic]
- examples [Visual Basic], text files
ms.assetid: 304956eb-530d-4df7-b48f-9b4d1f2581a0
ms.openlocfilehash: 3f94999c1d20002074ecf57577d3402c350248ec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797347"
---
# <a name="how-to-write-text-to-files-in-visual-basic"></a><span data-ttu-id="2283e-103">Nasıl Yapılır: Visual Basic'te Dosyalara Metin Yazma</span><span class="sxs-lookup"><span data-stu-id="2283e-103">How to: Write Text to Files in Visual Basic</span></span>

<span data-ttu-id="2283e-104"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>Yöntemi, dosyalara metin yazmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2283e-104">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method can be used to write text to files.</span></span> <span data-ttu-id="2283e-105">Belirtilen dosya yoksa, oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2283e-105">If the specified file does not exist, it is created.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="2283e-106">Yordam</span><span class="sxs-lookup"><span data-stu-id="2283e-106">Procedure</span></span>  
  
#### <a name="to-write-text-to-a-file"></a><span data-ttu-id="2283e-107">Bir dosyaya metin yazmak için</span><span class="sxs-lookup"><span data-stu-id="2283e-107">To write text to a file</span></span>  
  
- <span data-ttu-id="2283e-108">`WriteAllText`Bir dosyaya metin yazmak için yöntemini kullanın, yazılacak dosyayı ve metni belirtin.</span><span class="sxs-lookup"><span data-stu-id="2283e-108">Use the `WriteAllText` method to write text to a file, specifying the file and text to be written.</span></span> <span data-ttu-id="2283e-109">Bu örnek `"This is new text."` `test.txt` , metni dosyasındaki varolan metne ekleyerek satırı adlı dosyaya yazar.</span><span class="sxs-lookup"><span data-stu-id="2283e-109">This example writes the line `"This is new text."` to the file named `test.txt`, appending the text to any existing text in the file.</span></span>  
  
     [!code-vb[VbFileIOWrite#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#3)]  
  
#### <a name="to-write-a-series-of-strings-to-a-file"></a><span data-ttu-id="2283e-110">Bir dosyaya bir dizi dize yazmak için</span><span class="sxs-lookup"><span data-stu-id="2283e-110">To write a series of strings to a file</span></span>  
  
- <span data-ttu-id="2283e-111">Dize koleksiyonu aracılığıyla döngü yapın.</span><span class="sxs-lookup"><span data-stu-id="2283e-111">Loop through the string collection.</span></span> <span data-ttu-id="2283e-112">`WriteAllText`Eklenecek hedef dosyayı ve dizeyi belirterek bir dosyaya metin yazmak için yöntemini kullanın `append` `True` .</span><span class="sxs-lookup"><span data-stu-id="2283e-112">Use the `WriteAllText` method to write text to a file, specifying the target file and string to be added and setting `append` to `True`.</span></span>  
  
     <span data-ttu-id="2283e-113">Bu örnek, dizinde bulunan dosyaların adlarını `Documents and Settings` `FileList.txt` , daha iyi okunabilirlik için her biri arasına bir satır başı ekleyerek yazar.</span><span class="sxs-lookup"><span data-stu-id="2283e-113">This example writes the names of the files in the `Documents and Settings` directory to `FileList.txt`, inserting a carriage return between each for better readability.</span></span>  
  
     [!code-vb[VbFileIOWrite#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#4)]  
  
## <a name="robust-programming"></a><span data-ttu-id="2283e-114">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="2283e-114">Robust Programming</span></span>  

 <span data-ttu-id="2283e-115">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="2283e-115">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="2283e-116">Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (ile başlar \\ \\ . \\ ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="2283e-116">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="2283e-117">Yol () olduğu için geçerli değil `Nothing` <xref:System.ArgumentNullException> .</span><span class="sxs-lookup"><span data-stu-id="2283e-117">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="2283e-118">`File` varolmayan bir yola işaret eder ( <xref:System.IO.FileNotFoundException> veya <xref:System.IO.DirectoryNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="2283e-118">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="2283e-119">Dosya başka bir işlem tarafından kullanılıyor veya bir g/ç hatası oluştu ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="2283e-119">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="2283e-120">Yol, sistem tarafından tanımlanan uzunluk üst sınırını ( <xref:System.IO.PathTooLongException> ) aşıyor.</span><span class="sxs-lookup"><span data-stu-id="2283e-120">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="2283e-121">Yoldaki bir dosya veya dizin adı iki nokta içerir (:) ya da geçersiz bir biçimde ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="2283e-121">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="2283e-122">Kullanıcı, () yolunu görüntülemek için gerekli izinlere sahip değil <xref:System.Security.SecurityException> .</span><span class="sxs-lookup"><span data-stu-id="2283e-122">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="2283e-123">Disk dolu ve `WriteAllText` () çağrısı başarısız olur <xref:System.IO.IOException> .</span><span class="sxs-lookup"><span data-stu-id="2283e-123">The disk is full, and the call to `WriteAllText` fails (<xref:System.IO.IOException>).</span></span>  
  
 <span data-ttu-id="2283e-124">Kısmi güven bağlamında çalıştırıyorsanız, yetersiz ayrıcalıklar nedeniyle kod bir özel durum oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="2283e-124">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="2283e-125">Daha fazla bilgi için bkz. [kod erişimi güvenlik temelleri](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="2283e-125">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2283e-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2283e-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- [<span data-ttu-id="2283e-127">Nasıl yapılır: metin dosyalarından okuma</span><span class="sxs-lookup"><span data-stu-id="2283e-127">How to: Read from Text Files</span></span>](how-to-read-from-text-files.md)
