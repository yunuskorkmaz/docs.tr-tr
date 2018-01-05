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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fcede920b0e57dee0449d8ff6d7c935b177dcbcd
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="ensuring-data-integrity-with-hash-codes"></a><span data-ttu-id="a4188-102">Karma Kodlarla Veri Bütünlüğünü Sağlama</span><span class="sxs-lookup"><span data-stu-id="a4188-102">Ensuring Data Integrity with Hash Codes</span></span>
<span data-ttu-id="a4188-103">Bir karma değer veri benzersiz olarak tanımlayan sabit uzunlukta sayısal bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="a4188-103">A hash value is a numeric value of a fixed length that uniquely identifies data.</span></span> <span data-ttu-id="a4188-104">Dijital imzalarla kullanıldıkları şekilde karma değerleri büyük miktarlarda verinin çok daha küçük sayısal değerler olarak temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a4188-104">Hash values represent large amounts of data as much smaller numeric values, so they are used with digital signatures.</span></span> <span data-ttu-id="a4188-105">Bir karma değer daha büyük bir değer imzalama değerinden daha verimli bir şekilde oturum açabilir.</span><span class="sxs-lookup"><span data-stu-id="a4188-105">You can sign a hash value more efficiently than signing the larger value.</span></span> <span data-ttu-id="a4188-106">Karma değerler, güvenli kanal gönderilen verilerin bütünlüğünü doğrulamak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="a4188-106">Hash values are also useful for verifying the integrity of data sent through insecure channels.</span></span> <span data-ttu-id="a4188-107">Veri değiştirilmiş olup olmadığını belirlemek için gönderildiği gibi alınan verilerin karma değerini verilerin karma değerini karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="a4188-107">The hash value of received data can be compared to the hash value of data as it was sent to determine whether the data was altered.</span></span>  
  
 <span data-ttu-id="a4188-108">Bu konu, oluşturma ve sınıflarda kullanarak karma kodlarını doğrulama açıklar <xref:System.Security.Cryptography?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="a4188-108">This topic describes how to generate and verify hash codes by using the classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="generating-a-hash"></a><span data-ttu-id="a4188-109">Bir karma oluşturma</span><span class="sxs-lookup"><span data-stu-id="a4188-109">Generating a Hash</span></span>  
 <span data-ttu-id="a4188-110">Yönetilen karma sınıfları bir bayt dizisi veya yönetilen stream nesnesi karma.</span><span class="sxs-lookup"><span data-stu-id="a4188-110">The managed hash classes can hash either an array of bytes or a managed stream object.</span></span> <span data-ttu-id="a4188-111">Aşağıdaki örnek, bir dize için bir karma değer oluşturmak için SHA1 karma algoritmasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="a4188-111">The following example uses the SHA1 hash algorithm to create a hash value for a string.</span></span> <span data-ttu-id="a4188-112">Örnek kullanır <xref:System.Text.UnicodeEncoding> kullanarak karma bir bayt dizisi dize dönüştürmek için sınıf <xref:System.Security.Cryptography.SHA1Managed> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a4188-112">The example uses the <xref:System.Text.UnicodeEncoding> class to convert the string into an array of bytes that are hashed by using the <xref:System.Security.Cryptography.SHA1Managed> class.</span></span> <span data-ttu-id="a4188-113">Karma değer daha sonra konsola görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a4188-113">The hash value is then displayed to the console.</span></span>  
  
 [!code-csharp[GeneratingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/generatingahash/cs/program.cs#1)]
 [!code-vb[GeneratingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/generatingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="a4188-114">Bu kod, aşağıdaki dizeyi konsola görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="a4188-114">This code will display the following string to the console:</span></span>  
  
 `59 4 248 102 77 97 142 201 210 12 224 93 25 41 100 197 213 134 130 135`  
  
## <a name="verifying-a-hash"></a><span data-ttu-id="a4188-115">Bir karma doğrulama</span><span class="sxs-lookup"><span data-stu-id="a4188-115">Verifying a Hash</span></span>  
 <span data-ttu-id="a4188-116">Veri bütünlüğünü belirlemek için bir karma değer karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="a4188-116">Data can be compared to a hash value to determine its integrity.</span></span> <span data-ttu-id="a4188-117">Genellikle, verileri belirli bir süre sonunda karma uygulanır ve karma değeri başka bir yolla korunur.</span><span class="sxs-lookup"><span data-stu-id="a4188-117">Usually, data is hashed at a certain time and the hash value is protected in some way.</span></span> <span data-ttu-id="a4188-118">Daha sonra verileri yeniden karma ve korumalı değerine karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="a4188-118">At a later time, the data can be hashed again and compared to the protected value.</span></span> <span data-ttu-id="a4188-119">Karma değerleri eşleşirse, verileri değiştirilmediğini.</span><span class="sxs-lookup"><span data-stu-id="a4188-119">If the hash values match, the data has not been altered.</span></span> <span data-ttu-id="a4188-120">Değerler eşleşmiyorsa, verileri bozuk.</span><span class="sxs-lookup"><span data-stu-id="a4188-120">If the values do not match, the data has been corrupted.</span></span> <span data-ttu-id="a4188-121">Bu sistemde çalışmak, korumalı karma şifrelenmiş veya tüm güvenilmeyen taraflardan gizli tutulur.</span><span class="sxs-lookup"><span data-stu-id="a4188-121">For this system to work, the protected hash must be encrypted or kept secret from all untrusted parties.</span></span>  
  
 <span data-ttu-id="a4188-122">Aşağıdaki örnek yeni bir karma değeri dizeye önceki karma değerini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="a4188-122">The following example compares the previous hash value of a string to a new hash value.</span></span> <span data-ttu-id="a4188-123">Bu örnekte her karma değerleri bayt döngüler ve bir karşılaştırma yapar.</span><span class="sxs-lookup"><span data-stu-id="a4188-123">This example loops through each byte of the hash values and makes a comparison.</span></span>  
  
 [!code-csharp[VerifyingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/verifyingahash/cs/program.cs#1)]
 [!code-vb[VerifyingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/verifyingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="a4188-124">İki karma değerleri eşleşirse, bu kod konsola şunları görüntüler:</span><span class="sxs-lookup"><span data-stu-id="a4188-124">If the two hash values match, this code displays the following to the console:</span></span>  
  
```  
The hash codes match.  
```  
  
 <span data-ttu-id="a4188-125">Bunlar eşleşmiyorsa kod şunları görüntüler:</span><span class="sxs-lookup"><span data-stu-id="a4188-125">If they do not match, the code displays the following:</span></span>  
  
```  
The hash codes do not match.  
```  
  
## <a name="see-also"></a><span data-ttu-id="a4188-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a4188-126">See Also</span></span>  
 [<span data-ttu-id="a4188-127">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="a4188-127">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
