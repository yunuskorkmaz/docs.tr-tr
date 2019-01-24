---
title: Saklı yordamları kullanarak işlemleri özelleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: aedbecc1-c33c-4fb4-8861-fdf7e1dc6b8a
ms.openlocfilehash: 91d74d1d72bb2a39c6b6d408839746c45ddad3db
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555524"
---
# <a name="customizing-operations-by-using-stored-procedures"></a>Saklı yordamları kullanarak işlemleri özelleştirme
Saklı yordamlar, varsayılan davranışı geçersiz kılma için yaygın bir yaklaşım temsil eder. Bu konuda show nasıl kullanabileceğiniz örnekler yöntemi sarmalayıcıları saklı yordamlar ve nasıl saklı yordamlar doğrudan çağırabilir miyim oluşturulur.  
  
 Visual Studio kullanıyorsanız, kullanabileceğiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] ekleme, güncelleştirme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama.  
  
> [!NOTE]
>  Geri veritabanı tarafından oluşturulan değerleri okumaya, saklı yordamlarınızı çıkış parametrelerini kullanın. Çıktı parametreleri kullanamıyorsanız, geçersiz kılmalar tarafından oluşturulan güvenmek yerine bir kısmi yöntem uygulaması yazma [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]. Veritabanı tarafından oluşturulan değerleri için eşlenmiş üyeleri ayarlayın, sonra uygun değerlere `INSERT` veya `UPDATE` işlemleri başarıyla tamamlandı. Daha fazla bilgi için [sorumlulukları geliştirici olarak geçersiz kılma varsayılan davranış](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md).  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnekte, varsayımında `Northwind` sınıf, türetilen bir sınıfta geçersiz kılmalar için kullanılan saklı yordamlar çağırmak için iki yöntem içerir.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DLinqOverrideDefaultSproc#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefaultSproc#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#1)]  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki sınıf geçersiz kılma için bu yöntemleri kullanır.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DLinqOverrideDefaultSproc#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefaultSproc#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#2)]  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Kullanabileceğiniz `NorthwindThroughSprocs` tam olarak kullanacağınız gibi `Northwnd`.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DLinqOverrideDefaultSproc#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefaultSproc#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Geliştiricinin Varsayılan Davranışı Geçersiz Kılma Sorumlulukları](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)
