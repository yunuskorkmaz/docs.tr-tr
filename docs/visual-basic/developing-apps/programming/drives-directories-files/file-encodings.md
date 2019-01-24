---
title: Dosya Kodlamaları (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
ms.openlocfilehash: f7ccd47b8778aa3a374ee102b39038e8df475e9b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54731926"
---
# <a name="file-encodings-visual-basic"></a><span data-ttu-id="aac19-102">Dosya Kodlamaları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aac19-102">File Encodings (Visual Basic)</span></span>
<span data-ttu-id="aac19-103">Dosya kodlamaları olarak da bilinen karakter kodlamalarını temsil etmek nasıl belirtin ne zaman karakter metin işleme.</span><span class="sxs-lookup"><span data-stu-id="aac19-103">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="aac19-104">Unicode genellikle tercih edilir olsa da bir kodlama başka hangi dil karakterlerini açısından olabilir veya işleyemez, tercih edilebilir.</span><span class="sxs-lookup"><span data-stu-id="aac19-104">One encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span>  
  
 <span data-ttu-id="aac19-105">Dosyalara yazma veya okuma, hatalı dosya kodlamaları eşleşen özel durumlar veya hatalı sonuçlar neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="aac19-105">When reading from or writing to files, improperly matching file encodings may result in exceptions or incorrect results.</span></span>  
  
## <a name="types-of-encodings"></a><span data-ttu-id="aac19-106">Tür kodlamayı</span><span class="sxs-lookup"><span data-stu-id="aac19-106">Types of Encodings</span></span>  
 <span data-ttu-id="aac19-107">Unicode dosyalarıyla çalışırken tercih edilen kodlamada değil.</span><span class="sxs-lookup"><span data-stu-id="aac19-107">Unicode is the preferred encoding when working with files.</span></span> <span data-ttu-id="aac19-108">Unicode modern teknik simgeleri ve yayımlama içinde kullanılan özel karakterler dahil olmak üzere bilgi işlem, içinde kullanılan tüm karakterleri temsil etmek için 16-bit kod değerleri kullanan bir dünya çapında karakter kodlama standardıdır.</span><span class="sxs-lookup"><span data-stu-id="aac19-108">Unicode is a worldwide character-encoding standard that uses 16-bit code values to represent all the characters used in modern computing, including technical symbols and special characters used in publishing.</span></span>  
  
 <span data-ttu-id="aac19-109">Belirli bir dil veya coğrafi bölge içinde kullanılan karakterleri temsil etmek için 8-bit kod değerleri veya 8-bit değerleri birleşimlerini kullanan Windows ANSI karakter kümesi gibi geleneksel karakter kümesi, önceki karakter kodlama standartları oluşmuştur.</span><span class="sxs-lookup"><span data-stu-id="aac19-109">Previous character-encoding standards consisted of traditional character sets, such as the Windows ANSI character set that uses 8-bit code values, or combinations of 8-bit values, to represent the characters used in a specific language or geographical region.</span></span>  
  
## <a name="encoding-class"></a><span data-ttu-id="aac19-110">Kodlama sınıfı</span><span class="sxs-lookup"><span data-stu-id="aac19-110">Encoding Class</span></span>  
 <span data-ttu-id="aac19-111"><xref:System.Text.Encoding> Sınıfı, karakter kodlamasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="aac19-111">The <xref:System.Text.Encoding> class represents a character encoding.</span></span> <span data-ttu-id="aac19-112">Bu tablo, kullanılabilir Kodlamalar türünü listeler ve her açıklar.</span><span class="sxs-lookup"><span data-stu-id="aac19-112">This table lists the type of encodings available and describes each.</span></span>  
  
|<span data-ttu-id="aac19-113">Ad</span><span class="sxs-lookup"><span data-stu-id="aac19-113">Name</span></span>|<span data-ttu-id="aac19-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aac19-114">Description</span></span>|
|---|---|    
|<xref:System.Text.ASCIIEncoding>|<span data-ttu-id="aac19-115">ASCII karakter kodlama Unicode karakterini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="aac19-115">Represents an ASCII character encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UnicodeEncoding>|<span data-ttu-id="aac19-116">UTF-16 kodlamasını Unicode karakterini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="aac19-116">Represents a UTF-16 encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UTF32Encoding>|<span data-ttu-id="aac19-117">UTF-32 kodlama Unicode karakterini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="aac19-117">Represents a UTF-32 encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UTF7Encoding>|<span data-ttu-id="aac19-118">UTF-7 kodlaması Unicode karakterini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="aac19-118">Represents a UTF-7 encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UTF8Encoding>|<span data-ttu-id="aac19-119">UTF-8 kodlamalı Unicode karakterini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="aac19-119">Represents a UTF-8 encoding of Unicode characters.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aac19-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aac19-120">See also</span></span>
- [<span data-ttu-id="aac19-121">Dosyalardan Okuma</span><span class="sxs-lookup"><span data-stu-id="aac19-121">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="aac19-122">Dosyalara Yazma</span><span class="sxs-lookup"><span data-stu-id="aac19-122">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
