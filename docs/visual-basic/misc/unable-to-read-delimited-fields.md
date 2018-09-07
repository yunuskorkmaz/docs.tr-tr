---
title: Ayrılmış alanlar EscapeQuotes True olarak ayarlandığında çift tırnak işareti yasal sınırlayıcı olmadığından okunamıyor
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
ms.openlocfilehash: a119bf2592982b87c4bd361f9d125e6e8b7173c1
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44087231"
---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a><span data-ttu-id="a50d2-102">Ayrılmış alanlar EscapeQuotes True olarak ayarlandığında çift tırnak işareti yasal sınırlayıcı olmadığından okunamıyor</span><span class="sxs-lookup"><span data-stu-id="a50d2-102">Unable to read delimited fields because a double quote is not a legal delimiter when EscapeQuotes is set to True</span></span>
<span data-ttu-id="a50d2-103">`TextFieldParser` Tırnak işareti (") ayırıcı olarak sağlanmadığından dosyasından okunamıyor ve `EscapeQuotes` ayarlanır `True`.</span><span class="sxs-lookup"><span data-stu-id="a50d2-103">The `TextFieldParser` cannot read from the file because a quotation mark (") has been supplied as the delimiter and `EscapeQuotes` is set to `True`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a50d2-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="a50d2-104">To correct this error</span></span>  
  
-   <span data-ttu-id="a50d2-105">Ayarlama `EscapeQuotes` için `False`.</span><span class="sxs-lookup"><span data-stu-id="a50d2-105">Set `EscapeQuotes` to `False`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a50d2-106">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a50d2-106">See also</span></span>

- [<span data-ttu-id="a50d2-107">TextFieldParser.SetDelimiters yöntemi</span><span class="sxs-lookup"><span data-stu-id="a50d2-107">TextFieldParser.SetDelimiters Method</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A)  
- [<span data-ttu-id="a50d2-108">TextFieldParser.Delimiters özelliği</span><span class="sxs-lookup"><span data-stu-id="a50d2-108">TextFieldParser.Delimiters Property</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A)  
- [<span data-ttu-id="a50d2-109">Nasıl Yapılır: Virgülle Ayrılmış Metin Dosyalarından Okuma</span><span class="sxs-lookup"><span data-stu-id="a50d2-109">How to: Read From Comma-Delimited Text Files</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)  
- [<span data-ttu-id="a50d2-110">TextFieldParser Nesnesi</span><span class="sxs-lookup"><span data-stu-id="a50d2-110">TextFieldParser Object</span></span>](../../visual-basic/language-reference/objects/textfieldparser-object.md)
