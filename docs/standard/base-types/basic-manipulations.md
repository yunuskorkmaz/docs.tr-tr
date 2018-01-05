---
title: "Nasıl yapılır: .NET Framework'te Temel Dize İşlemeleri Gerçekleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: strings [.NET Framework], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8d3d5351a0a639a3f0b674640bcaaf7321ca0d76
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a><span data-ttu-id="24508-102">Nasıl yapılır: .NET temel dize işlemeleri gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="24508-102">How to: Perform Basic String Manipulations in .NET</span></span>
<span data-ttu-id="24508-103">Aşağıdaki örnek ele yöntemlerin bazıları kullanır [temel dize işlemleri](../../../docs/standard/base-types/basic-string-operations.md) konuları gerçek uygulamada bulunan bir şekilde dize işlemeleri gerçekleştiren bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="24508-103">The following example uses some of the methods discussed in the [Basic String Operations](../../../docs/standard/base-types/basic-string-operations.md) topics to construct a class that performs string manipulations in a manner that might be found in a real-world application.</span></span> <span data-ttu-id="24508-104">`MailToData` Sınıf adını ve adresini tek bir ayrı özelliklerinde depolar ve birleştirmek için bir yol sağlar `City`, `State`, ve `Zip` alanlarına kullanıcıya görüntülenmesi için tek bir dize.</span><span class="sxs-lookup"><span data-stu-id="24508-104">The `MailToData` class stores the name and address of an individual in separate properties and provides a way to combine the `City`, `State`, and `Zip` fields into a single string for display to the user.</span></span> <span data-ttu-id="24508-105">Ayrıca, sınıfı tek bir dize Şehir, eyalet ve posta kodu bilgi girmek kullanıcı verir; uygulama otomatik olarak tek bir dize ayrıştırır ve karşılık gelen özelliği uygun bilgileri girer.</span><span class="sxs-lookup"><span data-stu-id="24508-105">Furthermore, the class allows the user to enter the city, state, and ZIP Code information as a single string; the application automatically parses the single string and enters the proper information into the corresponding property.</span></span>  
  
 <span data-ttu-id="24508-106">Kolaylık olması için bu örnek, bir komut satırı arabirimi ile bir konsol uygulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="24508-106">For simplicity, this example uses a console application with a command-line interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24508-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="24508-107">Example</span></span>  
 [!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
 [!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
 <span data-ttu-id="24508-108">Önceki kod yürütüldüğünde, kullanıcının kendi adı veya adresi girmesi istenir.</span><span class="sxs-lookup"><span data-stu-id="24508-108">When the preceding code is executed, the user is asked to enter his or her name and address.</span></span> <span data-ttu-id="24508-109">Uygulama bilgileri uygun özelliklerinde yerleştirir ve şehir, eyalet ve posta kodu bilgi görüntüler tek bir dize oluşturma geri kullanıcıya bilgi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="24508-109">The application places the information in the appropriate properties and displays the information back to the user, creating a single string that displays the city, state, and ZIP Code information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24508-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="24508-110">See Also</span></span>  
 [<span data-ttu-id="24508-111">Temel Dize İşlemleri</span><span class="sxs-lookup"><span data-stu-id="24508-111">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
