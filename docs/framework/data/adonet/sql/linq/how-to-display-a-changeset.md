---
title: 'Nasıl yapılır: Değişiklik kümesini görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 126e7245-c5a0-4ebf-800d-cc1fcf9cd0ab
ms.openlocfilehash: e6030a48a773dcf985eee5c4c113b02386780707
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55065823"
---
# <a name="how-to-display-a-changeset"></a>Nasıl yapılır: Değişiklik kümesini görüntüleme
Tarafından izlenen değişiklikleri görüntüleyebileceğiniz bir <xref:System.Data.Linq.DataContext> kullanarak <xref:System.Data.Linq.DataContext.GetChangeSet%2A>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, müşterilerin, şehir Londra olduğundan, Paris için Şehir değiştirir ve değişiklikleri veritabanına geri gönderir alır.  
  
 [!code-csharp[DLinqDebuggingSupport#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#2)]
 [!code-vb[DLinqDebuggingSupport#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#2)]  
  
 Bu kodun çıktısı aşağıdakine benzer görünür. Son Özet sekiz değişiklikler yapıldı gösterdiğine dikkat edin.  

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
  
## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklama Desteği](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)
