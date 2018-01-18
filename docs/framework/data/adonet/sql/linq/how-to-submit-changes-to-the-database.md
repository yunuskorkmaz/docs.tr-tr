---
title: "Nasıl yapılır: Veritabanı değişiklikleri gönderme"
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
ms.assetid: c7cba174-9d40-491d-b32c-f2d73b7e9eab
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: bf1f9c7982cf9f328fe060266762658ab9693c2e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-submit-changes-to-the-database"></a>Nasıl yapılır: Veritabanı değişiklikleri gönderme
Nesnelerinizi kaç değişiklikler bağımsız olarak, değişiklikler yalnızca bellek içi çoğaltmalar için yapılır. Veritabanındaki gerçek veriler için herhangi bir değişiklik yaptınız. Açıkça çağrısı tamamlanana kadar değişiklikleriniz sunucusuna iletilmez <xref:System.Data.Linq.DataContext.SubmitChanges%2A> üzerinde <xref:System.Data.Linq.DataContext>.  
  
 Bu arama yaparken <xref:System.Data.Linq.DataContext> değişikliklerinizi eşdeğer SQL komutlarını içine çevirmek çalışır. Bu eylemler geçersiz kılmak için kendi özel mantık kullanabilirsiniz, ancak gönderme sırası bir hizmet tarafından düzenlenmiş <xref:System.Data.Linq.DataContext> olarak bilinen *işlemci değiştirmek*. Olayların sırası aşağıdaki gibidir:  
  
1.  Çağırdığınızda <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yeni örnekleri kendisine eklenmiş olan olup olmadığını belirlemek için bilinen nesne kümesini inceler. Varsa, bu yeni örnekler izlenen nesneler kümesine eklenir.  
  
2.  Bekleyen değişiklikleri bulunan tüm nesneleri aralarındaki bağımlılıkları temel nesneleri dizisini içine sıralanır. Değişiklikleri bağımlı nesneler üzerinde nesneleri bağımlılıklarını sonra sıralanamadı.  
  
3.  Gerçek değişiklikleri hemen iletilmeden önce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tekil komutlar dizi kapsülleyen bir işlem başlatır.  
  
4.  Nesnelere değişiklikler çevrilmiş tek tek SQL komutları ve sunucuya gönderilen.  
  
 Bu noktada, veritabanı tarafından algılanan tüm hataları gönderme işleminin vermemesine neden ve özel durum oluşturuldu. Veritabanında yapılan tüm değişiklikler geri hiçbir gönderimlerini sürekli olarak oluştuysa alınır. <xref:System.Data.Linq.DataContext> Tüm değişiklikleri tam kaydını sürdürüyor. Bu nedenle çağrısı ve sorunu düzeltmek deneyebilirsiniz <xref:System.Data.Linq.DataContext.SubmitChanges%2A> yeniden, aşağıdaki kod örneğinde olduğu gibi.  
  
## <a name="example"></a>Örnek  
 Gönderme işlemi başarıyla tamamlandığında, <xref:System.Data.Linq.DataContext> değişiklik izleme bilgilerini yoksayarak tarafından yapılan değişiklikleri nesneleri kabul eder.  
  
 [!code-csharp[DLinqSubmittingChanges#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#1)]
 [!code-vb[DLinqSubmittingChanges#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Çakışan Gönderimleri Algılama ve Çözümleme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-detect-and-resolve-conflicting-submissions.md)  
 [Nasıl yapılır: Değişiklik Çakışmalarını Yönetme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [Örnek Veritabanları İndirme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [Veri Değişiklikleri Yapma ve Gönderme](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
