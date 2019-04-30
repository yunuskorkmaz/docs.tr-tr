---
title: TextFieldParser, boşluk içeren yorum belirtkeleri desteklemiyor.
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_WhitespaceInToken
ms.assetid: 55107656-270e-4bbb-841a-478904df8e07
ms.openlocfilehash: 9a14bc29ecfa917b6213f32cd170aa83d6f60f58
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61668997"
---
# <a name="textfieldparser-does-not-support-comment-tokens-that-contain-white-space"></a><span data-ttu-id="3d4b2-102">TextFieldParser, boşluk içeren yorum belirtkeleri desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="3d4b2-102">TextFieldParser does not support comment tokens that contain white space</span></span>
<span data-ttu-id="3d4b2-103">Boşluk içeren bir açıklama belirteci sağlandı.</span><span class="sxs-lookup"><span data-stu-id="3d4b2-103">A comment token that contains white space has been supplied.</span></span> <span data-ttu-id="3d4b2-104">`TextFieldParser` Belirteç başında boşluk gerçekleşmediği sürece, boşluk içeren yorum belirtkeleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="3d4b2-104">The `TextFieldParser` does not support comment tokens that contain white space unless the white space occurs at the beginning of the token.</span></span> <span data-ttu-id="3d4b2-105">Gerçekleşen bir belirteç başında boşluk yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="3d4b2-105">White space occurring at the beginning of a token is ignored.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3d4b2-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="3d4b2-106">To correct this error</span></span>  
  
- <span data-ttu-id="3d4b2-107">Doğru açıklama belirteci sağlayın.</span><span class="sxs-lookup"><span data-stu-id="3d4b2-107">Supply a correct comment token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d4b2-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d4b2-108">See also</span></span>

- [<span data-ttu-id="3d4b2-109">TextFieldParser.CommentTokens özelliği</span><span class="sxs-lookup"><span data-stu-id="3d4b2-109">TextFieldParser.CommentTokens Property</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.CommentTokens%2A)
- [<span data-ttu-id="3d4b2-110">TextFieldParser Nesnesiyle Metin Dosyalarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="3d4b2-110">Parsing Text Files with the TextFieldParser Object</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="3d4b2-111">TextFieldParser Nesnesi</span><span class="sxs-lookup"><span data-stu-id="3d4b2-111">TextFieldParser Object</span></span>](../../visual-basic/language-reference/objects/textfieldparser-object.md)
