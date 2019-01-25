---
title: 'Sorun giderme: Okuma ve yazma metin dosyaları (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting file I/O
- writing text to files [Visual Basic], troubleshooting
- troubleshooting Visual Basic, text files
- I/O [Visual Basic], troubleshooting text files
- writing to files [Visual Basic], troubleshooting
- reading text files [Visual Basic], troubleshooting
ms.assetid: a8e9b44d-facb-4718-8c0f-466537171182
ms.openlocfilehash: cc0ec3c624fc4f47a0ef8594669ba120e6628e82
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684404"
---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a><span data-ttu-id="537bc-102">Sorun giderme: Okuma ve yazma metin dosyaları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="537bc-102">Troubleshooting: reading from and writing to text files (Visual Basic)</span></span>
<span data-ttu-id="537bc-103">Bu konuda metinle çalışma dosyaları ve her bir yaklaşım önerir sık karşılaşılan sorunlar ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="537bc-103">This topic discusses common problems encountered when working with text files and suggests an approach to each.</span></span>  
  
## <a name="common-problems"></a><span data-ttu-id="537bc-104">Yaygın sorunlar</span><span class="sxs-lookup"><span data-stu-id="537bc-104">Common problems</span></span>  
 <span data-ttu-id="537bc-105">Metin dosyaları ile çalışma karşılaşılan en yaygın sorunları, güvenlik özel durumları, Dosya kodlamaları veya geçersiz yollarını içerir.</span><span class="sxs-lookup"><span data-stu-id="537bc-105">The most common issues encountered when working with text files include security exceptions, file encodings, or invalid paths.</span></span>  
  
### <a name="security-exceptions"></a><span data-ttu-id="537bc-106">Güvenlik özel durumları</span><span class="sxs-lookup"><span data-stu-id="537bc-106">Security exceptions</span></span>  
 <span data-ttu-id="537bc-107">A <xref:System.Security.SecurityException> bir güvenlik hatası oluştuğunda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="537bc-107">A <xref:System.Security.SecurityException> is thrown when a security error occurs.</span></span> <span data-ttu-id="537bc-108">Bu genellikle kullanıcının eksik izinler ekleyerek veya yalıtılmış depolamadaki dosyaları ile çalışma çözülmesi gerekli izinler sonucudur.</span><span class="sxs-lookup"><span data-stu-id="537bc-108">This is often a result of the user lacking necessary permissions, which may be solved by adding permissions or working with files in isolated storage.</span></span>  
  
### <a name="file-encodings"></a><span data-ttu-id="537bc-109">Dosya kodlamaları</span><span class="sxs-lookup"><span data-stu-id="537bc-109">File encodings</span></span>  
 <span data-ttu-id="537bc-110">Dosya kodlamaları olarak da bilinen karakter kodlamalarını temsil etmek nasıl belirtin ne zaman karakter metin işleme.</span><span class="sxs-lookup"><span data-stu-id="537bc-110">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="537bc-111">Bir metin dosyasında beklenmeyen karakter hatalı kodlama neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="537bc-111">Unexpected characters in a text file may result from incorrect encoding.</span></span> <span data-ttu-id="537bc-112">Unicode genellikle tercih edilir olsa da çoğu dosya için bir kodlama başka hangi dil karakterlerini açısından olabilir veya işleyemez, tercih edilebilir.</span><span class="sxs-lookup"><span data-stu-id="537bc-112">For most files, one encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span> <span data-ttu-id="537bc-113">Daha fazla bilgi için [Dosya kodlamaları](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) ve <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="537bc-113">For more information, see [File Encodings](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) and <xref:System.Text.Encoding>.</span></span>  
  
### <a name="incorrect-paths"></a><span data-ttu-id="537bc-114">Yanlış yol</span><span class="sxs-lookup"><span data-stu-id="537bc-114">Incorrect paths</span></span>  
 <span data-ttu-id="537bc-115">Dosya yollarını ayrıştırma, özellikle göreli yolları da yanlış veri sağlamak kolay.</span><span class="sxs-lookup"><span data-stu-id="537bc-115">When parsing file paths, particularly relative paths, it is easy to supply the wrong data.</span></span> <span data-ttu-id="537bc-116">Doğru yolu sağladığınız sağlayarak karşılaşılan birçok sorun düzeltilebilir.</span><span class="sxs-lookup"><span data-stu-id="537bc-116">Many problems can be corrected by making sure you are supplying the correct path.</span></span> <span data-ttu-id="537bc-117">Daha fazla bilgi için [nasıl yapılır: Dosya yollarını ayrıştırma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).</span><span class="sxs-lookup"><span data-stu-id="537bc-117">For more information, see [How to: Parse File Paths](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="537bc-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="537bc-118">See also</span></span>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [<span data-ttu-id="537bc-119">Dosyalardan Okuma</span><span class="sxs-lookup"><span data-stu-id="537bc-119">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="537bc-120">Dosyalara Yazma</span><span class="sxs-lookup"><span data-stu-id="537bc-120">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
- [<span data-ttu-id="537bc-121">TextFieldParser Nesnesiyle Metin Dosyalarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="537bc-121">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
