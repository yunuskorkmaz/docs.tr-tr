---
description: 'Daha fazla bilgi edinin: bir çift tırnak, kaçış eşlerini true olarak ayarlandığında geçerli bir sınırlayıcı olmadığından, ayrılmış alanlar okunamadı'
title: Kaçış eşler doğru olarak ayarlandığında çift tırnak işareti geçerli bir sınırlayıcı olmadığından, ayrılmış alanlar okunamıyor
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
ms.openlocfilehash: 066b5110eaddad74b64f1d86683d7ca2a0a619f7
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474401"
---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a><span data-ttu-id="b22a9-103">Kaçış eşler doğru olarak ayarlandığında çift tırnak işareti geçerli bir sınırlayıcı olmadığından, ayrılmış alanlar okunamıyor</span><span class="sxs-lookup"><span data-stu-id="b22a9-103">Unable to read delimited fields because a double quote is not a legal delimiter when EscapeQuotes is set to True</span></span>

<span data-ttu-id="b22a9-104">`TextFieldParser`Sınırlayıcı olarak bir tırnak işareti (") sağlandığı ve olarak `EscapeQuotes` ayarlandığı için dosyadan okunamıyor `True` .</span><span class="sxs-lookup"><span data-stu-id="b22a9-104">The `TextFieldParser` cannot read from the file because a quotation mark (") has been supplied as the delimiter and `EscapeQuotes` is set to `True`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b22a9-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="b22a9-105">To correct this error</span></span>  
  
- <span data-ttu-id="b22a9-106">`EscapeQuotes`Olarak ayarlayın `False` .</span><span class="sxs-lookup"><span data-stu-id="b22a9-106">Set `EscapeQuotes` to `False`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b22a9-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b22a9-107">See also</span></span>

- [<span data-ttu-id="b22a9-108">TextFieldParser. Setsınırlayıcılar yöntemi</span><span class="sxs-lookup"><span data-stu-id="b22a9-108">TextFieldParser.SetDelimiters Method</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A)
- [<span data-ttu-id="b22a9-109">TextFieldParser. sınırlayıcılar özelliği</span><span class="sxs-lookup"><span data-stu-id="b22a9-109">TextFieldParser.Delimiters Property</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A)
- [<span data-ttu-id="b22a9-110">Nasıl yapılır: Virgülle Ayrılmış Metin Dosyalarından Okuma</span><span class="sxs-lookup"><span data-stu-id="b22a9-110">How to: Read From Comma-Delimited Text Files</span></span>](../developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="b22a9-111">TextFieldParser Nesnesi</span><span class="sxs-lookup"><span data-stu-id="b22a9-111">TextFieldParser Object</span></span>](../language-reference/objects/textfieldparser-object.md)
