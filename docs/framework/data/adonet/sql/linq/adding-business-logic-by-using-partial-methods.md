---
title: Kısmi yöntemler kullanarak iş mantığı ekleme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 3a73991e-fd4e-4610-93fb-7ced4dc6b7f9
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 8ea345f01c68f8c962069a3e9fdca7feff84c5c0
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="adding-business-logic-by-using-partial-methods"></a>Kısmi yöntemler kullanarak iş mantığı ekleme
Özelleştirebileceğiniz Visual Basic ve C# oluşturulan kodda, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kullanarak projeleri *kısmi yöntemler*. Kod, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] oluşturur imzaları kısmi yöntemi bir parçası olarak tanımlar. Yöntem uygulamak istiyorsanız, kısmi yönteminizi ekleyebilirsiniz. Kendi uygulama eklemezseniz derleyici kısmi yöntemler imza atar ve varsayılan yöntemlerini çağrıları [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
> [!NOTE]
>  Visual Studio kullanıyorsanız, kullanabileceğiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] doğrulama ve diğer özelleştirmeleri varlık sınıfları eklemek için.  
  
 Örneğin, varsayılan eşleme için `Customer` Northwind örnek veritabanı sınıfında aşağıdaki kısmi yöntemi içerir:  
  
 [!code-csharp[DLinqOverrideDefault#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefault#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#2)]  
  
 Kendi kısmi aşağıdaki gibi kod ekleyerek, kendi yönteminizi uygulayabileceğiniz `Customer` sınıfı:  
  
 [!code-csharp[DLinqOverrideDefault#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefault#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/Module1.vb#3)]  
  
 Bu yaklaşım genellikle kullanılan [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] için varsayılan yöntemleri geçersiz kılmak için `Insert`, `Update`, `Delete`ve nesne yaşam döngüsü olayları sırasında özellikleri doğrulanacak.  
  
 Daha fazla bilgi için bkz: [kısmi yöntemler](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md) (Visual Basic) veya [partial (yöntem) (C# Başvurusu)](~/docs/csharp/language-reference/keywords/partial-method.md) (C#).  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnekte gösterildiği `ExampleClass` ilk SQLMetal ve ardından iki yöntemlerden sadece birini nasıl uygulayabilir gibi bir kod oluşturma aracı tarafından tanımlanan.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DLinqSubmittingChanges#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#4)]
 [!code-vb[DLinqSubmittingChanges#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#4)]  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, arasındaki ilişkiyi kullanır `Shipper` ve `Order` varlıklar. Kısmi yöntemler yöntemleri arasından Not `InsertShipper` ve `DeleteShipper`. Bu yöntemleri tarafından sağlanan varsayılan kısmi yöntemlerini geçersiz kılın [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] eşleme.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DLinqOverrideDefault#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefault#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Değişiklikleri Yapma ve Gönderme](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [Insert, Update ve Delete İşlemlerini Özelleştirme](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
