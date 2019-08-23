---
title: Kısmi Yöntemler Kullanarak İş Mantığı Ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3a73991e-fd4e-4610-93fb-7ced4dc6b7f9
ms.openlocfilehash: e3f82c260a2cab85270a9f33a87eb9a9f04b72c7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964151"
---
# <a name="adding-business-logic-by-using-partial-methods"></a>Kısmi Yöntemler Kullanarak İş Mantığı Ekleme
C# Uygulamanızda[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Visual Basic ve üretilen kodu, *kısmi Yöntemler*kullanarak özelleştirebilirsiniz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Üreten kod, imzaları kısmi bir metodun bir parçası olarak tanımlar. Yöntemini uygulamak istiyorsanız, kendi kısmi yönteminizi ekleyebilirsiniz. Kendi uygulamanızı eklemeyin, derleyici kısmi Yöntemler imzasını atar ve içinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]varsayılan yöntemleri çağırır.  
  
> [!NOTE]
> Visual Studio kullanıyorsanız, varlık sınıflarına doğrulama ve diğer özelleştirmeler eklemek için Nesne İlişkisel Tasarımcısı kullanabilirsiniz.  
  
 Örneğin, Northwind örnek veritabanındaki `Customer` sınıfının varsayılan eşlemesi aşağıdaki kısmi yöntemi içerir:  
  
 [!code-csharp[DLinqOverrideDefault#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefault#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#2)]  
  
 Kendi kısmi `Customer` Sınıfınıza aşağıdaki gibi kod ekleyerek kendi yönteminizi uygulayabilirsiniz:  
  
 [!code-csharp[DLinqOverrideDefault#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefault#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/Module1.vb#3)]  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Bu yaklaşım genellikle, `Insert` `Update`nesne yaşam döngüsü olayları sırasında özellikleri doğrulamak için,,, ve için varsayılan yöntemleri geçersiz kılmak üzere ' de kullanılır. `Delete`  
  
 Daha fazla bilgi için bkz. [kısmi Yöntemler](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) (Visual Basic) veya [partial (Yöntem)C# (başvuru)](../../../../../csharp/language-reference/keywords/partial-method.md) (C#).  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, ilk `ExampleClass` olarak SqlMetal gibi kod oluşturma aracı tarafından tanımlandıkları ve sonra iki yöntemden yalnızca birini nasıl uygulayabileceğinizi gösterir.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DLinqSubmittingChanges#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#4)]
 [!code-vb[DLinqSubmittingChanges#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#4)]  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek ve `Shipper` `Order` varlıkları arasındaki ilişkiyi kullanır. Kısmi yöntemlerin `InsertShipper` ve `DeleteShipper`yöntemleri arasında aklınızda yer. Bu yöntemler, eşleme tarafından [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sağlanan varsayılan kısmi yöntemleri geçersiz kılar.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DLinqOverrideDefault#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefault#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Değişiklikleri Yapma ve Gönderme](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
- [Insert, Update ve Delete İşlemlerini Özelleştirme](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
