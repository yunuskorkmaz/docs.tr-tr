---
title: 'How to: read from fixed-width text Files'
ms.date: 07/20/2015
helpviewer_keywords:
- fixed-width text file
- reading text files [Visual Basic], fixed-width
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- text files [Visual Basic], reading
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
ms.openlocfilehash: 3cea9bfe2388f0ca510b15cb020f899b81c4603c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74334623"
---
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a><span data-ttu-id="67e0c-102">How to: read from fixed-width text files in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="67e0c-102">How to: read from fixed-width text files in Visual Basic</span></span>

<span data-ttu-id="67e0c-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span><span class="sxs-lookup"><span data-stu-id="67e0c-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span>  
  
 <span data-ttu-id="67e0c-104">The `TextFieldType` property defines whether the parsed file is a delimited file or one that has fixed-width fields of text.</span><span class="sxs-lookup"><span data-stu-id="67e0c-104">The `TextFieldType` property defines whether the parsed file is a delimited file or one that has fixed-width fields of text.</span></span> <span data-ttu-id="67e0c-105">In a fixed-width text file, the field at the end can have a variable width.</span><span class="sxs-lookup"><span data-stu-id="67e0c-105">In a fixed-width text file, the field at the end can have a variable width.</span></span> <span data-ttu-id="67e0c-106">To specify that the field at the end has a variable width, define it to have a width less than or equal to zero.</span><span class="sxs-lookup"><span data-stu-id="67e0c-106">To specify that the field at the end has a variable width, define it to have a width less than or equal to zero.</span></span>  
  
### <a name="to-parse-a-fixed-width-text-file"></a><span data-ttu-id="67e0c-107">To parse a fixed-width text file</span><span class="sxs-lookup"><span data-stu-id="67e0c-107">To parse a fixed-width text file</span></span>  
  
1. <span data-ttu-id="67e0c-108">Create a new `TextFieldParser`.</span><span class="sxs-lookup"><span data-stu-id="67e0c-108">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="67e0c-109">The following code creates the `TextFieldParser` named `Reader` and opens the file `test.log`.</span><span class="sxs-lookup"><span data-stu-id="67e0c-109">The following code creates the `TextFieldParser` named `Reader` and opens the file `test.log`.</span></span>  
  
     [!code-vb[VbFileIORead#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#9)]  
  
2. <span data-ttu-id="67e0c-110">Define the `TextFieldType` property as `FixedWidth`, defining the width and format.</span><span class="sxs-lookup"><span data-stu-id="67e0c-110">Define the `TextFieldType` property as `FixedWidth`, defining the width and format.</span></span> <span data-ttu-id="67e0c-111">The following code defines the columns of text; the first is 5 characters wide, the second 10, the third 11, and the fourth is of variable width.</span><span class="sxs-lookup"><span data-stu-id="67e0c-111">The following code defines the columns of text; the first is 5 characters wide, the second 10, the third 11, and the fourth is of variable width.</span></span>  
  
     [!code-vb[VbFileIORead#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#10)]  
  
3. <span data-ttu-id="67e0c-112">Loop through the fields in the file.</span><span class="sxs-lookup"><span data-stu-id="67e0c-112">Loop through the fields in the file.</span></span> <span data-ttu-id="67e0c-113">If any lines are corrupted, report an error and continue parsing.</span><span class="sxs-lookup"><span data-stu-id="67e0c-113">If any lines are corrupted, report an error and continue parsing.</span></span>  
  
     [!code-vb[VbFileIORead#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#11)]  
  
4. <span data-ttu-id="67e0c-114">Close the `While` and `Using` blocks with `End While` and `End Using`.</span><span class="sxs-lookup"><span data-stu-id="67e0c-114">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="67e0c-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="67e0c-115">Example</span></span>  

 <span data-ttu-id="67e0c-116">This example reads from the file `test.log`.</span><span class="sxs-lookup"><span data-stu-id="67e0c-116">This example reads from the file `test.log`.</span></span>  
  
 [!code-vb[VbFileIORead#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#13)]  
  
## <a name="robust-programming"></a><span data-ttu-id="67e0c-117">Robust programming</span><span class="sxs-lookup"><span data-stu-id="67e0c-117">Robust programming</span></span>  

 <span data-ttu-id="67e0c-118">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="67e0c-118">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="67e0c-119">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="67e0c-119">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="67e0c-120">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span><span class="sxs-lookup"><span data-stu-id="67e0c-120">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>  
  
- <span data-ttu-id="67e0c-121">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="67e0c-121">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="67e0c-122">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span><span class="sxs-lookup"><span data-stu-id="67e0c-122">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="67e0c-123">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="67e0c-123">(<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="67e0c-124">The path is too long (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="67e0c-124">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="67e0c-125">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="67e0c-125">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67e0c-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67e0c-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [<span data-ttu-id="67e0c-127">Nasıl Yapılır: Virgülle Ayrılmış Metin Dosyalarından Okuma</span><span class="sxs-lookup"><span data-stu-id="67e0c-127">How to: Read From Comma-Delimited Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="67e0c-128">Nasıl Yapılır: Birden Çok Biçimli Metin Dosyalarından Okuma</span><span class="sxs-lookup"><span data-stu-id="67e0c-128">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="67e0c-129">TextFieldParser Nesnesiyle Metin Dosyalarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="67e0c-129">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="67e0c-130">Walkthrough: Manipulating Files and Directories in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="67e0c-130">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="67e0c-131">Sorun Giderme: Metin Dosyalarını Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="67e0c-131">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
