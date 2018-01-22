---
title: "EscapeQuotes True olarak ayarlandığında çift tırnak işareti geçerli ayırıcı olmadığından ayrılmış alanlar okunamıyor"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1b5ee30da2146d6fa9841a80cc0e841bd737961f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a><span data-ttu-id="1bbbe-102">EscapeQuotes True olarak ayarlandığında çift tırnak işareti geçerli ayırıcı olmadığından ayrılmış alanlar okunamıyor</span><span class="sxs-lookup"><span data-stu-id="1bbbe-102">Unable to read delimited fields because a double quote is not a legal delimiter when EscapeQuotes is set to True</span></span>
<span data-ttu-id="1bbbe-103">`TextFieldParser` Tırnak işareti (") sınırlayıcı sağlanmadığından dosyasından okunamıyor ve `EscapeQuotes` ayarlanır `True`.</span><span class="sxs-lookup"><span data-stu-id="1bbbe-103">The `TextFieldParser` cannot read from the file because a quotation mark (") has been supplied as the delimiter and `EscapeQuotes` is set to `True`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1bbbe-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="1bbbe-104">To correct this error</span></span>  
  
-   <span data-ttu-id="1bbbe-105">Ayarlama `EscapeQuotes` için `False`.</span><span class="sxs-lookup"><span data-stu-id="1bbbe-105">Set `EscapeQuotes` to `False`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bbbe-106">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1bbbe-106">See Also</span></span>  
 [<span data-ttu-id="1bbbe-107">TextFieldParser.SetDelimiters yöntemi</span><span class="sxs-lookup"><span data-stu-id="1bbbe-107">TextFieldParser.SetDelimiters Method</span></span>](http://msdn.microsoft.com/library/21fa40ec-5866-4d0e-9fd9-c708a190dcc9)  
 [<span data-ttu-id="1bbbe-108">TextFieldParser.Delimiters Property</span><span class="sxs-lookup"><span data-stu-id="1bbbe-108">TextFieldParser.Delimiters Property</span></span>](http://msdn.microsoft.com/library/4eb18f4d-3011-40a9-b668-be93eed0444f)  
 [<span data-ttu-id="1bbbe-109">Nasıl Yapılır: Virgülle Ayrılmış Metin Dosyalarından Okuma</span><span class="sxs-lookup"><span data-stu-id="1bbbe-109">How to: Read From Comma-Delimited Text Files</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)  
 [<span data-ttu-id="1bbbe-110">TextFieldParser Nesnesi</span><span class="sxs-lookup"><span data-stu-id="1bbbe-110">TextFieldParser Object</span></span>](../../visual-basic/language-reference/objects/textfieldparser-object.md)
