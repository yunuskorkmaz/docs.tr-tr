---
title: "Nasıl yapılır: .NET Framework'te Temel Dize İşlemeleri Gerçekleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: strings [.NET Framework], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ee9c00d02b7b5d1f391ce60f843c18445efd6edc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a>Nasıl yapılır: .NET temel dize işlemeleri gerçekleştirme
Aşağıdaki örnek ele yöntemlerin bazıları kullanır [temel dize işlemleri](../../../docs/standard/base-types/basic-string-operations.md) konuları gerçek uygulamada bulunan bir şekilde dize işlemeleri gerçekleştiren bir sınıf oluşturun. `MailToData` Sınıf adını ve adresini tek bir ayrı özelliklerinde depolar ve birleştirmek için bir yol sağlar `City`, `State`, ve `Zip` alanlarına kullanıcıya görüntülenmesi için tek bir dize. Ayrıca, sınıfı tek bir dize Şehir, eyalet ve posta kodu bilgi girmek kullanıcı verir; uygulama otomatik olarak tek bir dize ayrıştırır ve karşılık gelen özelliği uygun bilgileri girer.  
  
 Kolaylık olması için bu örnek, bir komut satırı arabirimi ile bir konsol uygulaması kullanır.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
 [!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
 Önceki kod yürütüldüğünde, kullanıcının kendi adı veya adresi girmesi istenir. Uygulama bilgileri uygun özelliklerinde yerleştirir ve şehir, eyalet ve posta kodu bilgi görüntüler tek bir dize oluşturma geri kullanıcıya bilgi görüntüler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel dize işlemleri](../../../docs/standard/base-types/basic-string-operations.md)
