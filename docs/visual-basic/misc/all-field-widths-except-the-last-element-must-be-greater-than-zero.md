---
title: Son öğe hariç tüm alan genişlikleri sıfırdan büyük olmalıdır
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_FieldWidthsMustPositive
ms.assetid: 41d8c661-a749-4c89-be56-905c6e7c3c9d
ms.openlocfilehash: 4fb40e5f2b458fbbd0bfdb329f75250e70fd7e28
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91083923"
---
# <a name="all-field-widths-except-the-last-element-must-be-greater-than-zero"></a><span data-ttu-id="f04d6-102">Son öğe hariç tüm alan genişlikleri sıfırdan büyük olmalıdır</span><span class="sxs-lookup"><span data-stu-id="f04d6-102">All field widths, except the last element, must be greater than zero</span></span>

<span data-ttu-id="f04d6-103">Son öğe hariç tüm alan genişlikleri sıfırdan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f04d6-103">All field widths, except the last element, must be greater than zero.</span></span> <span data-ttu-id="f04d6-104">Son öğede sıfıra eşit veya daha küçük bir alan genişliği, son alanın değişken uzunlukta olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f04d6-104">A field width less than or equal to zero in the last element indicates the last field is of variable length.</span></span>  
  
 <span data-ttu-id="f04d6-105">Son öğeden başka bir alan genişliği sıfır veya daha az olarak ayarlandığı için işlem başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="f04d6-105">The operation has failed because a field width other than the last element is set to zero or less.</span></span> <span data-ttu-id="f04d6-106">Sıfırdan küçük veya eşit bir alan genişliği, son alanın değişken uzunlukta olduğunu göstermek için son öğe olarak kullanılabilir, ancak başka bir öğesi olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f04d6-106">A field width less than or equal to zero can be used as the last element to indicate that the last field is of variable length, but it cannot be used as any other element.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f04d6-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="f04d6-107">To correct this error</span></span>  
  
- <span data-ttu-id="f04d6-108">Alan genişliğini doğru uzunluğa ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f04d6-108">Set the field width to the correct length.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f04d6-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f04d6-109">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetFieldWidths%2A?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.FieldWidths>
- [<span data-ttu-id="f04d6-110">Nasıl yapılır: Sabit Genişlikli Metin Dosyalarından Okuma</span><span class="sxs-lookup"><span data-stu-id="f04d6-110">How to: Read From Fixed-width Text Files</span></span>](../developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="f04d6-111">TextFieldParser Nesnesi</span><span class="sxs-lookup"><span data-stu-id="f04d6-111">TextFieldParser Object</span></span>](../language-reference/objects/textfieldparser-object.md)
