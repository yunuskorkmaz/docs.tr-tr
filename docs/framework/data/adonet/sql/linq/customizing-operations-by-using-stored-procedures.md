---
title: Saklı Yordamları Kullanarak İşlemleri Özelleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: aedbecc1-c33c-4fb4-8861-fdf7e1dc6b8a
ms.openlocfilehash: 93aa679e02482e5c237c233655ee19f3bae17fd3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59155954"
---
# <a name="customizing-operations-by-using-stored-procedures"></a>Saklı Yordamları Kullanarak İşlemleri Özelleştirme
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
