---
title: "Nasıl yapılır: veri gönderimleri işlemleri kullanarak köşeli ayraç"
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
ms.assetid: 94044a31-de90-479b-935a-8159b4ae5c5a
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a5d7f1e0b0419874f694a0b3953f6b037a777016
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a>Nasıl yapılır: veri gönderimleri işlemleri kullanarak köşeli ayraç
Kullanabileceğiniz <xref:System.Transactions.TransactionScope> veritabanına, gönderimlerini köşeli ayraç için. Daha fazla bilgi için bkz: [işlem desteği](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod veritabanı gönderisine kapsayan bir <xref:System.Transactions.TransactionScope>.  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Örnek Veritabanları İndirme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [Veri Değişiklikleri Yapma ve Gönderme](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [İşlem Desteği](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md)
