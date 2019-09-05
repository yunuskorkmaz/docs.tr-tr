---
title: Saklı Yordamları Kullanarak İşlemleri Özelleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: aedbecc1-c33c-4fb4-8861-fdf7e1dc6b8a
ms.openlocfilehash: 63f4cb3cbb90afc37629b336972b5e09d20346b3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247539"
---
# <a name="customizing-operations-by-using-stored-procedures"></a>Saklı Yordamları Kullanarak İşlemleri Özelleştirme
Saklı yordamlar, varsayılan davranışı geçersiz kılan yaygın bir yaklaşımı temsil eder. Bu konudaki örneklerde, saklı yordamlar için oluşturulan Yöntem sarmalayıcılarını nasıl kullanabileceğiniz ve saklı yordamları doğrudan nasıl çağırabilmeniz gösterilmektedir.  
  
 Visual Studio kullanıyorsanız, ekleme, güncelleştirme ve silme işlemlerini gerçekleştirmek için saklı yordamlar atamak üzere Nesne İlişkisel Tasarımcısı kullanabilirsiniz.  
  
> [!NOTE]
> Veritabanı tarafından oluşturulan değerleri geri okumak için, saklı yordamlarınızda çıkış parametrelerini kullanın. Çıkış parametrelerini kullanıdıysanız, Nesne İlişkisel Tasarımcısı tarafından oluşturulan geçersiz kılmalara güvenmek yerine kısmi bir yöntem uygulamasını yazın. Veritabanı tarafından oluşturulan değerlerle eşlenen üyelerin, veya `INSERT` `UPDATE` işlemler başarıyla tamamlandıktan sonra uygun değerlere ayarlanması gerekir. Daha fazla bilgi için, [varsayılan davranışı geçersiz kılan geliştiricinin sorumluluklarına](responsibilities-of-the-developer-in-overriding-default-behavior.md)bakın.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnekte, `Northwind` sınıfının türetilmiş bir sınıfta geçersiz Kılmalarda kullanılan saklı yordamları çağırmak için iki yöntem içerdiğini varsayın.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DLinqOverrideDefaultSproc#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefaultSproc#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#1)]  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki sınıf, geçersiz kılma için bu yöntemleri kullanır.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DLinqOverrideDefaultSproc#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefaultSproc#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#2)]  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Yalnızca kullandığınız `NorthwindThroughSprocs` `Northwnd`gibi kullanabilirsiniz.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DLinqOverrideDefaultSproc#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefaultSproc#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Geliştiricinin Varsayılan Davranışı Geçersiz Kılma Sorumlulukları](responsibilities-of-the-developer-in-overriding-default-behavior.md)
