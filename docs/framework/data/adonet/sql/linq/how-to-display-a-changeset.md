---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: değişiklik kümesi görüntüleme'
title: 'Nasıl yapılır: Değişiklik Kümesini Görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 126e7245-c5a0-4ebf-800d-cc1fcf9cd0ab
ms.openlocfilehash: e5ff7aebcc74ded1300433a3bf7b280db3a11b28
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786023"
---
# <a name="how-to-display-a-changeset"></a><span data-ttu-id="f22c0-103">Nasıl yapılır: Değişiklik Kümesini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="f22c0-103">How to: Display a ChangeSet</span></span>

<span data-ttu-id="f22c0-104">Kullanarak tarafından izlenen değişiklikleri görüntüleyebilirsiniz <xref:System.Data.Linq.DataContext> <xref:System.Data.Linq.DataContext.GetChangeSet%2A> .</span><span class="sxs-lookup"><span data-stu-id="f22c0-104">You can view changes tracked by a <xref:System.Data.Linq.DataContext> by using <xref:System.Data.Linq.DataContext.GetChangeSet%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f22c0-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="f22c0-105">Example</span></span>  

 <span data-ttu-id="f22c0-106">Aşağıdaki örnek, şehri Londra olan müşterileri alır, şehri Istanbul olarak değiştirir ve değişiklikleri veritabanına geri gönderir.</span><span class="sxs-lookup"><span data-stu-id="f22c0-106">The following example retrieves customers whose city is London, changes the city to Paris, and submits the changes back to the database.</span></span>  
  
 [!code-csharp[DLinqDebuggingSupport#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#2)]
 [!code-vb[DLinqDebuggingSupport#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#2)]  
  
 <span data-ttu-id="f22c0-107">Bu koddan alınan çıktı aşağıdakine benzer şekilde görünür.</span><span class="sxs-lookup"><span data-stu-id="f22c0-107">Output from this code appears similar to the following.</span></span> <span data-ttu-id="f22c0-108">Sonundaki Özet sekiz değişikliğin yapıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f22c0-108">Note that the summary at the end shows that eight changes were made.</span></span>  

 ```console
CustomerID: AROUT
   Original value: London
   Updated value: Paris
CustomerID: BSBEV
   Original value: London
   Updated value: Paris
CustomerID: CONSH
   Original value: London
   Updated value: Paris
CustomerID: EASTC
   Original value: London
   Updated value: Paris
CustomerID: NORTS
    Original value: London
    Updated value: Paris
CustomerID: PARIS
    Original value: London
    Updated value: Paris
CustomerID: SEVES
    Original value: London
    Updated value: Paris
CustomerID: SPECD
    Original value: London
    Updated value: Paris
Total changes: {Added: 0, Removed: 0, Modified: 8}
```
  
## <a name="see-also"></a><span data-ttu-id="f22c0-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f22c0-109">See also</span></span>

- [<span data-ttu-id="f22c0-110">Hata Ayıklama Desteği</span><span class="sxs-lookup"><span data-stu-id="f22c0-110">Debugging Support</span></span>](debugging-support.md)
