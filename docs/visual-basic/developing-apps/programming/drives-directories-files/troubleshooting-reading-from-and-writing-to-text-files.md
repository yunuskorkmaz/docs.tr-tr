---
description: 'Daha fazla bilgi edinin: sorun giderme: metin dosyalarını okuma ve yazma (Visual Basic)'
title: 'Sorun giderme: metin dosyalarını okuma ve yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting file I/O
- writing text to files [Visual Basic], troubleshooting
- troubleshooting Visual Basic, text files
- I/O [Visual Basic], troubleshooting text files
- writing to files [Visual Basic], troubleshooting
- reading text files [Visual Basic], troubleshooting
ms.assetid: a8e9b44d-facb-4718-8c0f-466537171182
ms.openlocfilehash: 1c01f7673ef021759a9c1892f685aa90ef1acdf6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675344"
---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a><span data-ttu-id="2e177-103">Sorun giderme: metin dosyalarını okuma ve yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e177-103">Troubleshooting: reading from and writing to text files (Visual Basic)</span></span>

<span data-ttu-id="2e177-104">Bu konuda, metin dosyalarıyla çalışırken karşılaşılan yaygın sorunlar ele alınmaktadır ve her birine bir yaklaşım önerisinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="2e177-104">This topic discusses common problems encountered when working with text files and suggests an approach to each.</span></span>  
  
## <a name="common-problems"></a><span data-ttu-id="2e177-105">Sık karşılaşılan sorunlar</span><span class="sxs-lookup"><span data-stu-id="2e177-105">Common problems</span></span>  

 <span data-ttu-id="2e177-106">Metin dosyalarıyla çalışırken karşılaşılan en yaygın sorunlar, güvenlik özel durumları, dosya kodlamaları veya geçersiz yollar içerir.</span><span class="sxs-lookup"><span data-stu-id="2e177-106">The most common issues encountered when working with text files include security exceptions, file encodings, or invalid paths.</span></span>  
  
### <a name="security-exceptions"></a><span data-ttu-id="2e177-107">Güvenlik özel durumları</span><span class="sxs-lookup"><span data-stu-id="2e177-107">Security exceptions</span></span>  

 <span data-ttu-id="2e177-108">Bir <xref:System.Security.SecurityException> güvenlik hatası oluştuğunda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2e177-108">A <xref:System.Security.SecurityException> is thrown when a security error occurs.</span></span> <span data-ttu-id="2e177-109">Bu genellikle kullanıcının gerekli izinlere sahip olmadığı bir sonucudur. Bu, izinleri ekleyerek veya yalıtılmış depolamada dosyalarla çalışarak çözülebilen bir sonucudur.</span><span class="sxs-lookup"><span data-stu-id="2e177-109">This is often a result of the user lacking necessary permissions, which may be solved by adding permissions or working with files in isolated storage.</span></span>  
  
### <a name="file-encodings"></a><span data-ttu-id="2e177-110">Dosya kodlamaları</span><span class="sxs-lookup"><span data-stu-id="2e177-110">File encodings</span></span>  

 <span data-ttu-id="2e177-111">Karakter kodlamaları olarak da bilinen dosya kodlamaları, metin işleme sırasında karakterlerin nasıl temsil edileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2e177-111">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="2e177-112">Metin dosyasında beklenmeyen karakterler yanlış kodlamadan kaynaklanıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="2e177-112">Unexpected characters in a text file may result from incorrect encoding.</span></span> <span data-ttu-id="2e177-113">Çoğu dosya için, tek bir kodlama bir veya işleyemeyen dil karakterleri açısından tercih edilebilir, ancak UNICODE genellikle tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="2e177-113">For most files, one encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span> <span data-ttu-id="2e177-114">Daha fazla bilgi için bkz. [dosya kodlamaları](file-encodings.md) ve <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="2e177-114">For more information, see [File Encodings](file-encodings.md) and <xref:System.Text.Encoding>.</span></span>  
  
### <a name="incorrect-paths"></a><span data-ttu-id="2e177-115">Yanlış yollar</span><span class="sxs-lookup"><span data-stu-id="2e177-115">Incorrect paths</span></span>  

 <span data-ttu-id="2e177-116">Dosya yollarını ayrıştırırken özellikle göreli yollar, yanlış verileri sağlamak kolaydır.</span><span class="sxs-lookup"><span data-stu-id="2e177-116">When parsing file paths, particularly relative paths, it is easy to supply the wrong data.</span></span> <span data-ttu-id="2e177-117">Doğru yolu belirttiğinizden emin olmak için birçok sorun düzeltilebilir.</span><span class="sxs-lookup"><span data-stu-id="2e177-117">Many problems can be corrected by making sure you are supplying the correct path.</span></span> <span data-ttu-id="2e177-118">Daha fazla bilgi için bkz. [nasıl yapılır: dosya yollarını ayrıştırma](how-to-parse-file-paths.md).</span><span class="sxs-lookup"><span data-stu-id="2e177-118">For more information, see [How to: Parse File Paths](how-to-parse-file-paths.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e177-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e177-119">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [<span data-ttu-id="2e177-120">Dosyalardan Okuma</span><span class="sxs-lookup"><span data-stu-id="2e177-120">Reading from Files</span></span>](reading-from-files.md)
- [<span data-ttu-id="2e177-121">Dosyalara Yazma</span><span class="sxs-lookup"><span data-stu-id="2e177-121">Writing to Files</span></span>](writing-to-files.md)
- [<span data-ttu-id="2e177-122">TextFieldParser Nesnesiyle Metin Dosyalarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="2e177-122">Parsing Text Files with the TextFieldParser Object</span></span>](parsing-text-files-with-the-textfieldparser-object.md)
