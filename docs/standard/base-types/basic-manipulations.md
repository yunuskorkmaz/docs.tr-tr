---
title: .NET 'teki temel dize Işlemeleri
description: Birçok dize yöntemini çağıran bir örneğe bakın.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET Framework], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
ms.openlocfilehash: 54de6451029fb268beb7ebe4ded0d7b437c3df3c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289869"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a><span data-ttu-id="2af28-103">Nasıl yapılır: .NET 'te temel dize Işlemeleri gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="2af28-103">How to: Perform Basic String Manipulations in .NET</span></span>

<span data-ttu-id="2af28-104">Aşağıdaki örnek, [temel dize işlemleri](basic-string-operations.md) konularında açıklanan yöntemlerin bazılarını kullanarak, bir gerçek dünya uygulamasında bulunabilir bir şekilde dize düzenlemeleri gerçekleştiren bir sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2af28-104">The following example uses some of the methods discussed in the [Basic String Operations](basic-string-operations.md) topics to construct a class that performs string manipulations in a manner that might be found in a real-world application.</span></span> <span data-ttu-id="2af28-105">`MailToData`Sınıfı, bir bireyin adı ve adresini ayrı özelliklerde depolar ve `City` ,, `State` ve `Zip` alanlarını kullanıcıya görüntüleme için tek bir dize olarak birleştirmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="2af28-105">The `MailToData` class stores the name and address of an individual in separate properties and provides a way to combine the `City`, `State`, and `Zip` fields into a single string for display to the user.</span></span> <span data-ttu-id="2af28-106">Ayrıca, sınıfı kullanıcının şehir, eyalet ve posta kodu bilgilerini tek bir dize olarak girmesine izin verir; uygulama, tek dizeyi otomatik olarak ayrıştırır ve ilgili özelliğe uygun bilgileri girer.</span><span class="sxs-lookup"><span data-stu-id="2af28-106">Furthermore, the class allows the user to enter the city, state, and ZIP Code information as a single string; the application automatically parses the single string and enters the proper information into the corresponding property.</span></span>  
  
<span data-ttu-id="2af28-107">Kolaylık olması için bu örnek, bir komut satırı arabirimi ile bir konsol uygulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="2af28-107">For simplicity, this example uses a console application with a command-line interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2af28-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="2af28-108">Example</span></span>  

[!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
[!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
<span data-ttu-id="2af28-109">Yukarıdaki kod yürütüldüğünde, kullanıcıdan ad ve adreslerini girmesi istenir.</span><span class="sxs-lookup"><span data-stu-id="2af28-109">When the preceding code is executed, the user is asked to enter their name and address.</span></span> <span data-ttu-id="2af28-110">Uygulama, bilgileri uygun özelliklere koyar ve bu bilgileri, şehir, eyalet ve ZIP kodu bilgilerini görüntüleyen tek bir dize oluşturarak kullanıcıya geri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2af28-110">The application places the information in the appropriate properties and displays the information back to the user, creating a single string that displays the city, state, and ZIP Code information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2af28-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2af28-111">See also</span></span>

- [<span data-ttu-id="2af28-112">Temel dize Işlemleri</span><span class="sxs-lookup"><span data-stu-id="2af28-112">Basic String Operations</span></span>](basic-string-operations.md)
