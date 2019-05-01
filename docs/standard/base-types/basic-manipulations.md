---
title: 'Nasıl yapılır: .NET içinde temel dize işlemeleri gerçekleştirme'
description: Birçok dize yöntemlerini çağıran bir örneğe bakın.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET Framework], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
author: rpetrusha
ms.author: ronpet
ms.custom: seodec18
ms.openlocfilehash: 11f8043745c631a642b437339240cbf06fc8df5b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62025944"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a>Nasıl yapılır: .NET içinde temel dize işlemeleri gerçekleştirme
Aşağıdaki örnek, bazı ele yöntemlerini kullanır [temel dize işlemleri](../../../docs/standard/base-types/basic-string-operations.md) dize işlemeleri gerçek bir uygulamada bulunan bir biçimde gerçekleştiren bir sınıf oluşturmak için konuları. `MailToData` Sınıf adını ve bireysel adresini ayrı özelliklerinde depolar ve birleştirmek için bir yol sağlar `City`, `State`, ve `Zip` alanlarına kullanıcıya görüntülemek için tek bir dize. Ayrıca, sınıfı tek bir dize olarak Şehir, eyalet ve posta kodu bilgilerini girmesini sağlar; Uygulama, otomatik olarak tek bir dizeyi ayrıştırır ve karşılık gelen özelliğine doğru bilgilerin girer.  
  
 Kolaylık olması için bu örnekte, bir komut satırı arabirimi ile bir konsol uygulaması kullanılmaktadır.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
 [!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
 Önceki kod yürütüldüğünde, kullanıcı adını ve adresini kendi girmesi istenir. Uygulama bilgileri uygun özellikler yerleştirir ve şehir, eyalet ve posta kodu bilgi görüntüler tek bir dize oluşturma geri kullanıcıya bilgi görüntüler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel Dize İşlemleri](../../../docs/standard/base-types/basic-string-operations.md)
