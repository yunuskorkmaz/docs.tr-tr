---
title: 'Nasıl yapılır: İkili Dosyalara Yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
ms.openlocfilehash: b36da82060b930101cb54dd852d050ac0155bd10
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411557"
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a><span data-ttu-id="52ce1-102">Nasıl Yapılır: Visual Basic'te İkili Dosyalara Yazma</span><span class="sxs-lookup"><span data-stu-id="52ce1-102">How to: Write to Binary Files in Visual Basic</span></span>

<span data-ttu-id="52ce1-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>Yöntemi, verileri bir ikili dosyaya yazar.</span><span class="sxs-lookup"><span data-stu-id="52ce1-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> method writes data to a binary file.</span></span> <span data-ttu-id="52ce1-104">`append`Parametresi ise `True` , verileri dosyaya ekler; Aksi halde dosyadaki verilerin üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="52ce1-104">If the `append` parameter is `True`, it will append the data to the file; otherwise data in the file is overwritten.</span></span>

<span data-ttu-id="52ce1-105">Dosya adı hariç belirtilen yol geçerli değilse, bir <xref:System.IO.DirectoryNotFoundException> özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="52ce1-105">If the specified path excluding the file name is not valid, a <xref:System.IO.DirectoryNotFoundException> exception will be thrown.</span></span> <span data-ttu-id="52ce1-106">Yol geçerliyse ancak dosya yoksa dosya oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="52ce1-106">If the path is valid but the file does not exist, the file will be created.</span></span>

## <a name="to-write-to-a-binary-file"></a><span data-ttu-id="52ce1-107">İkili bir dosyaya yazmak için</span><span class="sxs-lookup"><span data-stu-id="52ce1-107">To write to a binary file</span></span>

<span data-ttu-id="52ce1-108">`WriteAllBytes`Dosya yolu ve adı ve yazılacak baytları sağlayarak yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="52ce1-108">Use the `WriteAllBytes` method, supplying the file path and name and the bytes to be written.</span></span> <span data-ttu-id="52ce1-109">Bu örnek, veri dizisini `CustomerData` adlı dosyaya ekler `CollectedData.dat` .</span><span class="sxs-lookup"><span data-stu-id="52ce1-109">This example appends the data array `CustomerData` to the file named `CollectedData.dat`.</span></span>

[!code-vb[VbVbcnMyFileSystem#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#27)]

## <a name="robust-programming"></a><span data-ttu-id="52ce1-110">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="52ce1-110">Robust Programming</span></span>

<span data-ttu-id="52ce1-111">Aşağıdaki koşullar bir özel durum oluşturabilir:</span><span class="sxs-lookup"><span data-stu-id="52ce1-111">The following conditions may create an exception:</span></span>

- <span data-ttu-id="52ce1-112">Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir; yalnızca boşluk içeriyor; veya geçersiz karakterler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="52ce1-112">The path is not valid for one of the following reasons: it is a zero-length string; it contains only white space; or it contains invalid characters.</span></span> <span data-ttu-id="52ce1-113">(<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="52ce1-113">(<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="52ce1-114">Yol () olduğu için geçerli değil `Nothing` <xref:System.ArgumentNullException> .</span><span class="sxs-lookup"><span data-stu-id="52ce1-114">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="52ce1-115">`File`varolmayan bir yola işaret eder ( <xref:System.IO.FileNotFoundException> veya <xref:System.IO.DirectoryNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="52ce1-115">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>

- <span data-ttu-id="52ce1-116">Dosya başka bir işlem tarafından kullanılıyor veya bir g/ç hatası oluştu ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="52ce1-116">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="52ce1-117">Yol, sistem tarafından tanımlanan uzunluk üst sınırını ( <xref:System.IO.PathTooLongException> ) aşıyor.</span><span class="sxs-lookup"><span data-stu-id="52ce1-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>

- <span data-ttu-id="52ce1-118">Yoldaki bir dosya veya dizin adı iki nokta içerir (:) ya da geçersiz bir biçimde ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="52ce1-118">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="52ce1-119">Kullanıcı, () yolunu görüntülemek için gerekli izinlere sahip değil <xref:System.Security.SecurityException> .</span><span class="sxs-lookup"><span data-stu-id="52ce1-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="52ce1-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52ce1-120">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [<span data-ttu-id="52ce1-121">Nasıl yapılır: Dosyalara Metin Yazma</span><span class="sxs-lookup"><span data-stu-id="52ce1-121">How to: Write Text to Files</span></span>](how-to-write-text-to-files.md)
