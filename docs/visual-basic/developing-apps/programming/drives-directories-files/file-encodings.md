---
title: Dosya Kodlamaları (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
ms.openlocfilehash: c22e8046a8b88890f25bc6b671825eb6d68ec6b8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814009"
---
# <a name="file-encodings-visual-basic"></a><span data-ttu-id="39984-102">Dosya Kodlamaları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39984-102">File Encodings (Visual Basic)</span></span>
<span data-ttu-id="39984-103">Dosya kodlamaları olarak da bilinen karakter kodlamalarını temsil etmek nasıl belirtin ne zaman karakter metin işleme.</span><span class="sxs-lookup"><span data-stu-id="39984-103">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="39984-104">Unicode genellikle tercih edilir olsa da bir kodlama başka hangi dil karakterlerini açısından olabilir veya işleyemez, tercih edilebilir.</span><span class="sxs-lookup"><span data-stu-id="39984-104">One encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span>  
  
 <span data-ttu-id="39984-105">Dosyalara yazma veya okuma, hatalı dosya kodlamaları eşleşen özel durumlar veya hatalı sonuçlar neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="39984-105">When reading from or writing to files, improperly matching file encodings may result in exceptions or incorrect results.</span></span>  
  
## <a name="types-of-encodings"></a><span data-ttu-id="39984-106">Tür kodlamayı</span><span class="sxs-lookup"><span data-stu-id="39984-106">Types of Encodings</span></span>  
 <span data-ttu-id="39984-107">Unicode dosyalarıyla çalışırken tercih edilen kodlamada değil.</span><span class="sxs-lookup"><span data-stu-id="39984-107">Unicode is the preferred encoding when working with files.</span></span> <span data-ttu-id="39984-108">Unicode modern teknik simgeleri ve yayımlama içinde kullanılan özel karakterler dahil olmak üzere bilgi işlem, içinde kullanılan tüm karakterleri temsil etmek için 16-bit kod değerleri kullanan bir dünya çapında karakter kodlama standardıdır.</span><span class="sxs-lookup"><span data-stu-id="39984-108">Unicode is a worldwide character-encoding standard that uses 16-bit code values to represent all the characters used in modern computing, including technical symbols and special characters used in publishing.</span></span>  
  
 <span data-ttu-id="39984-109">Belirli bir dil veya coğrafi bölge içinde kullanılan karakterleri temsil etmek için 8-bit kod değerleri veya 8-bit değerleri birleşimlerini kullanan Windows ANSI karakter kümesi gibi geleneksel karakter kümesi, önceki karakter kodlama standartları oluşmuştur.</span><span class="sxs-lookup"><span data-stu-id="39984-109">Previous character-encoding standards consisted of traditional character sets, such as the Windows ANSI character set that uses 8-bit code values, or combinations of 8-bit values, to represent the characters used in a specific language or geographical region.</span></span>  
  
## <a name="encoding-class"></a><span data-ttu-id="39984-110">Kodlama sınıfı</span><span class="sxs-lookup"><span data-stu-id="39984-110">Encoding Class</span></span>  
 <span data-ttu-id="39984-111"><xref:System.Text.Encoding> Sınıfı, karakter kodlamasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="39984-111">The <xref:System.Text.Encoding> class represents a character encoding.</span></span> <span data-ttu-id="39984-112">Bu tablo, kullanılabilir Kodlamalar türünü listeler ve her açıklar.</span><span class="sxs-lookup"><span data-stu-id="39984-112">This table lists the type of encodings available and describes each.</span></span>  
  
|<span data-ttu-id="39984-113">Ad</span><span class="sxs-lookup"><span data-stu-id="39984-113">Name</span></span>|<span data-ttu-id="39984-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39984-114">Description</span></span>|
|---|---|    
|<xref:System.Text.ASCIIEncoding>|<span data-ttu-id="39984-115">ASCII karakter kodlama Unicode karakterini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="39984-115">Represents an ASCII character encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UnicodeEncoding>|<span data-ttu-id="39984-116">UTF-16 kodlamasını Unicode karakterini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="39984-116">Represents a UTF-16 encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UTF32Encoding>|<span data-ttu-id="39984-117">UTF-32 kodlama Unicode karakterini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="39984-117">Represents a UTF-32 encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UTF7Encoding>|<span data-ttu-id="39984-118">UTF-7 kodlaması Unicode karakterini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="39984-118">Represents a UTF-7 encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UTF8Encoding>|<span data-ttu-id="39984-119">UTF-8 kodlamalı Unicode karakterini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="39984-119">Represents a UTF-8 encoding of Unicode characters.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="39984-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39984-120">See also</span></span>

- [<span data-ttu-id="39984-121">Dosyalardan Okuma</span><span class="sxs-lookup"><span data-stu-id="39984-121">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="39984-122">Dosyalara Yazma</span><span class="sxs-lookup"><span data-stu-id="39984-122">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
