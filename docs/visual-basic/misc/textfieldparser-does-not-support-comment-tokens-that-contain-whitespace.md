---
title: TextFieldParser boşluk içeren açıklama belirteçlerini desteklemiyor
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_WhitespaceInToken
ms.assetid: 55107656-270e-4bbb-841a-478904df8e07
ms.openlocfilehash: 51dc2b82d7f04c652e18173b8450b65c15ee6ec2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411902"
---
# <a name="textfieldparser-does-not-support-comment-tokens-that-contain-white-space"></a><span data-ttu-id="4c5db-102">TextFieldParser boşluk içeren açıklama belirteçlerini desteklemiyor</span><span class="sxs-lookup"><span data-stu-id="4c5db-102">TextFieldParser does not support comment tokens that contain white space</span></span>
<span data-ttu-id="4c5db-103">Boşluk içeren bir açıklama belirteci sağlandı.</span><span class="sxs-lookup"><span data-stu-id="4c5db-103">A comment token that contains white space has been supplied.</span></span> <span data-ttu-id="4c5db-104">, `TextFieldParser` Belirtecin başlangıcında boşluk oluşmadığı takdirde boşluk içeren açıklama belirteçlerini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="4c5db-104">The `TextFieldParser` does not support comment tokens that contain white space unless the white space occurs at the beginning of the token.</span></span> <span data-ttu-id="4c5db-105">Belirtecin başlangıcında gerçekleşen boşluk yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="4c5db-105">White space occurring at the beginning of a token is ignored.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4c5db-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="4c5db-106">To correct this error</span></span>  
  
- <span data-ttu-id="4c5db-107">Doğru bir açıklama belirteci sağlayın.</span><span class="sxs-lookup"><span data-stu-id="4c5db-107">Supply a correct comment token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c5db-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c5db-108">See also</span></span>

- [<span data-ttu-id="4c5db-109">TextFieldParser. CommentTokens özelliği</span><span class="sxs-lookup"><span data-stu-id="4c5db-109">TextFieldParser.CommentTokens Property</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.CommentTokens%2A)
- [<span data-ttu-id="4c5db-110">TextFieldParser Nesnesiyle Metin Dosyalarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="4c5db-110">Parsing Text Files with the TextFieldParser Object</span></span>](../developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="4c5db-111">TextFieldParser Nesnesi</span><span class="sxs-lookup"><span data-stu-id="4c5db-111">TextFieldParser Object</span></span>](../language-reference/objects/textfieldparser-object.md)
