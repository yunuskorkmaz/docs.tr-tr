---
title: "Karma Kodlarla Veri Bütünlüğünü Sağlama"
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
helpviewer_keywords:
- generating hash
- verifying hash codes
- cryptography [.NET Framework], hash
- data integrity
- checking hash codes
- encryption [.NET Framework], hash
- hash
ms.assetid: 33660f33-b70f-4dca-8c87-ab35cfc2961a
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b5d54a608ae87a1b453b4fa2b4b351ac5fc9f068
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ensuring-data-integrity-with-hash-codes"></a>Karma Kodlarla Veri Bütünlüğünü Sağlama
Bir karma değer veri benzersiz olarak tanımlayan sabit uzunlukta sayısal bir değerdir. Dijital imzalarla kullanıldıkları şekilde karma değerleri büyük miktarlarda verinin çok daha küçük sayısal değerler olarak temsil eder. Bir karma değer daha büyük bir değer imzalama değerinden daha verimli bir şekilde oturum açabilir. Karma değerler, güvenli kanal gönderilen verilerin bütünlüğünü doğrulamak için yararlıdır. Veri değiştirilmiş olup olmadığını belirlemek için gönderildiği gibi alınan verilerin karma değerini verilerin karma değerini karşılaştırılabilir.  
  
 Bu konu, oluşturma ve sınıflarda kullanarak karma kodlarını doğrulama açıklar <xref:System.Security.Cryptography?displayProperty=nameWithType> ad alanı.  
  
## <a name="generating-a-hash"></a>Bir karma oluşturma  
 Yönetilen karma sınıfları bir bayt dizisi veya yönetilen stream nesnesi karma. Aşağıdaki örnek, bir dize için bir karma değer oluşturmak için SHA1 karma algoritmasını kullanır. Örnek kullanır <xref:System.Text.UnicodeEncoding> kullanarak karma bir bayt dizisi dize dönüştürmek için sınıf <xref:System.Security.Cryptography.SHA1Managed> sınıfı. Karma değer daha sonra konsola görüntülenir.  
  
 [!code-csharp[GeneratingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/generatingahash/cs/program.cs#1)]
 [!code-vb[GeneratingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/generatingahash/vb/program.vb#1)]  
  
 Bu kod, aşağıdaki dizeyi konsola görüntülenir:  
  
 `59 4 248 102 77 97 142 201 210 12 224 93 25 41 100 197 213 134 130 135`  
  
## <a name="verifying-a-hash"></a>Bir karma doğrulama  
 Veri bütünlüğünü belirlemek için bir karma değer karşılaştırılabilir. Genellikle, verileri belirli bir süre sonunda karma uygulanır ve karma değeri başka bir yolla korunur. Daha sonra verileri yeniden karma ve korumalı değerine karşılaştırılır. Karma değerleri eşleşirse, verileri değiştirilmediğini. Değerler eşleşmiyorsa, verileri bozuk. Bu sistemde çalışmak, korumalı karma şifrelenmiş veya tüm güvenilmeyen taraflardan gizli tutulur.  
  
 Aşağıdaki örnek yeni bir karma değeri dizeye önceki karma değerini karşılaştırır. Bu örnekte her karma değerleri bayt döngüler ve bir karşılaştırma yapar.  
  
 [!code-csharp[VerifyingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/verifyingahash/cs/program.cs#1)]
 [!code-vb[VerifyingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/verifyingahash/vb/program.vb#1)]  
  
 İki karma değerleri eşleşirse, bu kod konsola şunları görüntüler:  
  
```  
The hash codes match.  
```  
  
 Bunlar eşleşmiyorsa kod şunları görüntüler:  
  
```  
The hash codes do not match.  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md)
