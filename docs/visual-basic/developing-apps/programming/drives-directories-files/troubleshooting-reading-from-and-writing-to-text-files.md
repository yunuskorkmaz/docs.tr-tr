---
title: "Sorun giderme: Okuma ve yazma metin dosyalarına (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- troubleshooting file I/O
- writing text to files [Visual Basic], troubleshooting
- troubleshooting Visual Basic, text files
- I/O [Visual Basic], troubleshooting text files
- writing to files [Visual Basic], troubleshooting
- reading text files [Visual Basic], troubleshooting
ms.assetid: a8e9b44d-facb-4718-8c0f-466537171182
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e836f79cd05dbaa180cc7bf5413ce57004e3500b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a><span data-ttu-id="54d83-102">Sorun giderme: Okuma ve yazma metin dosyalarına (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="54d83-102">Troubleshooting: reading from and writing to text files (Visual Basic)</span></span>
<span data-ttu-id="54d83-103">Bu konuda metinle çalışma dosyaları ve her bir yaklaşım öneren sık karşılaşılan sorunlar ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="54d83-103">This topic discusses common problems encountered when working with text files and suggests an approach to each.</span></span>  
  
## <a name="common-problems"></a><span data-ttu-id="54d83-104">Sık karşılaşılan sorunları</span><span class="sxs-lookup"><span data-stu-id="54d83-104">Common problems</span></span>  
 <span data-ttu-id="54d83-105">Metin dosyaları ile çalışırken karşılaşılan en yaygın sorunları güvenlik özel durumları, Dosya kodlamaları veya geçersiz yolları içerir.</span><span class="sxs-lookup"><span data-stu-id="54d83-105">The most common issues encountered when working with text files include security exceptions, file encodings, or invalid paths.</span></span>  
  
### <a name="security-exceptions"></a><span data-ttu-id="54d83-106">Güvenlik özel durumları</span><span class="sxs-lookup"><span data-stu-id="54d83-106">Security exceptions</span></span>  
 <span data-ttu-id="54d83-107">A <xref:System.Security.SecurityException> bir güvenlik hatası oluştuğunda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="54d83-107">A <xref:System.Security.SecurityException> is thrown when a security error occurs.</span></span> <span data-ttu-id="54d83-108">Bu genellikle bir izinler ekleyerek veya yalıtılmış depolamadaki dosyaları ile çalışma çözülmesi gerekli izinleri yetersiz kullanıcı sonucudur.</span><span class="sxs-lookup"><span data-stu-id="54d83-108">This is often a result of the user lacking necessary permissions, which may be solved by adding permissions or working with files in isolated storage.</span></span>  
  
### <a name="file-encodings"></a><span data-ttu-id="54d83-109">Dosya kodlamaları</span><span class="sxs-lookup"><span data-stu-id="54d83-109">File encodings</span></span>  
 <span data-ttu-id="54d83-110">Dosya kodlamaları, olarak da bilinen karakter kodlamaları temsil etmek nasıl belirtin ne zaman karakter metin işleme.</span><span class="sxs-lookup"><span data-stu-id="54d83-110">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="54d83-111">Bir metin dosyasında beklenmeyen karakter yanlış kodlamadan neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="54d83-111">Unexpected characters in a text file may result from incorrect encoding.</span></span> <span data-ttu-id="54d83-112">Unicode genellikle tercih edilen olmasına rağmen çoğu dosya için bir kodlama başka hangi dil karakterlerini bakımından veya yükleyebilir işleyemez, tercih edilebilir.</span><span class="sxs-lookup"><span data-stu-id="54d83-112">For most files, one encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span> <span data-ttu-id="54d83-113">Daha fazla bilgi için bkz: [Dosya kodlamaları](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) ve <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="54d83-113">For more information, see [File Encodings](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) and <xref:System.Text.Encoding>.</span></span>  
  
### <a name="incorrect-paths"></a><span data-ttu-id="54d83-114">Yanlış yol</span><span class="sxs-lookup"><span data-stu-id="54d83-114">Incorrect paths</span></span>  
 <span data-ttu-id="54d83-115">Dosya yolları ayrıştırılırken özellikle göreli yollar, yanlış veri sağlamak kolay.</span><span class="sxs-lookup"><span data-stu-id="54d83-115">When parsing file paths, particularly relative paths, it is easy to supply the wrong data.</span></span> <span data-ttu-id="54d83-116">Doğru yolu sağladığını sağlayarak birçok sorun düzeltilebilir.</span><span class="sxs-lookup"><span data-stu-id="54d83-116">Many problems can be corrected by making sure you are supplying the correct path.</span></span> <span data-ttu-id="54d83-117">Daha fazla bilgi için bkz: [nasıl yapılır: dosya yollarını ayrıştırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).</span><span class="sxs-lookup"><span data-stu-id="54d83-117">For more information, see [How to: Parse File Paths](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54d83-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54d83-118">See also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 [<span data-ttu-id="54d83-119">Dosyaları okuma</span><span class="sxs-lookup"><span data-stu-id="54d83-119">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [<span data-ttu-id="54d83-120">Dosyalara yazma</span><span class="sxs-lookup"><span data-stu-id="54d83-120">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)  
 [<span data-ttu-id="54d83-121">TextFieldParser nesnesiyle metin dosyalarını ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="54d83-121">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
