---
title: Ayrılmış alanlar EscapeQuotes True olarak ayarlandığında çift tırnak işareti yasal sınırlayıcı olmadığından okunamıyor
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
ms.openlocfilehash: bc19fc7496b31eabca6dabedf212c89d6f5450d3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557454"
---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a><span data-ttu-id="896f5-102">Ayrılmış alanlar EscapeQuotes True olarak ayarlandığında çift tırnak işareti yasal sınırlayıcı olmadığından okunamıyor</span><span class="sxs-lookup"><span data-stu-id="896f5-102">Unable to read delimited fields because a double quote is not a legal delimiter when EscapeQuotes is set to True</span></span>
<span data-ttu-id="896f5-103">`TextFieldParser` Tırnak işareti (") ayırıcı olarak sağlanmadığından dosyasından okunamıyor ve `EscapeQuotes` ayarlanır `True`.</span><span class="sxs-lookup"><span data-stu-id="896f5-103">The `TextFieldParser` cannot read from the file because a quotation mark (") has been supplied as the delimiter and `EscapeQuotes` is set to `True`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="896f5-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="896f5-104">To correct this error</span></span>  
  
-   <span data-ttu-id="896f5-105">Ayarlama `EscapeQuotes` için `False`.</span><span class="sxs-lookup"><span data-stu-id="896f5-105">Set `EscapeQuotes` to `False`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="896f5-106">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="896f5-106">See also</span></span>

- [<span data-ttu-id="896f5-107">TextFieldParser.SetDelimiters yöntemi</span><span class="sxs-lookup"><span data-stu-id="896f5-107">TextFieldParser.SetDelimiters Method</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A)
- [<span data-ttu-id="896f5-108">TextFieldParser.Delimiters özelliği</span><span class="sxs-lookup"><span data-stu-id="896f5-108">TextFieldParser.Delimiters Property</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A)
- [<span data-ttu-id="896f5-109">Nasıl yapılır: Virgülle ayrılmış metin dosyalarından okuma</span><span class="sxs-lookup"><span data-stu-id="896f5-109">How to: Read From Comma-Delimited Text Files</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="896f5-110">TextFieldParser Nesnesi</span><span class="sxs-lookup"><span data-stu-id="896f5-110">TextFieldParser Object</span></span>](../../visual-basic/language-reference/objects/textfieldparser-object.md)
