---
title: 'Nasıl yapılır: .NET içinde temel dize işlemeleri gerçekleştirme'
description: Birçok dize yöntemlerini çağıran bir örneğe bakın.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET Framework], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
author: rpetrusha
ms.author: ronpet
ms.custom: seodec18
ms.openlocfilehash: 11f8043745c631a642b437339240cbf06fc8df5b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62025944"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a><span data-ttu-id="6f641-103">Nasıl yapılır: .NET içinde temel dize işlemeleri gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="6f641-103">How to: Perform Basic String Manipulations in .NET</span></span>
<span data-ttu-id="6f641-104">Aşağıdaki örnek, bazı ele yöntemlerini kullanır [temel dize işlemleri](../../../docs/standard/base-types/basic-string-operations.md) dize işlemeleri gerçek bir uygulamada bulunan bir biçimde gerçekleştiren bir sınıf oluşturmak için konuları.</span><span class="sxs-lookup"><span data-stu-id="6f641-104">The following example uses some of the methods discussed in the [Basic String Operations](../../../docs/standard/base-types/basic-string-operations.md) topics to construct a class that performs string manipulations in a manner that might be found in a real-world application.</span></span> <span data-ttu-id="6f641-105">`MailToData` Sınıf adını ve bireysel adresini ayrı özelliklerinde depolar ve birleştirmek için bir yol sağlar `City`, `State`, ve `Zip` alanlarına kullanıcıya görüntülemek için tek bir dize.</span><span class="sxs-lookup"><span data-stu-id="6f641-105">The `MailToData` class stores the name and address of an individual in separate properties and provides a way to combine the `City`, `State`, and `Zip` fields into a single string for display to the user.</span></span> <span data-ttu-id="6f641-106">Ayrıca, sınıfı tek bir dize olarak Şehir, eyalet ve posta kodu bilgilerini girmesini sağlar; Uygulama, otomatik olarak tek bir dizeyi ayrıştırır ve karşılık gelen özelliğine doğru bilgilerin girer.</span><span class="sxs-lookup"><span data-stu-id="6f641-106">Furthermore, the class allows the user to enter the city, state, and ZIP Code information as a single string; the application automatically parses the single string and enters the proper information into the corresponding property.</span></span>  
  
 <span data-ttu-id="6f641-107">Kolaylık olması için bu örnekte, bir komut satırı arabirimi ile bir konsol uygulaması kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6f641-107">For simplicity, this example uses a console application with a command-line interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f641-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="6f641-108">Example</span></span>  
 [!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
 [!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
 <span data-ttu-id="6f641-109">Önceki kod yürütüldüğünde, kullanıcı adını ve adresini kendi girmesi istenir.</span><span class="sxs-lookup"><span data-stu-id="6f641-109">When the preceding code is executed, the user is asked to enter his or her name and address.</span></span> <span data-ttu-id="6f641-110">Uygulama bilgileri uygun özellikler yerleştirir ve şehir, eyalet ve posta kodu bilgi görüntüler tek bir dize oluşturma geri kullanıcıya bilgi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6f641-110">The application places the information in the appropriate properties and displays the information back to the user, creating a single string that displays the city, state, and ZIP Code information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f641-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f641-111">See also</span></span>

- [<span data-ttu-id="6f641-112">Temel Dize İşlemleri</span><span class="sxs-lookup"><span data-stu-id="6f641-112">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
