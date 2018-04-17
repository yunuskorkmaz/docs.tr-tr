---
title: "Nasıl Yapılır: Visual Basic'de Bir StringBuilder Kullanarak Dize Oluşturma"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c0e15c7df07822ee104a88525c209768c05470e3
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="cfdee-102">Nasıl Yapılır: Visual Basic'de Bir StringBuilder Kullanarak Dize Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cfdee-102">How to: Create Strings Using a StringBuilder in Visual Basic</span></span>
<span data-ttu-id="cfdee-103">Bu örnek kullanarak çok sayıda küçük dizelerden uzun bir dize oluşturur <xref:System.Text.StringBuilder> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="cfdee-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="cfdee-104"><xref:System.Text.StringBuilder> Sınıftır daha verimlidir `&=` birçok dizeleri birleştirme işleci.</span><span class="sxs-lookup"><span data-stu-id="cfdee-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cfdee-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="cfdee-105">Example</span></span>  
 <span data-ttu-id="cfdee-106">Aşağıdaki örnekte bir örneğini oluşturur <xref:System.Text.StringBuilder> sınıfı, bu örneğe 1.000 dizeleri ekler ve kendi dize gösterimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="cfdee-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation.</span></span>  
  
 [!code-vb[VbVbalrStrings#70](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-strings-using-a-stringbuilder_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="cfdee-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cfdee-107">See Also</span></span>  
 [<span data-ttu-id="cfdee-108">StringBuilder Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="cfdee-108">Using the StringBuilder Class</span></span>](../../../../standard/base-types/stringbuilder.md)  
 [<span data-ttu-id="cfdee-109">&= İşleci</span><span class="sxs-lookup"><span data-stu-id="cfdee-109">&= Operator</span></span>](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [<span data-ttu-id="cfdee-110">Dizeler</span><span class="sxs-lookup"><span data-stu-id="cfdee-110">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)  
 [<span data-ttu-id="cfdee-111">Yeni Dizeler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cfdee-111">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)  
 [<span data-ttu-id="cfdee-112">Dizeleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="cfdee-112">Manipulating Strings</span></span>](../../../../standard/base-types/manipulating-strings.md)  
 <span data-ttu-id="cfdee-113">[Dizeleri örnek](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="cfdee-113">[Strings Sample](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))</span></span>
