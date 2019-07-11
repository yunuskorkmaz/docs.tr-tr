---
title: Saklı Yordamları Kullanarak İşlemleri Özelleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: aedbecc1-c33c-4fb4-8861-fdf7e1dc6b8a
ms.openlocfilehash: d9f8d15b46f6e5575bd206bf572ffda0365e58f6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743556"
---
# <a name="customizing-operations-by-using-stored-procedures"></a>Saklı Yordamları Kullanarak İşlemleri Özelleştirme
Saklı yordamlar, varsayılan davranışı geçersiz kılma için yaygın bir yaklaşım temsil eder. Bu konuda show nasıl kullanabileceğiniz örnekler yöntemi sarmalayıcıları saklı yordamlar ve nasıl saklı yordamlar doğrudan çağırabilir miyim oluşturulur.  
  
 Visual Studio kullanıyorsanız, ekleme, güncelleştirme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama için Nesne İlişkisel Tasarımcısı'nı kullanabilirsiniz.  
  
> [!NOTE]
>  Geri veritabanı tarafından oluşturulan değerleri okumaya, saklı yordamlarınızı çıkış parametrelerini kullanın. Çıktı parametreleri kullanamıyorsanız, Nesne İlişkisel Tasarımcısı tarafından oluşturulan yazma güvenmek yerine bir kısmi yöntem uygulaması geçersiz kılar. Veritabanı tarafından oluşturulan değerleri için eşlenmiş üyeleri ayarlayın, sonra uygun değerlere `INSERT` veya `UPDATE` işlemleri başarıyla tamamlandı. Daha fazla bilgi için [sorumlulukları geliştirici olarak geçersiz kılma varsayılan davranış](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md).  
  
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
