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
ms.openlocfilehash: a0383dc3024352b9fac879532ab2789a60488c96
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331641"
---
# <a name="ensuring-data-integrity-with-hash-codes"></a>Karma Kodlarla Veri Bütünlüğünü Sağlama
Karma değeri, verileri benzersiz bir şekilde tanımlayan sabit uzunlukta sayısal bir değerdir. Karma değerler, büyük miktarlarda veriyi çok daha küçük sayısal değerler halinde temsil eder, bu nedenle dijital imzalarla birlikte kullanılır. Karma değeri, daha büyük değeri imzalamadan daha verimli bir şekilde imzalayabilirsiniz. Karma değerleri, güvenli olmayan kanallar aracılığıyla gönderilen verilerin bütünlüğünü doğrulamak için de kullanışlıdır. Alınan verilerin karma değeri, verilerin değiştirilip değiştirilmediğini tespit etmek için gönderilen verilerin karma değeriyle karşılaştırılabilir.  
  
 Bu konu, <xref:System.Security.Cryptography?displayProperty=nameWithType> ad alanındaki sınıfları kullanarak karma kodların nasıl oluşturulacağını ve doğrulanacağını açıklamaktadır.  
  
## <a name="generating-a-hash"></a>Karma oluşturma  
 Yönetilen karma sınıflar bir bayt dizisini veya yönetilen bir akış nesnesini karma hale getirebilirsiniz. Aşağıdaki örnek, bir dize için bir karma değer oluşturmak üzere SHA1 karma algoritmasını kullanır. Örnek, sınıfını <xref:System.Security.Cryptography.SHA1Managed> kullanarak <xref:System.Text.UnicodeEncoding> dizeyi karma bir bayt dizisine dönüştürmek için sınıfını kullanır. Karma değeri daha sonra konsola görüntülenir.  

 Microsoft, SHA1 ile ilgili çakışma sorunları nedeniyle SHA256 veya daha iyi bir performans öneriyor.
  
 [!code-csharp[GeneratingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/generatingahash/cs/program.cs#1)]
 [!code-vb[GeneratingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/generatingahash/vb/program.vb#1)]  
  
 Bu kod konsola aşağıdaki dizeyi gösterir:  
  
 `59 4 248 102 77 97 142 201 210 12 224 93 25 41 100 197 213 134 130 135`  
  
## <a name="verifying-a-hash"></a>Karma doğrulama  
 Verileri, bütünlüğünü tespit etmek için bir karma değerle karşılaştırılabilir. Genellikle, veriler belirli bir zamanda karma hale getirilir ve karma değeri bir şekilde korunur. Daha sonra veriler karma hale getirilir ve korunan değerle karşılaştırılır. Karma değerleri eşleşiyorsa, veriler değiştirilmez. Değerler eşleşmiyorsa, veriler bozulmuş demektir. Bu sistemin çalışması için korunan karmaların güvenilmeyen tüm taraflardan şifrelenmesi veya gizli tutulması gerekir.  
  
 Aşağıdaki örnek bir dizenin önceki karma değerini yeni bir karma değerle karşılaştırır. Bu örnek, karma değerlerin her baytında döngü yapar ve bir karşılaştırma yapar.  
  
 [!code-csharp[VerifyingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/verifyingahash/cs/program.cs#1)]
 [!code-vb[VerifyingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/verifyingahash/vb/program.vb#1)]  
  
 İki karma değer eşleşiyorsa, bu kod konsola aşağıdakileri gösterir:  
  
```  
The hash codes match.  
```  
  
 Bunlar eşleşmiyorsa, kod aşağıdakileri görüntüler:  
  
```  
The hash codes do not match.  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md)
