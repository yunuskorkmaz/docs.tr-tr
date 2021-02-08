---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Visual Basic metin dosyalarına ekleme'
title: 'Nasıl yapılır: Metin Dosyalarına Ekleme'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], appending to files
- I/O [Visual Basic], My.Computer.FileSystem.WriteAllText method
- I/O [Visual Basic], WriteAllText method
ms.assetid: bbbd7fb5-f169-41a9-b53f-520ea9613913
ms.openlocfilehash: f66e1cb4ba299ee89f0d84d17d01af67650c9340
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797672"
---
# <a name="how-to-append-to-text-files-in-visual-basic"></a><span data-ttu-id="7d08d-103">Nasıl Yapılır: Visual Basic'te Metin Dosyalarına Ekleme</span><span class="sxs-lookup"><span data-stu-id="7d08d-103">How to: Append to Text Files in Visual Basic</span></span>

<span data-ttu-id="7d08d-104"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>Yöntemi, parametresinin olarak ayarlandığını belirterek bir metin dosyasına eklemek için kullanılabilir `append` `True` .</span><span class="sxs-lookup"><span data-stu-id="7d08d-104">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method can be used to append to a text file by specifying that the `append` parameter is set to `True`.</span></span>  
  
### <a name="to-append-to-a-text-file"></a><span data-ttu-id="7d08d-105">Bir metin dosyasına eklemek için</span><span class="sxs-lookup"><span data-stu-id="7d08d-105">To append to a text file</span></span>  
  
- <span data-ttu-id="7d08d-106">`WriteAllText`Eklenecek hedef dosyayı ve dizeyi belirterek ve parametresini olarak ayarlamak için yöntemini kullanın `append` `True` .</span><span class="sxs-lookup"><span data-stu-id="7d08d-106">Use the `WriteAllText` method, specifying the target file and string to be appended and setting the `append` parameter to `True`.</span></span>  
  
     <span data-ttu-id="7d08d-107">Bu örnek, dizeyi `"This is a test string."` adlı dosyaya yazar `Testfile.txt` .</span><span class="sxs-lookup"><span data-stu-id="7d08d-107">This example writes the string `"This is a test string."` to the file named `Testfile.txt`.</span></span>  
  
     [!code-vb[VbFileIOWrite#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#6)]  
  
## <a name="robust-programming"></a><span data-ttu-id="7d08d-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="7d08d-108">Robust Programming</span></span>  

 <span data-ttu-id="7d08d-109">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="7d08d-109">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="7d08d-110">Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu (ile başlar \\ \\ . \\ ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="7d08d-110">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="7d08d-111">Yol () olduğu için geçerli değil `Nothing` <xref:System.ArgumentNullException> .</span><span class="sxs-lookup"><span data-stu-id="7d08d-111">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="7d08d-112">`File` varolmayan bir yola işaret eder ( <xref:System.IO.FileNotFoundException> veya <xref:System.IO.DirectoryNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="7d08d-112">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="7d08d-113">Dosya başka bir işlem tarafından kullanılıyor veya bir g/ç hatası oluştu ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="7d08d-113">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="7d08d-114">Yol, sistem tarafından tanımlanan uzunluk üst sınırını ( <xref:System.IO.PathTooLongException> ) aşıyor.</span><span class="sxs-lookup"><span data-stu-id="7d08d-114">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="7d08d-115">Yoldaki bir dosya veya dizin adı iki nokta içerir (:) ya da geçersiz bir biçimde ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="7d08d-115">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="7d08d-116">Kullanıcı, () yolunu görüntülemek için gerekli izinlere sahip değil <xref:System.Security.SecurityException> .</span><span class="sxs-lookup"><span data-stu-id="7d08d-116">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d08d-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d08d-117">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [<span data-ttu-id="7d08d-118">Dosyalara Yazma</span><span class="sxs-lookup"><span data-stu-id="7d08d-118">Writing to Files</span></span>](writing-to-files.md)
