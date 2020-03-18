---
title: .NET'te Temel Dize Manipülasyonları
description: Birçok dize yöntemi çağıran bir örneğe bakın.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET Framework], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
ms.openlocfilehash: 87ce7a79ce18ca8f5579841ad9e52e2519d6ac73
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187253"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a><span data-ttu-id="78acc-103">Nasıl YapIlir: .NET'te Temel Dize Manipülasyonlarını Gerçekleştir</span><span class="sxs-lookup"><span data-stu-id="78acc-103">How to: Perform Basic String Manipulations in .NET</span></span>

<span data-ttu-id="78acc-104">Aşağıdaki örnek, dize işlemelerini gerçek dünya uygulamasında bulunabilecek şekilde gerçekleştiren bir sınıf oluşturmak için [Temel Dize İşlemleri](../../../docs/standard/base-types/basic-string-operations.md) konularında tartışılan yöntemlerden bazılarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="78acc-104">The following example uses some of the methods discussed in the [Basic String Operations](../../../docs/standard/base-types/basic-string-operations.md) topics to construct a class that performs string manipulations in a manner that might be found in a real-world application.</span></span> <span data-ttu-id="78acc-105">`MailToData` Sınıf, bir bireyin adını ve adresini ayrı özelliklerde depolar `City` `State`ve `Zip` kullanıcıya görüntülenmek üzere , ve alanları tek bir dize halinde birleştirmenin bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="78acc-105">The `MailToData` class stores the name and address of an individual in separate properties and provides a way to combine the `City`, `State`, and `Zip` fields into a single string for display to the user.</span></span> <span data-ttu-id="78acc-106">Ayrıca, sınıf kullanıcı nın şehir, eyalet ve Posta Kodu bilgilerini tek bir dize olarak girmesini sağlar; uygulama otomatik olarak tek dize parses ve ilgili özelliğine uygun bilgileri girer.</span><span class="sxs-lookup"><span data-stu-id="78acc-106">Furthermore, the class allows the user to enter the city, state, and ZIP Code information as a single string; the application automatically parses the single string and enters the proper information into the corresponding property.</span></span>  
  
<span data-ttu-id="78acc-107">Basitlik için bu örnek, komut satırı arabirimine sahip bir konsol uygulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="78acc-107">For simplicity, this example uses a console application with a command-line interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78acc-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="78acc-108">Example</span></span>  

[!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
[!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
<span data-ttu-id="78acc-109">Önceki kod yürütüldüğünde, kullanıcıdan ad larını ve adresini girmesi istenir.</span><span class="sxs-lookup"><span data-stu-id="78acc-109">When the preceding code is executed, the user is asked to enter their name and address.</span></span> <span data-ttu-id="78acc-110">Uygulama bilgileri uygun özelliklere yerleştirir ve bilgileri kullanıcıya geri görüntüler ve şehir, eyalet ve Posta Kodu bilgilerini görüntüleyen tek bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="78acc-110">The application places the information in the appropriate properties and displays the information back to the user, creating a single string that displays the city, state, and ZIP Code information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78acc-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78acc-111">See also</span></span>

- [<span data-ttu-id="78acc-112">Temel Dize İşlemleri</span><span class="sxs-lookup"><span data-stu-id="78acc-112">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
