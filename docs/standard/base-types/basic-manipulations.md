---
title: "Nasıl yapılır: .NET 'te temel dize Işlemeleri gerçekleştirme"
description: Birçok dize yöntemini çağıran bir örneğe bakın.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET Framework], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
ms.openlocfilehash: ff7abee460b4085fa9e039e678c975338ccb511a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711512"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a><span data-ttu-id="4837c-103">Nasıl yapılır: .NET 'te temel dize Işlemeleri gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="4837c-103">How to: Perform Basic String Manipulations in .NET</span></span>
<span data-ttu-id="4837c-104">Aşağıdaki örnek, [temel dize işlemleri](../../../docs/standard/base-types/basic-string-operations.md) konularında açıklanan yöntemlerin bazılarını kullanarak, bir gerçek dünya uygulamasında bulunabilir bir şekilde dize düzenlemeleri gerçekleştiren bir sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4837c-104">The following example uses some of the methods discussed in the [Basic String Operations](../../../docs/standard/base-types/basic-string-operations.md) topics to construct a class that performs string manipulations in a manner that might be found in a real-world application.</span></span> <span data-ttu-id="4837c-105">`MailToData` sınıfı, bir bireyin adı ve adresini ayrı özelliklerde depolar ve `City`, `State`ve `Zip` alanlarını kullanıcıya göstermek için tek bir dizeye birleştirmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="4837c-105">The `MailToData` class stores the name and address of an individual in separate properties and provides a way to combine the `City`, `State`, and `Zip` fields into a single string for display to the user.</span></span> <span data-ttu-id="4837c-106">Ayrıca, sınıfı kullanıcının şehir, eyalet ve posta kodu bilgilerini tek bir dize olarak girmesine izin verir; uygulama, tek dizeyi otomatik olarak ayrıştırır ve ilgili özelliğe uygun bilgileri girer.</span><span class="sxs-lookup"><span data-stu-id="4837c-106">Furthermore, the class allows the user to enter the city, state, and ZIP Code information as a single string; the application automatically parses the single string and enters the proper information into the corresponding property.</span></span>  
  
 <span data-ttu-id="4837c-107">Kolaylık olması için bu örnek, bir komut satırı arabirimi ile bir konsol uygulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="4837c-107">For simplicity, this example uses a console application with a command-line interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4837c-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="4837c-108">Example</span></span>  
 [!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
 [!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
 <span data-ttu-id="4837c-109">Yukarıdaki kod yürütüldüğünde, kullanıcıdan adını ve adresini girmesi istenir.</span><span class="sxs-lookup"><span data-stu-id="4837c-109">When the preceding code is executed, the user is asked to enter his or her name and address.</span></span> <span data-ttu-id="4837c-110">Uygulama, bilgileri uygun özelliklere koyar ve bu bilgileri, şehir, eyalet ve ZIP kodu bilgilerini görüntüleyen tek bir dize oluşturarak kullanıcıya geri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4837c-110">The application places the information in the appropriate properties and displays the information back to the user, creating a single string that displays the city, state, and ZIP Code information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4837c-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4837c-111">See also</span></span>

- [<span data-ttu-id="4837c-112">Temel Dize İşlemleri</span><span class="sxs-lookup"><span data-stu-id="4837c-112">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
