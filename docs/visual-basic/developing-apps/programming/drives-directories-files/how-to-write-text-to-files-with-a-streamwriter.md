---
description: 'Daha fazla bilgi edinin: nasıl yapılır: StreamWriter ile dosyalara metin yazma Visual Basic'
title: 'Nasıl yapılır: StreamWriter ile Dosyalara Metin Yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
ms.openlocfilehash: d5528d0b5e7de40062558d29c0d3bebc227583a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797360"
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a><span data-ttu-id="09dce-103">Nasıl Yapılır: Visual Basic'te StreamWriter ile Dosyalara Metin Yazma</span><span class="sxs-lookup"><span data-stu-id="09dce-103">How to: Write Text to Files with a StreamWriter in Visual Basic</span></span>

<span data-ttu-id="09dce-104">Bu örnek <xref:System.IO.StreamWriter> , yöntemi ile bir nesnesi açar `My.Computer.FileSystem.OpenTextFileWriter` ve onu sınıfının yöntemiyle bir metin dosyasına bir dize yazmak için kullanır <xref:System.IO.TextWriter.WriteLine%2A> <xref:System.IO.StreamWriter> .</span><span class="sxs-lookup"><span data-stu-id="09dce-104">This example opens a <xref:System.IO.StreamWriter> object with the `My.Computer.FileSystem.OpenTextFileWriter` method and uses it to write a string to a text file with the <xref:System.IO.TextWriter.WriteLine%2A> method of the <xref:System.IO.StreamWriter> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09dce-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="09dce-105">Example</span></span>  

 [!code-vb[VbFileIOWrite#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#5)]  
  
## <a name="robust-programming"></a><span data-ttu-id="09dce-106">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="09dce-106">Robust Programming</span></span>  

 <span data-ttu-id="09dce-107">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="09dce-107">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="09dce-108">Dosya var ve salt okunurdur ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="09dce-108">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="09dce-109">Disk dolu ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="09dce-109">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="09dce-110">Yol adı çok uzun ( <xref:System.IO.PathTooLongException> ).</span><span class="sxs-lookup"><span data-stu-id="09dce-110">The pathname is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="09dce-111">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="09dce-111">.NET Framework Security</span></span>  

 <span data-ttu-id="09dce-112">Bu örnek, dosya zaten yoksa yeni bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="09dce-112">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="09dce-113">Uygulamanın bir dosya oluşturması gerekiyorsa, bu uygulamanın `Create` klasöre erişmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="09dce-113">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="09dce-114">Dosya zaten mevcutsa, uygulamanın yalnızca daha `Write` az bir ayrıcalığa erişmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="09dce-114">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="09dce-115">Mümkün olduğunda, dağıtım sırasında dosyanın oluşturulması daha güvenlidir ve `Read` `Create` bir klasör için erişim yerine yalnızca tek bir dosyaya erişim izni verir.</span><span class="sxs-lookup"><span data-stu-id="09dce-115">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09dce-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09dce-116">See also</span></span>

- <xref:System.IO.StreamWriter>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- [<span data-ttu-id="09dce-117">Nasıl yapılır: metin dosyalarından okuma</span><span class="sxs-lookup"><span data-stu-id="09dce-117">How to: Read from Text Files</span></span>](how-to-read-from-text-files.md)
- [<span data-ttu-id="09dce-118">Dosyalara Yazma</span><span class="sxs-lookup"><span data-stu-id="09dce-118">Writing to Files</span></span>](writing-to-files.md)
