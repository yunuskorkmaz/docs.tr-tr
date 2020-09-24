---
title: Kısmi Yöntemler Kullanarak İş Mantığı Ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3a73991e-fd4e-4610-93fb-7ced4dc6b7f9
ms.openlocfilehash: 9ad3329c621b8bf8eaa0fd5f986ac7e8cff97d9e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156166"
---
# <a name="adding-business-logic-by-using-partial-methods"></a>Kısmi Yöntemler Kullanarak İş Mantığı Ekleme

Uygulamanızda Visual Basic ve C# tarafından üretilen kodu, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *kısmi Yöntemler*kullanarak özelleştirebilirsiniz. Üreten kod, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] imzaları kısmi bir metodun bir parçası olarak tanımlar. Yöntemini uygulamak istiyorsanız, kendi kısmi yönteminizi ekleyebilirsiniz. Kendi uygulamanızı eklemeyin, derleyici kısmi Yöntemler imzasını atar ve içinde varsayılan yöntemleri çağırır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .  
  
> [!NOTE]
> Visual Studio kullanıyorsanız, varlık sınıflarına doğrulama ve diğer özelleştirmeler eklemek için Nesne İlişkisel Tasarımcısı kullanabilirsiniz.  
  
 Örneğin, `Customer` Northwind örnek veritabanındaki sınıfının varsayılan eşlemesi aşağıdaki kısmi yöntemi içerir:  
  
 [!code-csharp[DLinqOverrideDefault#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefault#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#2)]  
  
 Kendi kısmi Sınıfınıza aşağıdaki gibi kod ekleyerek kendi yönteminizi uygulayabilirsiniz `Customer` :  
  
 [!code-csharp[DLinqOverrideDefault#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefault#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/Module1.vb#3)]  
  
 Bu yaklaşım genellikle [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Insert` , `Update` `Delete` nesne yaşam döngüsü olayları sırasında özellikleri doğrulamak için,,, ve için varsayılan yöntemleri geçersiz kılmak üzere ' de kullanılır.  
  
 Daha fazla bilgi için bkz. [kısmi Yöntemler](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) (Visual Basic) veya [partial (Yöntem) (c# başvurusu)](../../../../../csharp/language-reference/keywords/partial-method.md) (c#).  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  

 Aşağıdaki örnek, `ExampleClass` ilk olarak SQLMetal gibi kod oluşturma aracı tarafından tanımlandıkları ve sonra iki yöntemden yalnızca birini nasıl uygulayabileceğinizi gösterir.  
  
### <a name="code"></a>Kod  

 [!code-csharp[DLinqSubmittingChanges#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#4)]
 [!code-vb[DLinqSubmittingChanges#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#4)]  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  

 Aşağıdaki örnek ve varlıkları arasındaki ilişkiyi kullanır `Shipper` `Order` . Kısmi yöntemlerin ve yöntemleri arasında aklınızda yer `InsertShipper` `DeleteShipper` . Bu yöntemler, eşleme tarafından sağlanan varsayılan kısmi yöntemleri geçersiz kılar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .  
  
### <a name="code"></a>Kod  

 [!code-csharp[DLinqOverrideDefault#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefault#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Değişiklikleri Yapma ve Gönderme](making-and-submitting-data-changes.md)
- [Insert, Update ve Delete İşlemlerini Özelleştirme](customizing-insert-update-and-delete-operations.md)
