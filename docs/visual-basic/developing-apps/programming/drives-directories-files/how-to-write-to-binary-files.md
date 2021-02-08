---
description: 'Daha fazla bilgi: nasıl yapılır: Visual Basic Ikili dosyalara yazma'
title: 'Nasıl yapılır: İkili Dosyalara Yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
ms.openlocfilehash: a1fe18c9143c26fd40e6a1d9cde36581c2c0be12
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797334"
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a><span data-ttu-id="d64dc-103">Nasıl Yapılır: Visual Basic'te İkili Dosyalara Yazma</span><span class="sxs-lookup"><span data-stu-id="d64dc-103">How to: Write to Binary Files in Visual Basic</span></span>

<span data-ttu-id="d64dc-104"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>Yöntemi, verileri bir ikili dosyaya yazar.</span><span class="sxs-lookup"><span data-stu-id="d64dc-104">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> method writes data to a binary file.</span></span> <span data-ttu-id="d64dc-105">`append`Parametresi ise `True` , verileri dosyaya ekler; Aksi halde dosyadaki verilerin üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="d64dc-105">If the `append` parameter is `True`, it will append the data to the file; otherwise data in the file is overwritten.</span></span>

<span data-ttu-id="d64dc-106">Dosya adı hariç belirtilen yol geçerli değilse, bir <xref:System.IO.DirectoryNotFoundException> özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d64dc-106">If the specified path excluding the file name is not valid, a <xref:System.IO.DirectoryNotFoundException> exception will be thrown.</span></span> <span data-ttu-id="d64dc-107">Yol geçerliyse ancak dosya yoksa dosya oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d64dc-107">If the path is valid but the file does not exist, the file will be created.</span></span>

## <a name="to-write-to-a-binary-file"></a><span data-ttu-id="d64dc-108">İkili bir dosyaya yazmak için</span><span class="sxs-lookup"><span data-stu-id="d64dc-108">To write to a binary file</span></span>

<span data-ttu-id="d64dc-109">`WriteAllBytes`Dosya yolu ve adı ve yazılacak baytları sağlayarak yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d64dc-109">Use the `WriteAllBytes` method, supplying the file path and name and the bytes to be written.</span></span> <span data-ttu-id="d64dc-110">Bu örnek, veri dizisini `CustomerData` adlı dosyaya ekler `CollectedData.dat` .</span><span class="sxs-lookup"><span data-stu-id="d64dc-110">This example appends the data array `CustomerData` to the file named `CollectedData.dat`.</span></span>

[!code-vb[VbVbcnMyFileSystem#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#27)]

## <a name="robust-programming"></a><span data-ttu-id="d64dc-111">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="d64dc-111">Robust Programming</span></span>

<span data-ttu-id="d64dc-112">Aşağıdaki koşullar bir özel durum oluşturabilir:</span><span class="sxs-lookup"><span data-stu-id="d64dc-112">The following conditions may create an exception:</span></span>

- <span data-ttu-id="d64dc-113">Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir; yalnızca boşluk içeriyor; veya geçersiz karakterler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="d64dc-113">The path is not valid for one of the following reasons: it is a zero-length string; it contains only white space; or it contains invalid characters.</span></span> <span data-ttu-id="d64dc-114">(<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="d64dc-114">(<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="d64dc-115">Yol () olduğu için geçerli değil `Nothing` <xref:System.ArgumentNullException> .</span><span class="sxs-lookup"><span data-stu-id="d64dc-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="d64dc-116">`File` varolmayan bir yola işaret eder ( <xref:System.IO.FileNotFoundException> veya <xref:System.IO.DirectoryNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="d64dc-116">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>

- <span data-ttu-id="d64dc-117">Dosya başka bir işlem tarafından kullanılıyor veya bir g/ç hatası oluştu ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="d64dc-117">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="d64dc-118">Yol, sistem tarafından tanımlanan uzunluk üst sınırını ( <xref:System.IO.PathTooLongException> ) aşıyor.</span><span class="sxs-lookup"><span data-stu-id="d64dc-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>

- <span data-ttu-id="d64dc-119">Yoldaki bir dosya veya dizin adı iki nokta içerir (:) ya da geçersiz bir biçimde ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="d64dc-119">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="d64dc-120">Kullanıcı, () yolunu görüntülemek için gerekli izinlere sahip değil <xref:System.Security.SecurityException> .</span><span class="sxs-lookup"><span data-stu-id="d64dc-120">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="d64dc-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d64dc-121">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [<span data-ttu-id="d64dc-122">Nasıl yapılır: Dosyalara Metin Yazma</span><span class="sxs-lookup"><span data-stu-id="d64dc-122">How to: Write Text to Files</span></span>](how-to-write-text-to-files.md)
