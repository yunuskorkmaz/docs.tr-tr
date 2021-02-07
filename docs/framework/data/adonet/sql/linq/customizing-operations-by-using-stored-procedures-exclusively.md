---
description: 'Hakkında daha fazla bilgi edinin: yalnızca saklı yordamları kullanarak Işlemleri özelleştirme'
title: Saklı Yordamları Özel Olarak Kullanarak İşlemleri Özelleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 441e8ef3-998c-4d12-8825-ce66a178f90f
ms.openlocfilehash: 4ddcc6b4face1abccb502e12617105a734bb5f0b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729555"
---
# <a name="customizing-operations-by-using-stored-procedures-exclusively"></a>Saklı Yordamları Özel Olarak Kullanarak İşlemleri Özelleştirme

Yalnızca saklı yordamlar kullanılarak verilere erişim, yaygın bir senaryodur.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Description  

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
