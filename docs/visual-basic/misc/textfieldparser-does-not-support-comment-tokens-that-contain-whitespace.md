---
description: 'Hakkında daha fazla bilgi edinin: TextFieldParser boşluk içeren açıklama belirteçlerini desteklemez'
title: TextFieldParser boşluk içeren açıklama belirteçlerini desteklemiyor
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_WhitespaceInToken
ms.assetid: 55107656-270e-4bbb-841a-478904df8e07
ms.openlocfilehash: 27ca19f0a901ca1644d4b121951ed9fdf4d553bd
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100455346"
---
# <a name="textfieldparser-does-not-support-comment-tokens-that-contain-white-space"></a><span data-ttu-id="d2c59-103">TextFieldParser boşluk içeren açıklama belirteçlerini desteklemiyor</span><span class="sxs-lookup"><span data-stu-id="d2c59-103">TextFieldParser does not support comment tokens that contain white space</span></span>

<span data-ttu-id="d2c59-104">Boşluk içeren bir açıklama belirteci sağlandı.</span><span class="sxs-lookup"><span data-stu-id="d2c59-104">A comment token that contains white space has been supplied.</span></span> <span data-ttu-id="d2c59-105">, `TextFieldParser` Belirtecin başlangıcında boşluk oluşmadığı takdirde boşluk içeren açıklama belirteçlerini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d2c59-105">The `TextFieldParser` does not support comment tokens that contain white space unless the white space occurs at the beginning of the token.</span></span> <span data-ttu-id="d2c59-106">Belirtecin başlangıcında gerçekleşen boşluk yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="d2c59-106">White space occurring at the beginning of a token is ignored.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d2c59-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="d2c59-107">To correct this error</span></span>  
  
- <span data-ttu-id="d2c59-108">Doğru bir açıklama belirteci sağlayın.</span><span class="sxs-lookup"><span data-stu-id="d2c59-108">Supply a correct comment token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2c59-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2c59-109">See also</span></span>

- [<span data-ttu-id="d2c59-110">TextFieldParser. CommentTokens özelliği</span><span class="sxs-lookup"><span data-stu-id="d2c59-110">TextFieldParser.CommentTokens Property</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.CommentTokens%2A)
- [<span data-ttu-id="d2c59-111">TextFieldParser Nesnesiyle Metin Dosyalarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="d2c59-111">Parsing Text Files with the TextFieldParser Object</span></span>](../developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="d2c59-112">TextFieldParser Nesnesi</span><span class="sxs-lookup"><span data-stu-id="d2c59-112">TextFieldParser Object</span></span>](../language-reference/objects/textfieldparser-object.md)
