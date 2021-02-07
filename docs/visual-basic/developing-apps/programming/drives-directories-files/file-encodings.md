---
description: 'Daha fazla bilgi edinin: dosya kodlamaları (Visual Basic)'
title: Dosya Kodlamaları
ms.date: 07/20/2015
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
ms.openlocfilehash: f573b5d8f83c27cbf4ddacb9fd40474d7d1be1ae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675370"
---
# <a name="file-encodings-visual-basic"></a><span data-ttu-id="b106f-103">Dosya Kodlamaları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b106f-103">File Encodings (Visual Basic)</span></span>

<span data-ttu-id="b106f-104">Karakter kodlamaları olarak da bilinen dosya kodlamaları, metin işleme sırasında karakterlerin nasıl temsil edileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b106f-104">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="b106f-105">Tek bir kodlama, bir veya işleyemeyen dil karakterleri açısından başka bir şekilde tercih edilebilir, ancak UNICODE genellikle tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="b106f-105">One encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span>

<span data-ttu-id="b106f-106">Dosyadan okuma veya yazma yaparken, dosya kodlamaları yanlış şekilde eşleştirilirken özel durumlar veya hatalı sonuçlar oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="b106f-106">When reading from or writing to files, improperly matching file encodings may result in exceptions or incorrect results.</span></span>

## <a name="types-of-encodings"></a><span data-ttu-id="b106f-107">Kodlamalar türleri</span><span class="sxs-lookup"><span data-stu-id="b106f-107">Types of Encodings</span></span>

<span data-ttu-id="b106f-108">Unicode, dosyalarla çalışırken tercih edilen kodlanıyor.</span><span class="sxs-lookup"><span data-stu-id="b106f-108">Unicode is the preferred encoding when working with files.</span></span> <span data-ttu-id="b106f-109">Unicode, yayımlamak için kullanılan teknik semboller ve özel karakterler de dahil olmak üzere modern bilgi işlem 'da kullanılan tüm karakterleri temsil etmek için 16 bit kod değerlerini kullanan dünya çapındaki bir karakter kodlama standardıdır.</span><span class="sxs-lookup"><span data-stu-id="b106f-109">Unicode is a worldwide character-encoding standard that uses 16-bit code values to represent all the characters used in modern computing, including technical symbols and special characters used in publishing.</span></span>

<span data-ttu-id="b106f-110">Önceki karakter kodlama standartları, 8 bit kod değerleri kullanan Windows ANSI karakter kümesi veya belirli bir dilde veya coğrafi bölgede kullanılan karakterleri göstermek için 8 bit değer bileşimleri gibi geleneksel karakter kümelerinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="b106f-110">Previous character-encoding standards consisted of traditional character sets, such as the Windows ANSI character set that uses 8-bit code values, or combinations of 8-bit values, to represent the characters used in a specific language or geographical region.</span></span>

## <a name="encoding-class"></a><span data-ttu-id="b106f-111">Kodlama sınıfı</span><span class="sxs-lookup"><span data-stu-id="b106f-111">Encoding Class</span></span>

<span data-ttu-id="b106f-112"><xref:System.Text.Encoding>Sınıfı bir karakter kodlamasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b106f-112">The <xref:System.Text.Encoding> class represents a character encoding.</span></span> <span data-ttu-id="b106f-113">Bu tabloda, kullanılabilir kodlamalar türü listelenmekte ve her biri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b106f-113">This table lists the type of encodings available and describes each.</span></span>

|<span data-ttu-id="b106f-114">Ad</span><span class="sxs-lookup"><span data-stu-id="b106f-114">Name</span></span>|<span data-ttu-id="b106f-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b106f-115">Description</span></span>|
|---|---|
|<xref:System.Text.ASCIIEncoding>|<span data-ttu-id="b106f-116">Unicode karakterlerinin ASCII karakter kodlamasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b106f-116">Represents an ASCII character encoding of Unicode characters.</span></span>|
|<xref:System.Text.UnicodeEncoding>|<span data-ttu-id="b106f-117">Unicode karakterlerinin UTF-16 kodlamasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b106f-117">Represents a UTF-16 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF32Encoding>|<span data-ttu-id="b106f-118">Unicode karakterlerinin UTF-32 kodlamasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b106f-118">Represents a UTF-32 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF7Encoding>|<span data-ttu-id="b106f-119">Unicode karakterlerinin UTF-7 kodlamasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b106f-119">Represents a UTF-7 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF8Encoding>|<span data-ttu-id="b106f-120">Unicode karakterlerinin UTF-8 kodlamasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b106f-120">Represents a UTF-8 encoding of Unicode characters.</span></span>|

## <a name="see-also"></a><span data-ttu-id="b106f-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b106f-121">See also</span></span>

- [<span data-ttu-id="b106f-122">Dosyalardan Okuma</span><span class="sxs-lookup"><span data-stu-id="b106f-122">Reading from Files</span></span>](reading-from-files.md)
- [<span data-ttu-id="b106f-123">Dosyalara Yazma</span><span class="sxs-lookup"><span data-stu-id="b106f-123">Writing to Files</span></span>](writing-to-files.md)
