---
title: Karma Kodlarla Veri Bütünlüğünü Sağlama
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16770ea938973372d1d94c628c42d5d5bf10c695
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44075591"
---
# <a name="ensuring-data-integrity-with-hash-codes"></a>Karma Kodlarla Veri Bütünlüğünü Sağlama
Bir karma değer veri benzersiz olarak tanımlayan sabit uzunlukta sayısal bir değerdir. Kullanıldıkları ile dijital imzalar için karma değerlerini büyük miktarlarda veri çok daha küçük sayısal değer olarak temsil eder. Bir karma değer değerinden daha büyük bir değer imzalama daha verimli bir şekilde oturum açabilirsiniz. Karma değerleri, güvenli kanal gönderilen verilerin bütünlüğünü doğrulamak için kullanışlıdır. Veri değiştirilmiş olup olmadığını belirlemek için gönderildiği gibi veri karma değeri için alınan veri karma değeri karşılaştırılabilir.  
  
 Bu konu, oluşturmak ve karma kodları sınıflarını kullanarak doğrulamak açıklar <xref:System.Security.Cryptography?displayProperty=nameWithType> ad alanı.  
  
## <a name="generating-a-hash"></a>Bir karma oluşturma  
 Yönetilen karma sınıflar, bir bayt dizisi ya da yönetilen akış nesnesi karma. Aşağıdaki örnek, bir dize için bir karma değer oluşturmak için SHA1 karma algoritmasını kullanır. Örnekte <xref:System.Text.UnicodeEncoding> kullanarak karma bir bayt dizisi dize dönüştürmek için sınıf <xref:System.Security.Cryptography.SHA1Managed> sınıfı. Karma değeri daha sonra konsolda görüntülenir.  
  
 [!code-csharp[GeneratingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/generatingahash/cs/program.cs#1)]
 [!code-vb[GeneratingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/generatingahash/vb/program.vb#1)]  
  
 Bu kod, konsola aşağıdaki dizeyi görüntülenir:  
  
 `59 4 248 102 77 97 142 201 210 12 224 93 25 41 100 197 213 134 130 135`  
  
## <a name="verifying-a-hash"></a>Bir karma değer doğrulanıyor  
 Veri bütünlüğünü belirlemek için bir karma değer karşılaştırılabilir. Genellikle, verileri belirli bir süre sonunda karma uygulanır ve karma değeri herhangi bir şekilde korunur. Daha sonra verileri yeniden karma ve korumalı değerine karşılaştırılır. Karma değerleri eşleşirse, veri değiştirilmediğinden. Değerler eşleşmiyorsa veriler bozulmuş. Bu sistem çalışmaya korumalı karma şifrelenmiş veya güvenilmeyen taraflardan gizli tutulduğundan.  
  
 Aşağıdaki örnek yeni bir karma değer dizeye önceki karma değerini karşılaştırır. Bu örnekte, karma değerleri ait her baytın döngüye girer ve bir karşılaştırma yapar.  
  
 [!code-csharp[VerifyingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/verifyingahash/cs/program.cs#1)]
 [!code-vb[VerifyingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/verifyingahash/vb/program.vb#1)]  
  
 Bu kod, iki karma değerleri eşleşirse, konsola aşağıdaki görüntüler:  
  
```  
The hash codes match.  
```  
  
 Bunlar eşleşmiyorsa, kod şunları görüntüler:  
  
```  
The hash codes do not match.  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md)
