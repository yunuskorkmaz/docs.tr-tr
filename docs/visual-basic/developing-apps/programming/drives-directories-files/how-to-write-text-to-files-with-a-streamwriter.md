---
title: "Nasıl yapılır: Visual Basic'te StreamWriter ile dosyalara metin yazma"
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
ms.openlocfilehash: 39c6ad59ad965f566c77f72dd4a97335494d6382
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54678531"
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a><span data-ttu-id="edb3a-102">Nasıl yapılır: Visual Basic'te StreamWriter ile dosyalara metin yazma</span><span class="sxs-lookup"><span data-stu-id="edb3a-102">How to: Write Text to Files with a StreamWriter in Visual Basic</span></span>
<span data-ttu-id="edb3a-103">Bu örnek açılır bir <xref:System.IO.StreamWriter> nesnesi ile `My.Computer.FileSystem.OpenTextFileWriter` yöntemi ve bir dize içeren bir metin dosyası yazmak için kullandığı <xref:System.IO.TextWriter.WriteLine%2A> yöntemi <xref:System.IO.StreamWriter> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="edb3a-103">This example opens a <xref:System.IO.StreamWriter> object with the `My.Computer.FileSystem.OpenTextFileWriter` method and uses it to write a string to a text file with the <xref:System.IO.TextWriter.WriteLine%2A> method of the <xref:System.IO.StreamWriter> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="edb3a-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="edb3a-104">Example</span></span>  
 [!code-vb[VbFileIOWrite#5](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-with-a-streamwriter_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="edb3a-105">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="edb3a-105">Robust Programming</span></span>  
 <span data-ttu-id="edb3a-106">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="edb3a-106">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="edb3a-107">Dosya var ve salt okunur (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="edb3a-107">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="edb3a-108">Disk dolu (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="edb3a-108">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="edb3a-109">Yol çok uzun (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="edb3a-109">The pathname is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="edb3a-110">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="edb3a-110">.NET Framework Security</span></span>  
 <span data-ttu-id="edb3a-111">Bu örnek, bir dosya zaten mevcut değilse yeni bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="edb3a-111">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="edb3a-112">Bir uygulama bir dosya oluşturması gerekiyorsa, bu uygulamayı gerekli `Create` klasörü için erişim.</span><span class="sxs-lookup"><span data-stu-id="edb3a-112">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="edb3a-113">Dosya zaten varsa, uygulamanın yalnızca ihtiyacı `Write` erişim, daha az ayrıcalıkla.</span><span class="sxs-lookup"><span data-stu-id="edb3a-113">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="edb3a-114">Mümkün olan yerlerde, dosyayı dağıtım sırasında oluşturmak ve yalnızca vermek için daha güvenli olan `Read` tek bir dosyaya erişimi yerine `Create` erişim için bir klasör.</span><span class="sxs-lookup"><span data-stu-id="edb3a-114">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edb3a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="edb3a-115">See also</span></span>
- <xref:System.IO.StreamWriter>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- [<span data-ttu-id="edb3a-116">Nasıl yapılır: Metin dosyalarını okuma</span><span class="sxs-lookup"><span data-stu-id="edb3a-116">How to: Read from Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
- [<span data-ttu-id="edb3a-117">Dosyalara Yazma</span><span class="sxs-lookup"><span data-stu-id="edb3a-117">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
