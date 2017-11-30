---
title: "Dosya Kodlamaları (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: deaab4371ab0d5d15c627bfd6352a7090bf08024
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="file-encodings-visual-basic"></a><span data-ttu-id="8d591-102">Dosya Kodlamaları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d591-102">File Encodings (Visual Basic)</span></span>
<span data-ttu-id="8d591-103">Dosya kodlamaları, olarak da bilinen karakter kodlamaları temsil etmek nasıl belirtin ne zaman karakter metin işleme.</span><span class="sxs-lookup"><span data-stu-id="8d591-103">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="8d591-104">Unicode genellikle tercih edilen olmasına rağmen bir kodlama başka hangi dil karakterlerini bakımından veya yükleyebilir işleyemez, tercih edilebilir.</span><span class="sxs-lookup"><span data-stu-id="8d591-104">One encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span>  
  
 <span data-ttu-id="8d591-105">Dosyalara yazma veya okuma, hatalı dosya kodlamaları eşleşen özel durumları veya hatalı sonuçlar neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="8d591-105">When reading from or writing to files, improperly matching file encodings may result in exceptions or incorrect results.</span></span>  
  
## <a name="types-of-encodings"></a><span data-ttu-id="8d591-106">Kodlamalar türleri</span><span class="sxs-lookup"><span data-stu-id="8d591-106">Types of Encodings</span></span>  
 <span data-ttu-id="8d591-107">Unicode dosyaları ile çalışırken, tercih edilen kodlamayı ' dir.</span><span class="sxs-lookup"><span data-stu-id="8d591-107">Unicode is the preferred encoding when working with files.</span></span> <span data-ttu-id="8d591-108">Unicode modern, teknik simgeler ve yayımlama içinde kullanılan özel karakterleri dahil olmak üzere bilgisayar kullanılan tüm karakterleri temsil edecek 16 bit kod değerleri kullanan bir dünya çapında karakter kodlamasını standardıdır.</span><span class="sxs-lookup"><span data-stu-id="8d591-108">Unicode is a worldwide character-encoding standard that uses 16-bit code values to represent all the characters used in modern computing, including technical symbols and special characters used in publishing.</span></span>  
  
 <span data-ttu-id="8d591-109">Belirli bir dil veya coğrafi bölge içinde kullanılan karakterleri temsil etmek için 8 bit kod değerleri veya 8 bit değerleri birleşimlerini kullanan Windows ANSI karakter kümesini gibi geleneksel karakter kümesinden karakter kodlamasını önceki standartları içermektedir.</span><span class="sxs-lookup"><span data-stu-id="8d591-109">Previous character-encoding standards consisted of traditional character sets, such as the Windows ANSI character set that uses 8-bit code values, or combinations of 8-bit values, to represent the characters used in a specific language or geographical region.</span></span>  
  
## <a name="encoding-class"></a><span data-ttu-id="8d591-110">Kodlama sınıfı</span><span class="sxs-lookup"><span data-stu-id="8d591-110">Encoding Class</span></span>  
 <span data-ttu-id="8d591-111"><xref:System.Text.Encoding> Sınıfı, bir karakter kodlama temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8d591-111">The <xref:System.Text.Encoding> class represents a character encoding.</span></span> <span data-ttu-id="8d591-112">Bu tabloda Kodlamalar kullanılabilir türünü listeler ve her açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8d591-112">This table lists the type of encodings available and describes each.</span></span>  
  
|<span data-ttu-id="8d591-113">Ad</span><span class="sxs-lookup"><span data-stu-id="8d591-113">Name</span></span>|<span data-ttu-id="8d591-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8d591-114">Description</span></span>|
|---|---|    
|<xref:System.Text.ASCIIEncoding>|<span data-ttu-id="8d591-115">Bir ASCII karakteri Unicode karakter kodlama temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8d591-115">Represents an ASCII character encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UnicodeEncoding>|<span data-ttu-id="8d591-116">UTF-16 kodlamasını Unicode karakterinden temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8d591-116">Represents a UTF-16 encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UTF32Encoding>|<span data-ttu-id="8d591-117">UTF-32 kodlama Unicode karakterinden temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8d591-117">Represents a UTF-32 encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UTF7Encoding>|<span data-ttu-id="8d591-118">UTF-7 kodlama Unicode karakterinden temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8d591-118">Represents a UTF-7 encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UTF8Encoding>|<span data-ttu-id="8d591-119">UTF-8 kodlaması Unicode karakterinden temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8d591-119">Represents a UTF-8 encoding of Unicode characters.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8d591-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8d591-120">See Also</span></span>  
 [<span data-ttu-id="8d591-121">Dosyaları okuma</span><span class="sxs-lookup"><span data-stu-id="8d591-121">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [<span data-ttu-id="8d591-122">Dosyalara yazma</span><span class="sxs-lookup"><span data-stu-id="8d591-122">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
