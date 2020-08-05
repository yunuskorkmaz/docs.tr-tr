---
title: Karma Kodlarla Veri Bütünlüğünü Sağlama
description: .NET 'teki karma kodları kullanarak veri bütünlüğünü sağlama hakkında bilgi edinin. Karma değeri, verileri benzersiz bir şekilde tanımlayan sabit uzunlukta sayısal bir değerdir.
ms.date: 07/14/2020
ms.technology: dotnet-standard
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
ms.openlocfilehash: 3205e37f283cb205f5edfc5948a9cb9f7256f752
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556962"
---
# <a name="ensuring-data-integrity-with-hash-codes"></a><span data-ttu-id="00693-104">Karma Kodlarla Veri Bütünlüğünü Sağlama</span><span class="sxs-lookup"><span data-stu-id="00693-104">Ensuring Data Integrity with Hash Codes</span></span>
<span data-ttu-id="00693-105">Karma değeri, verileri benzersiz bir şekilde tanımlayan sabit uzunlukta sayısal bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="00693-105">A hash value is a numeric value of a fixed length that uniquely identifies data.</span></span> <span data-ttu-id="00693-106">Karma değerler, büyük miktarlarda veriyi çok daha küçük sayısal değerler halinde temsil eder, bu nedenle dijital imzalarla birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="00693-106">Hash values represent large amounts of data as much smaller numeric values, so they are used with digital signatures.</span></span> <span data-ttu-id="00693-107">Karma değeri, daha büyük değeri imzalamadan daha verimli bir şekilde imzalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00693-107">You can sign a hash value more efficiently than signing the larger value.</span></span> <span data-ttu-id="00693-108">Karma değerleri, güvenli olmayan kanallar aracılığıyla gönderilen verilerin bütünlüğünü doğrulamak için de kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="00693-108">Hash values are also useful for verifying the integrity of data sent through insecure channels.</span></span> <span data-ttu-id="00693-109">Alınan verilerin karma değeri, verilerin değiştirilip değiştirilmediğini tespit etmek için gönderilen verilerin karma değeriyle karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="00693-109">The hash value of received data can be compared to the hash value of data as it was sent to determine whether the data was altered.</span></span>  
  
<span data-ttu-id="00693-110">Bu konu, ad alanındaki sınıfları kullanarak karma kodların nasıl oluşturulacağını ve doğrulanacağını açıklamaktadır <xref:System.Security.Cryptography> .</span><span class="sxs-lookup"><span data-stu-id="00693-110">This topic describes how to generate and verify hash codes by using the classes in the <xref:System.Security.Cryptography> namespace.</span></span>  
  
