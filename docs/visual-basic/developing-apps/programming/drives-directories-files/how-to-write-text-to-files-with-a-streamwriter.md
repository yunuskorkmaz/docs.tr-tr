---
title: 'Nasıl Yapılır: StreamWriter ile Dosyalara Metin Yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
ms.openlocfilehash: 869e29263abcdd8525b2c372c7bb466e3e21fc65
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74334493"
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a><span data-ttu-id="c79fe-102">Nasıl Yapılır: Visual Basic'te StreamWriter ile Dosyalara Metin Yazma</span><span class="sxs-lookup"><span data-stu-id="c79fe-102">How to: Write Text to Files with a StreamWriter in Visual Basic</span></span>

<span data-ttu-id="c79fe-103">This example opens a <xref:System.IO.StreamWriter> object with the `My.Computer.FileSystem.OpenTextFileWriter` method and uses it to write a string to a text file with the <xref:System.IO.TextWriter.WriteLine%2A> method of the <xref:System.IO.StreamWriter> class.</span><span class="sxs-lookup"><span data-stu-id="c79fe-103">This example opens a <xref:System.IO.StreamWriter> object with the `My.Computer.FileSystem.OpenTextFileWriter` method and uses it to write a string to a text file with the <xref:System.IO.TextWriter.WriteLine%2A> method of the <xref:System.IO.StreamWriter> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c79fe-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="c79fe-104">Example</span></span>  

 [!code-vb[VbFileIOWrite#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#5)]  
  
## <a name="robust-programming"></a><span data-ttu-id="c79fe-105">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="c79fe-105">Robust Programming</span></span>  

 <span data-ttu-id="c79fe-106">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="c79fe-106">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="c79fe-107">The file exists and is read-only (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="c79fe-107">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="c79fe-108">The disk is full (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="c79fe-108">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="c79fe-109">The pathname is too long (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="c79fe-109">The pathname is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="c79fe-110">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c79fe-110">.NET Framework Security</span></span>  

 <span data-ttu-id="c79fe-111">This example creates a new file, if the file does not already exist.</span><span class="sxs-lookup"><span data-stu-id="c79fe-111">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="c79fe-112">If an application needs to create a file, that application needs `Create` access for the folder.</span><span class="sxs-lookup"><span data-stu-id="c79fe-112">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="c79fe-113">If the file already exists, the application needs only `Write` access, a lesser privilege.</span><span class="sxs-lookup"><span data-stu-id="c79fe-113">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="c79fe-114">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span><span class="sxs-lookup"><span data-stu-id="c79fe-114">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c79fe-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c79fe-115">See also</span></span>

- <xref:System.IO.StreamWriter>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- [<span data-ttu-id="c79fe-116">How to: Read from Text Files</span><span class="sxs-lookup"><span data-stu-id="c79fe-116">How to: Read from Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
- [<span data-ttu-id="c79fe-117">Dosyalara Yazma</span><span class="sxs-lookup"><span data-stu-id="c79fe-117">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
