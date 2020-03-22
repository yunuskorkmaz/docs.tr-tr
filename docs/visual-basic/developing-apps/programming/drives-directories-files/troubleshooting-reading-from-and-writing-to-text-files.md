---
title: 'Sorun giderme: metin dosyalarından okuma ve yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting file I/O
- writing text to files [Visual Basic], troubleshooting
- troubleshooting Visual Basic, text files
- I/O [Visual Basic], troubleshooting text files
- writing to files [Visual Basic], troubleshooting
- reading text files [Visual Basic], troubleshooting
ms.assetid: a8e9b44d-facb-4718-8c0f-466537171182
ms.openlocfilehash: dbc53ca3cc9ae9b2d14b925f891d0409b2b7debd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74333793"
---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a><span data-ttu-id="105a9-102">Sorun giderme: metin dosyalarından okuma ve yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="105a9-102">Troubleshooting: reading from and writing to text files (Visual Basic)</span></span>

<span data-ttu-id="105a9-103">Bu konu, metin dosyalarıyla çalışırken karşılaşılan sık karşılaşılan sorunları tartışır ve her birine bir yaklaşım önerir.</span><span class="sxs-lookup"><span data-stu-id="105a9-103">This topic discusses common problems encountered when working with text files and suggests an approach to each.</span></span>  
  
## <a name="common-problems"></a><span data-ttu-id="105a9-104">Sık karşılaşılan sorunlar</span><span class="sxs-lookup"><span data-stu-id="105a9-104">Common problems</span></span>  

 <span data-ttu-id="105a9-105">Metin dosyalarıyla çalışırken karşılaşılan en sık karşılaşılan sorunlar arasında güvenlik özel durumları, dosya kodlamaları veya geçersiz yollar yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="105a9-105">The most common issues encountered when working with text files include security exceptions, file encodings, or invalid paths.</span></span>  
  
### <a name="security-exceptions"></a><span data-ttu-id="105a9-106">Güvenlik özel durumları</span><span class="sxs-lookup"><span data-stu-id="105a9-106">Security exceptions</span></span>  

 <span data-ttu-id="105a9-107">Bir <xref:System.Security.SecurityException> güvenlik hatası oluştuğunda A atılır.</span><span class="sxs-lookup"><span data-stu-id="105a9-107">A <xref:System.Security.SecurityException> is thrown when a security error occurs.</span></span> <span data-ttu-id="105a9-108">Bu genellikle, kullanıcının gerekli izinlerden yoksun olmasının bir sonucudur ve bu izinler eklenerek veya yalıtılmış depolama daki dosyalarla çalışarak çözülebilir.</span><span class="sxs-lookup"><span data-stu-id="105a9-108">This is often a result of the user lacking necessary permissions, which may be solved by adding permissions or working with files in isolated storage.</span></span>  
  
### <a name="file-encodings"></a><span data-ttu-id="105a9-109">Dosya kodlamaları</span><span class="sxs-lookup"><span data-stu-id="105a9-109">File encodings</span></span>  

 <span data-ttu-id="105a9-110">Karakter kodlamaları olarak da bilinen dosya kodlamaları, metin işlenirken karakterlerin nasıl temsil edilecek lerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="105a9-110">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="105a9-111">Metin dosyasındaki beklenmeyen karakterler yanlış kodlamadan kaynaklanabilir.</span><span class="sxs-lookup"><span data-stu-id="105a9-111">Unexpected characters in a text file may result from incorrect encoding.</span></span> <span data-ttu-id="105a9-112">Çoğu dosya için, unicode genellikle tercih edilse de, bir kodlama hangi dil karakterlerini işleyebileceği veya işleyemeyeceği açısından diğerine göre tercih edilebilir.</span><span class="sxs-lookup"><span data-stu-id="105a9-112">For most files, one encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span> <span data-ttu-id="105a9-113">Daha fazla bilgi için Dosya <xref:System.Text.Encoding> [Kodlamaları](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) ve .</span><span class="sxs-lookup"><span data-stu-id="105a9-113">For more information, see [File Encodings](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) and <xref:System.Text.Encoding>.</span></span>  
  
### <a name="incorrect-paths"></a><span data-ttu-id="105a9-114">Yanlış yollar</span><span class="sxs-lookup"><span data-stu-id="105a9-114">Incorrect paths</span></span>  

 <span data-ttu-id="105a9-115">Dosya yollarını, özellikle de göreli yolları ayrıştırırken, yanlış verileri sağlamak kolaydır.</span><span class="sxs-lookup"><span data-stu-id="105a9-115">When parsing file paths, particularly relative paths, it is easy to supply the wrong data.</span></span> <span data-ttu-id="105a9-116">Doğru yolu sağladığından emin olunarak birçok sorun düzeltilebilir.</span><span class="sxs-lookup"><span data-stu-id="105a9-116">Many problems can be corrected by making sure you are supplying the correct path.</span></span> <span data-ttu-id="105a9-117">Daha fazla bilgi için [bkz: Dosya Yollarını Ayrışdırın.](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)</span><span class="sxs-lookup"><span data-stu-id="105a9-117">For more information, see [How to: Parse File Paths](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="105a9-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="105a9-118">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [<span data-ttu-id="105a9-119">Dosyalardan Okuma</span><span class="sxs-lookup"><span data-stu-id="105a9-119">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="105a9-120">Dosyalara Yazma</span><span class="sxs-lookup"><span data-stu-id="105a9-120">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
- [<span data-ttu-id="105a9-121">TextFieldParser Nesnesiyle Metin Dosyalarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="105a9-121">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
