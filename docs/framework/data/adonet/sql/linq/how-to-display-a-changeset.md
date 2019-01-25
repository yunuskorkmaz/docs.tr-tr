---
title: 'Nasıl yapılır: Değişiklik kümesini görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 126e7245-c5a0-4ebf-800d-cc1fcf9cd0ab
ms.openlocfilehash: 773e72d52a934bc7c6fa80fe252d62e67f87a34b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596806"
---
# <a name="how-to-display-a-changeset"></a><span data-ttu-id="a40cd-102">Nasıl yapılır: Değişiklik kümesini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="a40cd-102">How to: Display a ChangeSet</span></span>
<span data-ttu-id="a40cd-103">Tarafından izlenen değişiklikleri görüntüleyebileceğiniz bir <xref:System.Data.Linq.DataContext> kullanarak <xref:System.Data.Linq.DataContext.GetChangeSet%2A>.</span><span class="sxs-lookup"><span data-stu-id="a40cd-103">You can view changes tracked by a <xref:System.Data.Linq.DataContext> by using <xref:System.Data.Linq.DataContext.GetChangeSet%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a40cd-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a40cd-104">Example</span></span>  
 <span data-ttu-id="a40cd-105">Aşağıdaki örnek, müşterilerin, şehir Londra olduğundan, Paris için Şehir değiştirir ve değişiklikleri veritabanına geri gönderir alır.</span><span class="sxs-lookup"><span data-stu-id="a40cd-105">The following example retrieves customers whose city is London, changes the city to Paris, and submits the changes back to the database.</span></span>  
  
 [!code-csharp[DLinqDebuggingSupport#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#2)]
 [!code-vb[DLinqDebuggingSupport#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#2)]  
  
 <span data-ttu-id="a40cd-106">Bu kodun çıktısı aşağıdakine benzer görünür.</span><span class="sxs-lookup"><span data-stu-id="a40cd-106">Output from this code appears similar to the following.</span></span> <span data-ttu-id="a40cd-107">Son Özet sekiz değişiklikler yapıldı gösterdiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="a40cd-107">Note that the summary at the end shows that eight changes were made.</span></span>  
  
 `CustomerID: AROUT`  
  
 `Original value: London`  
  
 `Updated value: Paris`  
  
 `CustomerID: BSBEV`  
  
 `Original value: London`  
  
 `Updated value: Paris`  
  
 `CustomerID: CONSH`  
  
 `Original value: London`  
  
 `Updated value: Paris`  
  
 `CustomerID: EASTC`  
  
 `Original value: London`  
  
 `Updated value: Paris`  
  
 `CustomerID: NORTS`  
  
 `Original value: London`  
  
 `Updated value: Paris`  
  
 `CustomerID: PARIS`  
  
 `Original value: London`  
  
 `Updated value: Paris`  
  
 `CustomerID: SEVES`  
  
 `Original value: London`  
  
 `Updated value: Paris`  
  
 `CustomerID: SPECD`  
  
 `Original value: London`  
  
 `Updated value: Paris`  
  
 ``  
  
 `Total changes: {Added: 0, Removed: 0, Modified: 8}`  
  
## <a name="see-also"></a><span data-ttu-id="a40cd-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a40cd-108">See also</span></span>
- [<span data-ttu-id="a40cd-109">Hata Ayıklama Desteği</span><span class="sxs-lookup"><span data-stu-id="a40cd-109">Debugging Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)
