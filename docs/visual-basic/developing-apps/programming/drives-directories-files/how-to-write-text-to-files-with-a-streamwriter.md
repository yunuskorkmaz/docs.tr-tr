---
title: "Nasıl Yapılır: Visual Basic'te StreamWriter ile Dosyalara Metin Yazma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 874bb9cb88bbf25cb6208a0a33858855a7b26a49
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a><span data-ttu-id="81fab-102">Nasıl Yapılır: Visual Basic'te StreamWriter ile Dosyalara Metin Yazma</span><span class="sxs-lookup"><span data-stu-id="81fab-102">How to: Write Text to Files with a StreamWriter in Visual Basic</span></span>
<span data-ttu-id="81fab-103">Bu örnek açılır bir <xref:System.IO.StreamWriter> nesnesi ile `My.Computer.FileSystem.OpenTextFileWriter` yöntemi ve bir metin dosyasına bir dize yazmak için kullandığı <xref:System.IO.TextWriter.WriteLine%2A> yöntemi <xref:System.IO.StreamWriter> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="81fab-103">This example opens a <xref:System.IO.StreamWriter> object with the `My.Computer.FileSystem.OpenTextFileWriter` method and uses it to write a string to a text file with the <xref:System.IO.TextWriter.WriteLine%2A> method of the <xref:System.IO.StreamWriter> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81fab-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="81fab-104">Example</span></span>  
 [!code-vb[VbFileIOWrite#5](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-with-a-streamwriter_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="81fab-105">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="81fab-105">Robust Programming</span></span>  
 <span data-ttu-id="81fab-106">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="81fab-106">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="81fab-107">Dosya var ve salt okunurdur (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="81fab-107">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="81fab-108">Disk dolu olduğundan (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="81fab-108">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="81fab-109">Yol çok uzun (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="81fab-109">The pathname is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="81fab-110">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="81fab-110">.NET Framework Security</span></span>  
 <span data-ttu-id="81fab-111">Bu örnek, dosyanın zaten mevcut değilse yeni bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="81fab-111">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="81fab-112">Bir uygulama bir dosya oluşturmak gerekirse, bu uygulamanın ihtiyacı `Create` klasörü için erişim.</span><span class="sxs-lookup"><span data-stu-id="81fab-112">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="81fab-113">Dosya zaten varsa, uygulamanın yalnızca ihtiyacı `Write` erişimi, daha düşük ayrıcalık.</span><span class="sxs-lookup"><span data-stu-id="81fab-113">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="81fab-114">Mümkünse, dağıtım sırasında dosyası oluşturun ve yalnızca izni için daha güvenli olan `Read` tek bir dosyaya erişim yerine `Create` bir klasör için erişim.</span><span class="sxs-lookup"><span data-stu-id="81fab-114">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81fab-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="81fab-115">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>  
 [<span data-ttu-id="81fab-116">Nasıl yapılır: metin dosyalarını okuma</span><span class="sxs-lookup"><span data-stu-id="81fab-116">How to: Read from Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)  
 [<span data-ttu-id="81fab-117">Dosyalara yazma</span><span class="sxs-lookup"><span data-stu-id="81fab-117">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
