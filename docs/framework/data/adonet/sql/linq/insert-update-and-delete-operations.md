---
title: "INSERT, Update ve silme işlemleri"
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
ms.assetid: 26a43a4f-83c9-4732-806d-bb23aad0ff6b
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 51af1dad545f6ac948b17d1bdbd39bfc688c7f11
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="insert-update-and-delete-operations"></a>INSERT, Update ve silme işlemleri
Gerçekleştirdiğiniz `Insert`, `Update`, ve `Delete` işlemlerinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ekleyerek, değiştirerek ve nesne modelinde nesneleri kaldırılıyor. Varsayılan olarak, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] eylemlerinizi SQL dönüşür ve değişiklikler veritabanına gönderir.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]düzenleme ve, nesnelere yapılan değişiklikleri devam ettirmeden en büyük esnekliği sağlar. Varlık nesnesi (veya bunları bir sorgu aracılığıyla alarak mı başlatacağı oluşturma tarafından) kullanılabilir duruma geldiğinde, bunları uygulamanızda gibi tipik nesneleri değiştirebilirsiniz. Diğer bir deyişle, kendi değerlerini değiştirebilirsiniz, Koleksiyonlarınız için ekleyebilirsiniz ve, koleksiyonları kaldırabilirsiniz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]yaptığınız değişiklikleri izler ve çağırdığınızda bunları veritabanına aktarmak hazır <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]desteklemez veya art arda silme işlemleri algılar. Bu karşı kısıtlamalarına sahip bir tablosunda bir satırı silmek istiyorsanız, ayarlayın ya da gerekir `ON DELETE CASCADE` kural veritabanındaki yabancı anahtar kısıtlaması içinde ya da kendi kodunuzu ilk üst nesne silinmesini engellemek alt nesneleri silmek için kullanın. Aksi takdirde, bir özel durum oluşturulur. Daha fazla bilgi için bkz: [nasıl yapılır: Sil satırları veritabanından](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).  
  
 Aşağıdaki parçalarını kullanım `Customer` ve `Order` Northwind örnek veritabanı sınıflardan. Sınıf tanımları okumanızdır gösterilmez.  
  
 [!code-csharp[DLinqCRUDOps#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCRUDOps/cs/Program.cs#1)]
 [!code-vb[DLinqCRUDOps#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCRUDOps/vb/Module1.vb#1)]  
  
 Çağırdığınızda <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] otomatik olarak oluşturur ve değişikliklerinizi veritabanına aktarmak için gereken SQL komutlarını yürütür.  
  
> [!NOTE]
>  Saklı yordam yapmamanız genellikle kendi özel mantık kullanarak bu davranışı geçersiz kılabilirsiniz. Daha fazla bilgi için bkz: [Geliştirici içinde geçersiz kılma varsayılan davranışı sorumluluklarını](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md).  
>   
>  Kullanan geliştiriciler [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] kullanabilirsiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] bu amaç için saklı yordamlar geliştirilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Örnek Veritabanları İndirme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [Insert, Update ve Delete İşlemlerini Özelleştirme](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
