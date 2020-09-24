---
title: Saklı Yordamları Özel Olarak Kullanarak İşlemleri Özelleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 441e8ef3-998c-4d12-8825-ce66a178f90f
ms.openlocfilehash: 78db5cf448a19056d7265ab84d97d055748c3faa
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164330"
---
# <a name="customizing-operations-by-using-stored-procedures-exclusively"></a>Saklı Yordamları Özel Olarak Kullanarak İşlemleri Özelleştirme

Yalnızca saklı yordamlar kullanılarak verilere erişim, yaygın bir senaryodur.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  

 Saklı yordamları kullanarak, bir saklı yordamı sarmalayan ilk sorgu (dinamik SQL yürütmeye neden olur) bir yöntem çağrısıyla değiştirerek, [Işlemleri özelleştirme](customizing-operations-by-using-stored-procedures.md) bölümünde belirtilen örneği değiştirebilirsiniz.  
  
 `CustomersByCity`Aşağıdaki örnekte olduğu gibi yönteminin yöntemi olduğunu varsayalım.  
  
### <a name="code"></a>Kod  

 [!code-csharp[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#4)]
 [!code-vb[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#4)]  
  
 Aşağıdaki kod herhangi bir dinamik SQL olmadan yürütülür.  
  
 [!code-csharp[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#5)]
 [!code-vb[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Geliştiricinin Varsayılan Davranışı Geçersiz Kılma Sorumlulukları](responsibilities-of-the-developer-in-overriding-default-behavior.md)
