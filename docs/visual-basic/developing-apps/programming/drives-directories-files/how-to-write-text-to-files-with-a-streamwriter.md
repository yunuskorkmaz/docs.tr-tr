---
title: "Nasıl yapılır: Visual Basic'te StreamWriter ile dosyalara metin yazma"
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
ms.openlocfilehash: ca792106bdd341fa4be8f3554ce70cd7d3f22522
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58816074"
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a><span data-ttu-id="97cca-102">Nasıl yapılır: Visual Basic'te StreamWriter ile dosyalara metin yazma</span><span class="sxs-lookup"><span data-stu-id="97cca-102">How to: Write Text to Files with a StreamWriter in Visual Basic</span></span>
<span data-ttu-id="97cca-103">Bu örnek açılır bir <xref:System.IO.StreamWriter> nesnesi ile `My.Computer.FileSystem.OpenTextFileWriter` yöntemi ve bir dize içeren bir metin dosyası yazmak için kullandığı <xref:System.IO.TextWriter.WriteLine%2A> yöntemi <xref:System.IO.StreamWriter> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="97cca-103">This example opens a <xref:System.IO.StreamWriter> object with the `My.Computer.FileSystem.OpenTextFileWriter` method and uses it to write a string to a text file with the <xref:System.IO.TextWriter.WriteLine%2A> method of the <xref:System.IO.StreamWriter> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97cca-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="97cca-104">Example</span></span>  
 [!code-vb[VbFileIOWrite#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#5)]  
  
## <a name="robust-programming"></a><span data-ttu-id="97cca-105">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="97cca-105">Robust Programming</span></span>  
 <span data-ttu-id="97cca-106">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="97cca-106">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="97cca-107">Dosya var ve salt okunur (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="97cca-107">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="97cca-108">Disk dolu (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="97cca-108">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="97cca-109">Yol çok uzun (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="97cca-109">The pathname is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="97cca-110">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="97cca-110">.NET Framework Security</span></span>  
 <span data-ttu-id="97cca-111">Bu örnek, bir dosya zaten mevcut değilse yeni bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="97cca-111">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="97cca-112">Bir uygulama bir dosya oluşturması gerekiyorsa, bu uygulamayı gerekli `Create` klasörü için erişim.</span><span class="sxs-lookup"><span data-stu-id="97cca-112">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="97cca-113">Dosya zaten varsa, uygulamanın yalnızca ihtiyacı `Write` erişim, daha az ayrıcalıkla.</span><span class="sxs-lookup"><span data-stu-id="97cca-113">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="97cca-114">Mümkün olan yerlerde, dosyayı dağıtım sırasında oluşturmak ve yalnızca vermek için daha güvenli olan `Read` tek bir dosyaya erişimi yerine `Create` erişim için bir klasör.</span><span class="sxs-lookup"><span data-stu-id="97cca-114">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97cca-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97cca-115">See also</span></span>

- <xref:System.IO.StreamWriter>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- [<span data-ttu-id="97cca-116">Nasıl yapılır: Metin dosyalarını okuma</span><span class="sxs-lookup"><span data-stu-id="97cca-116">How to: Read from Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
- [<span data-ttu-id="97cca-117">Dosyalara Yazma</span><span class="sxs-lookup"><span data-stu-id="97cca-117">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