## <a name="generating-a-hash"></a><span data-ttu-id="00693-111">Karma oluşturma</span><span class="sxs-lookup"><span data-stu-id="00693-111">Generating a Hash</span></span>

 <span data-ttu-id="00693-112">Yönetilen karma sınıflar bir bayt dizisini veya yönetilen bir akış nesnesini karma hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00693-112">The managed hash classes can hash either an array of bytes or a managed stream object.</span></span> <span data-ttu-id="00693-113">Aşağıdaki örnek, bir dize için bir karma değer oluşturmak üzere SHA1 karma algoritmasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="00693-113">The following example uses the SHA1 hash algorithm to create a hash value for a string.</span></span> <span data-ttu-id="00693-114">Örnek, sınıfını <xref:System.Text.UnicodeEncoding> kullanarak dizeyi karma bir bayt dizisine dönüştürmek için sınıfını kullanır <xref:System.Security.Cryptography.SHA256> .</span><span class="sxs-lookup"><span data-stu-id="00693-114">The example uses the <xref:System.Text.UnicodeEncoding> class to convert the string into an array of bytes that are hashed by using the <xref:System.Security.Cryptography.SHA256> class.</span></span> <span data-ttu-id="00693-115">Karma değeri daha sonra konsola görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="00693-115">The hash value is then displayed to the console.</span></span>  

 [!code-csharp[GeneratingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/generatingahash/cs/program.cs#1)]
 [!code-vb[GeneratingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/generatingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="00693-116">Bu kod konsola aşağıdaki dizeyi gösterir:</span><span class="sxs-lookup"><span data-stu-id="00693-116">This code will display the following string to the console:</span></span>  
  
 `185 203 236 22 3 228 27 130 87 23 244 15 87 88 14 43 37 61 106 224 81 172 224 211 104 85 194 197 194 25 120 217`  
  
## <a name="verifying-a-hash"></a><span data-ttu-id="00693-117">Karma doğrulama</span><span class="sxs-lookup"><span data-stu-id="00693-117">Verifying a Hash</span></span>

 <span data-ttu-id="00693-118">Verileri, bütünlüğünü tespit etmek için bir karma değerle karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="00693-118">Data can be compared to a hash value to determine its integrity.</span></span> <span data-ttu-id="00693-119">Genellikle, veriler belirli bir zamanda karma hale getirilir ve karma değeri bir şekilde korunur.</span><span class="sxs-lookup"><span data-stu-id="00693-119">Usually, data is hashed at a certain time and the hash value is protected in some way.</span></span> <span data-ttu-id="00693-120">Daha sonra veriler karma hale getirilir ve korunan değerle karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="00693-120">At a later time, the data can be hashed again and compared to the protected value.</span></span> <span data-ttu-id="00693-121">Karma değerleri eşleşiyorsa, veriler değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="00693-121">If the hash values match, the data has not been altered.</span></span> <span data-ttu-id="00693-122">Değerler eşleşmiyorsa, veriler bozulmuş demektir.</span><span class="sxs-lookup"><span data-stu-id="00693-122">If the values do not match, the data has been corrupted.</span></span> <span data-ttu-id="00693-123">Bu sistemin çalışması için korunan karmaların güvenilmeyen tüm taraflardan şifrelenmesi veya gizli tutulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="00693-123">For this system to work, the protected hash must be encrypted or kept secret from all untrusted parties.</span></span>  
  
 <span data-ttu-id="00693-124">Aşağıdaki örnek bir dizenin önceki karma değerini yeni bir karma değerle karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="00693-124">The following example compares the previous hash value of a string to a new hash value.</span></span> <span data-ttu-id="00693-125">Bu örnek, karma değerlerin her baytında döngü yapar ve bir karşılaştırma yapar.</span><span class="sxs-lookup"><span data-stu-id="00693-125">This example loops through each byte of the hash values and makes a comparison.</span></span>  
  
 [!code-csharp[VerifyingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/verifyingahash/cs/program.cs#1)]
 [!code-vb[VerifyingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/verifyingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="00693-126">İki karma değer eşleşiyorsa, bu kod konsola aşağıdakileri gösterir:</span><span class="sxs-lookup"><span data-stu-id="00693-126">If the two hash values match, this code displays the following to the console:</span></span>  
  
```console  
The hash codes match.  
```  
  
 <span data-ttu-id="00693-127">Bunlar eşleşmiyorsa, kod aşağıdakileri görüntüler:</span><span class="sxs-lookup"><span data-stu-id="00693-127">If they do not match, the code displays the following:</span></span>  
  
```console  
The hash codes do not match.  
```  
  
## <a name="see-also"></a><span data-ttu-id="00693-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00693-128">See also</span></span>

- [<span data-ttu-id="00693-129">Şifreleme Modeli</span><span class="sxs-lookup"><span data-stu-id="00693-129">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="00693-130">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="00693-130">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="00693-131">Platformlar arası şifreleme</span><span class="sxs-lookup"><span data-stu-id="00693-131">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="00693-132">ASP.NET Core veri koruma</span><span class="sxs-lookup"><span data-stu-id="00693-132">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
