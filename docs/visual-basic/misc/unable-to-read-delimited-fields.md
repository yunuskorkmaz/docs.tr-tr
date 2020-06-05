---
title: Kaçış eşler doğru olarak ayarlandığında çift tırnak işareti geçerli bir sınırlayıcı olmadığından, ayrılmış alanlar okunamıyor
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
ms.openlocfilehash: cd2dd4226296ecd210a1e72a7b7fb593874b0008
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398480"
---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a><span data-ttu-id="269b2-102">Kaçış eşler doğru olarak ayarlandığında çift tırnak işareti geçerli bir sınırlayıcı olmadığından, ayrılmış alanlar okunamıyor</span><span class="sxs-lookup"><span data-stu-id="269b2-102">Unable to read delimited fields because a double quote is not a legal delimiter when EscapeQuotes is set to True</span></span>
<span data-ttu-id="269b2-103">`TextFieldParser`Sınırlayıcı olarak bir tırnak işareti (") sağlandığı ve olarak `EscapeQuotes` ayarlandığı için dosyadan okunamıyor `True` .</span><span class="sxs-lookup"><span data-stu-id="269b2-103">The `TextFieldParser` cannot read from the file because a quotation mark (") has been supplied as the delimiter and `EscapeQuotes` is set to `True`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="269b2-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="269b2-104">To correct this error</span></span>  
  
- <span data-ttu-id="269b2-105">`EscapeQuotes`Olarak ayarlayın `False` .</span><span class="sxs-lookup"><span data-stu-id="269b2-105">Set `EscapeQuotes` to `False`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="269b2-106">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="269b2-106">See also</span></span>

- [<span data-ttu-id="269b2-107">TextFieldParser. Setsınırlayıcılar yöntemi</span><span class="sxs-lookup"><span data-stu-id="269b2-107">TextFieldParser.SetDelimiters Method</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A)
- [<span data-ttu-id="269b2-108">TextFieldParser. sınırlayıcılar özelliği</span><span class="sxs-lookup"><span data-stu-id="269b2-108">TextFieldParser.Delimiters Property</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A)
- [<span data-ttu-id="269b2-109">Nasıl yapılır: Virgülle Ayrılmış Metin Dosyalarından Okuma</span><span class="sxs-lookup"><span data-stu-id="269b2-109">How to: Read From Comma-Delimited Text Files</span></span>](../developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="269b2-110">TextFieldParser Nesnesi</span><span class="sxs-lookup"><span data-stu-id="269b2-110">TextFieldParser Object</span></span>](../language-reference/objects/textfieldparser-object.md)
