---
title: 'Nasıl yapılır: Visual Basic Ikili dosyalara yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
ms.openlocfilehash: ab42fa50aaf39397ac51db8a4cc3a3b00f6ce878
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039412"
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a><span data-ttu-id="d4c3b-102">Nasıl yapılır: Visual Basic Ikili dosyalara yazma</span><span class="sxs-lookup"><span data-stu-id="d4c3b-102">How to: Write to Binary Files in Visual Basic</span></span>

<span data-ttu-id="d4c3b-103">Yöntemi <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> , verileri bir ikili dosyaya yazar.</span><span class="sxs-lookup"><span data-stu-id="d4c3b-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> method writes data to a binary file.</span></span> <span data-ttu-id="d4c3b-104">`append` Parametresi ise`True`, verileri dosyaya ekler; Aksi halde dosyadaki verilerin üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="d4c3b-104">If the `append` parameter is `True`, it will append the data to the file; otherwise data in the file is overwritten.</span></span>

<span data-ttu-id="d4c3b-105">Dosya adı hariç belirtilen yol geçerli değilse, bir <xref:System.IO.DirectoryNotFoundException> özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d4c3b-105">If the specified path excluding the file name is not valid, a <xref:System.IO.DirectoryNotFoundException> exception will be thrown.</span></span> <span data-ttu-id="d4c3b-106">Yol geçerliyse ancak dosya yoksa dosya oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d4c3b-106">If the path is valid but the file does not exist, the file will be created.</span></span>

## <a name="to-write-to-a-binary-file"></a><span data-ttu-id="d4c3b-107">İkili bir dosyaya yazmak için</span><span class="sxs-lookup"><span data-stu-id="d4c3b-107">To write to a binary file</span></span>

<span data-ttu-id="d4c3b-108">Dosya yolu ve adı ve yazılacak baytları sağlayarak yönteminikullanın.`WriteAllBytes`</span><span class="sxs-lookup"><span data-stu-id="d4c3b-108">Use the `WriteAllBytes` method, supplying the file path and name and the bytes to be written.</span></span> <span data-ttu-id="d4c3b-109">Bu örnek, veri dizisini `CustomerData` adlı `CollectedData.dat`dosyaya ekler.</span><span class="sxs-lookup"><span data-stu-id="d4c3b-109">This example appends the data array `CustomerData` to the file named `CollectedData.dat`.</span></span>

[!code-vb[VbVbcnMyFileSystem#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#27)]

## <a name="robust-programming"></a><span data-ttu-id="d4c3b-110">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="d4c3b-110">Robust Programming</span></span>

<span data-ttu-id="d4c3b-111">Aşağıdaki koşullar bir özel durum oluşturabilir:</span><span class="sxs-lookup"><span data-stu-id="d4c3b-111">The following conditions may create an exception:</span></span>

- <span data-ttu-id="d4c3b-112">Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir; yalnızca boşluk içeriyor; veya geçersiz karakterler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="d4c3b-112">The path is not valid for one of the following reasons: it is a zero-length string; it contains only white space; or it contains invalid characters.</span></span> <span data-ttu-id="d4c3b-113">(<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="d4c3b-113">(<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="d4c3b-114">Yol `Nothing` (<xref:System.ArgumentNullException>) olduğu için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="d4c3b-114">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="d4c3b-115">`File`varolmayan bir yola işaret eder (<xref:System.IO.FileNotFoundException> veya <xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="d4c3b-115">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>

- <span data-ttu-id="d4c3b-116">Dosya başka bir işlem tarafından kullanılıyor veya bir g/ç hatası oluştu (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="d4c3b-116">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="d4c3b-117">Yol, sistem tarafından tanımlanan uzunluk üst sınırını (<xref:System.IO.PathTooLongException>) aşıyor.</span><span class="sxs-lookup"><span data-stu-id="d4c3b-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>

- <span data-ttu-id="d4c3b-118">Yoldaki bir dosya veya dizin adı iki nokta içerir (:) ya da geçersiz bir biçimde (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="d4c3b-118">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="d4c3b-119">Kullanıcı, (<xref:System.Security.SecurityException>) yolunu görüntülemek için gerekli izinlere sahip değil.</span><span class="sxs-lookup"><span data-stu-id="d4c3b-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="d4c3b-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4c3b-120">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [<span data-ttu-id="d4c3b-121">Nasıl yapılır: Dosyalara metin yazma</span><span class="sxs-lookup"><span data-stu-id="d4c3b-121">How to: Write Text to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)
