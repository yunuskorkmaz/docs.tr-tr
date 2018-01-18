---
title: "Nasıl yapılır: bir değişiklik kümesini görüntüleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 126e7245-c5a0-4ebf-800d-cc1fcf9cd0ab
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f6de059f56318ed910f4583ba9618a5a20040ec7
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-display-a-changeset"></a><span data-ttu-id="74085-102">Nasıl yapılır: bir değişiklik kümesini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="74085-102">How to: Display a ChangeSet</span></span>
<span data-ttu-id="74085-103">Tarafından izlenen değişiklikleri görüntüleyebilirsiniz bir <xref:System.Data.Linq.DataContext> kullanarak <xref:System.Data.Linq.DataContext.GetChangeSet%2A>.</span><span class="sxs-lookup"><span data-stu-id="74085-103">You can view changes tracked by a <xref:System.Data.Linq.DataContext> by using <xref:System.Data.Linq.DataContext.GetChangeSet%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74085-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="74085-104">Example</span></span>  
 <span data-ttu-id="74085-105">Aşağıdaki örnek, şehir Londra olduğundan, Paris için Şehir değiştirir ve değişiklikleri veritabanına geri gönderir müşteriler alır.</span><span class="sxs-lookup"><span data-stu-id="74085-105">The following example retrieves customers whose city is London, changes the city to Paris, and submits the changes back to the database.</span></span>  
  
 [!code-csharp[DLinqDebuggingSupport#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#2)]
 [!code-vb[DLinqDebuggingSupport#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#2)]  
  
 <span data-ttu-id="74085-106">Bu kod çıktısı aşağıdakine benzer görünür.</span><span class="sxs-lookup"><span data-stu-id="74085-106">Output from this code appears similar to the following.</span></span> <span data-ttu-id="74085-107">Sonunda Özet sekiz değişikliklerin yapıldığı gösterdiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="74085-107">Note that the summary at the end shows that eight changes were made.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="74085-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="74085-108">See Also</span></span>  
 [<span data-ttu-id="74085-109">Hata Ayıklama Desteği</span><span class="sxs-lookup"><span data-stu-id="74085-109">Debugging Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)
