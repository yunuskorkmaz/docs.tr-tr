---
title: "Nasıl yapılır: .NET Framework'te Temel Dize İşlemeleri Gerçekleştirme"
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
ms.openlocfilehash: 1206648c694c9f09a600e3c70f4aa27118b2d458
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44178058"
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
