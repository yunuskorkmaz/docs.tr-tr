---
title: Karma Kodlarla Veri Bütünlüğünü Sağlama
description: .NET 'teki karma kodları kullanarak veri bütünlüğünü sağlama hakkında bilgi edinin. Karma değeri, verileri benzersiz bir şekilde tanımlayan sabit uzunlukta sayısal bir değerdir.
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- generating hash
- verifying hash codes
- cryptography [.NET], hash
- data integrity
- checking hash codes
- encryption [.NET], hash
- hash
ms.assetid: 33660f33-b70f-4dca-8c87-ab35cfc2961a
ms.openlocfilehash: 085a0ea387e3415e6e916bcdf9055ffaa6753fef
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94831097"
---
# <a name="ensuring-data-integrity-with-hash-codes"></a>Karma Kodlarla Veri Bütünlüğünü Sağlama
Karma değeri, verileri benzersiz bir şekilde tanımlayan sabit uzunlukta sayısal bir değerdir. Karma değerler, büyük miktarlarda veriyi çok daha küçük sayısal değerler halinde temsil eder, bu nedenle dijital imzalarla birlikte kullanılır. Karma değeri, daha büyük değeri imzalamadan daha verimli bir şekilde imzalayabilirsiniz. Karma değerleri, güvenli olmayan kanallar aracılığıyla gönderilen verilerin bütünlüğünü doğrulamak için de kullanışlıdır. Alınan verilerin karma değeri, verilerin değiştirilip değiştirilmediğini tespit etmek için gönderilen verilerin karma değeriyle karşılaştırılabilir.  
  
Bu konu, ad alanındaki sınıfları kullanarak karma kodların nasıl oluşturulacağını ve doğrulanacağını açıklamaktadır <xref:System.Security.Cryptography> .  
  
## <a name="generating-a-hash"></a>Karma oluşturma

 Yönetilen karma sınıflar bir bayt dizisini veya yönetilen bir akış nesnesini karma hale getirebilirsiniz. Aşağıdaki örnek, bir dize için bir karma değer oluşturmak üzere SHA1 karma algoritmasını kullanır. Örnek, sınıfını <xref:System.Text.UnicodeEncoding> kullanarak dizeyi karma bir bayt dizisine dönüştürmek için sınıfını kullanır <xref:System.Security.Cryptography.SHA256> . Karma değeri daha sonra konsola görüntülenir.  

 [!code-csharp[GeneratingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/generatingahash/cs/program.cs#1)]
 [!code-vb[GeneratingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/generatingahash/vb/program.vb#1)]  
  
 Bu kod konsola aşağıdaki dizeyi gösterir:  
  
 `185 203 236 22 3 228 27 130 87 23 244 15 87 88 14 43 37 61 106 224 81 172 224 211 104 85 194 197 194 25 120 217`  
  
## <a name="verifying-a-hash"></a>Karma doğrulama

 Verileri, bütünlüğünü tespit etmek için bir karma değerle karşılaştırılabilir. Genellikle, veriler belirli bir zamanda karma hale getirilir ve karma değeri bir şekilde korunur. Daha sonra veriler karma hale getirilir ve korunan değerle karşılaştırılır. Karma değerleri eşleşiyorsa, veriler değiştirilmez. Değerler eşleşmiyorsa, veriler bozulmuş demektir. Bu sistemin çalışması için korunan karmaların güvenilmeyen tüm taraflardan şifrelenmesi veya gizli tutulması gerekir.  
  
 Aşağıdaki örnek bir dizenin önceki karma değerini yeni bir karma değerle karşılaştırır. Bu örnek, karma değerlerin her baytında döngü yapar ve bir karşılaştırma yapar.  
  
 [!code-csharp[VerifyingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/verifyingahash/cs/program.cs#1)]
 [!code-vb[VerifyingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/verifyingahash/vb/program.vb#1)]  
  
 İki karma değer eşleşiyorsa, bu kod konsola aşağıdakileri gösterir:  
  
```console  
The hash codes match.  
```  
  
 Bunlar eşleşmiyorsa, kod aşağıdakileri görüntüler:  
  
```console  
The hash codes do not match.  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şifreleme Modeli](cryptography-model.md)
- [Şifreleme Hizmetleri](cryptographic-services.md)
- [Platformlar arası şifreleme](cross-platform-cryptography.md)
- [ASP.NET Core veri koruma](/aspnet/core/security/data-protection/introduction)
