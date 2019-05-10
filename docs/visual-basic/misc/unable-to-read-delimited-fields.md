---
title: Ayrılmış alanlar EscapeQuotes True olarak ayarlandığında çift tırnak işareti yasal sınırlayıcı olmadığından okunamıyor
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
ms.openlocfilehash: ca764d5258daf54a7149661549a78b3aca709718
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619811"
---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a><span data-ttu-id="d9113-102">Ayrılmış alanlar EscapeQuotes True olarak ayarlandığında çift tırnak işareti yasal sınırlayıcı olmadığından okunamıyor</span><span class="sxs-lookup"><span data-stu-id="d9113-102">Unable to read delimited fields because a double quote is not a legal delimiter when EscapeQuotes is set to True</span></span>
<span data-ttu-id="d9113-103">`TextFieldParser` Tırnak işareti (") ayırıcı olarak sağlanmadığından dosyasından okunamıyor ve `EscapeQuotes` ayarlanır `True`.</span><span class="sxs-lookup"><span data-stu-id="d9113-103">The `TextFieldParser` cannot read from the file because a quotation mark (") has been supplied as the delimiter and `EscapeQuotes` is set to `True`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d9113-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="d9113-104">To correct this error</span></span>  
  
- <span data-ttu-id="d9113-105">Ayarlama `EscapeQuotes` için `False`.</span><span class="sxs-lookup"><span data-stu-id="d9113-105">Set `EscapeQuotes` to `False`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9113-106">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9113-106">See also</span></span>

- [<span data-ttu-id="d9113-107">TextFieldParser.SetDelimiters yöntemi</span><span class="sxs-lookup"><span data-stu-id="d9113-107">TextFieldParser.SetDelimiters Method</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A)
- [<span data-ttu-id="d9113-108">TextFieldParser.Delimiters özelliği</span><span class="sxs-lookup"><span data-stu-id="d9113-108">TextFieldParser.Delimiters Property</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A)
- [<span data-ttu-id="d9113-109">Nasıl yapılır: Virgülle ayrılmış metin dosyalarından okuma</span><span class="sxs-lookup"><span data-stu-id="d9113-109">How to: Read From Comma-Delimited Text Files</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="d9113-110">TextFieldParser Nesnesi</span><span class="sxs-lookup"><span data-stu-id="d9113-110">TextFieldParser Object</span></span>](../../visual-basic/language-reference/objects/textfieldparser-object.md)
