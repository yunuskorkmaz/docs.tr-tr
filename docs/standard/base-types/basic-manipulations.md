---
title: .NET'te Temel Dize Manipülasyonları
description: Birçok dize yöntemi çağıran bir örneğe bakın.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET Framework], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
ms.openlocfilehash: 87ce7a79ce18ca8f5579841ad9e52e2519d6ac73
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187253"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a>Nasıl YapIlir: .NET'te Temel Dize Manipülasyonlarını Gerçekleştir

Aşağıdaki örnek, dize işlemelerini gerçek dünya uygulamasında bulunabilecek şekilde gerçekleştiren bir sınıf oluşturmak için [Temel Dize İşlemleri](../../../docs/standard/base-types/basic-string-operations.md) konularında tartışılan yöntemlerden bazılarını kullanır. `MailToData` Sınıf, bir bireyin adını ve adresini ayrı özelliklerde depolar `City` `State`ve `Zip` kullanıcıya görüntülenmek üzere , ve alanları tek bir dize halinde birleştirmenin bir yolunu sağlar. Ayrıca, sınıf kullanıcı nın şehir, eyalet ve Posta Kodu bilgilerini tek bir dize olarak girmesini sağlar; uygulama otomatik olarak tek dize parses ve ilgili özelliğine uygun bilgileri girer.  
  
Basitlik için bu örnek, komut satırı arabirimine sahip bir konsol uygulaması kullanır.  
  
## <a name="example"></a>Örnek  

[!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
[!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
Önceki kod yürütüldüğünde, kullanıcıdan ad larını ve adresini girmesi istenir. Uygulama bilgileri uygun özelliklere yerleştirir ve bilgileri kullanıcıya geri görüntüler ve şehir, eyalet ve Posta Kodu bilgilerini görüntüleyen tek bir dize oluşturur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel Dize İşlemleri](../../../docs/standard/base-types/basic-string-operations.md)
