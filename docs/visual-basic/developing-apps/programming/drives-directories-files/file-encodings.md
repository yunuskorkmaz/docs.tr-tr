---
title: Dosya Kodlamaları
ms.date: 07/20/2015
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
ms.openlocfilehash: 52770187568d0ba0f54ec36ee2c3d754a9b4d9a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348888"
---
# <a name="file-encodings-visual-basic"></a><span data-ttu-id="d4d84-102">Dosya Kodlamaları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4d84-102">File Encodings (Visual Basic)</span></span>

<span data-ttu-id="d4d84-103">Karakter kodlamaları olarak da bilinen dosya kodlamaları, metin işlenirken karakterlerin nasıl temsil edilecek lerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d4d84-103">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="d4d84-104">Unicode genellikle tercih edilse de, bir kodlama, işleyebileceği veya işleyemeyeceği dil karakterleri açısından diğerine göre tercih edilebilir.</span><span class="sxs-lookup"><span data-stu-id="d4d84-104">One encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span>

<span data-ttu-id="d4d84-105">Dosyalardan okuma veya dosyalara yazma, dosya kodlamalarının yanlış eşleşmesi özel durumlara veya yanlış sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="d4d84-105">When reading from or writing to files, improperly matching file encodings may result in exceptions or incorrect results.</span></span>

## <a name="types-of-encodings"></a><span data-ttu-id="d4d84-106">Kodlama Türleri</span><span class="sxs-lookup"><span data-stu-id="d4d84-106">Types of Encodings</span></span>

<span data-ttu-id="d4d84-107">Unicode, dosyalarla çalışırken tercih edilen kodlamadır.</span><span class="sxs-lookup"><span data-stu-id="d4d84-107">Unicode is the preferred encoding when working with files.</span></span> <span data-ttu-id="d4d84-108">Unicode, modern bilgi işlemde kullanılan teknik semboller ve yayımlamada kullanılan özel karakterler de dahil olmak üzere tüm karakterleri temsil etmek için 16 bit kod değerlerini kullanan dünya çapında bir karakter kodlama standardıdır.</span><span class="sxs-lookup"><span data-stu-id="d4d84-108">Unicode is a worldwide character-encoding standard that uses 16-bit code values to represent all the characters used in modern computing, including technical symbols and special characters used in publishing.</span></span>

<span data-ttu-id="d4d84-109">Önceki karakter kodlama standartları, belirli bir dilde veya coğrafi bölgede kullanılan karakterleri temsil etmek için 8 bit kod değerleri veya 8 bit değerlerinbirlöleri kullanan Windows ANSI karakter kümesi gibi geleneksel karakter kümelerinden oluşuyordu.</span><span class="sxs-lookup"><span data-stu-id="d4d84-109">Previous character-encoding standards consisted of traditional character sets, such as the Windows ANSI character set that uses 8-bit code values, or combinations of 8-bit values, to represent the characters used in a specific language or geographical region.</span></span>

## <a name="encoding-class"></a><span data-ttu-id="d4d84-110">Kodlama Sınıfı</span><span class="sxs-lookup"><span data-stu-id="d4d84-110">Encoding Class</span></span>

<span data-ttu-id="d4d84-111">Sınıf, <xref:System.Text.Encoding> bir karakter kodlamasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d4d84-111">The <xref:System.Text.Encoding> class represents a character encoding.</span></span> <span data-ttu-id="d4d84-112">Bu tablo, kullanılabilir kodlama türünü listeler ve her birini açıklar.</span><span class="sxs-lookup"><span data-stu-id="d4d84-112">This table lists the type of encodings available and describes each.</span></span>

|<span data-ttu-id="d4d84-113">Adı</span><span class="sxs-lookup"><span data-stu-id="d4d84-113">Name</span></span>|<span data-ttu-id="d4d84-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4d84-114">Description</span></span>|
|---|---|
|<xref:System.Text.ASCIIEncoding>|<span data-ttu-id="d4d84-115">Unicode karakterlerinin ASCII karakterini kodlamayı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d4d84-115">Represents an ASCII character encoding of Unicode characters.</span></span>|
|<xref:System.Text.UnicodeEncoding>|<span data-ttu-id="d4d84-116">Unicode karakterlerinin UTF-16 kodlayıcılarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d4d84-116">Represents a UTF-16 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF32Encoding>|<span data-ttu-id="d4d84-117">Unicode karakterlerinin UTF-32 kodlayıcılarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d4d84-117">Represents a UTF-32 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF7Encoding>|<span data-ttu-id="d4d84-118">Unicode karakterlerinin UTF-7 kodlaması temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d4d84-118">Represents a UTF-7 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF8Encoding>|<span data-ttu-id="d4d84-119">Unicode karakterlerinin UTF-8 kodlaması temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d4d84-119">Represents a UTF-8 encoding of Unicode characters.</span></span>|

## <a name="see-also"></a><span data-ttu-id="d4d84-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4d84-120">See also</span></span>

- [<span data-ttu-id="d4d84-121">Dosyalardan Okuma</span><span class="sxs-lookup"><span data-stu-id="d4d84-121">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="d4d84-122">Dosyalara Yazma</span><span class="sxs-lookup"><span data-stu-id="d4d84-122">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
